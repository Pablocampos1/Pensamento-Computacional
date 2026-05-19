# Lista de Desafios Críticos e Soluções Mitigadoras

Durante o desenvolvimento da aplicação, foram identificados e mitigados os seguintes desafios reais de sistemas complexos de larga escala:

* **Desafio 1: Escalabilidade e Gargalo de Conexões**
  * **Problema:** Risco de falhas no banco de dados por excesso de requisições simultâneas de vários usuários.
  * **Solução Mitigadora:** Implementação do padrão de **Connection Pooling** utilizando a biblioteca `DBUtils` (`PooledDB`) para gerenciar ativamente um pool de conexões com o banco de dados.

* **Desafio 2: Performance em Listagens Massivas**
  * **Problema:** A aplicação poderia travar e o banco de dados sobrecarregar ao carregar milhares de transações históricas.
  * **Solução Mitigadora:** Implementação de **Paginação Server-Side** com os parâmetros `page` e `per_page` utilizando comandos `LIMIT` e `OFFSET` no SQL.

* **Desafio 3: Segurança de Credenciais Sensíveis**
  * **Problema:** Garantir a segurança do acesso e impedir o vazamento de informações críticas.
  * **Solução Mitigadora:** Implementação de técnicas de salting e hashing (através da biblioteca Werkzeug) para assegurar que nenhuma senha seja armazenada em texto claro no banco de dados.

* **Desafio 4: Consistência de Dados Concorrentes**
  * **Problema:** Um pagamento registrado num módulo poderia não se refletir adequadamente no saldo geral do sistema.
  * **Solução Mitigadora:** Gestão de transações atômicas para garantir que um pagamento registrado em um contrato de Compra Programada reflita corretamente e instantaneamente no Livro Caixa.

* **Desafio 5: Performance em Relatórios (Volume Histórico)**
  * **Problema:** O processamento futuro de relatórios poderia gerar consultas demasiado pesadas em tabelas históricas gigantescas.
  * **Solução Mitigadora:** O módulo de fechamento de caixa atua de forma preventiva, consolidando dados em formato estático JSON (snapshot imutável do período) para evitar recálculos pesados no futuro.