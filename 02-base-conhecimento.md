# Base de Conhecimento

## Dados Utilizados

O agente utiliza dados fictícios (mockados) para simular receitas e despesas.  
Esses dados podem estar organizados em arquivos na pasta `data`.

| Arquivo               | Formato | Utilização no Agente                          |
|------------------------|---------|-----------------------------------------------|
| `transacoes.csv`       | CSV     | Analisar padrão de receitas e despesas        |
| `transacoes.json`      | JSON    | Alternativa para simulação das transações     |
| `limites_config.json`  | JSON    | Definir limites de alerta para despesas       |

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

- Foram adicionadas novas categorias de despesas (ex.: supermercado, transporte, lazer) para enriquecer os testes.
- Incluímos um campo `data` nas transações para permitir análises temporais.
- Ajustamos valores de despesas recorrentes para simular cenários de alerta (ex.: aluguel e cartão de crédito).
- Criamos um arquivo `limites_config.json` para definir limites de gastos e facilitar a emissão de alertas.

## Estratégia de Integração

### Como os dados são carregados?
- Os arquivos `transacoes.csv` ou `transacoes.json` são carregados no início da execução do agente.
- Os dados são lidos em memória e organizados em estruturas Python (listas/dicionários).
- A lógica do agente utiliza esses dados para:
  - Calcular saldo entre receitas e despesas.
  - Gerar gráficos de visualização.
  - Emitir alertas quando despesas ultrapassam limites definidos em `limites_config.json`.
- Não há conexão com bancos reais ou APIs externas: toda a base de conhecimento é mockada e usada apenas para simulação.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

- Os dados não são enviados para um system prompt, pois o agente não utiliza LLM para gerar respostas.
- Os arquivos CSV/JSON são carregados dinamicamente no início da execução do agente.
- A lógica em Python acessa esses dados diretamente para:
  - Calcular saldo entre receitas e despesas.
  - Gerar gráficos de visualização.
  - Emitir alertas quando despesas ultrapassam limites definidos.
- Toda a interação com os dados ocorre localmente, sem envio para modelos externos.

  ## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:

- Nome: Ana Maria

- Perfil: Moderado

- Saldo disponível: R$ 5.000

Últimas transações:

- 01/11: Supermercado - R$ 500
- 05/11: Aluguel - R$ 1.000
- 07/11: Cartão de Crédito - R$ 1.000
- 10/11: Salário - R$ 3.000
...
```
