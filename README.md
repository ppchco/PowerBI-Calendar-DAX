# PowerBI-Calendar-DAX

## Como Utilizar
### 1. Crie a Tabela Calendário:
No Power BI Desktop, abra a guia Modelagem e clique em Nova Tabela. Copie e cole o código da criação da tabela dCALENDARIO (ajustando 'Tabela'[coluna_data] conforme seu modelo).

### 2. Crie as Colunas Calculadas:
Com a tabela dCALENDARIO criada, vá na mesma guia e adicione as colunas calculadas utilizando os códigos fornecidos.

### 3. Atualize seu Modelo:
Após a criação, a tabela calendário estará disponível para relacionamentos e análises em seu modelo Power BI.
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

## Requisitos

- Power BI Desktop
- Modelo de dados com uma coluna de data (`'Tabela'[coluna_data]`)
---
- A tabela de calendário pode ser relacionada com outras tabelas para análises mais avançadas

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---
