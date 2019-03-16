---
title: Mots clés d’aide en fonction du commentaire | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: af8a151070d26ffe236800076115c964f625e572
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058077"
---
# <a name="comment-based-help-keywords"></a>Mots clés de l’aide basée sur les commentaires

Cette rubrique répertorie et décrit les mots clés dans l’aide en fonction du commentaire.

## <a name="keywords-in-comment-based-help"></a>Mots clés dans l’aide basée sur le commentaire

Valide en fonction du commentaire des mots clés sont les suivantes : Ils sont répertoriés dans l’ordre dans lequel ils apparaissent généralement dans une rubrique d’aide, ainsi que leur utilisation prévue. Ces mots clés peuvent apparaître dans n’importe quel ordre dans l’aide de commentaire, et ils ne respectent pas la casse.

Notez que le `.ExternalHelp` mot clé est prioritaire sur tous les autres en fonction des commentaires des mots clés. Lorsque `.ExternalHelp` est présent, le [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) applet de commande n’affiche pas de commentaire-aide, même lorsqu’il ne trouve pas un fichier d’aide qui correspond à la valeur du mot clé.

`.Synopsis` Une brève description de la fonction ou d’un script. Ce mot clé peut être utilisé qu’une seule fois dans chaque rubrique.

`.Description` Une description détaillée de la fonction ou d’un script. Ce mot clé peut être utilisé qu’une seule fois dans chaque rubrique.

`.Parameter` *\<Nom de paramètre >* la description d’un paramètre. Vous pouvez inclure un `.Parameter` mot clé pour chaque paramètre dans la fonction ou un script.

Le `.Parameter` mots clés peuvent apparaître dans n’importe quel ordre dans le bloc de commentaire, mais l’ordre dans lequel les paramètres apparaissent dans le `Param` déclaration d’instruction ou la fonction détermine l’ordre dans lequel les paramètres apparaissent dans la rubrique d’aide. Pour modifier l’ordre des paramètres dans la rubrique d’aide, modifiez l’ordre des paramètres dans le `Param` déclaration d’instruction ou la fonction.

Vous pouvez également spécifier une description du paramètre en plaçant un commentaire dans la `Param` instruction immédiatement avant le nom de variable de paramètre. Si vous utilisez à la fois un `Param` commentaire de l’instruction et un `.Parameter` mot clé, la description associée le `.Parameter` mot clé est utilisé et le `Param` commentaire de l’instruction est ignorée.

`.Example` Un exemple de commande qui utilise la fonction ou un script, suivie éventuellement d’exemple de sortie et une description. Répétez ce mot clé pour chaque exemple.

`.Inputs` Types d’objets qui peuvent être transmis à la fonction ou un script Microsoft .NET Framework. Vous pouvez également inclure une description des objets d’entrée.

`.Outputs` Le type .NET Framework des objets qui retourne l’applet de commande. Vous pouvez également inclure une description des objets renvoyés.

`.Notes` Informations supplémentaires sur la fonction ou un script.

`.Link` Le nom d’une rubrique connexe. Répétez ce mot clé pour chaque rubrique connexe. Ce contenu s’affiche dans la section liens connexes de la rubrique d’aide.

Le `.Link` contenu de mot clé peut également inclure un identificateur URI (Uniform Resource) vers une version en ligne de la même rubrique d’aide. La version en ligne s’ouvre lorsque vous utilisez le `Online` paramètre de Get-Help. L’URI doit commencer par « http » ou « https ».

`.Component` La technologie ou une fonctionnalité qui utilise de la fonction ou un script ou à laquelle il est associé. Ce contenu s’affiche lorsque la commande Get-Help inclut le `Component` paramètre de Get-Help.

`.Role` Le rôle d’utilisateur pour la rubrique d’aide. Ce contenu s’affiche lorsque la commande Get-Help inclut le `Role` paramètre de Get-Help.

`.Functionality` L’utilisation prévue de la fonction. Ce contenu s’affiche lorsque la commande Get-Help inclut le `Functionality` paramètre de Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Effectue une redirection vers la rubrique d’aide pour la commande spécifiée. Vous pouvez rediriger les utilisateurs vers une rubrique d’aide, y compris des rubriques d’aide pour une fonction, un script, une applet de commande ou un fournisseur.

`.ForwardHelpCategory` `<Category>` Spécifie la catégorie de l’aide de l’élément dans ForwardHelpTargetName. Valeurs valides sont Alias, applet de commande, HelpFile, fonction, fournisseur, général, FAQ, glossaire, commande de script, ExternalScript, filtre ou tous. Utilisez ce mot clé pour éviter les conflits lorsqu’il existe des commandes portant le même nom.

`.RemoteHelpRunspace` `<PSSession-variable>` Spécifie une session qui contient la rubrique d’aide. Entrez une variable qui contient une session PSSession. Ce mot clé est utilisé par le `Export-PSSession` applet de commande pour rechercher les rubriques d’aide pour les commandes exportées.

`.ExternalHelp` `<XML Help File>` Spécifie le chemin d’accès et/ou le nom d’un fichier d’aide basé sur XML pour le script ou la fonction.

Le `.ExternalHelp` mot clé indique le [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) applet de commande pour obtenir de l’aide du script ou une fonction dans un fichier XML. Le **. ExternalHelp** mot clé est requis lors de l’utilisation d’un fichier d’aide basé sur XML pour une fonction ou un script. Sans cela, `Get-Help` ne trouvera pas un fichier d’aide pour la fonction ou d’un script.

Le `.ExternalHelp` mot clé est prioritaire sur tous les autres en fonction des commentaires des mots clés. Lorsque `.ExternalHelp` est présent, le [Microsoft.PowerShell.Commands.Get-Help](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) applet de commande n’affiche pas de commentaire-aide, même lorsqu’il ne trouve pas un fichier d’aide qui correspond à la valeur du mot clé.

Lorsque la fonction est exportée par un module de script, la valeur de `.ExternalHelp` doit être un nom de fichier sans un chemin d’accès. `Get-Help` recherche le fichier dans un sous-répertoire spécifique aux paramètres régionaux du répertoire du module. Aucune n’est requise pour le nom de fichier, mais une bonne pratique consiste à utiliser le format de nom de fichier suivant : `<ScriptModule>.psm1-help.xml`.

Lorsque la fonction n’est pas associée à un module, incluez un chemin d’accès et nom de fichier dans la valeur de la **. ExternalHelp** mot clé. Si le chemin d’accès spécifié dans le fichier XML contient des sous-répertoires spécifiques de culture de l’interface utilisateur, `Get-Help` recherche dans la sous-répertoires de manière récursive pour un fichier XML avec le nom du script ou fonction conformément à la langue de secours normes établies pour Windows, tel qu’il effectue pour toutes les rubriques d’aide basé sur XML.

Pour plus d’informations sur le format de fichier d’aide basé sur XML aide applet de commande, consultez [écriture Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).