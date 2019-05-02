---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utiliser des informations d’identification avec des ressources DSC
ms.openlocfilehash: af54c286ce744cd7db0b0e2d05087f60cdf1a33c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080048"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="f1b0b-103">Utiliser des informations d’identification avec des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="f1b0b-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="f1b0b-104">S’applique à : Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f1b0b-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="f1b0b-105">Vous pouvez exécuter une ressource DSC sous un jeu d’informations d’identification spécifié à l’aide de la propriété automatique **PsDscRunAsCredential** dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span>
<span data-ttu-id="f1b0b-106">Par défaut, DSC exécute chaque ressource comme compte système.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-106">By default, DSC runs each resource as the system account.</span></span>
<span data-ttu-id="f1b0b-107">Voici les heures où l’exécution en tant qu’utilisateur est nécessaire, par exemple, l’installation de packages MSI dans un contexte d’utilisateur spécifique, la définition de clés de Registre d’un utilisateur, l’accès à un annuaire local spécifique d’un utilisateur ou l’accès à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span>

<span data-ttu-id="f1b0b-108">Toutes les ressources DSC ont une propriété **PsDscRunAsCredential** qui peut être définie sur n’importe quelles informations d’identification de l’utilisateur (un objet [PSCredential](/dotnet/api/system.management.automation.pscredential)).</span><span class="sxs-lookup"><span data-stu-id="f1b0b-108">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span>
<span data-ttu-id="f1b0b-109">Les informations d’identification peuvent être codées en dur comme valeur de la propriété dans la configuration, ou vous pouvez définir la valeur sur [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), ce qui invite l’utilisateur à entrer des informations d’identification lors de la compilation de la configuration (pour plus d’informations sur la compilation des configurations, consultez [Configurations](configurations.md)).</span><span class="sxs-lookup"><span data-stu-id="f1b0b-109">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f1b0b-110">Dans PowerShell 5.0, l’utilisation de la propriété **PsDscRunAsCredential** dans des configurations appelant des ressources composites n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-110">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span>
> <span data-ttu-id="f1b0b-111">Dans PowerShell 5.1, la propriété **PsDscRunAsCredential** est prise en charge dans les configurations appelant des ressources composites.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-111">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span>
> <span data-ttu-id="f1b0b-112">La propriété **PsDscRunAsCredential** n’est pas disponible dans PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-112">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="f1b0b-113">Dans l’exemple suivant, `Get-Credential` est utilisée pour demander les informations d’identification de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-113">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span>
<span data-ttu-id="f1b0b-114">La ressource **Registry** permet de modifier la clé de Registre qui spécifie la couleur d’arrière-plan de la fenêtre d’invite de commandes Windows.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-114">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

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

> [!NOTE]
> <span data-ttu-id="f1b0b-115">Cet exemple part du principe que vous disposez d’un certificat valide dans `C:\publicKeys\targetNode.cer` et que l’empreinte du certificat est la valeur affichée.</span><span class="sxs-lookup"><span data-stu-id="f1b0b-115">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span>
> <span data-ttu-id="f1b0b-116">Pour plus d’informations sur le chiffrement des informations d’identification dans les fichiers MOF de configuration DSC, consultez [Sécurisation du fichier MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="f1b0b-116">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
