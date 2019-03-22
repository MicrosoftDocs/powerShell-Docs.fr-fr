---
ms.date: 08/27/2018
keywords: powershell,applet de commande
title: Obtention d’informations d’aide détaillées
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794567"
---
# <a name="getting-detailed-help-information"></a>Obtention d’informations d’aide détaillées

PowerShell inclut des articles d’aide détaillés qui expliquent les concepts de PowerShell et le langage PowerShell. Il existe également des articles d’aide pour chaque cmdlet et fournisseur, et pour un grand nombre de fonctions et de scripts.

Vous pouvez afficher ces articles d’aide à l’invite de commandes, ou afficher les versions les plus récemment mises à jour de ces articles dans la documentation [PowerShell](/powershell/scripting/overview) en ligne.

## <a name="getting-help-for-cmdlets"></a>Obtention d’aide sur les cmdlets

Pour obtenir de l’aide sur les cmdlets PowerShell, utilisez la cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help). Par exemple, pour obtenir de l’aide sur la cmdlet `Get-ChildItem` :

```powershell
Get-Help Get-ChildItem
```

ou

```powershell
Get-ChildItem -?
```

Vous pouvez même obtenir de l’aide sur l’applet de commande Get-Help. Par exemple :

```powershell
Get-Help Get-Help
```

Pour obtenir la liste de tous les articles d’aide sur la cmdlet dans votre session, tapez :

```powershell
Get-Help -Category Cmdlet
```

Pour afficher une page de chaque article d’aide à la fois, utilisez la fonction `help` ou son alias `man`.
Par exemple, pour afficher l’aide concernant la cmdlet `Get-ChildItem`, tapez

```powershell
man Get-ChildItem
```

ou

```powershell
help Get-ChildItem
```

Pour afficher des informations détaillées, utilisez le paramètre **Detailed** de la cmdlet `Get-Help`. Par exemple, pour obtenir des informations détaillées sur la cmdlet `Get-ChildItem`, tapez :

```powershell
Get-Help Get-ChildItem -Detailed
```

Pour afficher tout le contenu de l’article d’aide, utilisez le paramètre **Full** de la cmdlet `Get-Help`. Par exemple, pour afficher tout le contenu de l’article d’aide pour la cmdlet `Get-ChildItem`, tapez :

```powershell
Get-Help Get-ChildItem -Full
```

Pour obtenir une aide détaillée sur les paramètres d’une cmdlet, utilisez le paramètre **Parameter** de la cmdlet `Get-Help`. Par exemple, pour obtenir une aide détaillée sur tous les paramètres de la cmdlet `Get-ChildItem`, tapez :

```powershell
Get-Help Get-ChildItem -Parameter *
```

Pour afficher uniquement les exemples d’un article d’aide, utilisez le paramètre **Example** de la cmdlet `Get-Help`.
Par exemple, pour afficher uniquement les exemples de l’article d’aide pour l’applet de commande `Get-ChildItem`, tapez :

```powershell
Get-Help Get-ChildItem -Examples
```

Pour plus d’informations sur la manière de rédiger des articles d’aide sur les cmdlets que vous écrivez, consultez [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).

## <a name="getting-conceptual-help"></a>Obtention d’aide conceptuelle

La cmdlet `Get-Help` affiche également des informations sur des articles conceptuels dans PowerShell, dont des articles sur le langage PowerShell. Les articles d’aide conceptuelle commencent par le préfixe « about_ », par exemple, « about_line_editing ». (Le nom de l’article conceptuel doit être saisi en anglais, même dans les versions non anglaises de PowerShell.)

Pour afficher la liste des articles conceptuels, tapez :

```powershell
Get-Help about_*
```

Pour afficher un article d’aide spécifique, tapez son nom, par exemple :

```powershell
Get-Help about_command_syntax
```

Les paramètres de la cmdlet `Get-Help`, tels que **Detailed**, **Parameter** et **Examples**, n’ont aucune incidence sur l’affichage des articles d’aide conceptuelle.

## <a name="getting-help-about-providers"></a>Obtention d’aide sur les fournisseurs

La cmdlet `Get-Help` affiche des informations sur les fournisseurs PowerShell. Pour obtenir de l’aide sur un fournisseur, tapez `Get-Help`, suivi du nom du fournisseur. Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :

```powershell
Get-Help registry
```

Pour obtenir la liste de tous les articles d’aide sur le fournisseur dans votre session, tapez

```powershell
Get-Help -Category provider
```

Les paramètres de la cmdlet `Get-Help`, tels que **Detailed**, **Parameter** et **Examples**, n’ont aucune incidence sur l’affichage des articles d’aide sur le fournisseur.

## <a name="getting-help-about-scripts-and-functions"></a>Obtention d’aide sur les fonctions et les scripts

De nombreux scripts et fonctions dans PowerShell ont des articles d’aide associés. Utilisez la cmdlet `Get-Help` pour afficher les articles d’aide sur les scripts et fonctions.

Pour afficher l’aide sur une fonction, tapez `Get-Help`, suivi du nom de la fonction. Par exemple, pour obtenir de l’aide sur la fonction `Disable-PSRemoting`, tapez :

```powershell
Get-Help Disable-PSRemoting
```

Pour afficher l’aide sur un script, tapez le chemin d’accès au fichier de script. Si le script n’est pas dans un chemin d’accès répertorié dans la variable d’environnement Path, vous devez utiliser le chemin d’accès qualifié complet.

Par exemple, si vous avez un script nommé « TestScript.ps1 » dans le répertoire C:\\PS-Test, pour afficher l’article d’aide sur le script, tapez :

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Les paramètres qui sont conçus pour afficher l’aide sur la cmdlet fonctionnent aussi pour l’aide sur le script et la fonction. Toutefois, l’aide sur les fonctions et les scripts ne s’affiche pas lorsque vous exécutez `Get-Help *`.

Pour plus d’informations sur l’écriture d’articles d’aide pour vos fonctions et vos scripts, consultez les articles suivants :

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Obtention d’aide en ligne

Afficher les articles d’aide en ligne est l’une des meilleures façons d’obtenir de l’aide. Les articles en ligne sont plus faciles à mettre à jour et fournissent le contenu le plus récent.

Pour obtenir l’aide en ligne, utilisez le paramètre **Online** de la cmdlet `Get-Help`. Tous les articles d’aide fournis avec PowerShell, y compris les articles d’aide sur le fournisseur et les articles d’aide conceptuelle (À propos), sont disponibles en ligne dans la documentation [PowerShell](/powershell/scripting/powershell-scripting).

> [!NOTE]
> Vous ne pouvez pas utiliser le paramètre **Online** avec des articles d’aide conceptuelle (about_\*) ou des articles d’aide du fournisseur.
> L’aide en ligne est facultative, donc elle ne fonctionne pas pour chaque cmdlet, fonction ou script.

Par exemple, pour obtenir la version en ligne de l’article d’aide sur la cmdlet `Get-ChildItem`, tapez :

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell ouvre l’article dans votre navigateur par défaut. Si l’aide en ligne est prise en charge pour un article d’aide, vous pouvez également afficher l’URL de l’article d’aide. L’URL apparaît dans la section Liens connexes d’un article d’aide.

Par exemple, pour afficher l’URL de la version en ligne de l’applet de commande Add-Computer, tapez :

```powershell
Get-Help Add-Computer
```

La première ligne de la section Liens connexes de l’article est présentée ci-dessous.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Pour plus d’informations sur la façon de fournir un support en ligne pour vos articles d’aide, consultez [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Voir aussi

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
