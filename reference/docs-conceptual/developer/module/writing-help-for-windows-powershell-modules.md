---
title: Écriture de l’aide pour les modules PowerShell
ms.date: 04/10/2020
ms.openlocfilehash: 496b7e6cadff4d2db15b6452e9d38efcdf1739ec
ms.sourcegitcommit: 8f55c0157280afa4598fe385a706faf330e723a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219657"
---
# <a name="writing-help-for-powershell-modules"></a>Écriture de l’aide pour les modules PowerShell

Les modules PowerShell peuvent inclure des rubriques d’aide sur le module et sur les membres du module, tels que des applets de commande, des fournisseurs, des fonctions et des scripts. L' `Get-Help` applet de commande affiche les rubriques d’aide du module dans le même format qu’il affiche l’aide pour les autres éléments `Get-Help` PowerShell, et les utilisateurs utilisent des commandes standard pour obtenir les rubriques d’aide.

Ce document explique le format et le positionnement correct des rubriques d’aide du module, et propose des instructions pour le contenu de l’aide du module.

## <a name="types-of-module-help"></a>Types d’aide sur les modules

Un module peut inclure les types d’aide suivants.

- **Aide sur l’applet**de commande. Les rubriques d’aide qui décrivent les applets de commande d’un module sont des fichiers XML qui utilisent le schéma de l’aide de la commande

- **Aide du fournisseur**. Les rubriques d’aide qui décrivent les fournisseurs dans un module sont des fichiers XML qui utilisent le schéma d’aide du fournisseur.

- **Aide sur la fonction**. Les rubriques d’aide qui décrivent les fonctions d’un module peuvent être des fichiers XML qui utilisent le schéma de l’aide de la commande ou des rubriques d’aide basées sur les commentaires au sein de la fonction, ou du script ou du module de script.

- **Aide sur les scripts**. Les rubriques d’aide qui décrivent les scripts d’un module peuvent être des fichiers XML qui utilisent le schéma de l’aide de la commande ou des rubriques d’aide basées sur les commentaires dans le script ou le module de script.

- **Aide conceptuelle (« à propos de »)**. Vous pouvez utiliser une rubrique d’aide conceptuelle (« à propos de ») pour décrire le module et ses membres, et pour expliquer comment les membres peuvent être utilisés ensemble pour effectuer des tâches.
  Les rubriques d’aide conceptuelle sont des fichiers texte avec l’encodage Unicode (UTF-8). Le nom de fichier doit utiliser `about_<name>.help.txt` le format, par `about_MyModule.help.txt`exemple. Par défaut, PowerShell comprend plus de 100 de ces rubriques d’aide conceptuelles, et elles sont mises en forme comme dans l’exemple suivant.

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
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

Tous les fichiers de schéma se trouvent dans le `$PSHOME\Schemas\PSMaml` dossier.

## <a name="placement-of-module-help"></a>Emplacement de l’aide du module

L' `Get-Help` applet de commande recherche les fichiers de rubrique d’aide du module dans les sous-répertoires spécifiques à la langue du répertoire du module.

Par exemple, le diagramme de structure de répertoire suivant montre l’emplacement des rubriques d’aide pour le module SampleModule.

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
> Dans l’exemple, l' `<ModulePath>` espace réservé représente l’un des chemins d' `PSModulePath` accès dans la variable d' `$HOME\Documents\Modules`environnement `$PSHOME\Modules`, tel que, ou un chemin d’accès personnalisé que l’utilisateur spécifie.

## <a name="getting-module-help"></a>Obtention d’aide sur le module

Lorsqu’un utilisateur importe un module dans une session, les rubriques d’aide de ce module sont importées dans la session avec le module. Vous pouvez répertorier les fichiers de rubriques d’aide dans la valeur de la clé FileList dans le manifeste de module, mais les rubriques d' `Export-ModuleMember` aide ne sont pas affectées par l’applet de commande.

Vous pouvez fournir des rubriques d’aide sur les modules dans différents langages. L' `Get-Help` applet de commande affiche automatiquement les rubriques d’aide du module dans la langue spécifiée pour l’utilisateur actuel dans l’élément Options régionales et linguistiques du panneau de configuration. Dans Windows Vista et les versions ultérieures de `Get-Help` Windows, recherche les rubriques d’aide dans les sous-répertoires spécifiques au langage du répertoire du module, conformément aux normes de langue de secours établies pour Windows.

