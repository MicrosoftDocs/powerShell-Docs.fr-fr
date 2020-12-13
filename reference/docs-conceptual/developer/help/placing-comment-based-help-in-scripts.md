---
ms.date: 09/12/2016
ms.topic: reference
title: Mise en place de l’aide basée sur les commentaires dans les scripts
description: Mise en place de l’aide basée sur les commentaires dans les scripts
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645446"
---
# <a name="placing-comment-based-help-in-scripts"></a>Mise en place de l’aide basée sur les commentaires dans les scripts

Cette rubrique explique où placer l’aide basée sur les commentaires pour un script afin que l’applet de commande `Get-Help` associe la rubrique d’aide basée sur des commentaires à des scripts et non à des fonctions qui peuvent être dans le script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Où placer Comment-Based aide pour un script

- Au début du fichier de script.

  L’aide sur les scripts peut être précédée du script uniquement par des commentaires et des lignes vides.

- À la fin du fichier de script.

  Si le premier élément du corps du script (après l’aide) est une déclaration de fonction, il doit y avoir au moins deux lignes vides entre la fin de l’aide du script et la déclaration de la fonction. Dans le cas contraire, l’aide est interprétée comme une aide pour la fonction, et non pour l’aide du script.

## <a name="examples-of-help-placement-in-a-script"></a>Exemples de placement d’aide dans un script

Les exemples suivants montrent chacune des options de positionnement pour l’aide basée sur des commentaires pour un script.

### <a name="help-at-the-beginning-of-a-script"></a>Aide au début d’un script

L’exemple suivant illustre la base de commentaires au début d’un script.

```powershell
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
