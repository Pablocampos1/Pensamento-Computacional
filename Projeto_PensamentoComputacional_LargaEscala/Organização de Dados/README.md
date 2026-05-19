# Aula – Organização de Dados
**Disciplina:** Pensamento Computacional  
**Professora:** Kadidja Valéria  
**Data:** 14/05/2026  
**Prazo Final:** 21/05/2026  

---

## 🎯 Objetivo da Atividade

Aplicar as três arquiteturas de organização de dados — **Lista**, **Grafo** e **Hierarquia** — sobre um mesmo conjunto de informações do mundo real, demonstrando como dados brutos podem ser estruturados de formas distintas conforme a necessidade computacional.

---

## 📦 Conjunto de Dados Escolhido: Sistema

O conjunto escolhido é o sistema de gestão da **, uma loja de veículos, implementado em Python/Flask (`main.py`). O sistema gerencia entidades como **usuários, clientes, vendedores, motos, vendas e compras**.

Esse conjunto é rico para análise porque:
- Possui sequências ordenadas (lista de vendas, histórico)
- Possui relações hierárquicas (usuários com cargos/roles)
- Possui conexões complexas entre entidades (grafo de relacionamentos)

---

## 📁 Arquivos do Repositório

| Arquivo | Descrição |
|---|---|
| `README.md` | Explicação da atividade e objetivos |
| `Lista.md` | Representação linear dos dados do sistema |
| `Grafo.png` | Imagem da rede de conexões entre entidades |
| `Hierarquia.png` | Imagem do organograma de usuários e permissões |

---

## 🔍 Por que esse conjunto funciona nas 3 estruturas?

| Estrutura | Aplicação no Sistem |
|---|---|
| **Lista** | Histórico de vendas ordenadas por data (a mais recente no topo) |
| **Hierarquia** | Organograma de permissões: Admin → Gerente → Vendedor → Caixa |
| **Grafo** | Rede de conexões: Cliente ↔ Venda ↔ Vendedor ↔ Moto ↔ Compra |

---

## 📚 Bibliografia

SANTOS, Marcelo da Silva dos; VOGEL, Adriano José (rev. técnica). **Pensamento Computacional**. Porto Alegre: SAGAH, 2021.
