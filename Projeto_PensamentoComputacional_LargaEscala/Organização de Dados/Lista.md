# Estrutura 1: Lista — Histórico de Vendas

> **Princípio:** Sequência linear e ordenada. Cada elemento ocupa uma posição fixa;
> a posição dita a ordem de acesso. Ideal para representar passos, inventários e ordem cronológica.

---

## 📋 Lista de Vendas — Ordenada por Data (mais recente primeiro)

```
Posição [0] → Venda #1042 | Data: 2026-05-12 | Tipo: Moto | Descrição: Honda CG 160 Titan 2024
              Comprador: Carlos Souza | Vendedor: Rafael Lima | Valor: R$ 14.500,00 | Método: PIX

Posição [1] → Venda #1041 | Data: 2026-05-10 | Tipo: Moto | Descrição: Yamaha Fazer 250 2023
              Comprador: Ana Paula Ferreira | Vendedor: Juliana Costa | Valor: R$ 18.900,00 | Método: Financiamento

Posição [2] → Venda #1040 | Data: 2026-05-08 | Tipo: Carro | Descrição: Fiat Uno 2019
              Comprador: Marcos Oliveira | Vendedor: Rafael Lima | Valor: R$ 32.000,00 | Método: Transferência

Posição [3] → Venda #1039 | Data: 2026-05-05 | Tipo: Moto | Descrição: Honda Biz 125 2023
              Comprador: Fernanda Lima | Vendedor: Juliana Costa | Valor: R$ 9.800,00 | Método: PIX

Posição [4] → Venda #1038 | Data: 2026-05-01 | Tipo: Moto | Descrição: Yamaha Lander 250 2022
              Comprador: Roberto Nunes | Vendedor: Rafael Lima | Valor: R$ 21.500,00 | Método: Financiamento

Posição [5] → Venda #1037 | Data: 2026-04-28 | Tipo: Moto | Descrição: Suzuki GSR 150i 2024
              Comprador: Patrícia Mendes | Vendedor: Juliana Costa | Valor: R$ 12.300,00 | Método: PIX

Posição [6] → Venda #1036 | Data: 2026-04-25 | Tipo: Carro | Descrição: Chevrolet Onix 2021
              Comprador: Diego Alves | Vendedor: Rafael Lima | Valor: R$ 58.000,00 | Método: Financiamento

Posição [7] → Venda #1035 | Data: 2026-04-20 | Tipo: Moto | Descrição: Honda PCX 150 2023
              Comprador: Larissa Campos | Vendedor: Juliana Costa | Valor: R$ 15.200,00 | Método: PIX
```

---

## 🧠 Justificativa da Escolha

A **Lista** é a estrutura ideal para o histórico de vendas porque:

- Cada venda ocupa uma **posição única e ordenada** (por data ou ID)
- O acesso é **sequencial e direto** — para ver a venda mais recente, acessa-se a posição `[0]`
- Corresponde exatamente à rota `/api/vendas?sort_by=data&sort_dir=desc` do sistema real
- A **API do `main.py`** retorna os dados nesse formato (array JSON ordenado)

---

## 💻 Representação em Python (extraída do main.py)

```python
# Rota real do sistema — retorna lista ordenada de vendas
# GET /api/vendas?sort_by=data&sort_dir=desc

vendas = [
    {"id": 1042, "data": "2026-05-12", "tipo_veiculo": "moto",  "descricao": "Honda CG 160 Titan 2024",  "valor": 14500.00, "metodo": "PIX"},
    {"id": 1041, "data": "2026-05-10", "tipo_veiculo": "moto",  "descricao": "Yamaha Fazer 250 2023",     "valor": 18900.00, "metodo": "Financiamento"},
    {"id": 1040, "data": "2026-05-08", "tipo_veiculo": "carro", "descricao": "Fiat Uno 2019",             "valor": 32000.00, "metodo": "Transferência"},
    {"id": 1039, "data": "2026-05-05", "tipo_veiculo": "moto",  "descricao": "Honda Biz 125 2023",        "valor":  9800.00, "metodo": "PIX"},
    {"id": 1038, "data": "2026-05-01", "tipo_veiculo": "moto",  "descricao": "Yamaha Lander 250 2022",    "valor": 21500.00, "metodo": "Financiamento"},
]

# Acesso por posição — princípio fundamental da Lista
venda_mais_recente = vendas[0]   # Honda CG 160
segunda_venda      = vendas[1]   # Yamaha Fazer 250
```

---

## 📊 Vantagem da Lista neste contexto

| Característica | Benefício |
|---|---|
| Ordem por posição | Fácil exibir do mais recente ao mais antigo |
| Acesso por índice | Paginação eficiente (posições 0–9, 10–19...) |
| Simplicidade | Leitura direta, sem necessidade de navegação por nós |

---
