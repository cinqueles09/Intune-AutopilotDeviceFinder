<img src="https://github.com/user-attachments/assets/fc62dabf-260b-47fb-bff2-15d0ba0f75b5" alt="Imagen" width="300" height="300">

## Objective

This tool is designed for scenarios where, in a fleet of devices managed by **Intune**, we have a large number of machines and need to locate a device's **Hash ID** without having access to the serial number. Additionally, if the serial number is available, the tool allows identifying how many "orphan" devices are associated with the same Hash ID.

The issue arises when using **hybrid Autopilot** and formatting a device without removing its corresponding object from **Active Directory (AD)**. In this case, **Entra Connect** syncs the object, uploading it to **Azure AD**, turning it into an **orphan object**.

This tool will help **eliminate this issue** by enabling the identification and management of orphan devices in the system, even without knowing the serial number, making device fleet administration easier.

## Description

This script enables management of devices in **Azure Active Directory (Azure AD)** and **Autopilot**, providing the ability to search for devices by **name** or **serial number**.

- When searching by **device name**, the script retrieves the device’s **ZTDID** from Autopilot and displays related information, including the owners associated with that **ZTDID**.
- When searching by **serial number**, the script retrieves the corresponding **ZTDID** and then searches for related devices in **Azure AD**.

## Requirements

- **Requires connection to Microsoft Graph** with the following permissions:
  - `Device.Read.All`
  - `User.Read.All`
  
- **Dependencies**:
  - PowerShell module `Microsoft.Graph`
  - PowerShell module `WindowsAutopilotIntune`

- **Requires PowerShell** with sufficient privileges to execute the aforementioned modules.

## Usage

The script is interactive and requires the user to provide a **device name** or **serial number** to perform the search.

### Parameters

- **deviceName**: The name of the device to search for in Azure AD. If this parameter is provided, the script will look for devices matching that name and display the corresponding **ZTDID**.
- **serialNumber**: The serial number of the device to search for in Autopilot. If this parameter is provided, the script will find the device with that serial number and then display the associated devices in Azure AD.

### Examples

#### Example 1: Search for device by name

```powershell
# Enter the device name
Enter the device name: AutoPilot-PC

```
#### Example 2: Search for device by serial number

```powershell
# Enter the device's serial number
Enter the serial number: ABC123456789

