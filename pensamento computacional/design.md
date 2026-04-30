# Documentação de Design

## 1. Decomposição
A gestão complexa do sistema foi dividida nos seguintes subproblemas tratáveis:
* **Autenticação:** Login multinível (Admin/Funcionário) e gestão de sessões.
* **Livro Caixa:** Registro de entradas/saídas e métodos de pagamento (PIX, Dinheiro, etc).
* **Contratos (CP):** Gestão de clientes, itens, valores totais e controle de parcelas pagas.
* **Fechamentos:** Sumarização de saldo diário e mensal com auditoria.

## 2. Reconhecimento de Padrões
* **Arquitetura REST:** Padronização de endpoints `/api/...` para facilitar integrações futuras.
* **Tratamento de Datas:** Padrão de ciclo de 30 dias para pagamentos recorrentes, com ajuste automático para meses curtos.

## 3. Abstração
A abstração foi fundamental para modelar o banco de dados e isolar a lógica de negócio da infraestrutura de deploy:
* **Variáveis de Ambiente:** Abstração de configurações sensíveis (senhas de DB, chaves secretas) através de arquivos `.env`.
* **Docker Compose:** Abstração de toda a pilha de infraestrutura em um único comando de orquestração.

## 4. Algoritmos
* **Algoritmo de Pagamento de Contrato:** Recebe um valor, incrementa o `paidValue`, atualiza o `last_payment_date` e projeta o próximo `payDate` saltando exatamente um mês no calendário.
* **Algoritmo de Fechamento:** Itera sobre transações, calcula o somatório de tipos (entrada/saída) e gera um snapshot imutável do período.