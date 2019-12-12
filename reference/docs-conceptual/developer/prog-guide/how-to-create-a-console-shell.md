---
title: Comment créer un interpréteur de commandes de console | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360268"
---
# <a name="how-to-create-a-console-shell"></a>Guide pratique pour créer un shell de console

Windows PowerShell fournit un outil make-shell, également appelé « make-Kit », qui est utilisé pour créer un interpréteur de commandes de console qui n’est pas extensible. Les coques créées avec ce nouvel outil ne peuvent pas être étendues ultérieurement via un composant logiciel enfichable Windows PowerShell.

## <a name="syntax"></a>Syntaxe

Voici la syntaxe utilisée pour exécuter make-shell à partir d’un fichier make-file.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Paramètres

Voici une brève description des paramètres de make-shell.

> [!CAUTION]
> Les chemins d’accès UNC aux assemblys ne sont pas pris en charge par make-shell.

|Paramètre|Description|
|---------------|-----------------|
|-out n. exe|Obligatoire. Nom de l’interpréteur de commandes à produire. Le chemin d’accès est spécifié dans le cadre de ce paramètre.<br /><br /> Make-shell ajoute « . exe » à cette valeur, s’il n’est pas spécifié. **Attention :**  Ne créez pas de fichier de sortie portant le même nom que le fichier. dll référencé. Si vous tentez cette opération, l’outil make-shell crée un fichier. cs portant le même nom, ce qui remplace le fichier. cs qui contient le code source de l’applet de commande.|
|-namespace NS|Obligatoire. Espace de noms à utiliser pour la classe [System. Management. Automation. instances d’exécution. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) dérivée que make-Kit génère et compile.|
|-lib libdirectory1 [, libdirectory2,..]|Les répertoires dans lesquels sont recherchés les assemblys .NET, y compris les assemblys Windows PowerShell, les assemblys spécifiés par le paramètre `reference`, les assemblys indirectement référencés par un autre assembly et les assemblys système .NET.|
|-Reference CA1. dll [, Ca2. dll,...]|Liste séparée par des virgules des assemblys à inclure dans l’interpréteur de commandes. Ces assemblys incluent tous les assemblys d’applet de commande et de fournisseur, ainsi que les assemblys de ressource qui doivent être chargés. Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les applets de commande et les fournisseurs de base fournis par Windows PowerShell est généré.<br /><br /> Les assemblys peuvent être spécifiés à l’aide de leur chemin d’accès complet. dans le cas contraire, ils seront recherchés à l’aide du chemin d’accès spécifié par le paramètre `lib`.|
|-FormatData FD1 en. format. ps1xml [, FD2. format. ps1xml,...]|Liste séparée par des virgules des données de format à inclure dans l’interpréteur de commandes. Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les données de format fournies par Windows PowerShell est généré.|
|-TypeData TD1. type. ps1xml [, TD2. type. ps1xml,...]|Liste séparée par des virgules des données de type à inclure dans l’interpréteur de commandes. Si ce paramètre n’est pas spécifié, un interpréteur de commandes qui contient uniquement les données de type fournies par Windows PowerShell est généré.|
|-source c1.cs [, c2.cs,...]|Nom d’un fichier, fourni par le développeur de l’interpréteur de commandes, qui contient le code source nécessaire pour générer le shell.<br /><br /> Le fichier de code source peut contenir l’un des codes source suivants :<br /><br /> : Implémentation du gestionnaire d’autorisations qui remplace le gestionnaire d’autorisations par défaut. (Cela peut également être fourni dans un assembly.)<br />-Déclarations d’attribut d’informations d’assembly : telles que AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute et AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|Type qui contient l’implémentation du gestionnaire d’autorisations. Cela peut être défini dans le code source ou compilé dans un assembly (spécifié par le paramètre `reference`). Si ce paramètre n’est pas spécifié, le gestionnaire de sécurité par défaut est utilisé. La valeur doit être le nom de type complet, y compris les espaces de noms.|
|-win32icon i. ico|Icône du fichier. exe pour l’interpréteur de commandes. S’il n’est pas spécifié, l’interpréteur de commandes aura l’icône include par le compilateur c# (le cas échéant).|
|-initscript p. ps1|Profil de démarrage de l’interpréteur de commandes. Le fichier est inclus « en l’or »; aucune vérification de validité n’est effectuée par make-shell.|
|-builtinscript S1. ps1 [, S2. ps1,...]|Liste de scripts intégrés pour l’interpréteur de commandes. Ces scripts sont découverts avant les scripts dans le chemin d’accès et leur contenu ne peut pas être modifié une fois l’interpréteur de commandes généré.<br /><br /> Les fichiers sont inclus « en l’absence »; aucune vérification de validité n’est effectuée par make-shell.|
|-ressource ResourceFile. txt|Fichier. txt contenant les ressources d’aide et de bannière pour l’interpréteur de commandes. La première ressource est nommée ShellHelp et contient le texte affiché si l’interpréteur de commandes est appelé avec le paramètre `help`. La deuxième ressource est nommée ShellBanner et contient le texte et les informations de copyright affichés lorsque l’interpréteur de commandes est lancé en mode interactif.<br /><br /> Si ce paramètre n’est pas fourni, ou si ces ressources ne sont pas présentes, une aide et une bannière génériques sont utilisées.|
|-cscflags cscFlags|Indicateurs qui doivent être passés au C# compilateur (CSC. exe). Celles-ci sont transmises sans modification. Si ce paramètre comprend des espaces, il doit être placé entre guillemets doubles.|
|-?<br /><br /> -help|Affiche les options de ligne de commande message de copyright et make-shell.|
|-verbose|Affiche des informations détaillées pendant la création de l’interpréteur de commandes.|

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)