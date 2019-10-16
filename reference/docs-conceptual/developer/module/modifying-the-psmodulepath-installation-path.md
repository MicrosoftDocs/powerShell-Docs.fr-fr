---
title: Modification du chemin d’installation de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360668"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="5b585-102">Modification du chemin d’Installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5b585-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="5b585-103">La variable d’environnement `PSModulePath` stocke les chemins d’accès aux emplacements des modules installés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="5b585-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="5b585-104">Windows PowerShell utilise cette variable pour localiser les modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module.</span><span class="sxs-lookup"><span data-stu-id="5b585-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="5b585-105">Les chemins d’accès de cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="5b585-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="5b585-106">Au démarrage de Windows PowerShell, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="5b585-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="5b585-107">Pour afficher la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5b585-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="5b585-108">Pour afficher les chemins d’accès spécifiés dans la variable `PSModulePath`, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="5b585-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="5b585-109">Pour ajouter des emplacements à la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5b585-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="5b585-110">Pour ajouter des chemins d’accès à cette variable, utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b585-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="5b585-111">Pour ajouter une valeur temporaire qui est uniquement disponible pour la session active, exécutez la commande suivante sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="5b585-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="5b585-112">Pour ajouter une valeur persistante qui est disponible chaque fois qu’une session est ouverte, ajoutez la commande suivante à un profil Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="5b585-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="5b585-113">Pour plus d’informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) dans la bibliothèque Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="5b585-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="5b585-114">Pour ajouter une variable persistante au registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de variables d’environnement dans la boîte de dialogue **Propriétés système** .</span><span class="sxs-lookup"><span data-stu-id="5b585-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="5b585-115">Pour ajouter une variable persistante à l’aide d’un script, utilisez la méthode **SetEnvironmentVariable ne contient** sur la classe d’environnement.</span><span class="sxs-lookup"><span data-stu-id="5b585-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="5b585-116">Par exemple, le script suivant ajoute le chemin d’accès C:\Program Files\Fabrikam\Module à la valeur de la variable d’environnement PSModulePath pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5b585-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="5b585-117">Pour ajouter le chemin d’accès à la variable d’environnement User PSModulePath, définissez la cible sur « User ».</span><span class="sxs-lookup"><span data-stu-id="5b585-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="5b585-118">Pour supprimer des emplacements du PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5b585-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="5b585-119">Vous pouvez supprimer les chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` supprime le chemin **c:\ModulePath** de la session active.</span><span class="sxs-lookup"><span data-stu-id="5b585-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b585-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b585-120">See Also</span></span>

[<span data-ttu-id="5b585-121">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5b585-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
