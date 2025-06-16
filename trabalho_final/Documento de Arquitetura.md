# Documento de Arquitetura de Software - Sistema de Bem-estar Corporativo

## 1. Visão Geral do Sistema

O sistema de bem-estar corporativo surge como resposta à crescente demanda por ambientes de trabalho mais saudáveis e humanizados. Em um cenário onde a produtividade está cada vez mais ligada ao equilíbrio emocional e à satisfação dos colaboradores, as organizações buscam soluções tecnológicas que promovam a saúde integral de seus times de forma mensurável.

Este sistema foi concebido como uma plataforma digital integrada, voltada ao fortalecimento do bem-estar no ambiente corporativo por meio de recursos que apoiam tanto a escuta ativa quanto a oferta de suporte personalizado. Seu escopo ultrapassa o simples monitoramento de indicadores de saúde, atuando também como instrumento de cultura organizacional positiva, transparência e valorização humana. 

### 1.1 Motivação e Justificativa

A saúde mental e o bem-estar no ambiente de trabalho deixaram de ser temas secundários para se tornarem pilares centrais da sustentabilidade organizacional. Pesquisas recentes apontam que ambientes tóxicos e a ausência de suporte emocional impactam diretamente nos índices de produtividade, absenteísmo, rotatividade e satisfação geral dos colaboradores.

A pandemia acelerou discussões sobre equilíbrio entre vida pessoal e profissional, evidenciando a necessidade de canais mais empáticos, flexíveis e orientados ao cuidado. Nesse cenário, organizações passaram a buscar soluções digitais que sejam mais do que simples ferramentas de RH — mas sim extensões da cultura organizacional voltadas ao bem-estar contínuo.

Justifica-se, portanto, o desenvolvimento deste sistema como uma resposta concreta à demanda por um espaço seguro e estruturado, onde colaboradores possam ser ouvidos, acolhidos e estimulados a manter hábitos mais saudáveis. Ao mesmo tempo, fornece aos gestores dados consistentes e mecanismos de apoio que promovem ambientes mais saudáveis, colaborativos e sustentáveis.

### 1.2 Objetivos Estratégicos

O sistema tem como metas principais:

- **Promover escuta ativa e segura**: viabilizar que colaboradores relatem sentimentos, situações e sugestões com anonimato e confiança.
- **Fortalecer ações de bem-estar corporativo**: facilitar o agendamento, gestão e avaliação de atividades como consultas, rodas de conversa e desafios coletivos.
- **Aumentar o engajamento e a satisfação**: estimular a participação dos colaboradores em iniciativas de saúde e qualidade de vida por meio de gamificação e recomendações personalizadas.
- **Gerar inteligência organizacional**: apoiar gestores com relatórios e insights sobre o clima organizacional e as principais demandas de bem-estar.
- **Facilitar integração com especialistas**: permitir que profissionais parceiros atuem diretamente na plataforma, mantendo a confidencialidade e o controle administrativo.
- **Reduzir custos indiretos com saúde**: ao antecipar questões críticas por meio de indicadores comportamentais e intervenções oportunas.

Estes objetivos sustentam uma abordagem holística e contínua do bem-estar corporativo, transformando-o em um processo estruturado e mensurável — e não apenas em ações pontuais ou campanhas isoladas.

O público-alvo principal são empresas de médio e grande porte que desejam implementar programas contínuos de bem-estar, com foco em prevenção, engajamento e melhoria do clima organizacional. Os usuários finais incluem colaboradores, gestores de RH, psicólogos organizacionais e consultores parceiros.

O sistema foi idealizado para operar como uma extensão natural da experiência do colaborador na empresa, sendo acessível tanto via desktop quanto dispositivos móveis, com interface intuitiva e adaptável a diferentes perfis de usuários. Além disso, seu modelo modular facilita a adoção progressiva por organizações que estejam em diferentes estágios de maturidade em relação ao bem-estar corporativo.

## 2. Requisitos Arquiteturalmente Significativos (ASRs)

