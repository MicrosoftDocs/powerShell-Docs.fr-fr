---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 5280ef5ff95679dc8721be8f5f81031a4ffe796f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085236"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="9e502-102">Mises à jour de l’objet FileInfo</span><span class="sxs-lookup"><span data-stu-id="9e502-102">Updates to FileInfo object</span></span>
<span data-ttu-id="9e502-103">Les informations de version peuvent prêter à confusion, notamment dans les cas où le fichier a été corrigé.</span><span class="sxs-lookup"><span data-stu-id="9e502-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="9e502-104">Cette version de WMF 5.0 ajoute de nouvelles propriétés de script **FileVersionRaw** et **ProductVersionRaw** aux objets FileInfo.</span><span class="sxs-lookup"><span data-stu-id="9e502-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="9e502-105">Voici les propriétés telles qu’elles sont affichées pour powershell.exe (en supposant que $pid est l’ID du processus PowerShell) :</span><span class="sxs-lookup"><span data-stu-id="9e502-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
