---
title: Prise en charge des caractères génériques dans les paramètres de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059607"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Prise en charge des caractères génériques dans les paramètres des applets de commande

Souvent, vous devez concevoir une applet de commande à exécuter par rapport à un groupe de ressources, plutôt que sur une seule ressource. Par exemple, une applet de commande deviez trouver tous les fichiers dans un magasin de données qui ont le même nom ou l’extension. Vous devez fournir la prise en charge des caractères génériques lorsque vous concevez une applet de commande qui est exécutée par rapport à un groupe de ressources.

> [!NOTE]
> Utilisation de caractères génériques est parfois appelé *globbing*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Applets de commande Windows PowerShell qui utilisent des caractères génériques

 Nombreuses applets de commande Windows PowerShell prend en charge les caractères génériques pour leurs valeurs de paramètre. Par exemple, presque chaque applet de commande qui a un `Name` ou `Path` paramètre prend en charge les caractères génériques pour ces paramètres. (Bien que la plupart des applets de commande qui ont un `Path` paramètre ont également un `LiteralPath` paramètre qui ne prend pas en charge les caractères génériques.) La commande suivante montre comment un caractère générique est utilisé pour retourner toutes les applets de commande dans la session active, dont le nom contient le verbe Get.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Caractères génériques pris en charge

Windows PowerShell prend en charge les caractères génériques suivants.

|caractère générique|Description|Exemple|Correspond à|Ne correspond pas|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Correspond à zéro ou plusieurs caractères, en commençant à la position spécifiée|a*|A, groupe de disponibilité, Apple||
|?|Tout_caractère correspond à la position spécifiée|?n|Un, dans, sur|exécuté|
|[ ]|Correspond à une plage de caractères|[a-l]ook|book, cook, look|a duré|
|[ ]|Correspond aux caractères spécifiés|[bc]ook|book, cook|coup de œil|

Lorsque vous concevez des applets de commande qui prennent en charge les caractères génériques, autoriser pour les combinaisons de caractères génériques. Par exemple, la commande suivante utilise le `Get-ChildItem` applet de commande pour récupérer tous les fichiers .txt qui se trouvent dans le dossier c:\Techdocs et qui commencent par les lettres « a » à « l. »

**get-childitem c:\techdocs\\[a-l]\*.txt**

La commande précédente utilise le caractère générique de plage **[a-l]** pour spécifier le nom de fichier doit commencer par les caractères « a » à « l. » La commande utilise ensuite le * caractère générique comme espace réservé pour tous les caractères entre la première lettre du nom de fichier et l’extension .txt.

L’exemple suivant utilise un modèle de caractère générique de plage qui exclut la lettre « d », mais inclut toutes les autres lettres de « a » à « f. »

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Gestion des caractères littéraux dans les modèles de caractère générique

Si le modèle de caractère générique que vous spécifiez contient des caractères littéraux, utilisez le caractère accent grave (') comme caractère d’échappement. Lorsque vous spécifiez des caractères littéraux par programmation, utilisez un accent grave unique. Lorsque vous spécifiez des caractères littéraux à l’invite de commandes, utilisez deux accents graves. Par exemple, le modèle suivant contient deux crochets doivent être prises littéralement.

« John Smith \`[*'] » (spécifié par programmation)

« John Smith \` \`[*\`«] » (spécifié à l’invite de commande)

Ce modèle correspond à « John Smith [Marketing] » ou « John Smith (développement) ».

## <a name="cmdlet-output-and-wildcard-characters"></a>Sortie de l’applet de commande et des caractères génériques

Lorsque les paramètres de l’applet de commande prennent en charge les caractères génériques, une opération de l’applet de commande génère habituellement une sortie de tableau. Parfois, il n’a aucun sens pour prendre en charge d’un tableau de sortie, car l’utilisateur peut utiliser qu’un seul élément à la fois. Par exemple, le `Set-Location` applet de commande ne prend pas en charge un tableau de sortie, car l’utilisateur ne définit qu’un seul emplacement. Dans ce cas, l’applet de commande prend toujours en charge les caractères génériques, mais il force la résolution vers un emplacement unique.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Classe de WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