Os Requisitos Arquiteturalmente Significativos (ASRs) são aqueles que têm impacto substancial nas decisões arquiteturais e na estrutura do sistema. Para o sistema de bem-estar corporativo, optamos por uma abordagem iterativa, **priorizando na primeira iteração os cinco requisitos com maior impacto funcional e arquitetural**, incluindo funcionalidades críticas do sistema. 

Na segunda iteração, foram incorporados os requisitos restantes, de prioridade média e baixa, voltados principalmente a funcionalidades complementares. Essa estratégia permitiu iniciar a construção da espinha dorsal do sistema com foco em segurança, escalabilidade e integração externa, enquanto recursos auxiliares foram planejados para uma segunda fase, com menor impacto arquitetural direto, mas alto valor para a experiência do usuário.

A seguir, os ASRs estão organizados por prioridade funcional, seguidos pelos requisitos de qualidade mais relevantes.

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

#### RF-06 (Prioridade Média - ID 2): Ofertas de Serviços Externos
O sistema deve ofertar uma grade de serviços externos aos colaboradores, como lazer, atividades físicas e auxílios fora do trabalho, com possibilidade de atualizações periódicas. Impacta a arquitetura ao exigir mecanismos de configuração dinâmica e gerenciamento de conteúdo externo por parte da organização. 

#### RF-07 (Prioridade Baixa - ID 1): Meditação e Técnicas de Respiração
O sistema deve fornecer opções de áudios/guias para meditação e técnicas de respiração. Exige uma estrutura de mídia leve e um serviço de streaming interno ou integração com plataformas externas. 

#### RF-08 (Prioridade Baixa - ID 4): Sugestões de Pausas com Base no Uso do Computador
O sistema deve oferecer sugestões personalizadas de pausas para alongamento ou relaxamento, com base no tempo de uso do computador. Requer a coleta de eventos de atividade do usuário, análise de contexto e envio de sugestões em tempo real.

#### RF-09 (Prioridade Baixa - ID 7): Dicas de Ergonomia para Home Office
O sistema deve oferecer dicas de ergonomia para o home office, como ajustar a cadeira, altura do monitor e outros elementos. Pode ser implementado com conteúdos estáticos configuráveis por perfil de usuário.

#### RF-10 (Prioridade Baixa - ID 8): Lembretes Personalizados de Hábitos Saudáveis
O sistema deve permitir que funcionários configurem lembretes personalizados para hábitos saudáveis (beber água, fazer pausas, ajustar postura). Implica um agendador interno, capaz de gerar notificações contextuais e personalizadas.

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

Para contemplar os novos requisitos, o **Wellness Service** será estendido para incluir a gestão de lembretes personalizados (RF-10), dicas de ergonomia (RF-09), conteúdos de meditação (RF-07) e sugestões de pausas (RF-08), já que essas funcionalidades compartilham o foco em saúde preventiva e hábitos saudáveis. Um novo módulo interno de "Conteúdo e Notificações" será adicionado a este serviço. A funcionalidade de grade de serviços externos (RF-06) será tratada por um Content Manager integrado ao mesmo serviço, que permitirá a atualização dinâmica desses conteúdos. Por fim, a funcionalidade de grade de serviços externos (RF-06) será tratada por um Content Manager integrado ao mesmo serviço, que permitirá a atualização dinâmica desses conteúdos. 

### 3.2 Modelo de Coordenação

A comunicação deve ser implementada predominantemente de forma síncrona via **REST APIs** para operações principais, atendendo ao requisito de escalabilidade (QA-04) através de simplicidade de implementação e debugging. Um **API Gateway simples** (nginx) serve como ponto de entrada único, implementando autenticação centralizada e rate limiting para suportar o crescimento de 500 para 5.000 usuários. Este API Gateway direcionará as requisições aos serviços correspondentes gerenciados pelo Docker Swarm. 

Esta decisão foi influenciada pelo requisito de feedbacks anônimos (RF-01), que necessita de controle rigoroso de acesso e auditoria, beneficiando-se de um ponto de entrada centralizado onde todas as requisições podem ser logadas e monitoradas adequadamente.

