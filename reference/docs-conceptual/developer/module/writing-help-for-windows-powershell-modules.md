---
title: Écriture de l’aide pour les modules Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360558"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="a5d4f-102">Écriture d’une aide pour les modules Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5d4f-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="a5d4f-103">Les modules Windows PowerShell peuvent inclure des rubriques d’aide sur le module et sur les membres du module, tels que des applets de commande, des fournisseurs, des fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="a5d4f-104">L’applet de commande `Get-Help` affiche les rubriques d’aide du module dans le même format que celui utilisé pour afficher l’aide pour les autres éléments Windows PowerShell, et les utilisateurs utilisent des commandes standard `Get-Help` pour obtenir les rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="a5d4f-105">Ce document explique le format et le positionnement correct des rubriques d’aide du module, et propose des instructions pour le contenu de l’aide du module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="a5d4f-106">Types d’aide sur les modules</span><span class="sxs-lookup"><span data-stu-id="a5d4f-106">Types of Module Help</span></span>

<span data-ttu-id="a5d4f-107">Un module peut inclure les types d’aide suivants.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="a5d4f-108">**Aide sur l’applet**de commande.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-108">**Cmdlet Help**.</span></span> <span data-ttu-id="a5d4f-109">Les rubriques d’aide qui décrivent les applets de commande d’un module sont des fichiers XML qui utilisent le schéma de l’aide de la commande</span><span class="sxs-lookup"><span data-stu-id="a5d4f-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="a5d4f-110">**Aide du fournisseur**.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-110">**Provider Help**.</span></span> <span data-ttu-id="a5d4f-111">Les rubriques d’aide qui décrivent les fournisseurs dans un module sont des fichiers XML qui utilisent le schéma d’aide du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="a5d4f-112">**Aide sur la fonction**.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-112">**Function Help**.</span></span> <span data-ttu-id="a5d4f-113">Les rubriques d’aide qui décrivent les fonctions d’un module peuvent être des fichiers XML qui utilisent le schéma de l’aide de la commande ou des rubriques d’aide basées sur les commentaires au sein de la fonction, ou du script ou du module de script.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="a5d4f-114">**Aide sur les scripts**.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-114">**Script Help**.</span></span> <span data-ttu-id="a5d4f-115">Les rubriques d’aide qui décrivent les scripts d’un module peuvent être des fichiers XML qui utilisent le schéma de l’aide de la commande ou des rubriques d’aide basées sur les commentaires dans le script ou le module de script.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="a5d4f-116">**Aide conceptuelle (« à propos de »)** .</span><span class="sxs-lookup"><span data-stu-id="a5d4f-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="a5d4f-117">Vous pouvez utiliser une rubrique d’aide conceptuelle (« à propos de ») pour décrire le module et ses membres, et pour expliquer comment les membres peuvent être utilisés ensemble pour effectuer des tâches.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="a5d4f-118">Les rubriques d’aide conceptuelle sont des fichiers texte avec l’encodage Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="a5d4f-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="a5d4f-119">Le nom de fichier doit utiliser le format `about_<name>.help.txt`, par exemple about_MyModule. Help. txt.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="a5d4f-120">Par défaut, Windows PowerShell comprend plus de 100 de ces rubriques d’aide conceptuelles, et elles sont mises en forme comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="a5d4f-121">Emplacement de l’aide du module</span><span class="sxs-lookup"><span data-stu-id="a5d4f-121">Placement of Module Help</span></span>

<span data-ttu-id="a5d4f-122">L’applet de commande `Get-Help` recherche les fichiers de rubrique d’aide du module dans les sous-répertoires spécifiques à la langue du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="a5d4f-123">Par exemple, le diagramme de structure de répertoire suivant montre l’emplacement des rubriques d’aide pour le module SampleModule.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="a5d4f-124">Dans l’exemple, l’espace réservé *> \<ModulePath* représente l’un des chemins d’accès dans la variable d’environnement `PSModulePath`, par exemple $Home \documents\modules, $pshome nouvelle \modules., ou un chemin d’accès personnalisé que l’utilisateur spécifie.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="a5d4f-125">Obtention d’aide sur le module</span><span class="sxs-lookup"><span data-stu-id="a5d4f-125">Getting Module Help</span></span>

