# Diagrama de Base de Datos - Nova Sound 🔊

Este repositorio centraliza el diseño de la base de datos de Nova Sound. Cada área debe agregar sus tablas a este diagrama para poder visualizar las conexiones globales del sistema.

### ¿Por qué usar este archivo en GitHub?
Al escribir nuestro diagrama usando el formato **Mermaid**, GitHub dibujará automáticamente el diagrama visual aquí abajo. Así, nadie tiene que estar dibujando y arrastrando cajitas a mano; el código se encarga de todo.

---

## Diagrama Global (Preview)

> **Instrucciones para el equipo:** Solo agreguen sus tablas y relaciones en el bloque de código de abajo. Cuando hagan `commit`, GitHub actualizará el dibujo al instante.

```mermaid
erDiagram
    %% ==========================================
    %% ÁREA: SISTEMAS
    %% ==========================================

    Roles ||--o{ Usuarios : "tiene"
    Usuarios ||--o{ Bitacora : "registra_acciones_en"
    Usuarios ||--o{ Respaldos_Log : "solicita"

    Roles {
        int id PK
        varchar nombre
    }

    Usuarios {
        int id PK
        varchar nomina UK
        varchar nombre
        int rol_id FK
        boolean activo
    }

    Bitacora {
        int id PK
        datetime fecha
        int usuario_id FK
        varchar modulo
        varchar accion
    }

    Modelos {
        int id PK
        varchar codigo UK
        int piezas_por_caja
    }

    Parametros_Sistema {
        int id PK
        varchar clave UK
        int valor
        varchar descripcion
    }

    Respaldos_Log {
        int id PK
        datetime fecha_hora
        int usuario_id FK
        boolean exitoso
    }
    
    %% ==========================================
    %% ESPACIO PARA OTRAS ÁREAS (Producción, Calidad, Empaque, etc.)
    %% Agregar debajo:
    %% ==========================================
```
