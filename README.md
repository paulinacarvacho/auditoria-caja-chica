🏛️ Auditoría de Caja Chica Municipal: Detección de Anomalías

📋 Descripción del Proyecto
Auditoría de Datos aplicado a la gestión financiera municipal.
El objetivo fue analizar un dataset de rendiciones de "Caja Chica" para detectar errores administrativos y posibles incumplimientos de normativa interna antes de procesar los pagos.

Contexto: En la administración pública, la integridad de los datos es crítica. Un error de digitación o una duplicidad no detectada pueden derivar en problemas de probidad administrativa.

🎯 Objetivos del Análisis
1.- Integridad de Datos: Detectar transacciones duplicadas (mismo proveedor cobrando la misma boleta dos veces).
2.- Compliance (Normativa): Identificar gastos que exceden el tope legal para Caja Chica ($200.000 CLP).

🛠️ Metodología Aplicada (Google Sheets / Excel)
Para automatizar la revisión, apliqué lógica de bases de datos utilizando fórmulas de hoja de cálculo:

1.- Creación de Llave Primaria Compuesta (Primary Key)
Para identificar unicidad, no basta con el RUT ni con el Nro de Boleta por separado. Generé un **UID (Identificador Único)** combinando ambos campos.
Fórmula Lógica: `RUT_Proveedor` + `-` + `Nro_Boleta`
Resultado: `76.444.555-1-4002` (Huella digital única de la transacción).

2.- Detección de Duplicados
Utilicé funciones de conteo condicional (`COUNTIF` / `CONTAR.SI`) sobre la nueva Llave Primaria para marcar automáticamente cualquier registro que aparezca más de una vez.

3.- Validación de Montos
Apliqué formato condicional y funciones lógicas (`IF` / `SI`) para alertar visualmente sobre montos superiores a $200.000.

📊 Resultados del Caso
El análisis del archivo `Auditoría de Caja Chica Municipal_ Detección de Anomalías.xlsx` arrojó las siguientes alertas:

| ID Transacción | Hallazgo | Acción Recomendada |

| TRX-006 | **Duplicado exacto** de la TRX-002 (Mismo proveedor y boleta). | ❌ Rechazar pago duplicado. |
| TRX-005 | Monto ($210.000) excede el tope de caja chica. | ⚠️ Solicitar autorización especial o rechazar. |

### 📂 Archivos del Repositorio
`Auditoría de Caja Chica Municipal_ Detección de Anomalías.xlsx`: Dataset original con las transacciones procesadas.


Este ejercicio demuestra cómo técnicas simples de análisis de datos pueden prevenir errores financieros y mejorar la eficiencia en la gestión pública.
