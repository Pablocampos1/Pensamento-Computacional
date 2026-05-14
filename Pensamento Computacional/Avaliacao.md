# O que a gente concluiu

Depois de refatorar e testar, a gente refletiu sobre como a arquitetura do projeto do sistema evoluiu com essa atividade.

### 1. Clareza (Simplicidade)
O código ficou bem mais fácil de ler. Na aula, vimos que a complexidade desnecessária é o habitat natural dos bugs. Usar recursos simples da linguagem (como `or 0` e `max()`) manteve a lógica do nosso back-end muito mais limpa, sem precisar aninhar um monte de condicional `if/else`.

### 2. Eficiência (Resiliência)
Nossa API agora tá muito mais casca grossa. O filtro de validação tá segurando a onda antes mesmo do erro tentar estourar a execução. O usuário pode fazer a besteira que for no input ou na URL, que o sistema desvia para um estado seguro (atribuindo zero ou limitando o mínimo) em vez de simplesmente derrubar a aplicação.

### 3. Escalabilidade
Isso ajudou muito a gente a pensar no futuro do sistema. Nós acabamos de padronizar como tratar valores monetários e parâmetros de listagem que vêm da requisição. Agora, quando formos criar os próximos módulos do sistema, já temos esse modelo na cabeça. O sistema vai crescer com um risco muito menor de conflitos e quebras à toa.
