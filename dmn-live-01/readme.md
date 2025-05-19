DMN Live 01 – Estados de Aprobación

Se requiere determinar un modelo de decisiones que establezca el estado de aprobación, de acuerdo a las siguientes variables de entrada:
Edad: edad de la persona
Categoría de Riesgo: que puede ser “alto”,”medio”,”bajo”
Antecedente de solicitud: puede ser true o false

Se tiene las siguientes reglas de negocio a implementar:
1. Si la persona es mayor de edad y tiene la categoría de riesgo: ”bajo”, “medio” y tiene antecedente de solicitud, entonces, es “Aprobado”.
2. Si la persona es menor de edad y tiene la categoría de riesgo: “bajo”, “medio” y no tiene antecedente de solicitud, entonces, es “Rechazado”.
3. Si la persona tiene la categoría de riesgo: “alto” y tiene antecedente de solicitud, entonces, es “Rechazado”.
4. Si la persona no tiene antecedente, entonces, es “Rechazado”.
Que es lo que pasa si actualizamos nuestras reglas de negocio: 
2. Si la persona es menor de edad, entonces, es “Rechazado”
3. Si la persona tiene la categoría de riesgo: “alto”, entonces, es “Rechazado”.

Requerimientos

1. Diseñar el modelo DRD (Diagrama de requisitos de decisiones)
2. Implementar las reglas de negocio utilizado: Tablas de decisión y Expresión Literal
3. Testear el modelo de reglas utilizando el API de Camunda 8
