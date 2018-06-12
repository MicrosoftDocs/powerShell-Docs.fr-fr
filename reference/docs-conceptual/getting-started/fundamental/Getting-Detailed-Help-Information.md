---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Obtention d’informations d’aide détaillées
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483030"
---
# <a name="getting-detailed-help-information"></a>Obtention d’informations d’aide détaillées
Windows PowerShell inclut des rubriques d’aide détaillées qui expliquent les concepts de Windows PowerShell et le langage Windows PowerShell. Il existe également des rubriques d’aide pour chaque applet de commande et fournisseur, et des rubriques d’aide pour un grand nombre de fonctions et de scripts.

Vous pouvez afficher ces rubriques d’aide à l’invite de commandes, ou afficher les versions les plus récemment mises à jour de ces rubriques dans la Bibliothèque Microsoft TechNet. De nombreux programmes hébergeant Windows PowerShell, comme l’environnement d’écriture de scripts intégré de Windows PowerShell, fournissent des fonctionnalités d’aide supplémentaires, telles qu’une aide contextuelle et un fichier d’aide compilé (.chm).

## <a name="getting-help-for-cmdlets"></a>Obtention d’aide sur les applets de commande
Pour obtenir de l’aide sur les applets de commande Windows PowerShell, utilisez l’applet de commande [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2). Par exemple, pour obtenir de l’aide sur l’applet de commande [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), tapez :

```
get-help get-childitem
```

ou

```
get-childitem -?
```

Vous pouvez même obtenir de l’aide sur l’applet de commande Get-Help. Par exemple :

```
get-help get-help
```

Pour obtenir la liste de toutes les rubriques d’aide sur l’applet de commande dans votre session, tapez :

```
get-help -category cmdlet
```

Pour afficher une page de chaque rubrique d’aide à la fois, utilisez la fonction **help** ou son alias **man**. Par exemple, pour afficher l’aide sur l’applet de commande Get-ChildItem, tapez :

```
man get-childitem
```

ou

```
help get-childitem
```

Pour afficher des informations détaillées sur une applet de commande, une fonction ou un script, notamment des descriptions de ses paramètres et des exemples de son utilisation, utilisez le paramètre *Detailed* de l’applet de commande Get-Help. Par exemple, pour obtenir des informations détaillées sur l’applet de commande Get-ChildItem, tapez :

```
get-help get-childitem -detailed
```

Pour afficher tout le contenu de la rubrique d’aide, utilisez le paramètre *Full* de l’applet de commande Get-Help. Par exemple, pour afficher tout le contenu de la rubrique d’aide pour l’applet de commande Get-ChildItem, tapez :

```
get-help get-childitem -full
```

Pour obtenir une aide détaillée sur les paramètres d’une applet de commande, utilisez le paramètre *Parameter* de l’applet de commande Get-Help. Par exemple, pour obtenir une aide détaillée sur tous les paramètres de l’applet de commande Get-ChildItem, tapez :

```
get-help get-childitem -parameter *
```

Pour afficher uniquement les exemples d’une rubrique d’aide, utilisez le paramètre *Example* de l’applet de commande Get-Help. Par exemple, pour afficher uniquement les exemples de la rubrique d’aide sur l’applet de commande Get-ChildItem, tapez :

```
get-help get-childitem -examples
```

Pour plus d’informations sur la manière de rédiger des rubriques d’aide sur les applets de commande que vous écrivez, consultez [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) dans MSDN Library.

## <a name="getting-conceptual-help"></a>Obtention d’aide conceptuelle
L’applet de commande Get-Help affiche également des informations sur des rubriques conceptuelles de Windows PowerShell, dont des rubriques sur le langage Windows PowerShell. Les rubriques d’aide conceptuelle commencent par le préfixe « about_ », par exemple, « about_line_editing ». (Le nom de la rubrique conceptuelle doit être saisi en anglais, même dans les versions non anglaises de Windows PowerShell.)

Pour afficher la liste des rubriques conceptuelles, tapez :

```
get-help about_*
```

Pour afficher une rubrique d’aide spécifique, tapez son nom, par exemple :

```
get-help about_command_syntax
```

Les paramètres de l’applet de commande Get-Help, tels que *Detailed*, *Parameter* et *Examples*, n’ont aucune incidence sur l’affichage des rubriques d’aide conceptuelle.

