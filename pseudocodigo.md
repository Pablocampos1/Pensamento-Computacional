# Pseudocódigos - Nível 3 (Abstração Computacional)

INICIO Algoritmo ProcessarPagamento

pagamento <- ler_dados_pagamento_modal()
contrato_atual <- buscar_contrato(pagamento.id_contrato)

// Etapa 1: Abater parcela do contrato
contrato_atual.valor_pago <- contrato_atual.valor_pago + pagamento.valor
salvar_dados_contrato(contrato_atual)

// Etapa 2: Integração com Livro Caixa
transacao_caixa <- CRIAR_OBJETO(
    tipo: "entrada",
    descricao: "CP - " + contrato_atual.nome_cliente,
    valor: pagamento.valor,
    metodo: pagamento.metodo
)
inserir_no_livro_caixa(transacao_caixa)

// Etapa 3: Feedback Visual
fechar_modal_interface()
recalcular_e_renderizar_progresso()

FIM Algoritmo