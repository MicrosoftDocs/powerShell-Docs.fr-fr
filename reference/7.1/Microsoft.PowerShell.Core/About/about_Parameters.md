---
description: Décrit comment utiliser les paramètres de commande dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: 024c539e83fc84ccad2e27b513d71a3f7be8ea14
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208273"
---
# <a name="about-parameters"></a>À propos des paramètres

## <a name="short-description"></a>Description courte
Décrit comment utiliser les paramètres de commande dans PowerShell.

## <a name="long-description"></a>Description longue

La plupart des commandes PowerShell, telles que les applets de commande, les fonctions et les scripts, s’appuient sur des paramètres pour permettre aux utilisateurs de sélectionner des options ou de fournir une entrée. Les paramètres suivent le nom de la commande et se présentent sous la forme suivante :

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

Le nom du paramètre est précédé d’un trait d’Union (-), qui signale à PowerShell que le mot qui suit le trait d’Union est un nom de paramètre. Le nom et la valeur du paramètre peuvent être séparés par un espace ou un signe deux-points. Certains paramètres ne nécessitent pas ou n’acceptent pas une valeur de paramètre. D’autres paramètres requièrent une valeur, mais ne requièrent pas le nom du paramètre dans la commande.

Le type de paramètres et la configuration requise pour ces paramètres varient. Pour rechercher des informations sur les paramètres d’une commande, utilisez l’applet de commande `Get-Help` . Par exemple, pour rechercher des informations sur les paramètres de l’applet de commande `Get-ChildItem` , tapez :

```powershell
Get-Help Get-ChildItem
```

Pour rechercher des informations sur les paramètres d’un script, utilisez le chemin d’accès complet au fichier de script. Par exemple :

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

L' `Get-Help` applet de commande retourne divers détails sur la commande, y compris une description, la syntaxe de la commande, des informations sur les paramètres et des exemples montrant comment utiliser les paramètres dans une commande.

Vous pouvez également utiliser le paramètre parameter de l' `Get-Help` applet de commande pour rechercher des informations sur un paramètre particulier. Ou bien, vous pouvez utiliser le paramètre de **paramètre** avec la valeur de caractère générique ( `*` ) pour rechercher des informations sur tous les paramètres de la commande. Par exemple, la commande suivante obtient des informations sur tous les paramètres de l’applet de commande `Get-Member` :

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>Valeurs de paramètres par défaut

Les paramètres facultatifs ont une valeur par défaut, qui est la valeur utilisée ou supposée lorsque le paramètre n’est pas spécifié dans la commande.

Par exemple, la valeur par défaut du paramètre **ComputerName** de nombreuses applets de commande est le nom de l’ordinateur local. Par conséquent, le nom de l’ordinateur local est utilisé dans la commande, sauf si le paramètre **ComputerName** est spécifié.

Pour rechercher la valeur de paramètre par défaut, consultez la rubrique d’aide de l’applet de commande. La description du paramètre doit inclure la valeur par défaut.

Vous pouvez également définir une valeur par défaut personnalisée pour n’importe quel paramètre d’une applet de commande ou d’une fonction avancée. Pour plus d’informations sur la définition des valeurs par défaut personnalisées, consultez [about_Parameters_Default_Values](about_Parameters_Default_Values.md).

### <a name="parameter-attribute-table"></a>Table d’attributs de paramètre

Lorsque vous utilisez les paramètres **complet** , **Parameter** ou **Online** de l’applet de commande `Get-Help` , `Get-Help` affiche une table d’attributs de paramètre avec des informations détaillées sur le paramètre.

Ces informations comprennent les détails que vous devez connaître pour utiliser le paramètre.
Par exemple, la rubrique d’aide de l' `Get-ChildItem` applet de commande contient les détails suivants sur son paramètre Path :

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

Les informations sur les paramètres incluent la syntaxe du paramètre, une description du paramètre et les attributs du paramètre. Les sections suivantes décrivent les attributs du paramètre.

#### <a name="parameter-required"></a>Paramètre requis

Ce paramètre indique si le paramètre est obligatoire, c’est-à-dire si toutes les commandes qui utilisent cette applet de commande doivent inclure ce paramètre. Lorsque la valeur est **true** et que le paramètre est manquant dans la commande, PowerShell vous invite à entrer une valeur pour le paramètre.

#### <a name="parameter-position"></a>Position du paramètre

