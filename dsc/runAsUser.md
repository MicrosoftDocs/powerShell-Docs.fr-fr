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
# <a name="running-dsc-with-user-credentials"></a>Exécution de DSC avec les informations d’identification de l’utilisateur

> S’applique à : Windows PowerShell 5.0, Windows PowerShell 5.1

Vous pouvez exécuter une ressource DSC sous un jeu d’informations d’identification spécifié à l’aide de la propriété automatique **PsDscRunAsCredential** dans la configuration.
Par défaut, DSC exécute chaque ressource comme compte système.
Voici les heures où l’exécution en tant qu’utilisateur est nécessaire, par exemple, l’installation de packages MSI dans un contexte d’utilisateur spécifique, la définition de clés de Registre d’un utilisateur, l’accès à un annuaire local spécifique d’un utilisateur ou l’accès à un partage réseau.

Toutes les ressources DSC ont une propriété **PsDscRunAsCredential** qui peut être définie sur n’importe quelles informations d’identification de l’utilisateur (un objet [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx)).
Les informations d’identification peuvent être codées en dur comme valeur de la propriété dans la configuration, ou vous pouvez définir la valeur sur [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), ce qui invite l’utilisateur à entrer des informations d’identification lors de la compilation de la configuration (pour plus d’informations sur la compilation des configurations, consultez [Configurations](configurations.md)).

>**Remarque :** Dans PowerShell 5.0, l’utilisation de la propriété **PsDscRunAsCredential** dans des configurations appelant des ressources composites n’est pas prise en charge.
>Dans PowerShell 5.1, la propriété **PsDscRunAsCredential** est prise en charge dans les configurations appelant des ressources composites.

>**Remarque :** La propriété **PsDscRunAsCredential** n’est pas disponible dans PowerShell 4.0.

Dans l’exemple suivant, **Get-Credential** est utilisé pour demander les informations d’identification de l’utilisateur.
La ressource [Registry](registryResource.md) permet de modifier la clé de Registre qui spécifie la couleur d’arrière-plan de la fenêtre d’invite de commandes Windows.

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
>**Remarque :** Cet exemple suppose que vous disposez d’un certificat valide dans `C:\publicKeys\targetNode.cer` et que l’empreinte du certificat est la valeur affichée.
>Pour plus d’informations sur le chiffrement des informations d’identification dans les fichiers MOF de configuration DSC, consultez [Sécurisation du fichier MOF](secureMOF.md).