---
description: Décrit l’attribut qui fait fonctionner une fonction comme une applet de commande compilée.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: eb6e161fd03898fe420103c04b26c0f6249be590
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207758"
---
# <a name="about-functions-cmdletbindingattribute"></a>À propos des fonctions CmdletBindingAttribute

## <a name="short-description"></a>Description courte
Décrit l’attribut qui fait fonctionner une fonction comme une applet de commande compilée.

## <a name="long-description"></a>Description longue

L' `CmdletBinding` attribut est un attribut des fonctions qui les font fonctionner comme des cmdlets compilées écrites en C#. Il permet d’accéder aux fonctionnalités des applets de commande.

PowerShell lie les paramètres des fonctions qui ont l' `CmdletBinding` attribut de la même manière qu’il lie les paramètres des applets de commande compilées. La `$PSCmdlet` variable automatique est disponible pour les fonctions avec l' `CmdletBinding` attribut, mais la `$Args` variable n’est pas disponible.

Dans les fonctions qui ont l' `CmdletBinding` attribut, les paramètres inconnus et les arguments positionnels qui n’ont pas de paramètres positionnels correspondants provoquent l’échec de la liaison de paramètre.

> [!NOTE]
> Les applets de commande compilées utilisent l’attribut required `Cmdlet` , qui est similaire à l' `CmdletBinding` attribut décrit dans cette rubrique.

## <a name="syntax"></a>Syntaxe

L’exemple suivant illustre le format d’une fonction qui spécifie tous les arguments facultatifs de l' `CmdletBinding` attribut. Une brève description de chaque argument suit cet exemple.

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

L’argument **ConfirmImpact** spécifie quand l’action de la fonction doit être confirmée par un appel à la méthode **ShouldProcess** . L’appel à la méthode **ShouldProcess** affiche une invite de confirmation uniquement lorsque l’argument **ConfirmImpact** est supérieur ou égal à la valeur de la `$ConfirmPreference` variable de préférence. (La valeur par défaut de l’argument est **Medium** .) Spécifiez cet argument uniquement lorsque l’argument **SupportsShouldProcess** est également spécifié.

Pour plus d’informations sur les demandes de confirmation, consultez [demande de confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).

## <a name="defaultparametersetname"></a>DefaultParameterSetName

L’argument **DefaultParameterSetName** spécifie le nom du jeu de paramètres que PowerShell essaiera d’utiliser lorsqu’il ne peut pas déterminer le jeu de paramètres à utiliser. Vous pouvez éviter ce problème en définissant le paramètre unique de chaque paramètre sur un paramètre obligatoire.

## <a name="helpuri"></a>HelpURI

L’argument **HelpURI** spécifie l’adresse Internet de la version en ligne de la rubrique d’aide qui décrit la fonction. La valeur de l’argument **HelpURI** doit commencer par « http » ou « HTTPS ».

La valeur de l’argument **HelpURI** est utilisée pour la valeur de la propriété **HelpURI** de l’objet **CommandInfo** qui `Get-Command` retourne pour la fonction.

Toutefois, lorsque des fichiers d’aide sont installés sur l’ordinateur et que la valeur du premier lien de la section **relatedlinks** du fichier d’aide est un URI, ou que la valeur de la première `.Link` directive dans l’aide basée sur les commentaires est un URI, l’URI du fichier d’aide est utilisé comme valeur de la propriété **HelpUri** de la fonction.

L' `Get-Help` applet de commande utilise la valeur de la propriété **HelpURI** pour rechercher la version en ligne de la rubrique d’aide de la fonction lorsque le paramètre **Online** de `Get-Help` est spécifié dans une commande.

## <a name="supportspaging"></a>SupportsPaging

L’argument **SupportsPaging** ajoute les paramètres **First** , **Skip** et **IncludeTotalCount** à la fonction. Ces paramètres permettent aux utilisateurs de sélectionner une sortie à partir d’un jeu de résultats très volumineux. Cet argument est conçu pour les applets de commande et les fonctions qui retournent des données à partir de banques de données volumineuses prenant en charge la sélection de données, par exemple une base de données SQL.

Cet argument a été introduit dans Windows PowerShell 3,0.

- **First** : obtient uniquement les « n » premiers objets.
- **Ignorer** : ignore les « n » premiers objets, puis obtient les objets restants.
- **IncludeTotalCount** : indique le nombre d’objets dans le jeu de données (un entier) suivis des objets. Si l’applet de commande ne peut pas déterminer le nombre total, elle retourne « nombre total inconnu ».

PowerShell comprend **NewTotalCount** , une méthode d’assistance qui obtient la valeur de nombre total à retourner et comprend une estimation de la précision de la valeur du nombre total.

L’exemple de fonction suivant montre comment ajouter la prise en charge des paramètres de pagination à une fonction avancée.

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

L’argument **SupportsShouldProcess** ajoute des paramètres **Confirm** et **WhatIf** à la fonction. Le paramètre **Confirm** invite l’utilisateur avant d’exécuter la commande sur chaque objet dans le pipeline. Le paramètre **WhatIf** répertorie les modifications apportées par la commande, au lieu d’exécuter la commande.

## <a name="positionalbinding"></a>PositionalBinding

L’argument **PositionalBinding** détermine si les paramètres de la fonction sont positionnels par défaut. La valeur par défaut est `$True`. Vous pouvez utiliser l’argument **PositionalBinding** avec la valeur `$False` pour désactiver la liaison de position.

L’argument **PositionalBinding** est introduit dans Windows PowerShell 3,0.

Lorsque les paramètres sont positionnels, le nom du paramètre est facultatif.
PowerShell associe les valeurs de paramètre sans nom aux paramètres de fonction en fonction de l’ordre ou de la position des valeurs de paramètre sans nom dans la commande de fonction.

Lorsque les paramètres ne sont pas positionnels (ils sont « nommés »), le nom du paramètre (ou une abréviation ou un alias du nom) est requis dans la commande.

Quand **PositionalBinding** a la `$True` valeur, les paramètres de fonction sont positionnels par défaut. PowerShell assigne le numéro de position aux paramètres dans l’ordre dans lequel ils sont déclarés dans la fonction.

Quand **PositionalBinding** a la `$False` valeur, les paramètres de fonction ne sont pas positionnels par défaut. À moins que l’argument **position** de l’attribut **Parameter** ne soit déclaré sur le paramètre, le nom du paramètre (ou un alias ou une abréviation) doit être inclus lorsque le paramètre est utilisé dans une fonction.

L’argument **position** de l’attribut **Parameter** est prioritaire par rapport à la valeur par défaut de **PositionalBinding** . Vous pouvez utiliser l’argument **position** pour spécifier une valeur de position pour un paramètre. Pour plus d’informations sur l’argument **position** , consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

## <a name="notes"></a>Notes

L’argument **SupportsTransactions** n’est pas pris en charge dans les fonctions avancées.

## <a name="keywords"></a>Mots clés

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>Voir aussi

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
