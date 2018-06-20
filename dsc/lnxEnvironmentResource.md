---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource nxEnvironment dans DSC pour Linux
ms.openlocfilehash: 3c9f39760e0fba7fac060f29f9e808a3a434401f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189480"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Ressource nxEnvironment dans DSC pour Linux

La ressource **nxEnvironment** dans DSC PowerShell fournit un mécanisme permettant de gérer les variables d’environnement système sur un nœud Linux.

## <a name="syntax"></a>Syntaxe

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propriétés

|  Propriété |  Description |
|---|---|
| Name| Spécifie le nom de la variable d’environnement pour laquelle vous voulez garantir un état spécifique.|
| Valeur| Valeur à attribuer à la variable d’environnement.|
| Ensure| Détermine si l’existence de la variable doit être vérifiée. Définissez cette propriété sur « Present » pour vous assurer que la variable existe. Définissez la propriété sur « Absent » pour vous assurer que la variable n’existe pas. La valeur par défaut est « Present ».|
| Path| Définit la variable d’environnement actuellement configurée. Définissez cette propriété sur **$true** si la variable est une variable **Path** ; sinon, affectez-lui la valeur **$false**. La valeur par défaut est **$false**. Si la variable actuellement configurée est une variable **Path**, la valeur fournie par la propriété **Value** est adjointe à la valeur existante.|
| DependsOn | Indique que la configuration d’une autre ressource doit être effectuée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’**ID** **ResourceName** et le type **ResourceType**, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informations supplémentaires

* Si **Path** est absent ou a la valeur **$false**, les variables d’environnement sont gérées dans `/etc/environment`. Vos programmes ou vos scripts peuvent nécessiter que la configuration « source » le fichier `/etc/environment` pour accéder aux variables d’environnement gérées.
* Si **Path** est défini sur **$true**, la variable d’environnement est gérée dans le fichier `/etc/profile.d/DSCenvironment.sh`. Ce fichier est créé s’il n’existe pas. Si **Ensure** est défini sur Absent et **Path** sur **$true**, une variable d’environnement existante n’est supprimée que de `/etc/profile.d/DSCenvironment.sh` et pas des autres fichiers.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la ressource **nxEnvironment** pour s’assurer que **TestEnvironmentVariable** est présent et a la valeur Test-Value. Si **TestEnvironmentVariable** est absent, il est créé.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```