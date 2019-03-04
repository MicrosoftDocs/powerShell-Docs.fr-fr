---
title: Modifier le chemin d’Installation de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855565"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="4e795-102">Modification du chemin d’Installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4e795-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="4e795-103">Le `PSModulePath` variable d’environnement stocke les chemins d’accès aux emplacements des modules qui sont installés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="4e795-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="4e795-104">Windows PowerShell utilise cette variable pour rechercher des modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module.</span><span class="sxs-lookup"><span data-stu-id="4e795-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="4e795-105">Les chemins d’accès dans cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="4e795-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="4e795-106">Lorsque Windows PowerShell démarre, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="4e795-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="4e795-107">Pour afficher la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4e795-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="4e795-108">Pour afficher les chemins d’accès qui sont spécifiés dans le `PSModulePath` variable, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="4e795-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="4e795-109">Pour ajouter des emplacements à la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4e795-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="4e795-110">Pour ajouter des chemins d’accès à cette variable, utilisez une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4e795-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="4e795-111">Pour ajouter une valeur temporaire qui est disponible uniquement pour la session active, exécutez la commande suivante à la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="4e795-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="4e795-112">Pour ajouter une valeur persistante est disponible chaque fois qu’une session est ouverte, ajoutez la commande suivante pour un profil Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="4e795-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="4e795-113">Pour plus d’informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) dans la bibliothèque Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="4e795-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="4e795-114">Pour ajouter une variable persistante dans le Registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de Variables d’environnement dans le **propriétés système** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4e795-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="4e795-115">Pour ajouter une variable persistante à l’aide d’un script, utilisez la **SetEnvironmentVariable** méthode sur la classe de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="4e795-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="4e795-116">Par exemple, le script suivant ajoute le « C:\Program Files\Fabrikam\Module chemin d’accès à la valeur de la variable d’environnement PSModulePath pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4e795-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="4e795-117">Pour ajouter le chemin d’accès à la variable d’environnement PSModulePath utilisateur, définissez la cible sur « Utilisateur ».</span><span class="sxs-lookup"><span data-stu-id="4e795-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="4e795-118">Pour supprimer des emplacements de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4e795-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="4e795-119">Vous pouvez supprimer des chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` supprimera le **c:\ModulePath** chemin d’accès de la session active.</span><span class="sxs-lookup"><span data-stu-id="4e795-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e795-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e795-120">See Also</span></span>

[<span data-ttu-id="4e795-121">Écrire un Module PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="4e795-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
