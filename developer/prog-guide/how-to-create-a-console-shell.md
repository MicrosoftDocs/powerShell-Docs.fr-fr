---
title: Comment créer un interpréteur de commandes de Console | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081571"
---
# <a name="how-to-create-a-console-shell"></a>Guide pratique pour créer un shell de console

Windows PowerShell fournit un outil de Make-Shell, également appelé le « make-kit », qui est utilisé pour créer un environnement de console qui n’est pas extensible. Interpréteurs de commandes créées avec ce nouvel outil ne peuvent pas être étendus ultérieurement par le biais d’un composant logiciel enfichable Windows PowerShell.

## <a name="syntax"></a>Syntaxe

Voici la syntaxe utilisée pour exécuter Make-Shell à partir d’un fichier de marque.

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

Voici une brève description des paramètres de Make-Shell.

> [!CAUTION]
> Chemins d’accès UNC aux assemblys ne sont pas pris en charge par Make-Shell.

|Paramètre|Description|
|---------------|-----------------|
|-out n.exe|Obligatoire. Le nom de l’interpréteur de commandes pour produire. Le chemin d’accès est spécifié dans le cadre de ce paramètre.<br /><br /> Make-shell permet d’ajouter « .exe » à cette valeur si elle n’est pas spécifiée. **Attention :**  Ne créez pas un fichier de sortie portant le même nom que le fichier .dll référencé. Si vous essayez de cela, l’outil de Make-Shell crée un fichier .cs portant le même nom, qui remplace le fichier .cs qui a votre code de l’applet de commande.|
|l’espace de noms - ns|Obligatoire. L’espace de noms à utiliser pour la dérivée [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) classe qui le kit de marque génère et compile.|
|-lib libdirectory1 [, libdirectory2,..]|Les répertoires dans lesquels sont recherchées les assemblys .NET, y compris les assemblys Windows PowerShell, les assemblys spécifiés par le `reference` paramètre, les assemblys référencés indirectement par un autre assembly et les assemblys système .NET.|
|-référence ca1.dll[,ca2.dll,...]|Une liste séparée par des virgules des assemblys à inclure dans l’interpréteur de commandes. Ces assemblys inclut toutes les applet de commande et assemblys de fournisseur, ainsi que des assemblys de ressource qui doivent être chargés. Si ce paramètre n’est pas spécifié, puis un interpréteur de commandes est généré qui contient uniquement les applets de commande principales et des fournisseurs fournis par Windows PowerShell.<br /><br /> Les assemblys peuvent être spécifiées à l’aide de leur chemin d’accès complet, sinon ils seront recherchées à l’aide du chemin d’accès spécifié par le `lib` paramètre.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Une liste séparée par des virgules des données de format à inclure dans l’interpréteur de commandes. Si ce paramètre n’est pas spécifié, puis un interpréteur de commandes est généré qui contient uniquement les données de format fournies par Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Une liste séparée par des virgules de type de données à inclure dans l’interpréteur de commandes. Si ce paramètre n’est pas spécifié, puis un interpréteur de commandes est généré qui contient uniquement les données de type fournies par Windows PowerShell.|
|-source c1.cs [, c2.cs,...]|Le nom d’un fichier, fourni par le développeur de l’interpréteur de commandes, qui contient un code source nécessaire pour générer l’interpréteur de commandes.<br /><br /> Le fichier de code source peut contenir du code source suivant :<br /><br /> -L’implémentation du Gestionnaire d’autorisation qui remplace le Gestionnaire d’autorisations par défaut. (Cela peut également être fourni compilé dans un assembly.)<br />-Déclarations d’attribut d’information assembly : telles que le AssemblyCompanyAttribute AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, et AssemblyTrademarkAttribute.|
|-Gestionnaire authorizationManagerType|Le type qui contient l’implémentation du Gestionnaire d’autorisation. Cela peut être défini dans le code source ou compilé dans un assembly (spécifié par le `reference` paramètre). Si ce paramètre n’est pas spécifié, le Gestionnaire de sécurité par défaut est utilisé. La valeur doit être le nom de type complet, y compris les espaces de noms.|
|-win32icon i.ico|L’icône pour le fichier .exe de l’interpréteur de commandes. Si non spécifié, l’interpréteur de commandes aura l’icône incluant le compilateur c# (le cas échéant).|
|-initscript p.ps1|Le profil de démarrage pour l’interpréteur de commandes. Le fichier est inclus » en tant que-est » ; Aucune vérification de validité n’a été effectuée par Make-Shell.|
|-s1.ps1[,s2.ps1 builtinscript,...]|Une liste de scripts intégrés de l’interpréteur de commandes. Ces scripts sont découverts avant les scripts dans le chemin d’accès, et leur contenu ne peut pas être modifié une fois que l’interpréteur de commandes est créé.<br /><br /> Les fichiers sont fournis « en tant que-est » ; Aucune vérification de validité n’a été effectuée par Make-Shell.|
|-resourcefile.txt de ressources|Le fichier .txt qui contient des ressources d’aide et de bannière pour l’interpréteur de commandes. La première ressource est nommée ShellHelp et contient le texte affiché si l’interpréteur de commandes est appelé avec le `help` paramètre. La deuxième ressource est nommée ShellBanner, et il contient le texte et les informations de copyright affichée au lancée de l’interpréteur de commandes en mode interactif.<br /><br /> Si ce paramètre n’est pas fourni ou si ces ressources ne sont pas présents, une aide générique et la bannière sont utilisés.|
|-cscflags cscFlags|Indicateurs qui doivent être passés à la C# compilateur (csc.exe). Ceux-ci sont transmis sans modification. Si ce paramètre comprend des espaces, il doit être encadrée de guillemets doubles.|
|-?<br /><br /> -help|Affiche le message de copyright et les options de ligne de commande Make-Shell.|
|-verbose|Affiche des informations détaillées lors de la création de l’interpréteur de commandes.|

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)