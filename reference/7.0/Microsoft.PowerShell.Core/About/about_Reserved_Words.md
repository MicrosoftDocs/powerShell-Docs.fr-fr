---
description: Répertorie les mots réservés qui ne peuvent pas être utilisés comme identificateurs, car ils ont une signification particulière dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: c4b67a523a40319635d159791b80ab302b9aa3b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208153"
---
# <a name="about-reserved-words"></a>À propos des mots réservés

## <a name="short-description"></a>DESCRIPTION COURTE
Répertorie les mots réservés qui ne peuvent pas être utilisés comme identificateurs, car ils ont une signification particulière dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Il existe certains mots qui ont une signification particulière dans PowerShell. Lorsque ces mots apparaissent sans guillemets, PowerShell tente d’appliquer leur signification spéciale plutôt que de les traiter comme des chaînes de caractères. Pour utiliser ces mots comme arguments de paramètre dans une commande ou un script sans appeler leur signification spéciale, mettez les mots réservés entre guillemets.

Les mots réservés dans PowerShell sont les suivants :

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

Plusieurs mots clés de langage, y compris `Foreach` ,, `If` `For` et `While` , ont leurs propres Articles d’aide. Pour les afficher, tapez `Get-Help about_` et ajoutez le mot clé. Par exemple, pour obtenir des informations sur l' `Foreach` instruction, tapez :

```powershell
Get-Help about_ForEach
```

Pour plus d’informations sur l' `Filter` instruction ou la syntaxe de l' `Return` instruction, tapez :

```powershell
Get-Help about_Functions
```

Pour plus d’informations sur les autres mots réservés, tapez :

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> Tous les mots réservés n’ont pas leur propre article d’aide. Si `Get-Help` ne retourne pas d’article, vous pouvez rechercher des articles qui traitent du mot réservé à l’aide de la commande suivante :
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a>VOIR AUSSI

- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Language_Keywords](about_Language_Keywords.md)
- [about_Parsing](about_Parsing.md)
- [about_Quoting_Rules](about_Quoting_Rules.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Special_Characters](about_Special_Characters.md)
