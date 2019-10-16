---
title: Mots clés d’aide basés sur des commentaires | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361358"
---
# <a name="comment-based-help-keywords"></a>Mots clés de l’aide basée sur les commentaires

Cette rubrique répertorie et décrit les mots clés de l’aide basée sur les commentaires.

## <a name="keywords-in-comment-based-help"></a>Mots clés dans l’aide basée sur des commentaires

Les éléments suivants sont des mots clés d’aide basés sur des commentaires valides. Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que l’utilisation prévue. Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide basée sur les commentaires, et ils ne respectent pas la casse.

Notez que le mot clé `.ExternalHelp` est prioritaire sur tous les autres mots clés d’aide basés sur des commentaires. Lorsque `.ExternalHelp` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.

`.Synopsis` une brève description de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

`.Description` une description détaillée de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

`.Parameter` *\<Parameter-Name >* la description d’un paramètre. Vous pouvez inclure un mot clé `.Parameter` pour chaque paramètre dans la fonction ou le script.

Les mots clés `.Parameter` peuvent apparaître dans n’importe quel ordre dans le bloc de commentaires, mais l’ordre dans lequel les paramètres apparaissent dans l’instruction `Param` ou la déclaration de fonction détermine l’ordre dans lequel les paramètres apparaissent dans la rubrique d’aide. Pour modifier l’ordre des paramètres dans la rubrique d’aide, modifiez l’ordre des paramètres dans l’instruction `Param` ou la déclaration de fonction.

Vous pouvez également spécifier une description de paramètre en plaçant un commentaire dans l’instruction `Param` immédiatement avant le nom de la variable de paramètre. Si vous utilisez à la fois un commentaire d’instruction `Param` et un mot clé `.Parameter`, la description associée au mot clé `.Parameter` est utilisée et le commentaire de l’instruction `Param` est ignoré.

`.Example` un exemple de commande qui utilise la fonction ou le script, éventuellement suivi d’un exemple de sortie et d’une description. Répétez ce mot clé pour chaque exemple.

`.Inputs` les types d’Microsoft .NET Framework d’objets qui peuvent être dirigés vers la fonction ou le script. Vous pouvez également inclure une description des objets d’entrée.

`.Outputs` type de .NET Framework des objets retournées par l’applet de commande. Vous pouvez également inclure une description des objets retournés.

`.Notes` informations supplémentaires sur la fonction ou le script.

`.Link` nom d’une rubrique associée. Répétez ce mot clé pour chaque rubrique associée. Ce contenu apparaît dans la section Liens connexes de la rubrique d’aide.

Le contenu du mot clé `.Link` peut également inclure un Uniform Resource Identifier (URI) à une version en ligne de la même rubrique d’aide. La version en ligne s’ouvre lorsque vous utilisez le paramètre `Online` de la rubrique obtenir-Help. L’URI doit commencer par « http » ou « HTTPS ».

`.Component` la technologie ou la fonctionnalité utilisée par la fonction ou le script, ou à laquelle elle est associée. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le paramètre `Component` de l’option « obtenir-aide ».

`.Role` le rôle d’utilisateur pour la rubrique d’aide. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le paramètre `Role` de l’option « obtenir-aide ».

`.Functionality` l’utilisation prévue de la fonction. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le paramètre `Functionality` de l’option « obtenir-aide ».

`.ForwardHelpTargetName` `<Command-Name>` redirige vers la rubrique d’aide de la commande spécifiée. Vous pouvez rediriger les utilisateurs vers n’importe quelle rubrique d’aide, y compris les rubriques d’aide d’une fonction, d’un script, d’une applet de commande ou d’un fournisseur.

`.ForwardHelpCategory` `<Category>` spécifie la catégorie d’aide de l’élément dans ForwardHelpTargetName. Les valeurs valides sont alias, applet de commande, FichierAide, fonction, fournisseur, général, FAQ, Glossaire, commande, ExternalScript, filtre ou tout. Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.

`.RemoteHelpRunspace` `<PSSession-variable>` spécifie une session qui contient la rubrique d’aide. Entrez une variable qui contient une session PSSession. Ce mot clé est utilisé par l’applet de commande `Export-PSSession` pour rechercher les rubriques d’aide pour les commandes exportées.

`.ExternalHelp` `<XML Help File>` spécifie le chemin d’accès et/ou le nom d’un fichier d’aide XML pour le script ou la fonction.

Le mot clé `.ExternalHelp` indique à l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) d’obtenir de l’aide pour le script ou la fonction dans un fichier XML. **.** Le mot clé commentaire ExternalHelp est requis lors de l’utilisation d’un fichier d’aide XML pour un script ou une fonction. Si ce n’est pas le cas, `Get-Help` ne trouvera pas de fichier d’aide pour la fonction ou le script.

Le mot clé `.ExternalHelp` est prioritaire sur tous les autres mots clés d’aide basés sur les commentaires. Lorsque `.ExternalHelp` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.

Lorsque la fonction est exportée par un module de script, la valeur de `.ExternalHelp` doit être un nom de fichier sans chemin d’accès. `Get-Help` recherche le fichier dans un sous-répertoire spécifique aux paramètres régionaux du répertoire du module. Il n’existe aucune condition requise pour le nom de fichier, mais il est recommandé d’utiliser le format de nom de fichier suivant : `<ScriptModule>.psm1-help.xml`.

Quand la fonction n’est pas associée à un module, incluez un chemin d’accès et un nom de fichier dans la valeur de **.** Mot clé commentaire ExternalHelp. Si le chemin d’accès spécifié au fichier XML contient des sous-répertoires spécifiques à la culture de l’interface utilisateur, `Get-Help` recherche les sous-répertoires de manière récursive pour un fichier XML portant le nom du script ou de la fonction conformément aux normes de langue de secours établies pour Windows , tout comme pour toutes les rubriques d’aide basées sur XML.

Pour plus d’informations sur le format de fichier d’aide XML de l’applet de commande, consultez écriture de l’aide sur les [applets de commande Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).