# Queries realizados

## Resumen por país
SigninLogs
| summarize Intentos = count() 
      by tostring(LocationDetails.countryOrRegion)
| order by Intentos desc

![Query por país](../screenshots/signinlogsintentos.png)

## Resumen por IP
SigninLogs
| summarize Intentos = count() 
      by IPAddress
| order by Intentos desc

## Intentos fallidos
SigninLogs
| where ResultType != 0
| summarize Fallos = count()
      by UserPrincipalName, IPAddress
| order by Fallos desc

## Impossible Travel
SigninLogs
| project 
    Usuario = UserPrincipalName,
    IP = IPAddress,
    País = tostring(LocationDetails.countryOrRegion),
    Hora = TimeGenerated
| order by Hora asc