Para os lembretes e sugestões contextuais, o **Wellness Service** utilizará agendamento assíncrono por meio de tarefas periódicas internas (cron jobs ou scheduler do Spring), além de uma fila leve para envio de notificações. Os conteúdos estáticos (áudios, dicas, listas) serão servidos via endpoints REST e cacheados em Redis.

### 3.3 Modelo de Dados

Adotamos o PostgreSQL como banco de dados principal do sistema, com organização lógica por schemas independentes para cada microserviço, a fim de garantir isolamento, facilitar manutenção e aumentar a resiliência da arquitetura. Cada schema corresponde a um domínio funcional do sistema:

- user_data: contém entidades relacionadas à autenticação, perfis de usuário, sessões e permissões (User Service).

- scheduling_data: armazena agendamentos de reuniões, consultas, e integrações com calendário externo (Scheduling Service).

- wellness_data: reúne informações voltadas ao bem-estar, como feedbacks, recomendações, gamificação e conteúdos personalizados (Wellness Service).

Essa divisão foi escolhida para reduzir o acoplamento entre serviços, evitar conflitos de dados e garantir que falhas ou mudanças em um domínio não afetem os demais. Cada serviço é responsável por manter seu schema e acessá-lo exclusivamente.

Além disso, também decidimos por usar o **Redis** que atua como cache para sessões de usuário e dados de recomendações frequentemente acessados (RF-04), melhorando performance e atendendo ao requisito de escalabilidade (QA-04) ao reduzir carga no banco principal durante picos de uso.

### 3.4 Gestão de Recursos

Decidimos pela implementação da containerização com **Docker** e e orquestração via Docker Swarm para simplificar deployment e gerenciamento. O Docker Swarm permite a criação de um cluster de nós Docker, onde nossos serviços podem ser replicados e distribuídos. Portanto, esta decisão atende ao requisito de disponibilidade (QA-01) já que o Swarm pode automaticamente reagendar containers de serviços que falhem em um nó para outros nós saudáveis do cluster, minimizando o tempo de inatividade. Além disso, facilita o escalonamento (QA-04) manual ou automático dos serviços, permitindo aumentar o número de réplicas dos containers para lidar com o crescimento de usuários e picos de demanda, distribuindo a carga entre os nós do cluster.

Um load balancer (Nginx) atua como API Gateway/Reverse Proxy na borda, distribuindo requisições externas para os serviços do Docker Swarm. O routing mesh interno do Swarm balanceia automaticamente a carga entre múltiplas instâncias de cada serviço. Por fim, para confiabilidade (QA-02), configuramos backup automatizado diário do PostgreSQL, garantindo RPO de 4 horas conforme especificado.

### 3.5 Mapeamento entre Elementos Arquiteturais

Estruturamos deployment em três camadas claras: **Nginx** como API Gateway e ponto de entrada único (camada de borda), os **três microserviços** (User, Wellness, Scheduling) como lógica de negócio, gerenciados e orquestrados pelo **Docker Swarm** em um cluster de nós (camada de aplicação), e **PostgreSQL + Redis** como camada de dados. Esta estrutura simples facilita compreensão e manutenção do nosso sistema.

### 3.6 Decisões de Binding Time

Decidimos por usarmos **variáveis de ambiente** e **arquivos de configuração** para parâmetros que podem necessitar ajustes, como URLs de integração externa para consultas virtuais (RF-03), algoritmos de recomendação (RF-04) e configurações de gamificação (RF-05). Esta flexibilidade permite ajustar comportamento do sistema sem redeploy, mantendo disponibilidade durante mudanças.

### 3.7 Escolha de Tecnologia

Optamos por **Java com Spring Boot** para microserviços, fornecendo Spring Security integrado que atende diretamente ao requisito de segurança (QA-03) e facilita implementação de anonimização para feedbacks (RF-01). **React** no frontend oferece interface responsiva necessária para boa experiência do usuário.

