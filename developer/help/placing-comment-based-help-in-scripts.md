---
title: Placer l’aide basée sur les commentaires dans les Scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083227"
---
# <a name="placing-comment-based-help-in-scripts"></a>Mise en place de l’aide basée sur les commentaires dans les scripts

Cette rubrique explique où placer aide basée sur un script afin que le `Get-Help` applet de commande associe la rubrique d’aide en fonction du commentaire avec des scripts et pas avec toutes les fonctions qui peuvent être dans le script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Où placer l’aide basée sur un Script

- Au début du fichier de script. Aide du script peut être précédée dans le script uniquement les lignes vides et les commentaires.

- À la fin du fichier de script.

  Si le premier élément dans le corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide sur le script et la déclaration de fonction. Sinon, l’aide est considérée comme étant aide à l’aide de la fonction, pas pour le script.

## <a name="examples-of-help-placement-in-a-script"></a>Exemples de sélection élective d’aide dans un Script

 Les exemples suivants montrent chacun des options de sélection élective de l’aide de commentaires pour un script.

### <a name="help-at-the-beginning-of-a-script"></a>Aide au début d’un Script

 L’exemple suivant montre des commentaires au début d’un script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Aide à la fin d’un Script

 L’exemple suivant montre en fonction de commentaire à la fin d’un script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```