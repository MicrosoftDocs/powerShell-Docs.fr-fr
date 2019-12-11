---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Ressource File DSC
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954676"
---
# <a name="dsc-file-resource"></a>Ressource File DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **File** dans DSC Windows PowerShell propose un mécanisme permettant de gérer les fichiers et les dossiers sur le nœud cible. **DestinationPath** et **SourcePath** doivent être accessibles au nœud cible.

## <a name="syntax"></a>Syntaxe

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|DestinationPath |Emplacement sur le nœud cible où vous voulez vérifier que la propriété **Ensure** a la valeur **Present** ou **Absent**. |
|Attributes |L’état souhaité des attributs du fichier ou du répertoire cible. Les valeurs valides sont _Archive_, _Hidden_, _ReadOnly_ et _System_. |
|Checksum |Le type de somme de contrôle à utiliser pour déterminer si deux fichiers sont identiques. Les valeurs valides sont les suivantes : **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Contents |Valide uniquement quand elle est utilisée avec **Type** **File**. Indique le contenu dont la présence ou l’absence doivent être garanties à partir du fichier cible avec **Ensure** et les valeurs **Present** ou **Absent**. |
|Credential |Les informations d’identification nécessaires pour accéder aux ressources, telles que des fichiers sources. |
|Force |Remplace les opérations d’accès qui entraîneraient une erreur (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire qui n’est pas vide). La valeur par défaut est `$false`. |
|Recurse |Valide uniquement quand elle est utilisée avec **Type** **Directory**. Exécute l’opération d’état de manière récursive sur tous les sous-répertoires. La valeur par défaut est `$false`. |
|SourcePath |Chemin à partir duquel copier la ressource de fichier ou de dossier. |
|Type |Le type de ressource en cours de configuration. Les valeurs valides sont **Directory** et **File**. La valeur par défaut est **File**. |
|MatchSource |Détermine si la ressource doit contrôler les nouveaux fichiers ajoutés au répertoire source après la copie initiale. La valeur `$true` indique que, après la copie initiale, les nouveaux fichiers source doivent être copiés dans la destination. Si la valeur est définie sur `$false`, la ressource met en cache le contenu du répertoire source et ignore les fichiers ajoutés après la copie initiale. La valeur par défaut est `$false`. |

> [!WARNING]
> Si vous ne spécifiez pas de valeur pour **Credential** ou **PSRunAsCredential**, la ressource utilise le compte d’ordinateur du nœud cible pour accéder à **SourcePath**. Quand **SourcePath** représente un partage UNC, cela peut provoquer une erreur « Accès refusé ». Vérifiez que vos autorisations sont définies en conséquence, ou utilisez les propriétés **Credential** ou **PSRunAsCredential** pour spécifier le compte qui doit être utilisé.

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine si le fichier et le contenu (**Contents**) à **Destination** doivent exister ou non. Définissez cette propriété sur **Present** pour garantir l’existence du fichier. Définissez la propriété sur **Absent** pour vous assurer que le contenu ne se trouve pas à l’emplacement donné. La valeur par défaut est **Present**. |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Informations complémentaires

- Quand vous spécifiez uniquement un **DestinationPath**, la ressource vérifie que le chemin existe si la valeur définie est **Present** ou qu’il n’existe pas si la valeur définie est **Absent**.
- Quand vous spécifiez un **SourcePath** et un **DestinationPath** et que **Type** a la valeur **Directory**, la ressource copie le répertoire source sur le chemin de destination. Les propriétés **Recurse**, **Force** et **MatchSource** modifient le type d’opération de copie effectuée, tandis que **Credential** détermine le compte à utiliser pour accéder au répertoire source.
- Si vous avez spécifié la valeur **ReadOnly** pour la propriété **Attributes** avec un **DestinationPath**, **Ensure** **Present** crée le chemin spécifié, tandis que **Contents** définit le contenu du fichier. Un paramètre **Ensure** **Absent** ignore entièrement la propriété **Attributes** et supprime les fichiers situés sur le chemin spécifié.

## <a name="example"></a>Exemple

L’exemple suivant copie un répertoire et ses sous-répertoires d’un serveur Pull vers à un nœud cible à l’aide de la ressource File. Si l’opération réussit, la ressource Log consigne un message de confirmation dans le journal des événements.

Le répertoire source est un chemin d’accès UNC (`\\PullServer\DemoSource`) partagé à partir du serveur Pull. La propriété **Recurse** vérifie que tous les sous-répertoires sont également copiés.

> [!IMPORTANT]
> Le gestionnaire de configuration local (LCM) sur le nœud cible s’exécute dans le contexte du compte système local par défaut. Pour autoriser l’accès à **SourcePath**, accordez les autorisations appropriées au compte d’ordinateur du nœud cible. **Credential** et **PSDSCRunAsCredential** modifient tous deux le contexte dont se sert le LCM pour accéder au **SourcePath**. Vous devez quand même accorder l’accès au compte qui sera utilisé pour accéder à **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Pour plus d’informations sur l’utilisation de **Credentials** dans DSC, consultez [Run As User](../../../configurations/runAsUser.md) (Exécuter en tant qu’utilisateur) ou [Config Data Credentials](../../../configurations/configDataCredentials.md) (Informations d’identification des données de configuration).