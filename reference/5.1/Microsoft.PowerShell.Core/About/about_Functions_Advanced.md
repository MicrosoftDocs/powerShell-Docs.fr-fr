---
description: Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: 53cba129778161d8c44186eb999387e51bb71e50
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207657"
---
# <a name="about-functions-advanced"></a>À propos des fonctions avancées

## <a name="short-description"></a>DESCRIPTION COURTE
Présente des fonctions avancées permettant de créer des applets de commande à l’aide de scripts.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Une applet de commande est une commande unique qui participe à la sémantique de pipeline de PowerShell. Cela comprend les applets de commande binaires, les fonctions de script avancées, le CDXML et les flux de travail.

Les fonctions avancées vous permettent de créer des applets de commande qui sont écrites en tant que fonction PowerShell. Les fonctions avancées facilitent la création d’applets de commande sans avoir à écrire et compiler une applet de commande binaire. Les applets de commande binaires sont des classes .NET qui sont écrites dans un langage .NET tel que C#.

Les fonctions avancées utilisent l' `CmdletBinding` attribut pour les identifier en tant que fonctions qui agissent comme des applets de commande. L' `CmdletBinding` attribut est semblable à l’attribut d’applet de commande utilisé dans les classes d’applet de commande compilées pour identifier la classe en tant qu’applet de commande. Pour plus d’informations sur cet attribut, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).

L’exemple suivant montre une fonction qui accepte un nom, puis imprime un message d’accueil à l’aide du nom fourni. Notez également que cette fonction définit un nom qui comprend une paire verbe (envoi) et substantif (salutation) comme la paire verbe-substantif d’une applet de commande compilée. Toutefois, il n’est pas nécessaire que les fonctions aient un nom de verbe-substantif.

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

Les paramètres de la fonction sont déclarés à l’aide de l’attribut Parameter.
Cet attribut peut être utilisé seul ou il peut être combiné avec l’attribut alias ou avec plusieurs autres attributs de validation de paramètre. Pour plus d’informations sur la façon de déclarer des paramètres (y compris des paramètres dynamiques ajoutés au moment de l’exécution), consultez [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

Le travail réel de la fonction précédente est effectué dans le bloc Process, qui est l’équivalent de la méthode ProcessingRecord utilisée par les applets de commande compilées pour traiter les données transmises à l’applet de commande. Ce bloc, ainsi que les blocs de début et de fin, sont décrits dans la rubrique [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) .

Les fonctions avancées diffèrent des applets de commande compilées des manières suivantes :

- La liaison de paramètre de fonction avancée ne lève pas d’exception lorsqu’un tableau de chaînes est lié à un paramètre booléen.
- L’attribut ValidateSet et l’attribut ValidatePattern ne peuvent pas passer de paramètres nommés.
- Les fonctions avancées ne peuvent pas être utilisées dans les transactions.

## <a name="see-also"></a>VOIR AUSSI

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
