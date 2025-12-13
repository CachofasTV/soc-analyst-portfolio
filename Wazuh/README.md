# Wazuh — Proyecto Blue Team 🛡️

Este directorio contiene toda la evidencia, configuración y documentación generada durante mi proyecto práctico con Wazuh.

## Contenido
- Instalación del Wazuh Manager  
- Conexión y monitoreo de agentes  
- Configuración de File Integrity Monitoring (FIM)  
- Detección de ataques de fuerza bruta  
- Dashboards y análisis de alertas  

Cada subcarpeta contiene documentación detallada.

# Wazuh – Security Monitoring Overview

## What is Wazuh?
Wazuh is an open-source security platform used for endpoint monitoring, log analysis, and threat detection. It combines SIEM and EDR capabilities and is commonly used in SOC environments.

## Architecture Overview
- **Wazuh Agent:** Installed on endpoints to collect logs, security events, and system information.
- **Wazuh Manager:** Centralizes and analyzes data received from agents.
- **Decoders:** Parse and structure raw log data.
- **Rules:** Evaluate events to detect abnormal or suspicious behavior.
- **Alerts:** Generated when rules are triggered and reviewed by the SOC.

## SOC Use Cases
- Endpoint activity monitoring
- Detection of suspicious behavior
- File integrity monitoring
- Support for incident detection and investigation

> Initial documentation created as part of hands-on SOC training.