Dessa maneira, a combinação **PostgreSQL + Redis + Docker Swarm** atende aos requisitos de qualidade, pois permite disponibilidade através de restart automático de containers, confiabilidade via backup automatizado, segurança através de isolamento de containers, e escalabilidade via múltiplas instâncias gerenciadas pelo Swarm. Esta escolha tecnológica mantém simplicidade operacional enquanto atende todos os requisitos funcionais e não funcionais identificados nesta primeira iteração.

---

# 4. Visões Arquiteturais

As visões arquiteturais representam diferentes perspectivas do sistema, cada uma focalizando aspectos específicos relevantes para diferentes stakeholders. Para o sistema de bem-estar corporativo, apresentamos quatro visões principais que capturam os elementos essenciais da arquitetura.

## 4.1 Visão de Módulos

A visão de módulos descreve como o sistema é estruturado em unidades de código e suas dependências. Esta visão é fundamental para desenvolvedores, arquitetos e gestores técnicos compreenderem a organização do código e planejarem atividades de desenvolvimento e manutenção.

### 4.1.1 Decomposição Modular

O sistema está organizado em uma arquitetura de microserviços com três módulos principais:

**User Service Module**
- Responsabilidades: Autenticação, autorização, gestão de perfis de usuário
- Justificativa: Centraliza operações sensíveis de segurança em um único ponto controlado
- Dependências: PostgreSQL (schema user_data), Redis (cache de sessões)

**Wellness Service Module**
- Responsabilidades: Feedbacks anônimos, recomendações personalizadas, gamificação
- Justificativa: Agrupa funcionalidades que compartilham dados comportamentais dos usuários
- Dependências: PostgreSQL (schema wellness_data), Redis (cache de recomendações)

**Scheduling Service Module**
- Responsabilidades: Agendamento de consultas virtuais e reuniões com especialistas
- Justificativa: Isola integrações externas (calendários, videoconferência) dos demais domínios
- Dependências: PostgreSQL (schema scheduling_data), APIs externas de calendário

### 4.1.2 Módulos de Infraestrutura

**Gateway Module**
- Implementação: nginx como reverse proxy
- Responsabilidades: Roteamento, autenticação centralizada, rate limiting
- Justificativa: Ponto único de entrada que facilita monitoramento e controle de acesso

**Data Layer Module**
- PostgreSQL: Armazenamento persistente com schemas isolados por serviço
- Redis: Cache distribuído para sessões e dados frequentemente acessados

## 4.2 Visão de Componentes e Conectores

Esta visão descreve elementos em tempo de execução e suas interações, sendo essencial para compreender o comportamento dinâmico do sistema e fluxos de dados.

### 4.2.1 Componentes Principais

**API Gateway Component**
- Tipo: Proxy/Load Balancer
- Responsabilidades: Distribuição de carga, autenticação inicial, logging
- Interfaces: HTTP REST (entrada), HTTP REST (saída para microserviços)

**User Service Component**
- Tipo: Microserviço
- Responsabilidades: Gestão de identidade, autorização baseada em roles
- Interfaces: REST API (entrada), Database Connection (PostgreSQL), Cache Connection (Redis)

**Wellness Service Component**
- Tipo: Microserviço
- Responsabilidades: Processamento de feedbacks anônimos, engine de recomendações, sistema de pontuação
- Interfaces: REST API (entrada), Database Connection (PostgreSQL), Cache Connection (Redis)

**Scheduling Service Component**
- Tipo: Microserviço
- Responsabilidades: Gestão de agendamentos, integração com sistemas externos
- Interfaces: REST API (entrada), Database Connection (PostgreSQL), External API Connector

### 4.2.2 Conectores e Fluxos de Dados

**Fluxo de Feedback Anônimo (RF-01)**
1. Cliente → API Gateway (HTTPS)
2. API Gateway → User Service (autenticação)
3. API Gateway → Wellness Service (processamento anônimo)
4. Wellness Service → PostgreSQL (armazenamento criptografado)

**Fluxo de Recomendações Personalizadas (RF-04)**
1. Cliente → API Gateway → Wellness Service
2. Wellness Service → Redis (verificação de cache)
3. Se não cached: Wellness Service → PostgreSQL (análise de dados)
4. Wellness Service → Redis (cache do resultado)
5. Retorno da recomendação ao cliente