Si le `Position` paramètre est défini sur un entier positif, le nom du paramètre n’est pas obligatoire. Ce type de paramètre est appelé un paramètre positionnel et le nombre indique la position dans laquelle le paramètre doit apparaître par rapport à d’autres paramètres positionnels. Un paramètre nommé peut figurer dans n’importe quelle position après le nom de l’applet de commande. Si vous incluez le nom de paramètre pour un paramètre positionnel, le paramètre peut être listé dans n’importe quelle position après le nom de l’applet de commande.

Par exemple, l' `Get-ChildItem` applet de commande a des paramètres Path et Exclude. Le `Position` paramètre **path** a la valeur **0** , ce qui signifie qu’il s’agit d’un paramètre positionnel. Le `Position` paramètre de l’option **exclure** est **nommé** .

Cela signifie que le **chemin d’accès** n’a pas besoin du nom du paramètre, mais que sa valeur de paramètre doit être la première ou la seule valeur de paramètre sans nom dans la commande.
Toutefois, étant donné que le paramètre Exclude est un paramètre nommé, vous pouvez le placer dans n’importe quelle position de la commande.

À la suite des `Position` paramètres de ces deux paramètres, vous pouvez utiliser l’une des commandes suivantes :

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

Si vous deviez inclure un autre paramètre positionnel sans inclure le nom du paramètre, ce paramètre doit être placé dans l’ordre spécifié par le `Position` paramètre.

#### <a name="parameter-type"></a>Type de paramètre

Ce paramètre spécifie le type de Microsoft .NET Framework de la valeur de paramètre. Par exemple, si le type est **Int32** , la valeur du paramètre doit être un entier. Si le type est String, la valeur du paramètre doit être une chaîne de caractères. Si la chaîne contient des espaces, la valeur doit être placée entre guillemets, ou les espaces doivent être précédés du caractère d’échappement (').

#### <a name="default-value"></a>Valeur par défaut

Ce paramètre spécifie la valeur que le paramètre doit supposer si aucune autre valeur n’est fournie. Par exemple, la valeur par défaut du paramètre Path est souvent le répertoire actif. Les paramètres obligatoires n’ont jamais de valeur par défaut.
Pour de nombreux paramètres facultatifs, il n’y a pas de valeur par défaut, car le paramètre n’a aucun effet s’il n’est pas utilisé.

#### <a name="accepts-multiple-values"></a>Accepte plusieurs valeurs

Ce paramètre indique si un paramètre accepte plusieurs valeurs de paramètre.
Lorsqu’un paramètre accepte plusieurs valeurs, vous pouvez taper une liste séparée par des virgules comme valeur du paramètre dans la commande, ou enregistrer une liste séparée par des virgules (un tableau) dans une variable, puis spécifier la variable comme valeur de paramètre.

Par exemple, le paramètre ServiceName de l' `Get-Service` applet de commande accepte plusieurs valeurs. Les commandes suivantes sont valides :

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>Accepte l’entrée de pipeline

Ce paramètre indique si vous pouvez utiliser l’opérateur de pipeline ( `|` ) pour envoyer une valeur au paramètre.

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

Lorsqu’un paramètre a la valeur « true (par valeur) », PowerShell tente d’associer toute valeur dirigée à ce paramètre avant de tenter d’autres méthodes pour interpréter la commande.

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

Par exemple, vous pouvez diriger une valeur vers un paramètre de **nom** uniquement lorsque la valeur a une propriété appelée **Name** .

> [!NOTE]
> Un paramètre typé qui accepte l’entrée de pipeline ( `by Value` ) ou ( `by PropertyName` ) permet d’utiliser des blocs de script de **liaison différée** sur le paramètre.
>
> Le bloc **de script de liaison différée** est exécuté automatiquement pendant la **ParameterBinding** . Le résultat est lié au paramètre. La liaison différée ne fonctionne **pas** pour les paramètres définis en tant que type `ScriptBlock` ou `System.Object` , le bloc de script est passé **sans** être appelé.
>
> Vous pouvez en savoir plus sur **les blocs de script de liaison différée** ici [about_Script_Blocks. MD](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>Accepte les caractères génériques

Ce paramètre indique si la valeur du paramètre peut contenir des caractères génériques afin que la valeur du paramètre puisse être mise en correspondance avec plusieurs éléments existants dans le conteneur cible.

#### <a name="common-parameters"></a>Paramètres communs

Les paramètres communs sont des paramètres que vous pouvez utiliser avec n’importe quelle applet de commande. Pour plus d’informations sur les paramètres communs, consultez [about_CommonParameters](about_CommonParameters.md).

## <a name="see-also"></a>Voir aussi

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_Pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)

