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
ms.openlocfilehash: 3c5736be7066a749744482cb79edad2f53705f07
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564105"
---
# <a name="comment-based-help-keywords"></a>Mots clés de l’aide basée sur les commentaires

Cette rubrique répertorie et décrit les mots clés de l’aide basée sur les commentaires.

## <a name="keywords-in-comment-based-help"></a>Mots clés dans l’aide basée sur des commentaires

Les éléments suivants sont des mots clés d’aide basés sur des commentaires valides. Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que l’utilisation prévue. Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide basée sur les commentaires, et ils ne respectent pas la casse.

Notez que le `.ExternalHelp` mot clé est prioritaire sur tous les autres mots clés d’aide basés sur les commentaires. Lorsque `.ExternalHelp` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.

`.Synopsis`Brève description de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

`.Description`Description détaillée de la fonction ou du script. Ce mot clé ne peut être utilisé qu’une seule fois dans chaque rubrique.

`.Parameter`* \< Parameter-Name>* la description d’un paramètre. Vous pouvez inclure un `.Parameter` mot clé pour chaque paramètre dans la fonction ou le script.

Les `.Parameter` Mots clés peuvent apparaître dans n’importe quel ordre dans le bloc de commentaires, mais l’ordre dans lequel les paramètres apparaissent dans la `Param` déclaration d’instruction ou de fonction détermine l’ordre dans lequel les paramètres apparaissent dans la rubrique d’aide. Pour modifier l’ordre des paramètres dans la rubrique d’aide, modifiez l’ordre des paramètres dans la `Param` déclaration de l’instruction ou de la fonction.

Vous pouvez également spécifier une description de paramètre en plaçant un commentaire dans l' `Param` instruction juste avant le nom de la variable de paramètre. Si vous utilisez à la fois un `Param` commentaire d’instruction et un `.Parameter` mot clé, la description associée au `.Parameter` mot clé est utilisée et le commentaire de l' `Param` instruction est ignoré.

`.Example`Exemple de commande qui utilise la fonction ou le script, éventuellement suivi d’un exemple de sortie et d’une description. Répétez ce mot clé pour chaque exemple.

`.Inputs`Microsoft .NET Framework types d’objets qui peuvent être dirigés vers la fonction ou le script. Vous pouvez également inclure une description des objets d’entrée.

`.Outputs`.NET Framework type des objets que l’applet de commande retourne. Vous pouvez également inclure une description des objets retournés.

`.Notes`Informations supplémentaires sur la fonction ou le script.

`.Link`Nom d’une rubrique associée. Répétez ce mot clé pour chaque rubrique associée. Ce contenu apparaît dans la section Liens connexes de la rubrique d’aide.

Le `.Link` contenu du mot clé peut également inclure une Uniform Resource Identifier (Uri) à une version en ligne de la même rubrique d’aide. La version en ligne s’ouvre lorsque vous utilisez le `Online` paramètre de la boîte de passe obtenir-Help. L’URI doit commencer par « http » ou « HTTPS ».

`.Component`Technologie ou fonctionnalité utilisée par la fonction ou le script, ou à laquelle elle est associée. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le `Component` paramètre de la commande obtenir-Help.

`.Role`Rôle d’utilisateur pour la rubrique d’aide. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le `Role` paramètre de la commande obtenir-Help.

`.Functionality`Utilisation prévue de la fonction. Ce contenu s’affiche lorsque la commande obtenir-Help comprend le `Functionality` paramètre de la commande obtenir-Help.

`.ForwardHelpTargetName``<Command-Name>`Redirige vers la rubrique d’aide pour la commande spécifiée. Vous pouvez rediriger les utilisateurs vers n’importe quelle rubrique d’aide, y compris les rubriques d’aide d’une fonction, d’un script, d’une applet de commande ou d’un fournisseur.

`.ForwardHelpCategory``<Category>`Spécifie la catégorie d’aide de l’élément dans ForwardHelpTargetName. Les valeurs valides sont alias, applet de commande, FichierAide, fonction, fournisseur, général, FAQ, Glossaire, commande, ExternalScript, filtre ou tout. Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.

`.RemoteHelpRunspace``<PSSession-variable>`Spécifie une session qui contient la rubrique d’aide. Entrez une variable qui contient une session PSSession. Ce mot clé est utilisé par l' `Export-PSSession` applet de commande pour rechercher les rubriques d’aide pour les commandes exportées.

`.ExternalHelp``<XML Help File>`Spécifie le chemin d’accès et/ou le nom d’un fichier d’aide XML pour le script ou la fonction.

Le `.ExternalHelp` mot clé indique à l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) d’obtenir de l’aide sur le script ou la fonction dans un fichier XML. **. **Le mot clé commentaire ExternalHelp est requis lors de l’utilisation d’un fichier d’aide XML pour un script ou une fonction. Sans celui-ci, `Get-Help` ne trouvera pas de fichier d’aide pour la fonction ou le script.

Le `.ExternalHelp` mot clé est prioritaire sur tous les autres mots clés d’aide basés sur les commentaires. Lorsque `.ExternalHelp` est présent, l’applet de [commande Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) n’affiche pas d’aide basée sur les commentaires, même lorsqu’il ne trouve pas de fichier d’aide qui correspond à la valeur du mot clé.

Lorsque la fonction est exportée par un module de script, la valeur de `.ExternalHelp` doit être un nom de fichier sans chemin d’accès. `Get-Help`recherche le fichier dans un sous-répertoire spécifique aux paramètres régionaux du répertoire du module. Il n’existe aucune condition requise pour le nom de fichier, mais il est recommandé d’utiliser le format de nom de fichier suivant : `<ScriptModule>.psm1-help.xml` .

Quand la fonction n’est pas associée à un module, incluez un chemin d’accès et un nom de fichier dans la valeur de **. **Mot clé commentaire ExternalHelp. Si le chemin d’accès spécifié au fichier XML contient des sous-répertoires spécifiques à la culture de l’interface utilisateur, `Get-Help` recherche les sous-répertoires de manière récursive pour un fichier XML portant le nom du script ou de la fonction conformément aux normes de langue de secours établies pour Windows, tout comme pour toutes les rubriques d’aide basées sur XML.

Pour plus d’informations sur le format de fichier d’aide XML de l’applet de commande, consultez écriture de l’aide sur les [applets de commande Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).
