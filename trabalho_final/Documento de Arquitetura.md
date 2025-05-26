# Documento de Arquitetura de Software - Sistema de Bem-estar Corporativo

## 2. Requisitos Arquiteturalmente Significativos (ASRs)

Os Requisitos Arquiteturalmente Significativos são aqueles que têm impacto substancial nas decisões arquiteturais e na estrutura do sistema. Para o sistema de bem-estar corporativo, trataremos inicialmente dos requisitos funcionais de maior prioridade, seguidos pelos requisitos de qualidade que são arquiteturalmente significativos.

### 2.1 Requisitos Funcionais Prioritários

#### RF-01 (Prioridade Alta - ID 5): Feedback e Reportes Anônimos
O aplicativo deve incluir funcionalidade para que colaboradores possam dar feedbacks e reportar problemas de maneira anônima e segura. Este requisito impacta diretamente a arquitetura pela necessidade de mecanismos de anonimização, criptografia de dados sensíveis, e separação clara de responsabilidades para garantir privacidade.

#### RF-02 (Prioridade Alta - ID 9): Agendamento de Reuniões de Bem-estar  
O sistema deve permitir agendar reuniões que promovam bem-estar com participação de profissionais parceiros como psicólogos e especialistas. Requer integração com sistemas de calendário, gestão de usuários externos, e sistema de notificações.

#### RF-03 (Prioridade Média - ID 3): Consultas Virtuais
O sistema deve permitir marcação de consultas virtuais com especialistas em saúde e bem-estar. Necessita integração com plataformas de videoconferência e gestão de agendamentos.

#### RF-04 (Prioridade Média - ID 6): Recomendações Personalizadas
O sistema deve fornecer recomendações personalizadas baseadas no perfil de saúde e hábitos de trabalho. Requer motor de recomendação e análise de dados comportamentais básicos.

#### RF-05 (Prioridade Média - ID 10): Desafios Gamificados
O sistema deve permitir criar desafios de bem-estar com gamificação e reconhecimento. Necessita sistema de pontuação, rankings simples, e notificações.

### 2.2 Requisitos de Qualidade Arquiteturalmente Significativos

#### QA-01: Disponibilidade
- **Cenário**: Sistema disponível 99,5% do tempo durante horário comercial (8h às 18h)
- **Medida**: Máximo 2 horas de downtime por mês
- **Justificativa**: Permite implementar load balancer simples e replicação básica

#### QA-02: Confiabilidade  
- **Cenário**: Dados preservados mesmo em caso de falhas
- **Medida**: RPO (Recovery Point Objective) de 4 horas - backup automatizado a cada 4 horas, RTO (Recovery Time Objective) de 2 horas - sistema deve voltar a funcionar em no máximo 2 horas após qualquer falha
- **Justificativa**: Justifica backup automatizado diário sem complexidade excessiva

#### QA-03: Segurança
- **Cenário**: Proteção de dados pessoais e feedbacks anônimos
- **Medida**: Conformidade com LGPD, criptografia básica, autenticação segura
- **Justificativa**: Implementação de segurança em camadas

#### QA-04: Escalabilidade
- **Cenário**: Suporte de 500 para 5.000 usuários simultâneos
- **Medida**: Tempo de resposta máximo de 3 segundos para 95% das requisições
- **Justificativa**: Arquitetura preparada para crescimento com auto-scaling simples

---

## 3. Decisões Arquiteturais

Uma arquitetura pode ser vista como o resultado da aplicação de um conjunto de decisões de design, onde cada decisão impacta diretamente a capacidade do sistema de atender aos requisitos funcionais e de qualidade estabelecidos. Isto é, as decisões arquiteturais representam as escolhas fundamentais que moldam a estrutura, comportamento e qualidades do sistema.

Assim, esta seção documenta as principais decisões arquiteturais tomadas para atender aos ASRs identificados na seção anterior.

### 3.1 Alocação de Responsabilidades

Decidimos organizar o sistema em três microserviços principais que atendem diretamente aos requisitos funcionais. O **User Service** concentra todas as operações sensíveis de autenticação, autorização e gestão de perfis de usuário em um único ponto controlado.

