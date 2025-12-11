Estructura básica de un KQL

<Table>
| where TimeGenerated between (datetime(YYYY-MM-DD) .. now())
| where <filtros importantes>
| summarize <agregación> by <campo1>, <campo2>
| order by <campo_orden> desc
| take 50
