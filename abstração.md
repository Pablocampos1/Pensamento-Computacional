# Aula_Abstracoes_PensamentoComputacional

**Alunos:** Amon Cardoso Timo e Pablo Campos de Miranda
**Contexto:** Módulo de "Compras Programadas" do Sistema de Gestão.

## Objetivo da Atividade
Aplicar os conceitos de pensamento computacional para destilar ações complexas do sistema (criação de contratos e baixa de parcelas) em representações lógicas e estruturadas, divididas em três níveis de abstração.

---

## 1. Abstração do Fluxo de Criação de Contrato (Amon)
**Foco:** Transformar o preenchimento e salvamento do modal "Novo Contrato" em um processo lógico, incluindo o sistema de contingência (fallback) caso o servidor falhe.

### Nível 1: Descrição Detalhada (Mundo Real)
* O usuário clica no botão vermelho "Criar Contrato".
* O modal desliza na tela e o usuário preenche Nome, CPF, Modelo do Veículo e o Valor Total do Plano.
* O usuário clica no botão de confirmação.
* O sistema mostra um ícone girando (loading) no botão.
* O sistema tenta enviar os dados para o banco de dados principal. Se a internet cair, ele salva silenciosamente na memória do navegador (LocalStorage).
* O modal se fecha, os campos são limpos e o novo card de contrato aparece na tela com o progresso zerado.

---

## 2. Abstração do Fluxo de Lançamento de Parcela (Pablo)
**Foco:** Destilar a lógica de dedução de uma parcela e como ela se integra automaticamente ao módulo principal do Livro Caixa.

### Nível 1: Descrição Detalhada (Mundo Real)
* O usuário clica em "Deduzir Parcela" no card de um contrato ativo.
* O usuário preenche a data, o valor pago (ex: R$ 500,00) e o método (PIX).
* O usuário clica em "Confirmar Pagamento".
* O sistema calcula o novo valor pago e diminui o que falta pagar no contrato.
* O sistema envia esse valor automaticamente como uma "Entrada" para o Livro Caixa da loja.
* A barra de progresso visual do contrato avança e o modal fecha.
