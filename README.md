# Sistema-integrado-de-gesti-n-de-tareas-y-notificaciones
Automatización de gestión de tareas: desde formularios a Trello/Asana  y notificaciones . Desarrollado con [Make].
![Make.com Logo]![image](https://github.com/user-attachments/assets/8223e1ed-963d-4d1a-94dc-ad8b79c15909) 

# Automatización de Gestión de Tareas y Notificaciones

## Descripción
Este proyecto automatiza la creación y seguimiento de tareas desde formularios (Google Forms/Typeform) hasta gestores como Trello/Asana. Desarrollado con **[Make]**:

-  Creación automática de tareas con detalles del formulario
-  Asignación inteligente 
-  Notificaciones por canal elejido según prioridad
-  Sincronización con hojas de cálculo
-  Recordatorios automáticos tras inactividad

![image](https://github.com/user-attachments/assets/200e8373-691e-46c7-8a27-d15a2e781ab2)
![image](https://github.com/user-attachments/assets/47f3582c-04b4-478f-8354-145b5fe60729)


### Flujo de Trabajo
1. **Trigger**: Monitorea nuevos envíos en formularios mediante conexión API
2. **Router**: Clasifica solicitudes usando filtros programables:
   - Palabras clave ("urgente", "factura", "soporte")
   - Campos específicos (tipo, ubicación, prioridad)
3. **Acciones por categoría**:
   - Crea tareas en Trello/Asana con plantillas predefinidas
   - Asigna automáticamente a equipos/miembros según reglas
   - Envía confirmaciones al remitente vía email/SMS
4. **Registro**: Actualiza Google Sheets/Base de datos con:
   ```plaintext
   Fecha | Remitente | Tipo | Asignado | Estado

![image](https://github.com/user-attachments/assets/e12adf93-9415-4a5c-a4be-9184d29145c3)

## Beneficios Clave

| Característica          | Ventaja                                  |
|-------------------------|------------------------------------------|
| **Trigger automatizado** | Monitorea Google Sheets cada 15 minutos sin intervención manual |
| **Integración Trello**   | Conexión directa vía API oficial (sin intermediarios) |
| **Mapeo de campos**      | Asignación precisa de datos Sheets→Trello |
| **Ejecución programada** | Intervalos configurables (15min/1h/24h) |
| **Registro de acciones** | Trazabilidad completa de operaciones |


## Requisitos Técnicos

### 1. **Cuentas Obligatorias**
- **[Make]**  
  - Cuenta gratuita o de pago (según volumen de operaciones).  

- **Google Workspace**  
  - Credenciales para:  
    - **Google Sheets API** (con permisos de edición).  
     

- **Trello/Asana**  
  - Cuenta con permisos para:  
    - Crear tarjetas/tareas  
    - Modificar estados  

### 2. **Configuraciones Previas**  
#### En Google Cloud Console:  
   - Habilitar Google Sheets API  

#### En Trello/Asana:  
   - Generar token de API  
   - Definir tableros/listas de destino  

### 3. **Estructura Mínima de Datos**  
- **Formulario/Sheets**:  
  ```plaintext
  Timestamp | Nombre | Tipo | Prioridad | Detalles  

# Configuración del Flujo en Make.com

##  Importar el Flujo
1. **Exporta tu flujo actual**:
   - En Make.com, ve a tu escenario > Haz clic en el menú de tres puntos (⋮) > Selecciona **"Export"**.
   - Guarda el archivo `GmailAutomation.json` en tu computadora.

2. **Importar en otro entorno**:
   ```plaintext
   • Crea un nuevo escenario en Make.com
   • Haz clic en "Import" > Sube el archivo JSON
   • Revisa que todos los módulos estén conectados

## Flujo de Trabajo

**Google Sheets Trigger (API):** Monitorea nuevas filas en la hoja de cálculo configurada.  
**Router:** Clasifica entradas usando condiciones programables (campos "Tipo" o "Prioridad").  
**Trello/Asana Action:** Crea tarjetas/tareas con mapeo de campos (Nombre → Título, Detalles → Descripción).  
**Notificaciones:** Envía alertas a Slack/Email según reglas de prioridad.  
**Google Sheets Update:** Registra ID de tarjeta creada y estado en la fila original.  
**Sincronización Bidireccional (Opcional):** Actualiza Sheets cuando cambia el estado en Trello/Asana.  

![image](https://github.com/user-attachments/assets/1875feab-5b4a-4c83-a470-fa1d849a6d43)
![image](https://github.com/user-attachments/assets/1951206e-a4da-4709-b4a6-9a7f8c6b3911)
![image](https://github.com/user-attachments/assets/bcf881e7-dd2e-498b-acff-bd399b417f1f)



##  Estructura del Proyecto
blueprint.json: Definición del flujo de trabajo en formato JSON. README.md: Este archivo.


## Uso del JSON

1. **Importar el flujo**:
   - Descarga `blueprint.json`
   - En Make.com: *Create Scenario* → *Import* → Sube el archivo

## Pruebas

1. **Crear entrada de prueba**:
   - Agrega manualmente una nueva fila en Google Sheets con datos de prueba:
     ```plaintext
     [Fecha] | [Nombre] | [Tipo] | [Prioridad] | [Detalles]
     ```

2. **Verificar automatización**:
   - Confirma que el sistema:
     Creó la tarjeta correspondiente en Trello/Asana  
     Mapeó correctamente todos los campos  
     Registró el ID de tarjeta en Sheets  
     Envió notificaciones (si aplica)  

3. **Prueba de actualización**:
   - Modifica el estado en Trello/Asana  
   - Verifica que Sheets actualizó el estado  
      
##  Autores
**David Sosa**  Y
**Alejandro Ramírez**  
---

## Contribuciones 

### ¡Las contribuciones son bienvenidas! Por favor, abre un issue o un pull request en este repositorio.
