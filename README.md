# Widget Notion – 15 Dias Úteis Anteriores

Este repositório contém dois arquivos principais:
- `index.html`: código do widget que exibe a data de *N* dias úteis anteriores à data atual.
- `holidays.json`: lista de feriados nacionais e específicos de um ano, usada para excluir dias não úteis do cálculo.

O objetivo é fornecer um **widget incorporável no Notion** que atualiza automaticamente todos os dias, mostrando a data que corresponde a um número definido de dias úteis atrás (por padrão, 15).

## Como funciona
1. O `index.html` calcula a data de *N* dias úteis antes de hoje.
2. Dias não úteis incluem:
   - Sábados e domingos
   - Feriados nacionais fixos
   - Feriados móveis nacionais (Carnaval, Sexta-feira Santa, Corpus Christi)
   - Datas listadas no `holidays.json`
3. O widget é incorporado no Notion via *embed*.

## Uso
1. Publique o repositório no GitHub Pages.
2. No Notion, crie um *embed* com a URL:
   ```
   https://SEU_USUARIO.github.io/NOME_REPO/?offset=15&json=https://raw.githubusercontent.com/SEU_USUARIO/NOME_REPO/main/holidays.json
   ```
   - `offset`: número de dias úteis para retroceder (padrão: 15)
   - `json`: URL do arquivo JSON com feriados

## Atualização dos feriados
O arquivo `holidays.json` possui duas chaves:
- `common`: feriados nacionais fixos (aplicáveis a todos os anos)
- `2025`: feriados específicos de 2025 (podendo incluir recesso forense, pontos facultativos, etc.)

Para atualizar:
1. No início de cada ano, adicione uma nova chave com o ano e a lista de feriados específicos.
2. Mantenha `common` com os feriados nacionais fixos.

Exemplo:
```json
{
  "common": ["AAAA-01-01", "AAAA-04-21"],
  "2025": ["2025-01-02", "2025-02-20"]
}
```

## Conteúdo atual (`holidays.json`)
```json
{
  "common": [
    "2025-01-01",
    "2025-04-21",
    "2025-05-01",
    "2025-09-07",
    "2025-10-12",
    "2025-11-02",
    "2025-11-15",
    "2025-12-25"
  ],
  "2025": [
    "2025-01-02","2025-01-03","2025-01-04","2025-01-05","2025-01-06",
    "2025-03-03","2025-03-04","2025-03-05",
    "2025-04-16","2025-04-17","2025-04-18","2025-04-19","2025-04-20",
    "2025-05-02",
    "2025-06-19","2025-06-20",
    "2025-08-11",
    "2025-10-31",
    "2025-11-01","2025-11-20","2025-11-21",
    "2025-12-08","2025-12-20","2025-12-21","2025-12-22","2025-12-23","2025-12-24","2025-12-26","2025-12-27","2025-12-28","2025-12-29","2025-12-30","2025-12-31"
  ]
}
```
