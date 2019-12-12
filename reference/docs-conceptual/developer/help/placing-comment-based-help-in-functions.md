---
title: Placement de l’aide basée sur des commentaires dans les fonctions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367778"
---
# <a name="placing-comment-based-help-in-functions"></a>Mise en place de l’aide basée sur les commentaires dans les fonctions

Cette rubrique explique où placer l’aide basée sur les commentaires pour une fonction afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur des commentaires à la fonction correcte.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Où placer l’aide basée sur les commentaires pour une fonction

- Au début du corps de la fonction.

- À la fin du corps de la fonction.

- Avant le mot clé `Function`. Lorsque la fonction se trouve dans un script ou un module de script, il ne peut pas y avoir plus d’une ligne vide entre la dernière ligne de l’aide basée sur les commentaires et le mot clé `Function`. Dans le cas contraire, `Get-Help` associe l’aide au script, et non à la fonction.

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