## 4.3 Visão de Alocação

A visão de alocação mapeia elementos de software para elementos do ambiente de execução, sendo crucial para deployment, operação e gestão de recursos.

### 4.3.1 Deployment Architecture

**Container Layer**
- nginx-gateway: Container para API Gateway e load balancing
- user-service: Container para User Service (múltiplas instâncias)
- wellness-service: Container para Wellness Service (múltiplas instâncias)
- scheduling-service: Container para Scheduling Service (múltiplas instâncias)

**Data Layer**
- postgresql-primary: Container principal do PostgreSQL
- postgresql-replica: Container de réplica para leitura (backup)
- redis-cache: Container para cache distribuído

**Orquestração**
- Docker Compose: Gerenciamento de containers e redes
- Configuração de restart automático para atender QA-01 (Disponibilidade)
- Health checks para monitoramento contínuo

### 4.3.2 Network Architecture

**Internal Network (Docker Network)**
- Comunicação entre microserviços via rede interna isolada
- PostgreSQL e Redis acessíveis apenas internamente
- DNS interno para resolução de nomes de serviços

**External Network**
- API Gateway exposto na porta 80/443
- Conexões externas apenas via HTTPS
- Rate limiting configurado no gateway

## 4.4 Visão de Informação

Esta visão descreve a estrutura e fluxo dos dados no sistema, essencial para compreender como as informações são capturadas, processadas e armazenadas.

### 4.4.1 Modelo de Dados Conceitual

**Domínio de Usuários**
- Entidades: User, Profile, Role, Session
- Dados sensíveis: Email, nome, departamento
- Anonimização: Hash irreversível para feedbacks

**Domínio de Bem-estar**
- Entidades: Feedback (anônimo), Recommendation, Challenge, UserActivity
- Dados comportamentais: Participação em atividades, pontuação, progresso
- Agregações: Métricas de engajamento, indicadores de clima organizacional

**Domínio de Agendamentos**
- Entidades: Appointment, Specialist, Calendar, Notification
- Integrações: Dados de calendário externo, links de videoconferência
- Histórico: Registros de consultas para relatórios de utilização

### 4.4.2 Fluxos de Informação Críticos

**Anonimização de Feedbacks**
1. Captura: Dados identificáveis temporariamente associados
2. Processamento: Aplicação de hash criptográfico irreversível
3. Armazenamento: Apenas dados anonimizados são persistidos
4. Auditoria: Log de operações sem dados pessoais

**Geração de Recomendações**
1. Coleta: Dados comportamentais agregados (não identificáveis)
2. Análise: Algoritmos de machine learning básicos para padrões
3. Personalização: Matching com perfil de usuário via identificadores hasheados
4. Entrega: Recomendações contextualizadas via API

# 5. Táticas e Padrões Aplicados

As táticas arquiteturais são abordagens específicas para atingir atributos de qualidade, enquanto os padrões são soluções comprovadas para problemas recorrentes. Esta seção documenta como estas técnicas foram aplicadas no sistema de bem-estar corporativo.

## 5.1 Táticas para Disponibilidade

### 5.1.1 Detecção de Falhas

**Health Checks Automáticos**
- Implementação: Endpoints `/health` em todos os microserviços
- Frequência: Monitoramento a cada 30 segundos via Docker Compose
- Ação: Restart automático de containers com falha
- Atende: QA-01 (Disponibilidade de 99,5%)

**Heartbeat Monitoring**
- Implementação: Logs estruturados com timestamps para rastreamento
- Escopo: Todas as operações críticas (autenticação, feedbacks, agendamentos)
- Benefício: Detecção proativa de degradação de performance

### 5.1.2 Recuperação de Falhas

**Restart Automático**
- Configuração: Docker Compose com política `restart: always`
- Timeout: 30 segundos para restart de containers com falha
- Escalonamento: Aumento automático de recursos durante picos

**Circuit Breaker Pattern**
- Implementação: Spring Boot Actuator para monitoramento de integrações externas
- Escopo: Comunicação com APIs de calendário e videoconferência (RF-03)
- Fallback: Agendamento manual quando APIs externas estão indisponíveis

