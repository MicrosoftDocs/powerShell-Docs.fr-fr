---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource Registry dans DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076954"
---
# <a name="dsc-registry-resource"></a>Ressource Registry dans DSC

_S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0_

La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.

## <a name="syntax"></a>Syntaxe

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Propriétés

| Propriété | Description |
| --- | --- |
| Clé| Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique. Ce chemin doit inclure la ruche.|
| ValueName| Indique le nom de la valeur de Registre. Pour ajouter ou supprimer une clé de Registre, spécifiez cette propriété comme une chaîne vide sans définir ValueType ou ValueData. Pour modifier ou supprimer la valeur par défaut d’une clé de Registre, spécifiez cette propriété comme une chaîne vide tout en définissant ValueType ou ValueData.|
| Ensure| Indique si la clé et la valeur existent. Pour vous assurer qu’elles existent, définissez cette propriété sur « Present ». Pour vous assurer qu’elles n’existent pas, définissez la propriété sur « Absent ». La valeur par défaut est « Present ».|
| Force| Si la clé de Registre spécifiée est présente, **Force** la remplace par la nouvelle valeur. Si vous supprimez une clé de Registre avec des sous-clés, la valeur doit être **$true** |
| Hex| Indique si les données sont exprimées au format hexadécimal. Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal. Non valide pour les autres types. La valeur par défaut est **$false**.|
| DependsOn| Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource **ResourceName** de type **ResourceType**, la syntaxe pour utiliser cette propriété est `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Les données de la valeur de Registre.|
| ValueType| Indique le type de la valeur. Les types pris en charge sont les suivants : chaîne (REG_SZ), binaire (REG-BINARY), dword 32 bits (REG_DWORD), qword 64 bits (REG_QWORD), chaîne multiple (REG_MULTI_SZ) et chaîne extensible (REG_EXPAND_SZ). |

## <a name="example"></a>Exemple

Cet exemple permet de s’assurer qu’une clé nommée « ExampleKey » est présente dans la ruche **HKEY\_LOCAL\_MACHINE**.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> Le changement d’un paramètre de Registre dans la ruche `HKEY\CURRENT\USER` nécessite l’exécution de la configuration à l’aide des informations d’identification de l’utilisateur, et non celles du système. Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration. Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../../../configurations/runAsUser.md).
