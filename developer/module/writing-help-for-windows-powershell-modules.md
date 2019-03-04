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
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="9d781-102">Écriture d’une aide pour les modules Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9d781-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="9d781-103">Modules Windows PowerShell peuvent inclure des rubriques d’aide sur le module et sur les membres de module, tels que les applets de commande, fournisseurs, fonctions et des scripts.</span><span class="sxs-lookup"><span data-stu-id="9d781-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="9d781-104">Le `Get-Help` applet de commande affiche les rubriques d’aide de module dans le même format qu’il affiche l’aide pour d’autres éléments de Windows PowerShell, et les utilisateurs utilisent la norme `Get-Help` commandes pour obtenir les rubriques d’aide.</span><span class="sxs-lookup"><span data-stu-id="9d781-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="9d781-105">Ce document explique le format et le positionnement correct de rubriques d’aide du module, et il suggère des indications pour le contenu d’aide de module.</span><span class="sxs-lookup"><span data-stu-id="9d781-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="9d781-106">Types d’aide du Module</span><span class="sxs-lookup"><span data-stu-id="9d781-106">Types of Module Help</span></span>

<span data-ttu-id="9d781-107">Un module peut inclure les types suivants de l’aide.</span><span class="sxs-lookup"><span data-stu-id="9d781-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="9d781-108">**Aide de l’applet de commande**.</span><span class="sxs-lookup"><span data-stu-id="9d781-108">**Cmdlet Help**.</span></span> <span data-ttu-id="9d781-109">Les rubriques d’aide qui décrivent les applets de commande dans un module sont des fichiers XML qui utilisent la commande aide schéma</span><span class="sxs-lookup"><span data-stu-id="9d781-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="9d781-110">**Aide du fournisseur**.</span><span class="sxs-lookup"><span data-stu-id="9d781-110">**Provider Help**.</span></span> <span data-ttu-id="9d781-111">Les rubriques d’aide qui décrivent les fournisseurs dans un module sont des fichiers XML qui utilisent le fournisseur aide schéma.</span><span class="sxs-lookup"><span data-stu-id="9d781-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="9d781-112">**Fonction Help**.</span><span class="sxs-lookup"><span data-stu-id="9d781-112">**Function Help**.</span></span> <span data-ttu-id="9d781-113">Les rubriques d’aide qui décrivent les fonctions dans un module peut être de fichiers XML qui utilisent la commande vous permettent de schéma ou les rubriques d’aide en fonction du commentaire dans la fonction, ou le script ou le module de script</span><span class="sxs-lookup"><span data-stu-id="9d781-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="9d781-114">**Script Help**.</span><span class="sxs-lookup"><span data-stu-id="9d781-114">**Script Help**.</span></span> <span data-ttu-id="9d781-115">Les rubriques d’aide qui décrivent des scripts dans un module peuvent être des fichiers XML qui utilisent la commande aide schéma ou commentaire rubriques d’aide dans le script ou d’un module de script.</span><span class="sxs-lookup"><span data-stu-id="9d781-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="9d781-116">**Conceptuelle (« About ») aide**.</span><span class="sxs-lookup"><span data-stu-id="9d781-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="9d781-117">Vous pouvez utiliser un conceptuelle (« about ») rubrique d’aide pour décrire le module et ses membres et d’expliquer comment les membres peuvent être utilisés pour effectuer des tâches.</span><span class="sxs-lookup"><span data-stu-id="9d781-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="9d781-118">Rubriques d’aide conceptuelle sont des fichiers texte avec encodage Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="9d781-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="9d781-119">Le nom de fichier doit utiliser le `about_<name>.help.txt` format, tel que about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="9d781-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="9d781-120">Par défaut, Windows PowerShell inclut plus de 100 de ces rubriques conceptuelles à propos d’aide, et ils sont mis en forme comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="9d781-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="9d781-121">Placement de l’aide du Module</span><span class="sxs-lookup"><span data-stu-id="9d781-121">Placement of Module Help</span></span>

<span data-ttu-id="9d781-122">Le `Get-Help` applet de commande recherche les fichiers de rubrique d’aide de module dans les sous-répertoires spécifiques au langage du répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="9d781-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="9d781-123">Par exemple, le diagramme de structure de répertoire suivant indique l’emplacement des rubriques d’aide pour le module SampleModule.</span><span class="sxs-lookup"><span data-stu-id="9d781-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="9d781-124">Dans l’exemple, le  *\<ModulePath >* espace réservé représente un des chemins dans la `PSModulePath` variable d’environnement, telles que $home\Documents\Modules, $pshome\Modules ou un chemin d’accès personnalisé qui spécifie l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d781-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="9d781-125">Obtention d’aide du Module</span><span class="sxs-lookup"><span data-stu-id="9d781-125">Getting Module Help</span></span>

