---
title: Modification du chemin d’installation de PSModulePath | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 795f2bd52aeceddd3c0ca092d0c0cf2ef44bcf23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784841"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="e92c3-102">Modification du chemin d’Installation de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e92c3-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="e92c3-103">La `PSModulePath` variable d’environnement stocke les chemins d’accès aux emplacements des modules installés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="e92c3-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="e92c3-104">PowerShell utilise cette variable pour localiser les modules lorsque l’utilisateur ne spécifie pas le chemin d’accès complet à un module.</span><span class="sxs-lookup"><span data-stu-id="e92c3-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="e92c3-105">Les chemins d’accès de cette variable sont recherchés dans l’ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="e92c3-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="e92c3-106">Lorsque PowerShell démarre, `PSModulePath` est créé en tant que variable d’environnement système avec la valeur par défaut suivante : `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` sur Windows et `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` sur Linux ou Mac, et `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e92c3-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="e92c3-107">L’emplacement **CurrentUser** propre à l’utilisateur est le `WindowsPowerShell\Modules` dossier situé à l’emplacement **documents** dans votre profil utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e92c3-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="e92c3-108">Le chemin d’accès spécifique de cet emplacement varie selon la version de Windows et si vous utilisez la redirection de dossiers ou non.</span><span class="sxs-lookup"><span data-stu-id="e92c3-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="e92c3-109">Par défaut, sur Windows 10, cet emplacement est `$HOME\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e92c3-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="e92c3-110">Pour afficher la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e92c3-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="e92c3-111">Pour afficher les chemins d’accès spécifiés dans la `PSModulePath` variable, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e92c3-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="e92c3-112">Pour ajouter des emplacements à la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e92c3-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="e92c3-113">Pour ajouter des chemins d’accès à cette variable, utilisez l’une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e92c3-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="e92c3-114">Pour ajouter une valeur temporaire qui est uniquement disponible pour la session active, exécutez la commande suivante sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="e92c3-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="e92c3-115">Pour ajouter une valeur persistante qui est disponible chaque fois qu’une session est ouverte, ajoutez la commande ci-dessus à un fichier de profil PowerShell ( `$PROFILE` ) ></span><span class="sxs-lookup"><span data-stu-id="e92c3-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="e92c3-116">Pour plus d'informations sur les profils, consultez [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="e92c3-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="e92c3-117">Pour ajouter une variable persistante au registre, créez une nouvelle variable d’environnement utilisateur appelée `PSModulePath` à l’aide de l’éditeur de variables d’environnement dans la boîte de dialogue **Propriétés système** .</span><span class="sxs-lookup"><span data-stu-id="e92c3-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="e92c3-118">Pour ajouter une variable persistante à l’aide d’un script, utilisez la méthode .NET [SetEnvironmentVariable ne contient](/dotnet/api/system.environment.setenvironmentvariable) sur la classe [System. Environment](/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="e92c3-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="e92c3-119">Par exemple, le script suivant ajoute le `C:\Program Files\Fabrikam\Module` chemin d’accès à la valeur de la `PSModulePath` variable d’environnement pour l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e92c3-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="e92c3-120">Pour ajouter le chemin d’accès à la `PSModulePath` variable d’environnement utilisateur, définissez la cible sur « User ».</span><span class="sxs-lookup"><span data-stu-id="e92c3-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="e92c3-121">Pour supprimer des emplacements du PSModulePath</span><span class="sxs-lookup"><span data-stu-id="e92c3-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="e92c3-122">Vous pouvez supprimer les chemins d’accès de la variable à l’aide de méthodes similaires : par exemple, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` supprime le chemin d’accès **c:\ModulePath** de la session active.</span><span class="sxs-lookup"><span data-stu-id="e92c3-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="e92c3-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e92c3-123">See Also</span></span>

[<span data-ttu-id="e92c3-124">Écriture d’un module Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e92c3-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="e92c3-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="e92c3-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
