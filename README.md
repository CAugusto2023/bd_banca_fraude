# bd_banca_fraude

📝 Nombre del caso:

Sistema de Control y Detección de Fraude con Tarjetas de Crédito

🎯 Objetivo del sistema

Diseñar una base de datos relacional para almacenar, analizar y detectar posibles fraudes en transacciones con tarjetas de crédito, considerando variables como ubicación, monto, tipo de comercio, dispositivo, y comportamiento del cliente.

🏦 Contexto del problema

El banco ha identificado un aumento en el número de fraudes mediante tarjetas de crédito. Se necesita una solución que permita almacenar y auditar las transacciones con el fin de aplicar reglas de detección o alimentar modelos de machine learning.

📦 Entidades principales

1. Clientes
- id_cliente (PK)
- nombre
- apellido
- dni
- fecha_nacimiento
- direccion
- ciudad
- fecha_registro
  
2. Tarjetas
- id_tarjeta (PK)
- id_cliente (FK)
- tipo_tarjeta (Crédito, Débito, Prepago)
- numero_enmascarado
- fecha_emision
- estado (Activa, Bloqueada, Vencida)
  
3. Comercios
- id_comercio (PK)
- nombre_comercio
- rubro (Retail, Tecnología, Restaurante, etc.)
- ciudad
- pais
  
4. Transacciones
- id_transaccion (PK)
- id_tarjeta (FK)
- id_comercio (FK)
- fecha_hora
- monto
- ubicacion
- dispositivo (Web, App, POS)
- ip_sospechosa (bit)
- autenticacion (PIN, Biometría, Token)
- es_fraude (bit) -- etiqueta de fraude
- puntuacion_riesgo (opcional)
  
5. Historial_alertas
- id_alerta (PK)
- id_transaccion (FK)
- tipo_alerta (Monto inusual, Ubicación sospechosa, etc.)
- fecha_alerta
- estado_alerta (Pendiente, Confirmada, Falsa)

🧠 Reglas de negocio (simples) para fraude

- Si el monto de la transacción supera los S/ 5,000 y el cliente no suele gastar más de S/ 500.
- Si la transacción se realiza desde otro país.
- Si el dispositivo es nuevo y el usuario nunca lo ha usado antes.
- Si hay múltiples transacciones en menos de 2 minutos.

📊 Consultas SQL esperadas

- Total de transacciones fraudulentas por cliente.
- Comercios con más fraude reportado.
- Promedio de gasto por cliente por rubro.
- Alertas activadas en la última semana.

DIAGRAMA ENTIDAD RELACIÓN

![Diagrama entidad relación](https://github.com/user-attachments/assets/092af056-8c00-48df-91e9-65a961228f8b)

DISEÑO LÓGICO

![bd_banca_fraude_1](https://github.com/user-attachments/assets/5944905a-f5e0-4292-b122-de48009a6ffb)

MODELO FÍSICO

![image](https://github.com/user-attachments/assets/02665a23-432c-420c-9d3d-c92069cf7874)
