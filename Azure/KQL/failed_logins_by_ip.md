# Detección de intentos fallidos de inicio de sesión por IP y país

## Objetivo
Identificar usuarios y direcciones IP que presentan múltiples intentos fallidos de autenticación en las últimas 24 horas dentro del tenant, con el fin de detectar posibles ataques de fuerza bruta o credenciales comprometidas.

## Query KQL

SigninLogs
// 1) Ventana de tiempo: últimas 24 horas
| where TimeGenerated > ago(24h)

// 2) Nos interesan solo los intentos fallidos
| where ResultType != 0

// 3) Reducimos las columnas a lo importante
| project TimeGenerated,
          UserPrincipalName,
          IPAddress,
          LocationDetails,
          ResultType,
          ResultDescription

// 4) Extraemos país (si viene en LocationDetails)
| extend Country = tostring(LocationDetails.countryOrRegion)

// 5) Agregamos por usuario + IP + país
| summarize FailedLogins = count()
          by UserPrincipalName, IPAddress, Country

// 6) Nos quedamos con los que tienen muchos fallos
| where FailedLogins > 3

// 7) Ordenamos por quien se ve más sospechoso
| order by FailedLogins desc

