---
title: Prise en charge des caractères génériques dans les paramètres des applets de commande
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104442"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Prise en charge des caractères génériques dans les paramètres des applets de commande

Souvent, vous devez concevoir une applet de commande à exécuter sur un groupe de ressources plutôt que sur une seule ressource. Par exemple, une applet de commande peut avoir besoin de localiser tous les fichiers d’une banque de données qui ont le même nom ou extension. Vous devez fournir la prise en charge des caractères génériques lors de la conception d’une applet de commande qui sera exécutée sur un groupe de ressources.

> [!NOTE]
> L’utilisation de caractères génériques est parfois appelée *globbing*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Applets de commande Windows PowerShell utilisant des caractères génériques

 De nombreuses applets de commande Windows PowerShell prennent en charge les caractères génériques pour leurs valeurs de paramètres. Par exemple, presque toutes les applets de `Name` commande `Path` avec un paramètre ou prennent en charge les caractères génériques pour ces paramètres. (Bien que la plupart des cmdlets `Path` ayant un paramètre aient `LiteralPath` également un paramètre qui ne prend pas en charge les caractères génériques.) La commande suivante montre comment un caractère générique est utilisé pour retourner toutes les applets de commande de la session active dont le nom contient le verbe obtenir.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Caractères génériques pris en charge

Windows PowerShell prend en charge les caractères génériques suivants.

| Caractère générique |                             Description                             |  Exemples   |     Correspond à      | Ne correspond pas |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Correspond à zéro ou plusieurs caractères, en commençant à la position spécifiée | `a*`       | A, AG, Apple     |                |
| ?        | Correspond à n’importe quel caractère à la position spécifiée                     | `?n`       | , Dans, sur       | antécédent            |
| [ ]      | Correspond à une plage de caractères                                       | `[a-l]ook` | livre, Cook, look | Nook, pris     |
| [ ]      | Correspond aux caractères spécifiés                                    | `[bn]ook`  | livre, Nook       | Cook, regarder     |

Lorsque vous concevez des applets de commande qui prennent en charge les caractères génériques, autorisez les combinaisons de caractères génériques. Par exemple, la commande suivante utilise l' `Get-ChildItem` applet de commande pour récupérer tous les fichiers. txt qui se trouvent dans le dossier c:\techdocs et qui commencent par les lettres «a» à «l».

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

La commande précédente utilise le caractère générique `[a-l]` de plage pour spécifier que le nom de fichier doit commencer par les caractères «a» à «l» `*` et utilise le caractère générique comme espace réservé pour tous les caractères de la première lettre du nom de fichier et extension **. txt** .

L’exemple suivant utilise un modèle de caractère générique de plage qui exclut la lettre «d», mais inclut toutes les autres lettres de «a» à «f».

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Gestion des caractères littéraux dans les modèles de caractères génériques

Si le modèle de caractère générique que vous spécifiez contient des caractères littéraux qui ne doivent pas être interprétés comme des`` ` ``caractères génériques, utilisez le caractère de soulignement () comme caractère d’échappement. Lorsque vous spécifiez des caractères littéraux int l’API PowerShell, utilisez un seul cycle. Lorsque vous spécifiez des caractères littéraux à l’invite de commandes PowerShell, utilisez deux cycles.

Par exemple, le modèle suivant contient deux crochets qui doivent être pris littéralement.

En cas d’utilisation dans l’API PowerShell, utilisez:

- «John Smith \`[* ']»

En cas d’utilisation à partir de l’invite de commandes PowerShell:

- «John Smith \` \`[*\`']»

Ce modèle correspond à «John Smith [marketing]» ou «John Smith [Development]». Par exemple :

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Sortie de l’applet de commande et caractères génériques

Lorsque les paramètres d’applet de commande prennent en charge les caractères génériques, l’opération génère généralement une sortie de tableau.
Parfois, il n’est pas judicieux de prendre en charge une sortie de tableau, car l’utilisateur ne peut utiliser qu’un seul élément. Par exemple, l' `Set-Location` applet de commande ne prend pas en charge la sortie de tableau, car l’utilisateur ne définit qu’un seul emplacement. Dans ce cas, l’applet de commande prend toujours en charge les caractères génériques, mais elle force la résolution sur un emplacement unique.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[WildcardPattern, classe](/dotnet/api/system.management.automation.wildcardpattern)
