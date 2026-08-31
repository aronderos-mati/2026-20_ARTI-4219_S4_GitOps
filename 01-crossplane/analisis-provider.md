# =====================================================================
# Análisis del Provider PostgreSQL
# =====================================================================

## Provider: tages/provider-postgresql v0.1.0

### 1. Managed Resources disponibles

| Categoría | Recurso (Kind) | Grupo de API | Descripción |
| :--- | :--- | :--- | :--- |
| **Estructura y Bases de Datos** | `Database` | `postgresql.postgresql.upbound.io` | Crea, actualiza y gestiona una base de datos completa dentro del servidor. |
| **Estructura y Bases de Datos** | `Schema` | `postgresql.postgresql.upbound.io` | Administra esquemas (namespaces lógicos para tablas, vistas, etc.) en una BD. |
| **Estructura y Bases de Datos** | `Extension` | `postgresql.postgresql.upbound.io` | Instala y gestiona extensiones nativas (ej. `uuid-ossp`, `postgis`). |
| **Estructura y Bases de Datos** | `Function` | `postgresql.postgresql.upbound.io` | Crea funciones o procedimientos almacenados definidos por el usuario. |
| **Seguridad y Control de Acceso** | `Role` | `postgresql.postgresql.upbound.io` | Crea y gestiona roles (usuarios o grupos de permisos) en el clúster. |
| **Seguridad y Control de Acceso** | `Role` | `grant.postgresql.upbound.io` | Administra la membresía entre roles (hereda permisos otorgando un rol a otro rol). |
| **Seguridad y Control de Acceso** | `Grant` | `postgresql.postgresql.upbound.io` | Otorga o revoca privilegios explícitos sobre objetos (tablas, secuencias) a un rol. |
| **Seguridad y Control de Acceso** | `Privileges` | `default.postgresql.upbound.io` | Configura privilegios por defecto para los nuevos objetos que se creen en un esquema. |
| **Seguridad y Control de Acceso** | `Mapping` | `user.postgresql.upbound.io` | Crea un mapeo de usuarios para autenticarse contra servidores remotos (Foreign Servers). |
| **Servidores y Replicación** | `Server` | `postgresql.postgresql.upbound.io` | Define servidores remotos/externos (usualmente con Foreign Data Wrappers). |
| **Servidores y Replicación** | `Publication` | `postgresql.postgresql.upbound.io` | Crea publicaciones para replicación lógica de tablas específicas. |
| **Servidores y Replicación** | `Subscription` | `postgresql.postgresql.upbound.io` | Crea suscripciones a publicaciones remotas para recibir flujo de datos replicado. |
| **Servidores y Replicación** | `ReplicationSlot` | `physical.postgresql.upbound.io` | Gestiona ranuras de replicación física reteniendo logs WAL. |
| **Servidores y Replicación** | `Slot` | `replication.postgresql.upbound.io` | Administra ranuras de replicación lógica decodificando transacciones. |

### 2. Campos requeridos del recurso Database

 El objeto raíz `forProvider` es obligatorio (tiene la etiqueta roja **Required**). Sin embargo, **todos los campos internos listados carecen de esta etiqueta**, lo que indica que, según esta definición específica, todos son **opcionales** (muchos asumen valores por defecto de la base de datos o de la instancia si se omiten).

| Campo | Tipo | Descripción Corta | Estado |
| :--- | :--- | :--- | :--- |
| `allowConnections` | Boolean | Define si se permiten conexiones a la base de datos (por defecto `true`). | Opcional |
| `connectionLimit` | Number | Límite de conexiones concurrentes permitidas (por defecto `-1`, sin límite). | Opcional |
| `encoding` | String | Codificación del conjunto de caracteres a utilizar (ej. UTF8). | Opcional |
| `isTemplate` | Boolean | Si es `true`, permite que la base de datos sea clonada por usuarios con privilegios CREATEDB. | Opcional |
| `lcCollate` | String | Orden de colación (`LC_COLLATE`) aplicado a strings (afecta índices y `ORDER BY`). | Opcional |
| `lcCtype` | String | Clasificación de caracteres (`LC_CTYPE`) para la base de datos (categorización de minúsculas, mayúsculas, etc.). | Opcional |
| `name` | String | Nombre de la base de datos (debe ser único en la instancia configurada). | Opcional |
| `owner` | String | Nombre del rol del usuario que será el propietario de la base de datos. | Opcional |
| `tablespaceName` | String | Nombre del tablespace que se asociará con la base de datos. | Opcional |
| `template` | String | Nombre de la base de datos plantilla desde la cual se creará esta nueva base. | Opcional |

### 3. Información requerida por el ProviderConfig

El único campo requerido para que el ProviderConfig pueda conectarse a PostgreSQL es el name, ya que aparece marcado como required.
