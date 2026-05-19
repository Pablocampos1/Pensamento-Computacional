# A Solução (Refatoração)

A gente arrumou esses problemas implementando "ações defensivas" pra preparar o sistema pro pior cenário, mantendo a simplicidade.

### Correção do Erro 1: Higienização simples e direta
* **A ideia:** Em vez de meter um monte de bloco `try/except` que ia deixar o código feio e confuso, a gente fez um filtro de validação rápido na hora de pegar o dado. Se o valor vier vazio (um valor falsy), ele assume `0` antes de tentar converter pra float.
* **Como ficou o código:**
```python
# Filtro de validação antes de processar e quebrar:
entry_raw = data.get('entryValue')
entry_value = float(entry_raw or 0)
```

### Correção do Erro 2: Ação Defensiva na Matemática
* **A ideia:** Pra evitar a divisão por zero, a gente aplicou uma pré-condição no limite de itens por página usando a função nativa `max()`. Assim, mesmo que o usuário mande 0 ou um número negativo na URL, o sistema garante que a página sempre vai ter no mínimo 1 item.
* **Como ficou o código:**
```python
# Prevenindo o erro lógico garantindo que per_page nunca seja menor que 1:
per_page = max(1, min(request.args.get('per_page', 20, type=int), 200))

# Agora a divisão tá totalmente segura:
"pages": max(1, math.ceil(total / per_page))
```


