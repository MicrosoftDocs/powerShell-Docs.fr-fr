---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219529"
---
# <a name="register-a-powershell-repository"></a>Inscrire un dépôt PowerShell
Vous pouvez configurer PowerShellGet pour qu’il opère sur des dépôts internes. Vous devez pour cela utiliser les ajouts suivants :
- Register-PSRepository : inscrit un dépôt pour l’utilisateur actuel.
- Unregister-PSRepository : supprime un dépôt inscrit pour l’utilisateur actuel.
- Set-PSRepository : définir des valeurs pour un dépôt inscrit.
- Get-PSRepository : obtenir tous les dépôts inscrits pour l’utilisateur actuel.

Après avoir inscrit un dépôt, vous pouvez utiliser Find-Module et Install-Module pour l’utiliser.

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