À compter de PowerShell 3,0, l' `Get-Help` exécution d’une commande pour une applet de commande ou une fonction déclenche l’importation automatique du module. L' `Get-Help` applet de commande affiche immédiatement le contenu des rubriques d’aide dans le module.

Si le module ne contient pas de rubriques d’aide et qu’il n’existe aucune rubrique d’aide pour les commandes du module sur l' `Get-Help` ordinateur de l’utilisateur, affiche l’aide générée automatiquement. L’aide générée automatiquement inclut la syntaxe de commande, les paramètres et les types d’entrée et de sortie, mais n’inclut aucune description. L’aide générée automatiquement comprend du texte qui indique à l’utilisateur d’essayer d’utiliser l' `Update-Help` applet de commande pour télécharger l’aide de la commande à partir d’Internet ou d’un partage de fichiers. Il recommande également l’utilisation du paramètre **Online** de `Get-Help` l’applet de commande pour obtenir la version en ligne de la rubrique d’aide.

## <a name="supporting-updatable-help"></a>Prise en charge de l’aide actualisable

Les utilisateurs de PowerShell 3,0 et des versions ultérieures de PowerShell peuvent télécharger et installer les fichiers d’aide mis à jour pour un module à partir d’Internet ou d’un partage de fichiers local. Les `Update-Help` applets de commande et `Save-Help` masquent les détails de gestion de l’utilisateur. Les utilisateurs exécutent l' `Update-Help` applet de commande `Get-Help` , puis utilisent l’applet de commande pour lire les fichiers d’aide les plus récents pour le module à l’invite de commandes PowerShell.
Les utilisateurs n’ont pas besoin de redémarrer Windows ou PowerShell.

Les utilisateurs se trouvant derrière des pare-feu et ceux qui n’ont pas accès à Internet peuvent également utiliser l’aide actualisable.
Les administrateurs disposant d’un `Save-Help` accès à Internet utilisent l’applet de commande pour télécharger et installer les fichiers d’aide les plus récents dans un partage de fichiers. Ensuite, les utilisateurs utilisent le paramètre **path** de `Update-Help` l’applet de commande pour obtenir les fichiers d’aide les plus récents à partir du partage de fichiers.

Les auteurs de modules peuvent inclure des fichiers d’aide dans le module et utiliser l’aide actualisable pour mettre à jour les fichiers d’aide, ou omettre les fichiers d’aide du module et utiliser l’aide actualisable pour installer et pour les mettre à jour.

Pour plus d’informations sur l’aide actualisable, consultez [prise en charge de l’aide actualisable](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Prise en charge de l’aide en ligne

Les utilisateurs qui ne peuvent pas ou n’installent pas les fichiers d’aide mis à jour sur leurs ordinateurs s’appuient souvent sur la version en ligne des rubriques d’aide du module. Le paramètre **Online** de l' `Get-Help` applet de commande ouvre la version en ligne de la rubrique d’aide d’une applet de commande ou d’une fonction avancée pour l’utilisateur dans son navigateur Internet par défaut.

L' `Get-Help` applet de commande utilise la valeur de la propriété **HelpUri** de l’applet de commande ou de la fonction pour rechercher la version en ligne de la rubrique d’aide.

À compter de PowerShell 3,0, vous pouvez aider les utilisateurs à trouver la version en ligne des rubriques d’aide sur les applets de commande et les fonctions en définissant l’attribut HelpUri sur la classe cmdlet ou la propriété **HelpUri** de l’attribut **CmdletBinding** . La valeur de l’attribut est la valeur de la propriété **HelpUri** de l’applet de commande ou de la fonction.

Pour plus d’informations, consultez [prise en charge de l’aide en ligne](./supporting-online-help.md).

## <a name="see-also"></a>Voir aussi

[Écriture d’un module PowerShell](./writing-a-windows-powershell-module.md)

[Prise en charge de l’aide actualisable](./supporting-updatable-help.md)

[Prise en charge de l’aide en ligne](./supporting-online-help.md)
