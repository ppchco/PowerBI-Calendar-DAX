# PowerBI-Calendar-DAX
# Power BI DAX: Tabela de Calendário

Este projeto contém scripts DAX para criar uma tabela de calendário no Power BI, com colunas calculadas úteis para análises temporais.

Este projeto contém um exemplo de criação de uma tabela calendário no Power BI utilizando DAX. O exemplo demonstra a criação de uma tabela utilizando a função `CALENDAR` e a adição de diversas colunas derivadas (como ano, trimestre, mês, dia, nome do dia, semana do ano, etc.). Além disso, inclui três colunas calculadas: `Data Base`, `Offset Mês` e `Offset Ano`.

## Tabela Calendário

O código abaixo cria uma tabela chamada `dCALENDARIO` com as seguintes colunas:
- **Date:** Data gerada pela função `CALENDAR` a partir do dia 01/01/2020 até a data máxima encontrada em `'Tabela'[coluna_data]`.
- **Ano:** Ano da data.
- **Trim:** Trimestre da data.
- **Mês:** Número do mês.
- **Dia:** Dia do mês.
- **Dia Nome:** Nome abreviado do dia da semana (com a primeira letra em maiúscula).
- **Dia Semana:** Número do dia da semana.
- **Semana Ano:** Número da semana do ano.
- **Mês Nome:** Nome completo do mês (com a primeira letra em maiúscula).
- **Mês Abrev:** Nome abreviado do mês.
- **Mês Ano:** Formatação “MM/AAAA” da data.
- **Mês Abrev Ano:** Formatação “MMM/AAAA” da data.
- **Trim Ano:** Formatação “qTAAAA” onde `q` é o trimestre.

## Colunas Calculadas

As seguintes colunas calculadas são criadas a partir da tabela calendário:

- **Data Base:** Retorna o primeiro dia do mês usando `STARTOFMONTH`.
- **Offset Mês:** Calcula a diferença, em meses, entre a data e o mês atual.
- **Offset Ano:** Calcula a diferença, em anos, entre a data e o ano atual.

## Código DAX

O arquivo `src/CalendarTable-DAX.txt` contém os códigos completos abaixo:

---

### Criação da Tabela Calendário

```dax
dCALENDARIO =
    ADDCOLUMNS(
        CALENDAR(DATE(2020, 01, 01), MAX('Tabela'[coluna_data])),
        "Ano", YEAR([Date]),
        "Trim", FORMAT([Date], "q"),
        "Mês", MONTH([Date]),
        "Dia", DAY([Date]),
        "Dia Nome", CONCATENATE(UPPER(LEFT(FORMAT([Date], "ddd"), 1)), MID(FORMAT([Date], "ddd"), 2, 2)),
        "Dia Semana", WEEKDAY([Date]),
        "Semana Ano", WEEKNUM([Date]),
        "Mês Nome", CONCATENATE(UPPER(LEFT(FORMAT([Date], "mmmm"), 1)), MID(FORMAT([Date], "mmmm"), 2, 9)),
        "Mês Abrev", CONCATENATE(UPPER(LEFT(FORMAT([Date], "mmm"), 1)), MID(FORMAT([Date], "mmm"), 2, 2)),
        "Mês Ano", FORMAT(MONTH([Date]), "00") & "/" & YEAR([Date]),
        "Mês Abrev Ano", CONCATENATE(UPPER(LEFT(FORMAT([Date], "mmm"), 1)), MID(FORMAT([Date], "mmm"), 2, 2)) & "/" & YEAR([Date]),
        "Trim Ano", FORMAT([Date], "q") & "T" & YEAR([Date])
    )
