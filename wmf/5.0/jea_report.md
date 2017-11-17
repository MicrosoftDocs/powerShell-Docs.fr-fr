---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: f3c218fc668e35fa50047459d8031d77cdf985a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="reporting-on-jea"></a><span data-ttu-id="c84ca-102">Création de rapports sur JEA</span><span class="sxs-lookup"><span data-stu-id="c84ca-102">Reporting on JEA</span></span>
<span data-ttu-id="c84ca-103">Pour signaler l’état de votre configuration JEA, vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="c84ca-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="c84ca-104">**Get-PSSessionConfiguration** pour retourner une liste de tous les points de terminaison inscrits sur un ordinateur donné.</span><span class="sxs-lookup"><span data-stu-id="c84ca-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="c84ca-105">**Get-PSSessionCapability** pour créer un rapport sur les capacités dont dispose tout utilisateur donné sur un point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="c84ca-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="c84ca-106">Voici un exemple de **Get-PSSessionCapability** :</span><span class="sxs-lookup"><span data-stu-id="c84ca-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

<span data-ttu-id="c84ca-107">Pour générer un rapport sur les _actions_ effectuées par les utilisateurs pendant une session de JEA, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c84ca-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="c84ca-108">Activer les transcriptions de « procuration de privilège » pour ce point de terminaison JEA et consulter le répertoire de transcription pour obtenir un journal complet des actions de chaque utilisateur</span><span class="sxs-lookup"><span data-stu-id="c84ca-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="c84ca-109">Activer la journalisation des modules PowerShell et inspecter les journaux des événements PowerShell</span><span class="sxs-lookup"><span data-stu-id="c84ca-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>

