# Week-3

# Aplicación de la Metodología MoSCoW  
Proyecto: FarmaExpres  

Priorización realizada con base en los requerimientos funcionales (RF), no funcionales (RNF) y necesidades del negocio previamente documentadas.

---

# MUST HAVE (Obligatorio – Versión 1.0)

Elementos críticos para que el sistema cumpla su propósito operativo y garantice integridad, seguridad y trazabilidad.

## 1. Seguridad y Gestión de Usuarios

- RF-01 Registro de usuarios con roles (Administrador, Farmacéutico, Auxiliar, Auditor).
- RF-02 Autenticación mediante credenciales únicas.
- RF-05 Bitácora de accesos y acciones críticas.
- RF-03 Recuperación de contraseña.
- RNF-15 Comunicación segura mediante HTTPS.
- RNF-16 Control de acceso basado en roles.
- RNF-17 Cierre automático de sesión por inactividad.
- RNF-31 Almacenamiento seguro de contraseñas (hash con sal).
- RNF-32 Validación de datos obligatorios.

Justificación: El sistema maneja información crítica y medicamentos; la seguridad es prioritaria.

---

## 2. Gestión de Inventario

- RF-06 Registro completo de medicamentos (código, nombre, principio activo, lote, vencimiento, sede, stock mínimo, estado).
- RF-07 Actualización de productos.
- RF-08 Eliminación lógica.
- RF-09 Descuento automático de stock.
- RF-10 Alertas de vencimiento y bloqueo automático.
- RF-11 Consulta de inventario en tiempo real.
- RNF-12 Prevención de duplicados por código + lote.
- RNF-06 Prevención de stock negativo.

Justificación: Es el núcleo funcional del sistema.

---

## 3. Movimientos y Transacciones

- RF-12 Registro de entradas (compras).
- RF-13 Registro de salidas (ventas, ajustes, vencimientos).
- RF-14 Historial completo de movimientos (usuario, fecha/hora, tipo, sede, cantidad).
- RNF-11 Atomicidad (todo o nada).
- RNF-13 Cancelación automática ante error.
- RNF-29 Sincronización de fecha y hora del servidor.

Justificación: Garantiza trazabilidad y coherencia contable.

---

## 4. Concurrencia

- RF-16 Acceso concurrente multiusuario.
- RF-17 Reflejar cambios en tiempo real.
- RNF-05 Evitar inconsistencias por actualizaciones simultáneas.
- RNF-07 Notificación de conflicto de edición.
- RNF-30 Límite configurable de sesiones por sede.

Justificación: El sistema es centralizado y multiusuario; la integridad depende de esto.

---

## 5. Reportes Básicos

- RF-15 Reporte de inventario actual.
- RF-15 Reporte de productos próximos a vencer.
- RF-15 Reporte de productos agotados.
- RF-15 Historial de movimientos.

Justificación: Son necesarios para toma de decisiones y control administrativo.

---

# SHOULD HAVE (Importante – Versión 1.1)

Mejoran rendimiento, confiabilidad y control, pero no impiden operación básica.

## 1. Rendimiento

- RNF-01 Soporte mínimo 15 usuarios concurrentes.
- RNF-02 Consulta de inventario ≤ 15 segundos.
- RNF-03 Registro de movimientos ≤ 15 segundos.
- RNF-04 Reportes ≤ 30 segundos.

## 2. Respaldo y Recuperación

- RNF-22 Backup automático diario.
- RNF-23 Restauración en máximo 1 día.

## 3. Disponibilidad

- RNF-08 Disponibilidad mínima 99% mensual.
- RNF-10 Consultas en modo solo lectura ante fallos de red.

## 4. Auditoría Avanzada

- RNF-18 Registro de nodo/servidor en bitácora.
- RNF-19 Bitácora solo lectura para usuarios no administradores.

---

# COULD HAVE (Deseable – Mejoras Futuras)

Aportan valor estratégico y escalabilidad técnica.

## 1. Escalabilidad

- RNF-20 Agregar segundo nodo sin modificar lógica principal.
- RNF-21 Balanceo básico de carga.

## 2. Portabilidad

- RNF-28 Despliegue en distintos entornos (local, nube, institucional).

## 3. Usabilidad y Mantenibilidad

- RNF-24 Capacitación básica en menos de 4 horas.
- RNF-25 Compatibilidad con navegadores modernos.
- RNF-26 Documentación técnica completa.
- RNF-27 Separación por capas y buenas prácticas.

---

# WON’T HAVE (Fuera del Alcance Actual)

- Arquitectura distribuida empresarial de alta disponibilidad real.
- Integraciones externas (facturación electrónica, APIs de proveedores).
- Aplicación móvil.
- Analítica avanzada o inteligencia predictiva.

---

# Revisión y Ajustes Propuestos

Conforme a la información enviada, se recomienda agregar formalmente como MUST HAVE:

1. Política configurable de alertas de vencimiento (ej. 30 y 15 días).
2. Validación obligatoria de sede en cada movimiento.
3. Restricción de eliminación física de registros (solo lógica).
4. Control de integridad referencial en base de datos.
5. Definición explícita del nivel de aislamiento de transacciones (ej. READ COMMITTED o superior).

También sería recomendable formalizar:

- Criterios de aceptación medibles para cada RF crítico.
- Definición clara de versión mínima viable (MVP).
- Matriz de trazabilidad RF ↔ RNF ↔ Necesidades del negocio.

