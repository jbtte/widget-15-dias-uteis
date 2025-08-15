# Widget Notion – 15 Dias Úteis Anteriores

Este repositório contém dois arquivos principais:
- `index.html`: **versão padrão** (com moldura leve). Exibe a data correspondente a *N* dias úteis anteriores.
- `widget.html`: **versão compacta para Notion** (fundo transparente, tipografia maior, sem bordas). Recomendada para incorporação.
- `holidays.json`: lista de feriados a serem excluídos do cálculo (nacionais + específicos por ano).

O objetivo é fornecer um **widget incorporável no Notion** que atualiza automaticamente e mostra a data *D-*`offset` de **dias úteis** atrás (por padrão, 15).

## Como funciona
1. Calculamos *N* dias úteis antes de hoje.
2. Dias não úteis incluem:
   - Sábados e domingos;
   - Feriados nacionais fixos;
   - Feriados nacionais móveis (Carnaval seg/ter, Sexta-feira Santa, Corpus Christi);
   - Datas definidas no `holidays.json` (e opcionais via `extra=`).
3. O arquivo `holidays.json` é carregado via parâmetro `?json=`.

## Como incorporar no Notion
1. Publique este repositório no **GitHub Pages**.
2. No Notion, use `/embed` e cole **uma** das URLs:

**Versão padrão (`index.html`):**
```
https://SEU_USUARIO.github.io/SEU_REPO/?offset=15&json=https://raw.githubusercontent.com/SEU_USUARIO/SEU_REPO/main/holidays.json
```

**Versão compacta (`widget.html`) — recomendada:**
```
https://SEU_USUARIO.github.io/SEU_REPO/widget.html?offset=15&json=https://raw.githubusercontent.com/SEU_USUARIO/SEU_REPO/main/holidays.json
```

> Dica: ative **Full width** na página do Notion e ajuste o tamanho do bloco para melhor visualização.

## Parâmetros de URL
- `offset` — número de dias úteis para retroceder. Ex.: `offset=20`.
- `json` — URL **raw** de um JSON com feriados. Ex.: `json=https://raw.githubusercontent.com/.../holidays.json`.
- `extra` — datas adicionais (pontuais) separadas por vírgula. Ex.: `extra=2025-09-30,2025-10-03`.
- `hidetoday` (apenas em `index.html`) — `1` para ocultar a linha "Hoje".
- `hidetz` (apenas em `index.html`) — `1` para ocultar a pill de fuso horário.

## Estrutura do `holidays.json`
O arquivo aceita formatos flexíveis. Recomendado:
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

Também é aceito:
- Um array simples: `["AAAA-MM-DD", ...]`;
- Um objeto com `dates`/`holidays`: `{ "dates": [ ... ] }`.

## Atualização anual dos feriados
- No início de cada ano, adicione uma nova chave com o ano (por ex. `"2026": [ ... ]`).
- Mantenha os feriados nacionais fixos em `common`.
- **Cache busting:** quando atualizar o JSON, acrescente um sufixo `?v=2` ao final da URL em `json=` no Notion para forçar a atualização.

## Testes e depuração
- **Teste fora do Notion**: abra a URL completa no navegador e verifique o resultado.
- **Forçar um feriado**: inclua uma data próxima no `holidays.json` e confira se o cálculo "pula" esse dia.
- **Console/Network**: abra as DevTools (F12) e confirme que há requisição `200` para o `holidays.json`.

## Segurança e disponibilidade
- Use URLs HTTPS públicas. Repositórios privados não funcionam no Notion.
- Prefira `raw.githubusercontent.com` para o JSON.

## Licença
Use e adapte livremente. Se redistribuir, cite a fonte do repositório original quando possível.
