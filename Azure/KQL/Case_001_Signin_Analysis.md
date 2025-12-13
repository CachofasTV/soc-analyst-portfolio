# SOC Case 001 – Análisis de Autenticación en Microsoft Entra ID

## 🎯 Objetivo
Analizar los registros de Sign-in (`SigninLogs`) del tenant para identificar:
- patrones de autenticación,
- posibles accesos no autorizados,
- actividad irregular por IP o ubicación,
- baseline de actividad legítima.

Este análisis corresponde a una ejecución real en mi tenant de Azure.

---

# 1. Consulta KQL utilizada

```kql`
SigninLogs
| extend 
    Usuario = UserPrincipalName,
    IP = IPAddress,
    App = AppDisplayName,
    País = tostring(LocationDetails.countryOrRegion),
    Resultado = ResultType,
    Mensaje = ResultDescription
| project TimeGenerated, Usuario, IP, País, App, Resultado, Mensaje
| sort by TimeGenerated desc

![Vista completa](screenshots/signinlosextend.png)
