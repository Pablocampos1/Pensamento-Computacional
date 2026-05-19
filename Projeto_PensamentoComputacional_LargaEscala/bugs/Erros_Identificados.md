# Os Bugs que a gente achou

Testando a API, a gente percebeu que tava funcionando bem, mas o sistema não tava totalmente preparado pra falhas de entrada do usuário (que é o que acaba causando o sintoma do bug no final das contas, como vimos na teoria).

### Erro 1: A API quebrando ao converter string vazia (Erro de Execução)
* **Onde deu erro:** Nas rotas de adicionar transação (`add_transaction`) e adicionar contrato (`add_cp`).
* **O que rolava:** Se o usuário apagasse o valor no formulário lá no front, o JSON mandava uma string vazia `""`. Quando o back-end em Python tentava fazer o casting com `float("")`, o sistema surtava, dava um `ValueError` e a API retornava um Status 500 na tela. 
* **Como tava o nosso código antes:**
```python
# Pegava o valor direto e tentava forçar pra float, se viesse "" dava erro
entry_value = float(data.get('entryValue', 0))
```

### Erro 2: Risco de Divisão por Zero na Paginação (Erro Lógico-Matemático)
* **Onde deu erro:** Nas rotas de listar as transações (`get_transactions`) e contratos (`get_cps`).
* **O que rolava:** A gente fez uma paginação pros relatórios e limitou o máximo de itens, mas esqueceu de travar o mínimo. Se alguém manipulasse a URL e passasse `?per_page=0`, o cálculo de total de páginas tentava dividir por zero. Como na matemática não rola divisão por zero, a aplicação disparava um `ZeroDivisionError` e o servidor caía.
* **Como tava o nosso código antes:**
```python
per_page = min(request.args.get('per_page', 20, type=int), 200)

# E na hora de calcular as páginas, quebrava tudo por conta do per_page = 0:
"pages": math.ceil(total / per_page)
```