<span data-ttu-id="a5d4f-126">Lorsqu’un utilisateur importe un module dans une session, les rubriques d’aide de ce module sont importées dans la session avec le module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="a5d4f-127">Vous pouvez répertorier les fichiers de rubriques d’aide dans la valeur de la clé FileList dans le manifeste de module, mais les rubriques d’aide ne sont pas affectées par l’applet de commande `Export-ModuleMember`.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="a5d4f-128">Vous pouvez fournir des rubriques d’aide sur les modules dans différents langages.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="a5d4f-129">L’applet de commande `Get-Help` affiche automatiquement les rubriques d’aide du module dans la langue spécifiée pour l’utilisateur actuel dans l’élément Options régionales et linguistiques du panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="a5d4f-130">Dans Windows Vista et les versions ultérieures de Windows, `Get-Help` recherche les rubriques d’aide dans les sous-répertoires spécifiques au langage du répertoire du module conformément aux normes de langue de secours établies pour Windows.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="a5d4f-131">À compter de Windows PowerShell 3,0, l’exécution d’une commande `Get-Help` pour une applet de commande ou une fonction déclenche l’importation automatique du module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="a5d4f-132">L’applet de commande `Get-Help` affiche immédiatement le contenu des rubriques d’aide dans le module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="a5d4f-133">Si le module ne contient pas de rubriques d’aide et qu’il n’existe aucune rubrique d’aide pour les commandes du module sur l’ordinateur de l’utilisateur, `Get-Help` affiche l’aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="a5d4f-134">L’aide générée automatiquement inclut la syntaxe de commande, les paramètres et les types d’entrée et de sortie, mais n’inclut aucune description.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="a5d4f-135">L’aide générée automatiquement comprend du texte qui indique à l’utilisateur d’essayer d’utiliser l’applet de commande `Update-Help` pour télécharger l’aide de la commande à partir d’Internet ou d’un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="a5d4f-136">Il recommande également l’utilisation du paramètre **Online** de l’applet de commande `Get-Help` pour obtenir la version en ligne de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="a5d4f-137">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="a5d4f-137">Supporting Updatable Help</span></span>

<span data-ttu-id="a5d4f-138">Les utilisateurs de Windows PowerShell 3,0 et des versions ultérieures de Windows PowerShell peuvent télécharger et installer les fichiers d’aide mis à jour pour un module à partir d’Internet ou d’un partage de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="a5d4f-139">Les applets de commande `Update-Help` et `Save-Help` masquent les détails de gestion de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="a5d4f-140">Les utilisateurs exécutent l’applet de commande `Update-Help`, puis utilisent l’applet de commande `Get-Help` pour lire les fichiers d’aide les plus récents pour le module à l’invite de commandes Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="a5d4f-141">Les utilisateurs n’ont pas besoin de redémarrer Windows ou Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="a5d4f-142">Les utilisateurs se trouvant derrière des pare-feu et ceux qui n’ont pas accès à Internet peuvent également utiliser l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="a5d4f-143">Les administrateurs disposant d’un accès à Internet utilisent l’applet de commande `Save-Help` pour télécharger et installer les fichiers d’aide les plus récents dans un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="a5d4f-144">Ensuite, les utilisateurs utilisent le paramètre **path** de l’applet de commande `Update-Help` pour obtenir les fichiers d’aide les plus récents à partir du partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="a5d4f-145">Les auteurs de modules peuvent inclure des fichiers d’aide dans le module et utiliser l’aide actualisable pour mettre à jour les fichiers d’aide, ou omettre les fichiers d’aide du module et utiliser l’aide actualisable pour installer et pour les mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="a5d4f-146">Pour plus d’informations sur l’aide actualisable, consultez [prise en charge de l’aide actualisable](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="a5d4f-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="a5d4f-147">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="a5d4f-147">Supporting Online Help</span></span>

<span data-ttu-id="a5d4f-148">Les utilisateurs qui ne peuvent pas ou n’installent pas les fichiers d’aide mis à jour sur leurs ordinateurs s’appuient souvent sur la version en ligne des rubriques d’aide du module.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="a5d4f-149">Le paramètre **Online** de l’applet de commande `Get-Help` ouvre la version en ligne de la rubrique d’aide d’une applet de commande ou d’une fonction avancée pour l’utilisateur dans son navigateur Internet par défaut.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="a5d4f-150">L’applet de commande `Get-Help` utilise la valeur de la propriété **HelpUri** de l’applet de commande ou de la fonction pour rechercher la version en ligne de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="a5d4f-151">À compter de Windows PowerShell 3,0, vous pouvez aider les utilisateurs à trouver la version en ligne des rubriques d’aide sur les applets de commande et les fonctions en définissant l’attribut HelpUri sur la classe cmdlet ou la propriété **HelpUri** de l’attribut **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="a5d4f-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="a5d4f-152">La valeur de l’attribut est la valeur de la propriété **HelpUri** de l’applet de commande ou de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a5d4f-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="a5d4f-153">Pour plus d’informations, consultez [prise en charge de l’aide en ligne](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="a5d4f-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a5d4f-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5d4f-154">See Also</span></span>

[<span data-ttu-id="a5d4f-155">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5d4f-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="a5d4f-156">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="a5d4f-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="a5d4f-157">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="a5d4f-157">Supporting Online Help</span></span>](./supporting-online-help.md)