### 5.1.3 Prevenção de Falhas

**Load Balancing**
- Implementação: nginx upstream com algoritmo round-robin
- Escopo: Distribuição entre múltiplas instâncias de cada microserviço
- Benefício: Evita sobrecarga de instâncias individuais

**Rate Limiting**
- Configuração: 1000 requests/minuto por IP no API Gateway
- Proteção: Previne ataques DDoS e uso abusivo
- Graceful Degradation: Respostas HTTP 429 com retry-after headers

## 5.2 Táticas para Confiabilidade

### 5.2.1 Detecção de Erros

**Logging Estruturado**
- Implementação: SLF4J com Logback em formato JSON
- Níveis: ERROR para falhas críticas, WARN para degradações, INFO para auditoria
- Correlação: Request ID único para rastreamento end-to-end

**Data Validation**
- Bean Validation (JSR-303) para validação de entrada
- Sanitização de dados antes do processamento
- Verificação de integridade referencial no banco de dados

### 5.2.2 Recuperação de Erros

**Database Backup Strategy**
- Frequência: Backup completo diário, logs transacionais a cada 4 horas
- RPO: 4 horas conforme QA-02
- RTO: 2 horas com restore automatizado
- Armazenamento: Múltiplas versões com rotação de 30 dias

**Transaction Management**
- Spring @Transactional para operações atômicas
- Rollback automático em caso de falhas
- Idempotência em operações críticas (feedbacks, agendamentos)

### 5.2.3 Prevenção de Erros

**Input Sanitization**
- Validação rigorosa de todos os inputs do usuário
- Escape de caracteres especiais para prevenir injection attacks
- Limites de tamanho para campos de texto livre

**Database Constraints**
- Chaves primárias e estrangeiras para integridade referencial
- Check constraints para validação de dados
- Unique constraints para prevenir duplicação

## 5.3 Táticas para Segurança

### 5.3.1 Resistir a Ataques

**Authentication & Authorization**
- JWT tokens com expiração de 1 hora
- Refresh tokens com rotação automática
- Role-based access control (RBAC) implementado via Spring Security

**Data Encryption**
- HTTPS obrigatório para todas as comunicações
- AES-256 para dados sensíveis em repouso
- Hash irreversível (SHA-256 + salt) para anonimização de feedbacks

### 5.3.2 Detectar Ataques

**Audit Logging**
- Log de todas as operações de autenticação
- Rastreamento de acessos a dados sensíveis
- Monitoramento de padrões anômalos de uso

**Rate Limiting Inteligente**
- Limites diferenciados por tipo de operação
- Bloqueio temporário por IP suspeito
- Alertas automáticos para administradores

### 5.3.3 Recuperar de Ataques

**Session Management**
- Invalidação automática de sessões comprometidas
- Logout forçado em caso de atividade suspeita
- Notificação ao usuário sobre acessos não autorizados

## 5.4 Táticas para Escalabilidade

### 5.4.1 Gerenciar Recursos

**Caching Strategy**
- Redis para cache de sessões (TTL: 1 hora)
- Cache de recomendações personalizadas (TTL: 24 horas)
- Cache de dados estáticos (configurações, listas de especialistas)

**Connection Pooling**
- HikariCP para pooling de conexões PostgreSQL
- Configuração: 10 conexões por instância de microserviço
- Timeout: 30 segundos para evitar bloqueios

### 5.4.2 Gerenciar Demanda

**Horizontal Scaling**
- Docker Compose configurado para múltiplas instâncias
- Auto-scaling manual baseado em métricas de CPU e memória
- Load balancing automático via nginx

**Data Partitioning**
- Particionamento por schema no PostgreSQL
- Separação de dados por microserviço
- Índices otimizados para queries frequentes

## 5.5 Padrões Arquiteturais Aplicados

### 5.5.1 Microservices Pattern

**Implementação**
- Decomposição por domínio de negócio (User, Wellness, Scheduling)
- Comunicação via REST APIs
- Banco de dados independente por serviço