## <a name="getting-help-about-providers"></a>Obtention d’aide sur les fournisseurs
L’applet de commande Get-Help affiche des informations sur les fournisseurs Windows PowerShell. Pour obtenir de l’aide sur un fournisseur, tapez « Get-Help », suivi du nom du fournisseur. Par exemple, pour obtenir de l’aide sur le fournisseur de Registre, tapez :

```
get-help registry
```

Pour obtenir la liste de toutes les rubriques d’aide sur le fournisseur dans votre session, tapez :

```
get-help -category provider
```

Les paramètres de l’applet de commande Get-Help, tels que *Detailed*, *Parameter* et *Examples*, n’ont aucune incidence sur l’affichage des rubriques d’aide sur le fournisseur.

## <a name="getting-help-about-scripts-and-functions"></a>Obtention d’aide sur les fonctions et les scripts
De nombreux scripts et fonctions dans Windows PowerShell ont des rubriques d’aide associées. Utilisez l’applet de commande Get-Help pour afficher les rubriques d’aide sur les scripts et fonctions.

Pour afficher l’aide sur une fonction, tapez « get-help », suivi du nom de la fonction. Par exemple, pour obtenir de l’aide sur la fonction Disable-PSRemoting, tapez :

```
get-help disable-psremoting
```

Pour afficher l’aide sur un script, tapez le chemin d’accès complet au fichier de script. Si le script figure dans un chemin d’accès répertorié dans la variable d’environnement Path, vous pouvez omettre le chemin d’accès de la commande.

Par exemple, si vous avez un script nommé « TestScript.ps1 » dans le répertoire C:\\PS-Test, pour afficher la rubrique d’aide sur le script, tapez :

```
get-help c:\ps-test\TestScript.ps1
```

Les paramètres conçus pour afficher de l’aide sur l’applet de commande, tels que *Detailed*, *Full*, *Examples*et *Parameter*, opèrent également pour l’aide sur le script et l’aide sur la fonction. Toutefois, lorsque vous affichez toute l’aide en tapant « get-help \* », l’aide sur les fonctions et les scripts ne s’affiche pas.

Pour plus d’informations sur l’écriture de rubriques d’aide pour vos fonctions et les scripts, voir [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af) et [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Obtention d’aide en ligne
Si vous êtes connecté à Internet, l’un des meilleurs moyens d’obtenir de l’aide consiste à afficher les rubriques d’aide en ligne. Étant donné que les rubriques en ligne sont faciles à mettre à jour, il est probable qu’elles fournissent le contenu à jour.

Pour obtenir l’aide en ligne, essayez le paramètre *Online* de l’applet de commande Get-Help. La paramètre *Online* de l’applet de commande Get-Help opère uniquement pour l’applet de commande Help, la fonction Help et le script Help. Vous ne pouvez pas utiliser le paramètre *Online* avec des rubriques conceptuelles (About) ou des rubriques d’aide sur le fournisseur. En outre, étant donné que cette fonctionnalité est facultative, elle n’opère pas pour chaque applet de commande, fonction ou une rubrique d’aide sur un script.

Toutefois, toutes les rubriques d’aide fournies avec Windows PowerShell, y compris l’aide sur le fournisseur et les rubriques d’aide conceptuelle (About) sont disponibles en ligne dans la section [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) de la Bibliothèque Microsoft TechNet.

Pour utiliser le paramètre *Online* de l’applet de commande Get-Help, utilisez le format de commande suivant.

```
get-help <command-name> -online
```

Par exemple, pour obtenir la version en ligne de la rubrique d’aide sur l’applet de commande Get-ChildItem, tapez :

```
get-help get-childitem -online
```

Si une version en ligne de la rubrique d’aide est disponible, elle s’ouvre dans votre navigateur par défaut.

Si l’aide en ligne est prise en charge pour une rubrique d’aide, vous pouvez également afficher l’adresse Internet (URL) de la rubrique d’aide. L’adresse Internet apparaît dans la section Liens connexes d’une rubrique d’aide.

Par exemple, pour afficher l’URL de la version en ligne de l’applet de commande Add-Computer, tapez :

```
get-help add-computer
```

La première ligne de la section Liens connexes de la rubrique est présentée ci-dessous.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Pour plus d’informations sur la manière de fournir un support en ligne pour vos rubriques d’aide, consultez [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) et [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) dans MSDN Library.

## <a name="see-also"></a>Voir aussi
- [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)