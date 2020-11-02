---
ms.date: 07/16/2020
ms.topic: reference
title: Ressource Registry dans DSC
description: Ressource Registry dans DSC
ms.openlocfilehash: 075f64abffb429b83958d859b0328b4eeec4cee6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142495"
---
# <a name="dsc-registry-resource"></a>Ressource Registry dans DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.x

La ressource **Registry** dans la configuration d’état souhaité (DSC) Windows PowerShell fournit un mécanisme pour gérer les clés et les valeurs de Registre sur un nœud cible.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntaxe

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété |Description |
|---|---|
|Clé |Indique le chemin de la clé de Registre pour laquelle vous voulez garantir un état spécifique. Ce chemin doit inclure la ruche. |
|ValueName |Indique le nom de la valeur de Registre. Pour ajouter ou supprimer une clé de Registre, spécifiez cette propriété en tant que chaîne vide sans définir **ValueType** ou **ValueData** . Pour modifier ou supprimer la valeur par défaut d’une clé de Registre, spécifiez cette propriété en tant que chaîne vide tout en définissant également **ValueType** ou **ValueData** . |
|Force |Si la clé de Registre spécifiée est présente, **Force** la remplace par la nouvelle valeur. Si vous supprimez une clé de Registre avec des sous-clés, la valeur doit être `$true`. |
|Hex |Indique si les données sont exprimées au format hexadécimal. Si elles sont spécifiées, les données de valeur DWORD/QWORD sont présentées au format hexadécimal. Non valide pour les autres types. La valeur par défaut est `$false`. |
|ValueData |Les données de la valeur de Registre. |
|ValueType |Indique le type de la valeur. Les types pris en charge sont les suivants : **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (REG_DWORD 32 bits), **Qword** (REG_QWORD 64 bits), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ). |

## <a name="common-properties"></a>Propriétés communes

|Propriété |Description |
|---|---|
|DependsOn |Indique que la configuration d’une autre ressource doit être exécutée avant celle de cette ressource. Par exemple, si vous voulez exécuter en premier le bloc de script de configuration de ressource ayant l’ID ResourceName et le type ResourceType, utilisez la syntaxe suivante pour cette propriété : `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indique si la clé et la valeur existent. Pour faire en sorte qu’elles existent, définissez cette propriété sur **Present** . Pour faire en sorte qu’elles n’existent pas, définissez la propriété sur **Absent** . La valeur par défaut est **Present** . |
|PsDscRunAsCredential |Définit les informations d’identification pour l’exécution de l’ensemble de la ressource. |

> [!NOTE]
> La propriété commune **PsDscRunAsCredential** a été ajoutée à WMF 5.0 pour permettre l’exécution d’une ressource DSC dans le contexte d’autres informations d’identification. Pour plus d’informations, consultez [Utiliser des informations d’identification avec des ressources DSC](../../../configurations/runasuser.md).

## <a name="examples"></a>Exemples

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a>Exemple 1 : Vérifier une valeur et des données spécifiées sous une clé de Registre spécifiée

Cet exemple vérifie que la valeur de Registre « TestValue » sous une clé nommée « ExampleKey1 » est présente dans la ruche `HKEY\_LOCAL\_MACHINE` et contient les données « TestData ».

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a>Exemple 2 : Vérifier l’existence d’une clé de Registre spécifiée

Cet exemple vérifie qu’une clé nommée « ExampleKey2 » est présente dans la ruche **HKEY\_LOCAL\_MACHINE** .

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> Le changement d’un paramètre de Registre dans la ruche `HKEY_CURRENT_USER` nécessite l’exécution de la configuration à l’aide des informations d’identification de l’utilisateur, et non celles du système. Vous pouvez utiliser la propriété **PsDscRunAsCredential** pour spécifier les informations d’identification de l’utilisateur pour la configuration. Pour obtenir un exemple, consultez [Exécution de DSC avec les informations d’identification de l’utilisateur](../../../configurations/runAsUser.md).
