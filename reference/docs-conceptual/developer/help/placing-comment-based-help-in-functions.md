---
ms.date: 09/12/2016
ms.topic: reference
title: Mise en place de l’aide basée sur les commentaires dans les fonctions
description: Mise en place de l’aide basée sur les commentaires dans les fonctions
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658206"
---
# <a name="placing-comment-based-help-in-functions"></a>Mise en place de l’aide basée sur les commentaires dans les fonctions

Cette rubrique explique où placer l’aide basée sur des commentaires pour une fonction afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur les commentaires à la fonction correcte.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Où placer Comment-Based aide pour une fonction

- Au début du corps de la fonction.

- À la fin du corps de la fonction.

- Avant le `Function` mot clé. Lorsque la fonction se trouve dans un script ou un module de script, il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide basée sur les commentaires et le `Function` mot clé. Sinon, `Get-Help` associe l’aide au script, et non à la fonction.

## <a name="examples-of-help-placement-in-a-function"></a>Exemples de placement d’aide dans une fonction

Les exemples suivants montrent chacune des trois options de placement pour une aide basée sur des commentaires pour une fonction.

### <a name="help-at-the-beginning-of-a-function-body"></a>Aide au début du corps d’une fonction

L’exemple suivant illustre la base de commentaires au début d’un corps de fonction.

```powershell
function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}
```

### <a name="help-at-the-end-of-a-function-body"></a>Aide à la fin du corps d’une fonction

 L’exemple suivant illustre la base de commentaires à la fin d’un corps de fonction.

```powershell
function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}
```

### <a name="help-before-the-function-keyword"></a>Aide avant le mot clé function

 Les exemples suivants illustrent les commentaires basés sur la ligne précédant le mot clé function.

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
