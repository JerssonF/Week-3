## Week 3

### Aplicación de la Metodología MoSCoW  
Proyecto: FarmaExpres  
Sistema de Gestión de Inventario Farmacéutico

La priorización se realiza con base en las necesidades del negocio, requerimientos funcionales (RF) y no funcionales (RNF) previamente definidos.

---

### MUST HAVE (Obligatorio – Versión 1.0)

Funcionalidades críticas sin las cuales el sistema no cumple su propósito operativo.

#### 1. Seguridad y Gestión de Usuarios

- RF-01 Registro de usuarios con roles.
- RF-02 Autenticación con credenciales únicas.
- RF-03 Recuperación de contraseña.
- RF-05 Bitácora de accesos y acciones críticas.
- RNF-15 Comunicación segura HTTPS.
- RNF-16 Control de acceso por roles.
- RNF-17 Cierre automático por inactividad.
- RNF-31 Almacenamiento cifrado de contraseñas.
- RNF-32 Validación de datos obligatorios.

---

#### 2. Gestión de Inventario

- RF-06 Registro completo de medicamentos (código, nombre, principio activo, lote, vencimiento, sede, stock mínimo, estado).
- RF-07 Actualización de productos.
- RF-08 Eliminación lógica.
- RF-09 Descuento automático de stock.
- RF-10 Alertas configurables de vencimiento y bloqueo automático.
- RF-11 Consulta de inventario en tiempo real.
- RNF-12 Prevención de duplicados código + lote.
- RNF-06 Prevención de stock negativo.

---

#### 3. Movimientos y Transacciones

- RF-12 Registro de entradas.
- RF-13 Registro de salidas.
- RF-14 Historial completo de movimientos.
- RNF-11 Atomicidad (todo o nada).
- RNF-13 Cancelación automática ante error.
- RNF-29 Sincronización de fecha y hora del servidor.

---

#### 4. Concurrencia

- RF-16 Acceso concurrente multiusuario.
- RF-17 Reflejar cambios en tiempo real.
- RNF-05 Prevención de inconsistencias simultáneas.
- RNF-07 Manejo de conflictos de edición.
- RNF-30 Límite configurable de sesiones por sede.

---

#### 5. Reportes Básicos

- RF-15 Inventario actual.
- RF-15 Productos próximos a vencer.
- RF-15 Productos agotados.
- RF-15 Historial de movimientos.

---

### SHOULD HAVE (Importante – Versión 1.1)

Mejoras relevantes para rendimiento y confiabilidad.

#### 1. Rendimiento

- RNF-01 Soporte mínimo de 15 usuarios concurrentes.
- RNF-02 Consulta ≤ 15 segundos.
- RNF-03 Registro ≤ 15 segundos.
- RNF-04 Reportes ≤ 30 segundos.

---

#### 2. Respaldo y Recuperación

- RNF-22 Backup automático diario.
- RNF-23 Restauración en máximo 1 día.

---

#### 3. Disponibilidad y Auditoría Extendida

- RNF-08 Disponibilidad mínima 99% mensual.
- RNF-10 Modo solo lectura ante fallo de red.
- RNF-18 Registro de nodo en bitácora.
- RNF-19 Bitácora solo lectura para no administradores.

---

### COULD HAVE (Deseable – Futuras Iteraciones)

#### 1. Escalabilidad

- RNF-20 Segundo nodo sin modificar lógica principal.
- RNF-21 Balanceo básico de carga.

---

#### 2. Portabilidad

- RNF-28 Despliegue en distintos entornos.

---

#### 3. Usabilidad y Mantenibilidad

- RNF-24 Capacitación en menos de 4 horas.
- RNF-25 Compatibilidad con navegadores modernos.
- RNF-26 Documentación técnica completa.
- RNF-27 Arquitectura por capas.

---

### WON’T HAVE (Fuera del Alcance Actual)

- Arquitectura empresarial distribuida completa.
- Integraciones externas (facturación electrónica).
- Aplicación móvil.
- Inteligencia predictiva.
- Infraestructura cloud avanzada.

---

### Criterios de Aceptación Medibles (RF Críticos)

#### RF-02 – Autenticación

- Acceso permitido solo con credenciales válidas.
- Registro de intentos fallidos.
- Cierre automático tras 20 minutos.

---

#### RF-06 – Registro de Medicamentos

- No permite campos obligatorios vacíos.
- No permite duplicar código + lote.
- Asignación obligatoria de sede.
- Persistencia correcta en base de datos.

---

#### RF-09 – Descuento de Stock

- Reducción automática tras venta confirmada.
- No permite stock negativo.
- Registro en historial con usuario y fecha.

---

#### RF-10 – Alertas de Vencimiento

- Genera alertas configurables (30 y 15 días).
- Bloquea productos vencidos.
- No permite su venta.

---

#### RF-14 – Historial de Movimientos

- Registra usuario, fecha/hora, tipo, sede y cantidad.
- No permite modificación posterior.
- Permite filtrado por fecha y producto.

---

#### RF-16 / RF-17 – Concurrencia

- No permite inconsistencias simultáneas.
- Refleja cambios en otros clientes ≤ 15 segundos.
- Aplica transacciones completas o rollback.

---

### Definición de la Versión Mínima Viable (MVP)

La MVP incluye exclusivamente los elementos clasificados como MUST HAVE:

1. Seguridad y autenticación.
2. Registro y control de medicamentos por lote y vencimiento.
3. Entradas y salidas con descuento automático.
4. Historial completo de movimientos.
5. Alertas de vencimiento.
6. Concurrencia controlada.
7. Reportes básicos.
8. Validaciones e integridad transaccional.

La MVP garantiza control, trazabilidad, integridad y funcionamiento multiusuario estable.

---

### Matriz de Trazabilidad (Necesidades ↔ RF ↔ RNF)

| Necesidad del Negocio | RF Asociados | RNF Asociados |
|------------------------|--------------|---------------|
| Control centralizado | RF-06, RF-11, RF-15 | RNF-14, RNF-29 |
| Gestión operativa interna | RF-12, RF-13, RF-09 | RNF-11, RNF-13 |
| Control por lote y vencimiento | RF-06, RF-10 | RNF-12, RNF-06 |
| Actualización en tiempo real | RF-17 | RNF-05, RNF-14 |
| Concurrencia segura | RF-16 | RNF-05, RNF-07 |
| Trazabilidad y auditoría | RF-05, RF-14 | RNF-18, RNF-19 |
| Seguridad y control de acceso | RF-01, RF-02 | RNF-15, RNF-16, RNF-31 |
| Soporte para decisiones | RF-15 | RNF-04 |
| Reducción de errores operativos | RF-09, RF-10 | RNF-32 |

---

### ¿Porqué Moscow?

La aplicación de MoSCoW permite:

- Priorizar el núcleo crítico del sistema.
- Definir claramente la MVP.
- Establecer entregas incrementales.
- Garantizar alineación entre necesidades del negocio y requerimientos técnicos.
- Reducir riesgos en la primera versión del sistema.

