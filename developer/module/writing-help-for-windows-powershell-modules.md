---
title: Écriture de l’aide pour les Modules de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854065"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Écriture d’une aide pour les modules Windows PowerShell

Modules Windows PowerShell peuvent inclure des rubriques d’aide sur le module et sur les membres de module, tels que les applets de commande, fournisseurs, fonctions et des scripts. Le `Get-Help` applet de commande affiche les rubriques d’aide de module dans le même format qu’il affiche l’aide pour d’autres éléments de Windows PowerShell, et les utilisateurs utilisent la norme `Get-Help` commandes pour obtenir les rubriques d’aide.

Ce document explique le format et le positionnement correct de rubriques d’aide du module, et il suggère des indications pour le contenu d’aide de module.

## <a name="types-of-module-help"></a>Types d’aide du Module

Un module peut inclure les types suivants de l’aide.

- **Aide de l’applet de commande**. Les rubriques d’aide qui décrivent les applets de commande dans un module sont des fichiers XML qui utilisent la commande aide schéma

- **Aide du fournisseur**. Les rubriques d’aide qui décrivent les fournisseurs dans un module sont des fichiers XML qui utilisent le fournisseur aide schéma.

- **Fonction Help**. Les rubriques d’aide qui décrivent les fonctions dans un module peut être de fichiers XML qui utilisent la commande vous permettent de schéma ou les rubriques d’aide en fonction du commentaire dans la fonction, ou le script ou le module de script

- **Script Help**. Les rubriques d’aide qui décrivent des scripts dans un module peuvent être des fichiers XML qui utilisent la commande aide schéma ou commentaire rubriques d’aide dans le script ou d’un module de script.

- **Conceptuelle (« About ») aide**. Vous pouvez utiliser un conceptuelle (« about ») rubrique d’aide pour décrire le module et ses membres et d’expliquer comment les membres peuvent être utilisés pour effectuer des tâches. Rubriques d’aide conceptuelle sont des fichiers texte avec encodage Unicode (UTF-8). Le nom de fichier doit utiliser le `about_<name>.help.txt` format, tel que about_MyModule.help.txt. Par défaut, Windows PowerShell inclut plus de 100 de ces rubriques conceptuelles à propos d’aide, et ils sont mis en forme comme dans l’exemple suivant.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Placement de l’aide du Module

Le `Get-Help` applet de commande recherche les fichiers de rubrique d’aide de module dans les sous-répertoires spécifiques au langage du répertoire du module.

Par exemple, le diagramme de structure de répertoire suivant indique l’emplacement des rubriques d’aide pour le module SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> Dans l’exemple, le  *\<ModulePath >* espace réservé représente un des chemins dans la `PSModulePath` variable d’environnement, telles que $home\Documents\Modules, $pshome\Modules ou un chemin d’accès personnalisé qui spécifie l’utilisateur.

## <a name="getting-module-help"></a>Obtention d’aide du Module

Lorsqu’un utilisateur importe un module dans une session, les rubriques d’aide pour ce module sont importées dans la session, ainsi que le module. Vous pouvez répertorier les fichiers de la rubrique d’aide dans la valeur de la clé de liste de fichiers dans le manifeste de module, mais les rubriques d’aide ne sont pas affectés par la `Export-ModuleMember` applet de commande.

Vous pouvez fournir des rubriques d’aide de module dans différentes langues. Le `Get-Help` applet de commande affiche automatiquement des rubriques d’aide du module dans la langue spécifiée pour l’utilisateur actuel dans l’élément Options régionales et linguistiques dans le panneau de configuration. Dans Windows Vista et versions ultérieures de Windows, `Get-Help` recherche les rubriques d’aide dans les sous-répertoires spécifiques au langage du répertoire du module selon les normes de secours de langue établie pour Windows.

À compter de Windows PowerShell 3.0, en cours d’exécution un `Get-Help` commande pour une fonction ou l’applet de commande ne déclenche pas l’importation automatique du module. Le `Get-Help` applet de commande affiche immédiatement le contenu des rubriques d’aide dans le module.

Si le module ne contient-elle pas de rubriques d’aide et aucune rubrique d’aide pour les commandes dans le module sur l’ordinateur, `Get-Help` affiche une aide générée automatiquement. L’aide générée automatiquement contient la syntaxe de commande, les paramètres et les types d’entrée et de sortie, mais n’inclut pas toutes les descriptions des. L’aide générée automatiquement contient le texte qui dirige l’utilisateur d’essayer d’utiliser le `Update-Help` applet de commande pour télécharger l’aide de la commande à partir d’Internet ou d’un partage de fichiers. Il recommande également d’utiliser le **Online** paramètre de la `Get-Help` pour obtenir la version de la rubrique d’aide en ligne.

## <a name="supporting-updatable-help"></a>Prise en charge de l’aide actualisable

Les utilisateurs de Windows PowerShell 3.0 et versions ultérieures de Windows PowerShell peuvent télécharger et installer les fichiers d’aide mis à jour d’un module à partir d’Internet ou d’un partage de fichiers local. Le `Update-Help` et `Save-Help` applets de commande masquent les détails de la gestion de l’utilisateur. Aux utilisateurs d’exécuter le `Update-Help` applet de commande, puis utiliser le `Get-Help` applet de commande pour lire les derniers fichiers d’aide pour le module à l’invite de commande Windows PowerShell. Utilisateurs n’ont pas besoin de redémarrer Windows ou Windows PowerShell.

Utilisateurs derrière des pare-feu et celles sans accès à Internet peuvent utiliser l’aide actualisable, également. Les administrateurs avec Internet, accéder à utiliser le `Save-Help` applet de commande pour télécharger et installer les derniers fichiers d’aide pour un partage de fichiers. Ensuite, les utilisateurs utilisent le **chemin d’accès** paramètre de la `Update-Help` pour obtenir les derniers fichiers d’aide à partir du partage de fichiers.

Les auteurs de modules peuvent inclure des fichiers d’aide dans le module et utiliser l’aide actualisable pour mettre à jour les fichiers d’aide, ou omettre les fichiers d’aide à partir du module et utiliser l’aide actualisable pour installer et mettre à jour.

Pour plus d’informations sur l’aide actualisable, consultez [Supporting Updatable Help](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Prise en charge de l’aide en ligne

Les utilisateurs qui ne peut pas ou n’installent pas mis à jour aide fichiers sur leurs ordinateurs s’appuient souvent sur la version en ligne des rubriques d’aide de module. Le **Online** paramètre de la `Get-Help` applet de commande ouvre la version en ligne d’une applet de commande ou d’une fonction avancée rubrique d’aide pour l’utilisateur dans leur navigateur par défaut.

Le `Get-Help` applet de commande utilise la valeur de la **HelpUri** propriété de l’applet de commande ou une fonction pour rechercher la version en ligne de la rubrique d’aide.

À compter de Windows PowerShell 3.0, vous pouvez aider les utilisateurs à trouver la version de l’applet de commande et de la fonction de rubriques d’aide en ligne en définissant l’attribut HelpUri sur la classe d’applet de commande ou le **HelpUri** propriété de la **CmdletBinding** attribut. La valeur de l’attribut est la valeur de la **HelpUri** propriété de la fonction ou l’applet de commande.

Pour plus d’informations, consultez [Supporting Online Help](./supporting-online-help.md).

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)

[Prise en charge d’aide actualisable](./supporting-updatable-help.md)

[Prise en charge de l’aide en ligne](./supporting-online-help.md)