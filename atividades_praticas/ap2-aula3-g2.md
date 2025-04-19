Pede-se a seleção de três dos requisitos de qualidade, desta aula 03 e a definição de estratégias necessárias para o atendimento a cada um deles, durante a implementação dos requisitos funcionais definidos na aula 2.


### 1) Cadastro de Prestadores e Clientes

1.1 Usabilidade: 
- Interface intuitiva e responsiva para fácil preenchimento de dados;
- Opção de login social (Google, Facebook, etc.);

1.2 Disponibilidade:
- Banco de dados redundante e escalável para suportar picos de acesso.
- Load balancer para distribuir requisições em caso de alta demanda.

1.3 Testabilidade:
- Testes automatizados para validação de formulários e autenticação;
- Testes de carga para verificar desempenho do cadastro com múltiplos acessos simultâneos;

### 2) Aumento do Tamanho da Fonte

2.1 Usabilidade: 
- Implementação de acessibilidade seguindo padrões WCAG;
- Opção para aumentar fonte disponível nas configurações do usuário;

2.2 Disponibilidade:
- Armazenamento da preferência do usuário no banco de dados ou cookies para persistência da configuração;

2.3 Testabilidade:
- Testes com leitores de tela e ferramentas de acessibilidade;
- Testes manuais e automatizados para diferentes resoluções e tamanhos de tela;

### 3) Agendamento de Serviços com Data e Hora:

3.1 Usabilidade: 
- Calendário interativo e fácil de usar;
- Indicação visual de horários disponíveis e já ocupados;

3.2 Disponibilidade:
- Banco de dados otimizado para buscas rápidas de horários disponíveis;
- Tolerância a falhas para evitar perda de dados em caso de erro na solicitação;

3.3 Testabilidade:
- Testes unitários para validação da lógica de agendamento;
- Testes de concorrência para verificar múltiplas solicitações simultâneas;

### 4) Avaliação de Prestadores com Nota e Comentário

4.1 Usabilidade: 
- Interface simplificada com estrelas e campo de comentário opcional;
- Feedback instantâneo para garantir que a avaliação foi registrada;

4.2 Disponibilidade:
- Armazenamento eficiente das avaliações para rápida consulta;
- Caching de avaliações populares para evitar sobrecarga no banco de dados;

4.3 Testabilidade:
- Testes de inserção e recuperação de avaliações no banco de dados;
- Testes de interface para avaliar a facilidade de uso do sistema de avaliação;

### 5) Integração com Pagamento

5.1 Usabilidade: 
- Opções de pagamento diversas (cartão de crédito, débito, Pix, boleto);
- Interface clara e segura para inserção de dados financeiros;

5.2 Disponibilidade:
- Uso de provedores confiáveis (Stripe, PayPal, Mercado Pago, etc.);
- Monitoramento contínuo para detectar e corrigir erros rapidamente;

5.3 Testabilidade:
- Testes de integração para validar comunicação com gateways de pagamento;
- Testes de segurança para evitar fraudes e vazamento de dados;