**Benefícios Realizados**
- Desenvolvimento independente por equipes
- Deploy independente de cada serviço
- Escalabilidade granular por funcionalidade

### 5.5.2 API Gateway Pattern

**Implementação**
- nginx como reverse proxy e load balancer
- Centralização de concerns transversais (autenticação, logging, rate limiting)
- Roteamento baseado em path para microserviços

**Benefícios Realizados**
- Ponto único de entrada para clientes
- Simplificação de configuração de segurança
- Monitoramento centralizado de tráfego

### 5.5.3 Database per Service Pattern

**Implementação**
- PostgreSQL com schemas isolados
- Sem compartilhamento de tabelas entre serviços
- Comunicação via APIs quando necessário dados de outros domínios

**Benefícios Realizados**
- Evolução independente de modelos de dados
- Isolamento de falhas entre domínios
- Flexibilidade tecnológica por serviço

### 5.5.4 Layered Architecture Pattern

**Implementação dentro de cada Microserviço**
- Controller Layer: REST endpoints e validação de entrada
- Service Layer: Lógica de negócio e orquestração
- Repository Layer: Abstração de acesso a dados
- Entity Layer: Modelo de domínio

**Benefícios Realizados**
- Separação clara de responsabilidades
- Facilidade de testes unitários por camada
- Manutenibilidade e evolução controlada

### 5.5.5 Repository Pattern

**Implementação**
- Spring Data JPA para abstração de acesso a dados
- Interfaces específicas por entidade de domínio
- Implementação automática via Spring Boot

**Benefícios Realizados**
- Testabilidade através de mocks
- Flexibilidade para mudança de tecnologia de persistência
- Queries otimizadas e type-safe

# 6. Análise de Qualidade 

Esta seção avalia como as decisões arquiteturais adotadas contribuem para alcançar os atributos de qualidade priorizados para o sistema, considerando aspectos como disponibilidade, confiabilidade, segurança, escalabilidade, manutenibilidade e desempenho. A análise é baseada na estrutura arquitetural proposta, nas táticas e padrões aplicados e nas necessidades explícitas dos stakeholders.

## 6.1 Métricas e Critérios de Aceitação

| Atributo         | Métrica / Critério de Aceitação                                             | 
|------------------|-----------------------------------------------------------------------------|
| Disponibilidade  | ≥ 99,5% de uptime mensal                                                    | 
| Confiabilidade   | Taxa de falhas < 1% em transações críticas                                  |
| Segurança        | 100% das requisições autenticadas e autorizadas corretamente                | 
| Escalabilidade   | Capacidade de atender a picos 10x a carga média sem degradação significativa| 

## 6.2 Disponibilidade

A arquitetura emprega múltiplas táticas voltadas à disponibilidade, demonstrando um compromisso claro com a meta de 99,5% definida pela QA-01. A presença de *health checks* automáticos, combinada com a política de reinício automático de containers, contribui significativamente para a detecção e recuperação ágil de falhas. Além disso, o uso de um gateway central com *rate limiting* protege o sistema contra sobrecargas e ataques externos, mitigando riscos de indisponibilidade.

A segmentação dos serviços em containers independentes, orquestrados por Docker Compose, permite substituições rápidas e minimamente invasivas em caso de falhas, reforçando o princípio de tolerância a falhas. A redundância de dados, com réplica do banco PostgreSQL, contribui ainda mais para a disponibilidade contínua dos serviços críticos.

As táticas selecionadas cobrem as três dimensões principais da disponibilidade: detecção, recuperação e prevenção de falhas. Essas práticas, em conjunto, sustentam a meta de disponibilidade geral, limitando o impacto de falhas parciais ou intermitentes.

## 6.3 Confiabilidade

A confiabilidade do sistema é reforçada por práticas rigorosas de validação e gestão de transações. A adoção de validações em nível de entrada, *constraints* no banco de dados e *logging* estruturado com correlação de requisições assegura rastreabilidade e integridade dos dados.

