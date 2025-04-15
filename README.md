<img src="https://github.com/user-attachments/assets/fc62dabf-260b-47fb-bff2-15d0ba0f75b5" alt="Imagen" width="300" height="300">

## Objetivo

Esta herramienta está diseñada para situaciones en las que, en un parque de dispositivos administrados por **Intune**, tenemos una gran cantidad de equipos y necesitamos localizar el **Hash ID** de un dispositivo sin tener acceso al número de serie. Además, si disponemos del número de serie, la herramienta permite identificar cuántos dispositivos "huérfanos" están asociados al mismo Hash ID.

El problema surge cuando utilizamos **Autopilot híbrido** y formateamos un equipo sin eliminar el objeto correspondiente de **Active Directory (AD)**. En este caso, **Entra Connect** sincroniza el objeto, subiéndolo a **Azure AD**, convirtiéndolo en un **objeto huérfano**. 

Esta herramienta nos ayudará a **erradicar este problema**, permitiendo identificar y gestionar dispositivos huérfanos en el sistema, incluso sin contar con el número de serie, lo que facilita la administración del parque de dispositivos.


## Descripción

Este script permite gestionar dispositivos en **Azure Active Directory (Azure AD)** y **Autopilot**, proporcionando la capacidad de buscar dispositivos por **nombre** o **número de serie**.

- Si se realiza la búsqueda por **nombre** de dispositivo, el script obtiene el **ZTDID** del dispositivo en Autopilot y muestra información relacionada, incluyendo los propietarios asociados a ese **ZTDID**.
- Si se realiza la búsqueda por **número de serie**, el script obtiene el **ZTDID** correspondiente del dispositivo y luego busca los dispositivos relacionados en **Azure AD**.

## Requisitos

- **Requiere conexión a Microsoft Graph** con los permisos:
  - `Device.Read.All`
  - `User.Read.All`
  
- **Dependencias**:
  - Módulo `Microsoft.Graph` de PowerShell.
  - Módulo `WindowsAutopilotIntune` de PowerShell.

- **Requiere PowerShell** con permisos suficientes para ejecutar los módulos mencionados.

## Uso

El script es interactivo y requiere que el usuario proporcione un **nombre de dispositivo** o **número de serie** para realizar la búsqueda.

### Parámetros

- **deviceName**: El nombre del dispositivo a buscar en Azure AD. Si se proporciona este parámetro, el script buscará dispositivos que coincidan con ese nombre y mostrará el **ZTDID** correspondiente.
- **serialNumber**: El número de serie del dispositivo a buscar en Autopilot. Si se proporciona este parámetro, el script buscará el dispositivo con ese número de serie y luego mostrará los dispositivos asociados en Azure AD.

### Ejemplos

#### Ejemplo 1: Buscar dispositivo por nombre

```powershell
# Introduce el nombre del dispositivo
Introduzca el nombre del dispositivo: AutoPilot-PC
```
#### Ejemplo 2: Buscar dispositivo por nombre
```powershell
# Introduce el número de serie del dispositivo
Introduzca el número de serie: ABC123456789
