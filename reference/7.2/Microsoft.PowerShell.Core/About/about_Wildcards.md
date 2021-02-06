---
description: Décrit comment utiliser des caractères génériques dans PowerShell.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598777"
---
# <a name="about-wildcards"></a>À propos des caractères génériques

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit comment utiliser des caractères génériques dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les caractères génériques représentent un ou plusieurs caractères. Vous pouvez les utiliser pour créer des séquences de mots dans des commandes. Par exemple, pour obtenir tous les fichiers du `C:\Techdocs` répertoire avec une `.ppt` extension de nom de fichier, tapez :

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

Dans ce cas, le `*` caractère générique astérisque () représente tous les caractères qui apparaissent avant l' `.ppt` extension de nom de fichier.

PowerShell prend en charge les caractères génériques suivants :

|Caractère générique|Description               |Exemple |Faire correspondre        |Aucune correspondance|
|--------|--------------------------|--------|-------------|--------|
|\*      |Correspond à zéro ou plusieurs caractères | un\*  | aA, AG, Apple | Banana |
|?       |Correspond à un caractère de cette position | ? n | , dans, sur | antécédent |
|\[ \]   |Correspond à une plage de caractères | \[ook a-l \] | livre, Cook, look | prit |
|\[ \]   |Rechercher des caractères spécifiques | \[\]ook BC | livre, Cook | rester |

Vous pouvez inclure plusieurs caractères génériques dans le même modèle de mot. Par exemple, pour rechercher des fichiers texte dont les noms commencent par les lettres **a** à **l**, tapez :

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

De nombreuses cmdlets acceptent les caractères génériques dans les valeurs de paramètre. La rubrique d’aide de chaque applet de commande décrit les paramètres qui acceptent des caractères génériques. Pour les paramètres qui acceptent des caractères génériques, leur utilisation ne respecte pas la casse.

Vous pouvez utiliser des caractères génériques dans les commandes et les blocs de script, par exemple pour créer un modèle Word qui représente des valeurs de propriété. Par exemple, la commande suivante obtient les services dans lesquels la valeur de la propriété **serviceType** comprend **interactive**.

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

Dans l’exemple suivant, l' `If` instruction comprend une condition qui utilise des caractères génériques pour rechercher des valeurs de propriété. Si la **Description** du point de restauration inclut **PowerShell**, la commande ajoute la valeur de la propriété **CreationTime** du point de restauration dans un fichier journal.

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a>VOIR AUSSI

[about_Language_Keywords](about_Language_Keywords.md)

[about_If](about_If.md)

[about_Script_Blocks](about_Script_Blocks.md)

