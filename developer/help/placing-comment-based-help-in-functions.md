---
title: Placer l’aide basée sur un commentaire dans les fonctions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083193"
---
# <a name="placing-comment-based-help-in-functions"></a>Mise en place de l’aide basée sur les commentaires dans les fonctions

Cette rubrique explique où placer aide basée sur une fonction afin que le `Get-Help` applet de commande associe la rubrique d’aide en fonction du commentaire à la fonction correcte.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Où placer l’aide basée sur une fonction

- Au début du corps de la fonction.

- À la fin du corps de la fonction.

- Avant du `Function` mot clé. Lorsque la fonction est dans un script ou d’un module de script, il ne peut pas être plus d’une ligne vide entre la dernière ligne de l’aide de commentaire et le `Function` mot clé. Sinon, `Get-Help` associe l’aide avec le script, et non avec la fonction.

## <a name="examples-of-help-placement-in-a-function"></a>Exemples de sélection élective d’aide dans une fonction

 Les exemples suivants montrent chacun des options trois positionnement pour l’aide basée sur une fonction.

### <a name="help-at-the-beginning-of-a-function-body"></a>Aide au début du corps d’une fonction

 L’exemple suivant montre les commentaires au début du corps d’une fonction.

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

### <a name="help-at-the-end-of-a-function-body"></a>Aide à la fin d’un corps de fonction

 L’exemple suivant montre en fonction de commentaire à la fin d’un corps de fonction.

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

### <a name="help-before-the-function-keyword"></a>Aide avant le mot clé (fonction)

 Les exemples suivants montrent des commentaires sur la ligne avant le mot clé function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```