<span data-ttu-id="9d781-126">Lorsqu’un utilisateur importe un module dans une session, les rubriques d’aide pour ce module sont importées dans la session, ainsi que le module.</span><span class="sxs-lookup"><span data-stu-id="9d781-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="9d781-127">Vous pouvez répertorier les fichiers de la rubrique d’aide dans la valeur de la clé de liste de fichiers dans le manifeste de module, mais les rubriques d’aide ne sont pas affectés par la `Export-ModuleMember` applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9d781-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="9d781-128">Vous pouvez fournir des rubriques d’aide de module dans différentes langues.</span><span class="sxs-lookup"><span data-stu-id="9d781-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="9d781-129">Le `Get-Help` applet de commande affiche automatiquement des rubriques d’aide du module dans la langue spécifiée pour l’utilisateur actuel dans l’élément Options régionales et linguistiques dans le panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="9d781-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="9d781-130">Dans Windows Vista et versions ultérieures de Windows, `Get-Help` recherche les rubriques d’aide dans les sous-répertoires spécifiques au langage du répertoire du module selon les normes de secours de langue établie pour Windows.</span><span class="sxs-lookup"><span data-stu-id="9d781-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="9d781-131">À compter de Windows PowerShell 3.0, en cours d’exécution un `Get-Help` commande pour une fonction ou l’applet de commande ne déclenche pas l’importation automatique du module.</span><span class="sxs-lookup"><span data-stu-id="9d781-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="9d781-132">Le `Get-Help` applet de commande affiche immédiatement le contenu des rubriques d’aide dans le module.</span><span class="sxs-lookup"><span data-stu-id="9d781-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="9d781-133">Si le module ne contient-elle pas de rubriques d’aide et aucune rubrique d’aide pour les commandes dans le module sur l’ordinateur, `Get-Help` affiche une aide générée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9d781-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="9d781-134">L’aide générée automatiquement contient la syntaxe de commande, les paramètres et les types d’entrée et de sortie, mais n’inclut pas toutes les descriptions des.</span><span class="sxs-lookup"><span data-stu-id="9d781-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="9d781-135">L’aide générée automatiquement contient le texte qui dirige l’utilisateur d’essayer d’utiliser le `Update-Help` applet de commande pour télécharger l’aide de la commande à partir d’Internet ou d’un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9d781-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="9d781-136">Il recommande également d’utiliser le **Online** paramètre de la `Get-Help` pour obtenir la version de la rubrique d’aide en ligne.</span><span class="sxs-lookup"><span data-stu-id="9d781-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="9d781-137">Prise en charge de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="9d781-137">Supporting Updatable Help</span></span>

<span data-ttu-id="9d781-138">Les utilisateurs de Windows PowerShell 3.0 et versions ultérieures de Windows PowerShell peuvent télécharger et installer les fichiers d’aide mis à jour d’un module à partir d’Internet ou d’un partage de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="9d781-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="9d781-139">Le `Update-Help` et `Save-Help` applets de commande masquent les détails de la gestion de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9d781-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="9d781-140">Aux utilisateurs d’exécuter le `Update-Help` applet de commande, puis utiliser le `Get-Help` applet de commande pour lire les derniers fichiers d’aide pour le module à l’invite de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d781-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="9d781-141">Utilisateurs n’ont pas besoin de redémarrer Windows ou Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d781-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="9d781-142">Utilisateurs derrière des pare-feu et celles sans accès à Internet peuvent utiliser l’aide actualisable, également.</span><span class="sxs-lookup"><span data-stu-id="9d781-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="9d781-143">Les administrateurs avec Internet, accéder à utiliser le `Save-Help` applet de commande pour télécharger et installer les derniers fichiers d’aide pour un partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9d781-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="9d781-144">Ensuite, les utilisateurs utilisent le **chemin d’accès** paramètre de la `Update-Help` pour obtenir les derniers fichiers d’aide à partir du partage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="9d781-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="9d781-145">Les auteurs de modules peuvent inclure des fichiers d’aide dans le module et utiliser l’aide actualisable pour mettre à jour les fichiers d’aide, ou omettre les fichiers d’aide à partir du module et utiliser l’aide actualisable pour installer et mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="9d781-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="9d781-146">Pour plus d’informations sur l’aide actualisable, consultez [Supporting Updatable Help](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="9d781-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="9d781-147">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="9d781-147">Supporting Online Help</span></span>

<span data-ttu-id="9d781-148">Les utilisateurs qui ne peut pas ou n’installent pas mis à jour aide fichiers sur leurs ordinateurs s’appuient souvent sur la version en ligne des rubriques d’aide de module.</span><span class="sxs-lookup"><span data-stu-id="9d781-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="9d781-149">Le **Online** paramètre de la `Get-Help` applet de commande ouvre la version en ligne d’une applet de commande ou d’une fonction avancée rubrique d’aide pour l’utilisateur dans leur navigateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9d781-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="9d781-150">Le `Get-Help` applet de commande utilise la valeur de la **HelpUri** propriété de l’applet de commande ou une fonction pour rechercher la version en ligne de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="9d781-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="9d781-151">À compter de Windows PowerShell 3.0, vous pouvez aider les utilisateurs à trouver la version de l’applet de commande et de la fonction de rubriques d’aide en ligne en définissant l’attribut HelpUri sur la classe d’applet de commande ou le **HelpUri** propriété de la **CmdletBinding** attribut.</span><span class="sxs-lookup"><span data-stu-id="9d781-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="9d781-152">La valeur de l’attribut est la valeur de la **HelpUri** propriété de la fonction ou l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="9d781-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="9d781-153">Pour plus d’informations, consultez [Supporting Online Help](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="9d781-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d781-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d781-154">See Also</span></span>

[<span data-ttu-id="9d781-155">Écrire un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="9d781-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="9d781-156">Prise en charge d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="9d781-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="9d781-157">Prise en charge de l’aide en ligne</span><span class="sxs-lookup"><span data-stu-id="9d781-157">Supporting Online Help</span></span>](./supporting-online-help.md)