O **Wellness Service** concentra as funcionalidades de bem-estar: feedbacks anônimos (RF-01), recomendações personalizadas (RF-04) e gamificação (RF-05). Esta decisão foi tomada considerando que estas funcionalidades compartilham dados comportamentais dos usuários e se beneficiam de processamento conjunto para gerar recomendações mais precisas.

O **Scheduling Service** gerencia agendamentos de consultas virtuais (RF-03) e reuniões com especialistas (RF-02). A separação deste serviço foi motivada pela necessidade de integração com sistemas externos como calendários e plataformas de videoconferência, isolando estas dependências externas dos demais domínios.

### 3.2 Modelo de Coordenação

A comunicação deve ser implementada predominantemente de forma síncrona via **REST APIs** para operações principais, atendendo ao requisito de escalabilidade (QA-04) através de simplicidade de implementação e debugging. Um **API Gateway simples** (nginx) serve como ponto de entrada único, implementando autenticação centralizada e rate limiting para suportar o crescimento de 500 para 5.000 usuários.

Esta decisão foi influenciada pelo requisito de feedbacks anônimos (RF-01), que necessita de controle rigoroso de acesso e auditoria, beneficiando-se de um ponto de entrada centralizado onde todas as requisições podem ser logadas e monitoradas adequadamente.

### 3.3 Modelo de Dados

Optamos por **PostgreSQL** como banco de dados principal para todos os serviços, simplificando operações e atendendo ao requisito de confiabilidade. Cada serviço possui seu próprio schema isolado, garantindo que falhas em um domínio não afetem outros. Esta escolha foi especificamente motivada pelo requisito de feedbacks anônimos (RF-01), que necessita de transações ACID para garantir que dados sensíveis sejam anonimizados atomicamente.

Além disso, também decidimos por usar o **Redis** que atua como cache para sessões de usuário e dados de recomendações frequentemente acessados (RF-04), melhorando performance e atendendo ao requisito de escalabilidade (QA-04) ao reduzir carga no banco principal durante picos de uso.

### 3.4 Gestão de Recursos

Decidimos pela implementação da containerização com **Docker** e orquestração via **Docker Compose** para simplificar deployment e gerenciamento. Esta decisão atende ao requisito de disponibilidade (QA-01) permitindo restart automático de containers e facilita escalonamento manual quando necessário para suportar crescimento de usuários.

Um **load balancer** (nginx) distribui requisições entre múltiplas instâncias dos serviços, atendendo diretamente aos requisitos de disponibilidade (QA-01) e escalabilidade (QA-04). Para confiabilidade (QA-02), configuramos backup automatizado diário do PostgreSQL, garantindo RPO de 4 horas conforme especificado.

### 3.5 Mapeamento entre Elementos Arquiteturais

Estruturamos deployment em três camadas claras: **nginx** como load balancer e entrada única, **três microserviços** (User, Wellness, Scheduling) como lógica de negócio, e **PostgreSQL + Redis** como camada de dados. Esta estrutura simples facilita compreensão e manutenção, atendendo indiretamente ao requisito de escalabilidade ao permitir escalonamento independente de cada camada.

### 3.6 Decisões de Binding Time

Decidimos por usarmos **variáveis de ambiente** e **arquivos de configuração** para parâmetros que podem necessitar ajustes, como URLs de integração externa para consultas virtuais (RF-03), algoritmos de recomendação (RF-04) e configurações de gamificação (RF-05). Esta flexibilidade permite ajustar comportamento do sistema sem redeploy, mantendo disponibilidade durante mudanças.

### 3.7 Escolha de Tecnologia

Optamos por **Java com Spring Boot** para microserviços, fornecendo Spring Security integrado que atende diretamente ao requisito de segurança (QA-03) e facilita implementação de anonimização para feedbacks (RF-01). **React** no frontend oferece interface responsiva necessária para boa experiência do usuário.

Dessa maneira, a combinação **PostgreSQL** + **Redis** + **Docker Compose** atende aos requisitos de qualidade, pois permite disponibilidade através de restart automático de containers, confiabilidade via backup automatizado, segurança através de isolamento de containers, e escalabilidade via múltiplas instâncias gerenciadas pelo compose. Esta escolha tecnológica mantém simplicidade operacional enquanto atende todos os requisitos funcionais e não funcionais identificados nesta primeira iteração.
