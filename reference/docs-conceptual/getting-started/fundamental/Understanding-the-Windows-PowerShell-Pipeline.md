---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Compréhension du pipeline Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951067"
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Compréhension du pipeline Windows PowerShell
Le piping fonctionne pratiquement partout dans Windows PowerShell. Même si vous voyez du texte à l’écran, Windows PowerShell ne canalise pas de texte entre des commandes. Au lieu de cela, il canalise des objets.

La notation utilisée pour les pipelines est similaire à celle utilisée dans d’autres interpréteurs de commandes. Ainsi, à première vue, les nouveautés de Windows PowerShell peuvent ne pas sembler évidentes. Par exemple, si vous utilisez l’applet de commande **Out-Host** pour forcer un affichage page par page de la sortie d’une autre commande, la sortie ressemble exactement au texte normal affiché à l’écran, mais divisé en pages :

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

La commande Out-Host -Paging est un élément de pipeline utile chaque fois que vous avez une sortie longue que vous souhaitez afficher lentement. Elle est particulièrement utile si l’opération nécessite une utilisation importante du processeur. Étant donné que le traitement est transféré à l’applet de commande Out-Host quand une page complète est prête pour affichage, les applets de commande précédentes dans le pipeline suspendent l’opération jusqu’à ce que la page de sortie suivante est disponible. Vous pouvez voir cela si vous utilisez le Gestionnaire des tâches de Windows pour surveiller l’utilisation du processeur et de la mémoire par Windows PowerShell.

Exécutez la commande suivante : **Get-ChildItem C:\\Windows -Recurse**. Comparez l’utilisation du processeur et de la mémoire à la sortie de la commande suivante : **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**. Si ce que vous voyez à l’écran est du texte, c’est parce qu’il est de nécessaire représenter les objets sous forme de texte dans une fenêtre de console. Il s’agit juste d’une représentation de ce qui se passe vraiment dans Windows PowerShell. Par exemple, considérez l’applet de commande Get-Location. Si vous tapez **Get-Location** alors que votre emplacement actuel est la racine du lecteur C, la sortie est la suivante :

```
PS> Get-Location

Path
----
C:\
```

Si le texte figure dans un pipeline Windows PowerShell, l’émission d’une commande telle que **Get-Location | Out-Host** a pour effet de transmettre de **Get-Location** à **Out-Host** un jeu de caractères dans l’ordre de leur affichage à l’écran. En d’autres termes, si vous deviez ignorer les informations d’en-tête, **Out-Host** recevrait d’abord le caractère « **C »**, puis le caractère «  **: »**, puis le caractère '**\\'**. Il se pourrait que l’applet de commande **Out-Host** ne puisse pas déterminer quelle signification associer à la sortie de caractères par l’applet de commande **Get-Location**.

Au lieu d’utiliser du texte pour vous permettre aux commandes dans un pipeline de communiquer, Windows PowerShell utilise des objets. Du point de vue d’un utilisateur, les objets empaquètent des informations connexes sous une forme facilitant la manipulation des informations en tant qu’unité, et l’extraction des éléments spécifiques dont vous avez besoin.

La commande **Get-Location** ne retourne pas de texte contenant le chemin d’accès actuel. Elle retourne un ensemble d’informations appelé objet **PathInfo**, qui contient le chemin d’accès actuel, ainsi que d’autres informations. L’applet de commande **Out-Host** envoie ensuite cet objet **PathInfo** à l’écran, tandis que Windows PowerShell choisit les informations à afficher et leur mode d’affichage en fonction de ses règles de mise en forme.

En fait, les informations d’en-tête retournées par l’applet de commande **Get-Location** ne sont ajoutées qu’à la fin du processus, dans le cadre de la mise en forme des données à afficher à l’écran. Ce que vous voyez à l’écran est un résumé des informations, non une représentation complète de l’objet de sortie.

Étant donné qu’il peut y avoir plus d’informations générées par une commande Windows PowerShell que ce que nous voyons dans la fenêtre de console, comment récupérer les éléments invisibles ? Comment afficher les données supplémentaires ? Et que se passe-t-il si vous souhaitez afficher les données dans un format différent de celui que Windows PowerShell utilise normalement ?

Le reste de ce chapitre explique comment découvrir la structure d’objets Windows PowerShell spécifiques, en sélectionnant des éléments et en les mettant en forme pour un affichage plus facile, ainsi que comment envoyer ces informations à d’autres emplacements de sortie tels que des fichiers et des imprimantes.