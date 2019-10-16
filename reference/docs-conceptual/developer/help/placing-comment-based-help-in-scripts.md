---
title: Placement de l’aide basée sur des commentaires dans des scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361178"
---
# <a name="placing-comment-based-help-in-scripts"></a>Mise en place de l’aide basée sur les commentaires dans les scripts

Cette rubrique explique où placer l’aide basée sur des commentaires pour un script afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur des commentaires à des scripts et non à des fonctions qui peuvent être dans le script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Où placer l’aide basée sur les commentaires pour un script

- Au début du fichier de script. L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.

- À la fin du fichier de script.

  Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction. Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.

## <a name="examples-of-help-placement-in-a-script"></a>Exemples de placement d’aide dans un script

 Les exemples suivants montrent chacune des options de positionnement pour l’aide basée sur des commentaires pour un script.

### <a name="help-at-the-beginning-of-a-script"></a>Aide au début d’un script

 L’exemple suivant illustre la base de commentaires au début d’un script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Aide à la fin d’un script

 L’exemple suivant illustre la base de commentaires à la fin d’un script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```