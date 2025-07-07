
DMN Live 03 – Flujos de Aprobación de Solicitud

Se requiere construir un modelo de decisiones para determinar los flujos de aprobaciones de una solicitud de crédito.
Se tiene una tabla de decisión para determinar aprobadores de la solicitud, con la siguiente información:
Variables de Entrada:
Tipo de Crédito: (nuevo, renovacion)
Tipo de Producto: (prestamo, financiamiento, fianza)
Importe: (numérico)
Variable de Salida: 
Aprobadores: (gerente-credito, comite-credito, gerente-agencia, gerente-cliente)
Reglas de Negocio:
Si Tipo de Crédito es “nuevo”, y Tipo de Producto es “prestamo”,  y el importe es mayor a 1000, entonces, aprobador es “gerente-credito” 
Si Tipo de Crédito es “renovacion”, y Tipo de Producto es “financiamiento”,  y el importe es mayor a 1000, entonces, aprobador es “comite-credito”
Si el importe se encuentra entre 1000 y 10000, entonces, aprobador es “gerente-agencia”
Si el Tipo de Producto es “fianza”, y el importe es mayor a 2000, entonces, aprobador es “gerente-cliente”
Considerar que la solicitud puede ser atendida por más de un aprobador.

Se  tiene la tabla de decisión para determinar flujos de aprobación, con la siguiente información:
Variables de Entrada:
Aprobadores: (lista)
Score Final Ajustado: (numérico)
Nivel de Riesgo: (bajo, medio, alto)
Requiere Verificación Adicional: (true, false)
Variable de Salida:
Resultado Flujo de Aprobación: (Aprobacion_Automatica,  Enviar_A_Gerente_Credito, Rechazar_Solicitud, Multiples_Aprobaciones_Manuales, Requiere_Investigacion_Adicional)
Reglas de Negocio:
Si aprobadores genera una lista vacía, y score final ajustado es mayor igual que 750, y el nivel de riesgo es “bajo”, y requiere verificación adicional es false, entonces, resultado flujos de aprobación es "Aprobacion_Automatica"; como anotación ingresar: “La solicitud cumple criterios y no requiere aprobación manual” 
Si aprobadores es “gerente-credito”, y score final ajustado es mayor igual que 600, y el nivel de riesgo es “bajo”, y requiere verificación adicional es false, entonces, resultado flujos de aprobación es "Enviar_A_Gerente_Credito"; como anotación ingresar: “La solicitud requiere aprobación del gerente de crédito” 
Si aprobadores es “comite-credito”, y el nivel de riesgo es “alto”, y  requiere verificación adicional es true, entonces, resultado flujos de aprobación es "Rechazar_Solicitud"; como anotación ingresar: “Riesgo de seguridad alto o ruta a comité con necesidad de verificación” 
Si hay más de un aprobador,  y score final ajustado es mayor igual que 650, y el nivel de riesgo es “medio”, y requiere verificación adicional es false, entonces, resultado flujos de aprobación es "Multiples_Aprobaciones_Manuales"; como anotación ingresar: “La solicitud requiere múltiples aprobaciones manuales”
Si existe aprobadores, y score final ajustado es menor que 500, y el nivel de riesgo es “Medio”, y requiere verificación adicional es true, entonces, resultado gestión flujos de aprobación es "Requiere_Investigacion_Adicional"; como anotación ingresar: “Riesgo o score bajo, requiere investigación adicional”

Requerimientos del caso:
Diseñar el modelo DRD (Diagrama de requisitos de decisiones)
Implementar las reglas de negocio utilizado: Tablas de decisión
Validar el modelo de decisiones utilizando el API de Camunda 8 Self Managed
