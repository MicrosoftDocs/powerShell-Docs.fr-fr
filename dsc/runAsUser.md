---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Exécution de DSC avec les informations d’identification de l’utilisateur
ms.openlocfilehash: b2992ad562dea375aba980611312c7b96a23189c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="running-dsc-with-user-credentials"></a><span data-ttu-id="a9742-103">Exécution de DSC avec les informations d’identification de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a9742-103">Running DSC with user credentials</span></span>

> <span data-ttu-id="a9742-104">S’applique à : Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="a9742-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="a9742-105">Vous pouvez exécuter une ressource DSC sous un jeu d’informations d’identification spécifié à l’aide de la propriété automatique **PsDscRunAsCredential** dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a9742-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="a9742-106">Par défaut, DSC exécute chaque ressource comme compte système.</span><span class="sxs-lookup"><span data-stu-id="a9742-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="a9742-107">Voici les heures où l’exécution en tant qu’utilisateur est nécessaire, par exemple, l’installation de packages MSI dans un contexte d’utilisateur spécifique, la définition de clés de Registre d’un utilisateur, l’accès à un annuaire local spécifique d’un utilisateur ou l’accès à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="a9742-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="a9742-108">Toutes les ressources DSC ont une propriété **PsDscRunAsCredential** qui peut être définie sur n’importe quelles informations d’identification de l’utilisateur (un objet [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx)).</span><span class="sxs-lookup"><span data-stu-id="a9742-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx) object).</span></span>
<span data-ttu-id="a9742-109">Les informations d’identification peuvent être codées en dur comme valeur de la propriété dans la configuration, ou vous pouvez définir la valeur sur [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), ce qui invite l’utilisateur à entrer des informations d’identification lors de la compilation de la configuration (pour plus d’informations sur la compilation des configurations, consultez [Configurations](configurations.md)).</span><span class="sxs-lookup"><span data-stu-id="a9742-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

><span data-ttu-id="a9742-110">**Remarque :** Dans PowerShell 5.0, l’utilisation de la propriété **PsDscRunAsCredential** dans des configurations appelant des ressources composites n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="a9742-110">**Note:** In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
><span data-ttu-id="a9742-111">Dans PowerShell 5.1, la propriété **PsDscRunAsCredential** est prise en charge dans les configurations appelant des ressources composites.</span><span class="sxs-lookup"><span data-stu-id="a9742-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>

><span data-ttu-id="a9742-112">**Remarque :** La propriété **PsDscRunAsCredential** n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="a9742-112">**Note:** The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="a9742-113">Dans l’exemple suivant, **Get-Credential** est utilisé pour demander les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9742-113">In the following example, **Get-Credential** is used to prompt the user for credentials.</span></span>
<span data-ttu-id="a9742-114">La ressource [Registry](registryResource.md) permet de modifier la clé de Registre qui spécifie la couleur d’arrière-plan de la fenêtre d’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="a9742-114">The [Registry](registryResource.md) resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
><span data-ttu-id="a9742-115">**Remarque :** Cet exemple suppose que vous disposez d’un certificat valide dans `C:\publicKeys\targetNode.cer` et que l’empreinte du certificat est la valeur affichée.</span><span class="sxs-lookup"><span data-stu-id="a9742-115">**Note:** This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
><span data-ttu-id="a9742-116">Pour plus d’informations sur le chiffrement des informations d’identification dans les fichiers MOF de configuration DSC, consultez [Sécurisation du fichier MOF](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="a9742-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](secureMOF.md).</span></span>