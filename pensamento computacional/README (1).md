# Projeto - Pensamento Computacional para Sistemas de Larga Escala

**Estudante:** Amon Cardoso Timo
**Estudante:** Maria Fernanda Dias
**Estudante:** Pablo Campos De Miranda
**Disciplina:** Pensamento Computacional
**Professora:** Kadidja Valéria
**Data de Entrega:** 23/04/2026

---

## 1. Descrição do Projeto
Este trabalho consiste na aplicação prática dos pilares do Pensamento Computacional (Decomposição, Reconhecimento de Padrões, Abstração e Algoritmos) no desenvolvimento e documentação de um sistema de software real. O sistema utilizado como objeto de estudo é um sistema de controle de caixa e gestão de contratos, uma aplicação de gestão comercial e financeira desenvolvida para lidar com fluxos de caixa e contratos de compras programadas.

---

## 2. Objetivos do Trabalho (Análise Específica do Sistema)

### 2.1 Relacionar Análise e Desenvolvimento de sistemas e Pensamento Computacional
O curso Análise e Desenvolvimento de Sistemas forneceu a estrutura arquitetural do projeto (modelo cliente-servidor com Flask e MySQL), enquanto o Pensamento Computacional foi a ferramenta para resolver os desafios lógicos. Através da decomposição, o problema complexo da gestão de uma oficina/loja foi dividido em subproblemas tratáveis: Autenticação, Fluxo de Caixa, Gestão de Contratos e Fechamentos Periódicos. A abstração foi fundamental para modelar o banco de dados e isolar a lógica de negócio da infraestrutura de deploy.

### 2.2 Reconhecer Princípios e Padrões de Larga Escala
O sistema incorpora padrões essenciais para suportar altas cargas de trabalho:
* **Connection Pooling:** Utilização da biblioteca `DBUtils` (`PooledDB`) para gerenciar um pool de conexões com o banco de dados, evitando falhas por excesso de requisições simultâneas.
* **Paginação Server-Side:** Implementação de parâmetros `page` e `per_page` com comandos `LIMIT` e `OFFSET` no SQL, garantindo que a aplicação não trave ao carregar milhares de transações.
* **Conteinerização:** Uso de Docker e Docker Compose para garantir escalabilidade e portabilidade do ambiente.

### 2.3 Identificar Dificuldades Reais em Aplicações Complexas
Durante o desenvolvimento, foram identificados e mitigados desafios reais:
* **Segurança de Credenciais:** Implementação de salting e hashing para que nenhuma senha seja armazenada em texto claro.
* **Consistência de Dados:** Gestão de transações atômicas para garantir que um pagamento registrado em um contrato de Compra Programada reflita corretamente e instantaneamente no Livro Caixa.
* **Performance em Relatórios:** O fechamento de caixa consolida dados em formato JSON para evitar consultas pesadas em tabelas históricas gigantescas no futuro.

### 2.4 Aplicar Metodologias Ágeis no Planejamento
O projeto foi planejado em sprints incrementais:
* **Sprint 1:** Modelagem do banco de dados e sistema de login seguro.
* **Sprint 2:** Desenvolvimento do módulo de Livro Caixa (CRUD de transações).
* **Sprint 3:** Lógica de Compras Programadas e automatização de vencimentos.
* **Sprint 4:** Configuração de infraestrutura (Docker) e documentação de deploy.

---

## 3. Sistema Proposto
**Nome do Sistema:** Plataforma de Gestão Jj Motos
**Descrição:** Uma aplicação web robusta para gestão comercial que integra cadastro e autenticação de usuários, módulo de livro caixa (entradas e saídas), sistema de compras programadas (vendas a prazo) e painel de auditoria com fechamentos de caixa em JSON.

---

## 4. Pensamento Computacional Aplicado

### 4.1 Decomposição
| Módulo | Funcionalidade Específica |
| :--- | :--- |
| **Autenticação** | Login multinível (Admin/Funcionário) e gestão de sessões. |
| **Livro Caixa** | Registro de entradas/saídas e métodos de pagamento. |
| **Contratos (CP)** | Gestão de clientes, itens, valores totais e controle de parcelas. |
| **Fechamentos** | Sumarização de saldo diário e mensal com auditoria. |

### 4.2 Reconhecimento de Padrões
* **Arquitetura REST:** Padronização de endpoints `/api/...` para facilitar integrações futuras.
* **Tratamento de Datas:** Padrão de ciclo de 30 dias para pagamentos recorrentes, com ajuste automático para meses curtos.

### 4.3 Abstração
* **Variáveis de Ambiente:** Abstração de configurações sensíveis (senhas de DB, chaves secretas) através de arquivos `.env`.
* **Docker Compose:** Abstração de toda a pilha de infraestrutura em um único comando de orquestração.

### 4.4 Algoritmos
* **Algoritmo de Pagamento de Contrato:** Recebe um valor, incrementa o valor pago, atualiza a data do último pagamento e projeta o próximo vencimento saltando exatamente um mês no calendário.
* **Algoritmo de Fechamento:** Itera sobre transações, calcula o somatório de tipos (entrada/saída) e gera um snapshot imutável do período.

---

## 5. Estrutura do Repositório

```text
Projeto_PensamentoComputacional_LargaEscala/
├── README.md         # Documentação principal
├── Design.md         # Decomposição, abstração e padrões aplicados
├── Diagrama.png      # Diagrama UML do sistema
└── Desafios.md       # Lista de desafios e soluções propostas