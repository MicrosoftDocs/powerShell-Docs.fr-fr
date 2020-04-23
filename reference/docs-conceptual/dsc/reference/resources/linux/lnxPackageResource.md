---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,installation
title: Ressource nxPackage dans DSC pour Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954816"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>Ressource nxPackage dans DSC pour Linux

La ressource **nxPackage** dans DSC (Desired State Configuration) PowerShell fournit un mécanisme permettant de gérer des packages sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Name |Nom du package pour lequel vous souhaitez garantir un état spécifique. |
|PackageManager |Les valeurs prises en charge sont **yum**, **apt** et **zypper**. Spécifie le gestionnaire de package à utiliser lors de l’installation de packages. Si **FilePath** est spécifié, le chemin fourni est utilisé pour installer le package. Sinon, un gestionnaire de package est utilisé pour installer le package à partir d’un référentiel préconfiguré. Si ni **PackageManager** ni **FilePath** ne sont spécifiés, le gestionnaire de package par défaut pour le système est utilisé. |
|PackageGroup |Si sa valeur est `$true`, **Name** doit correspondre au nom d’un groupe de package à utiliser avec **PackageManager**. **PackageGroup** n’est pas valide si **FilePath** est spécifié. |
|Arguments |Chaîne d’arguments transmise telle quelle au package. |
|ReturnCode |Code de retour attendu. Si le code de retour réel ne correspond pas à la valeur attendue indiquée ici, la configuration retourne une erreur. |
|FilePath |Chemin du fichier contenant le package. |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Détermine si l’existence du package doit être vérifiée. Définissez cette propriété sur **Present** pour vous assurer que le package existe. Définissez la propriété sur **Absent** pour vous assurer que le package n’existe pas. La valeur par défaut est **Present**. |

## <a name="example"></a>Exemple

L’exemple suivant vérifie que le package nommé « httpd » a été installé sur un ordinateur Linux, à l’aide du gestionnaire de package « Yum ».

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```