O uso extensivo de operações transacionais (`@Transactional`), *rollback* automático e idempotência em operações críticas (como envio de feedbacks) aumenta a previsibilidade do comportamento do sistema frente a falhas parciais. A política de backup com RPO e RTO claramente definidos mostra preocupação concreta com a recuperação segura de dados, alinhando-se com as expectativas de continuidade operacional.

As táticas adotadas para confiabilidade reforçam o controle sobre erros e a recuperação segura de estados consistentes. A confiabilidade do sistema é ainda reforçada por restrições no banco de dados, que atuam como linha de defesa adicional para a integridade de dados.

## 6.4 Segurança

A arquitetura demonstra maturidade na abordagem de segurança, cobrindo prevenção, detecção e resposta a incidentes. A combinação de autenticação JWT, controle de acesso baseado em papéis (RBAC), criptografia em repouso com AES-256 e anonimização com *hash* salgado evidencia uma preocupação explícita com dados sensíveis — particularmente relevantes no contexto de saúde e bem-estar.

Além disso, a centralização da autenticação no gateway, associada à segmentação de redes e restrição de acesso interno aos bancos de dados, mitiga a superfície de ataque. A presença de mecanismos de *audit logging* e bloqueios automáticos por IP suspeito mostra um compromisso real com a segurança em tempo de execução e conformidade com boas práticas de LGPD.

A arquitetura adota um conjunto robusto de táticas para lidar com ameaças e que tornam o sistema resiliente frente a ameaças internas e externas, promovendo segurança como um pilar fundamental do design.

## 6.5 Escalabilidade

A arquitetura proposta é altamente escalável, tanto em termos horizontais quanto verticais. A decomposição em microserviços permite escalar apenas os módulos com maior demanda, como o `Wellness Service`, sem impacto nos demais. O uso de cache com Redis para dados de sessão e recomendações personalizadas reduz a pressão sobre o banco de dados e melhora a resposta sob carga.

O gateway baseado em Nginx com balanceamento de carga *round-robin* e suporte a múltiplas instâncias dos serviços garante uma distribuição eficiente da carga. O modelo de dados com particionamento lógico por *schema* reforça a separação de responsabilidades e facilita ajustes finos no desempenho de *queries* críticas.

A arquitetura está bem preparada para escalar horizontal e verticalmente por meio de técnicas bem estabelecidas que garantem resposta eficiente mesmo sob crescimento contínuo da base de usuários e volume de dados.

## 6.6 Testabilidade

A arquitetura proposta favorece significativamente a testabilidade do sistema, especialmente por adotar uma abordagem baseada em microserviços com responsabilidades bem definidas. A independência entre os módulos permite a realização de testes unitários de forma isolada, utilizando técnicas como mocks e stubs para simular dependências externas. Além disso, a comunicação entre serviços por meio de APIs REST padronizadas facilita a implementação de testes automatizados de integração com ferramentas como Postman, Jest ou Testcontainers.

No entanto, alguns riscos precisam ser considerados, como a falta de cobertura em testes end-to-end, o que pode resultar em falhas não detectadas nas interações entre serviços. Outro ponto de atenção são os ambientes inconsistentes para testes, que podem comprometer a confiabilidade dos resultados dos testes automatizados. Para mitigar esses riscos, recomenda-se a criação de ambientes de staging que espelhem a produção, bem como a adoção de pipelines de integração contínua que incluam a execução automatizada de testes unitários e de integração.

As decisões arquiteturais que contribuem diretamente para a testabilidade incluem a definição de interfaces REST bem documentadas e a separação da lógica de negócio em camadas específicas, o que facilita a criação de testes mais precisos e reutilizáveis. Conclui-se, portanto, que a arquitetura é altamente testável, oferecendo suporte adequado tanto para testes automatizados quanto para práticas de entrega contínua com maior segurança.

## 6.7 Considerações Finais

A arquitetura avaliada apresenta boa aderência aos atributos de qualidade definidos para o sistema. Seu modelo baseado em serviços, com delimitação clara de responsabilidades, oferece **suporte robusto à escalabilidade, confiabilidade e testabilidade**, com **boa base para disponibilidade e segurança**.


