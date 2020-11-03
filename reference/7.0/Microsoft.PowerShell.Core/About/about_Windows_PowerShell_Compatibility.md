---
description: Décrit la fonctionnalité de compatibilité de Windows PowerShell pour PowerShell 7.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_Compatibility
ms.openlocfilehash: 777dab1cce4329958337a7c0857b0d712b4387a9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207477"
---
# <a name="about-windows-powershell-compatibility"></a><span data-ttu-id="252b9-104">À propos de la compatibilité Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="252b9-104">About Windows PowerShell compatibility</span></span>

## <a name="short-description"></a><span data-ttu-id="252b9-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="252b9-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="252b9-106">Décrit la fonctionnalité de compatibilité de Windows PowerShell pour PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="252b9-106">Describes the Windows PowerShell Compatibility functionality for PowerShell 7.</span></span>

## <a name="long-description"></a><span data-ttu-id="252b9-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="252b9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="252b9-108">À moins que le manifeste de module indique que le module est compatible avec PowerShell Core, les modules du `%windir%\system32\WindowsPowerShell\v1.0\Modules` dossier sont chargés dans un processus Windows powershell 5,1 en arrière-plan par la fonctionnalité de compatibilité Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-108">Unless the module manifest indicates that module is compatible with PowerShell Core, modules in the `%windir%\system32\WindowsPowerShell\v1.0\Modules` folder are loaded in a background Windows PowerShell 5.1 process by Windows PowerShell Compatibility feature.</span></span>

### <a name="using-the-compatibility-feature"></a><span data-ttu-id="252b9-109">Utilisation de la fonctionnalité de compatibilité</span><span class="sxs-lookup"><span data-stu-id="252b9-109">Using the Compatibility feature</span></span>

<span data-ttu-id="252b9-110">Lorsque le premier module est importé à l’aide de la fonctionnalité de compatibilité Windows PowerShell, PowerShell crée une session à distance nommée `WinPSCompatSession` qui s’exécute dans un processus Windows powershell 5,1 en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="252b9-110">When the first module is imported using Windows PowerShell Compatibility feature, PowerShell creates a remote session named `WinPSCompatSession` that is running in a background Windows PowerShell 5.1 process.</span></span> <span data-ttu-id="252b9-111">Ce processus est créé lorsque la fonctionnalité de compatibilité importe le premier module.</span><span class="sxs-lookup"><span data-stu-id="252b9-111">This process is created when the Compatibility feature imports the first module.</span></span> <span data-ttu-id="252b9-112">Le processus est fermé lorsque le dernier module de ce type est supprimé (à l’aide de `Remove-Module` ) ou lorsque le processus PowerShell s’arrête.</span><span class="sxs-lookup"><span data-stu-id="252b9-112">The process is closed when the last such module is removed (using `Remove-Module`) or when PowerShell process exits.</span></span>

<span data-ttu-id="252b9-113">Les modules chargés dans la `WinPSCompatSession` session sont utilisés via la communication à distance implicite et sont reflétés dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="252b9-113">The modules loaded in the `WinPSCompatSession` session are used via implicit remoting and reflected into current PowerShell session.</span></span> <span data-ttu-id="252b9-114">Il s’agit de la même méthode de transport que celle utilisée pour les travaux PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-114">This is the same transport method used for PowerShell jobs.</span></span>

<span data-ttu-id="252b9-115">Lorsqu’un module est importé dans la `WinPSCompatSession` session, la communication à distance implicite génère un module proxy dans le répertoire de l’utilisateur `$env:Temp` et importe ce module proxy dans la session PowerShell active.</span><span class="sxs-lookup"><span data-stu-id="252b9-115">When a module is imported into the `WinPSCompatSession` session, implicit remoting generates a proxy module in the user's `$env:Temp` directory and imports this proxy module into current PowerShell session.</span></span> <span data-ttu-id="252b9-116">PowerShell peut ainsi détecter que le module a été chargé à l’aide de la fonctionnalité de compatibilité Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-116">This allows PowerShell to detect that the module was loaded using Windows PowerShell Compatibility functionality.</span></span>

<span data-ttu-id="252b9-117">Une fois la session créée, elle peut être utilisée pour les opérations qui ne fonctionnent pas correctement sur les objets désérialisés.</span><span class="sxs-lookup"><span data-stu-id="252b9-117">Once the session is created, it can be used for operations that don't work correctly on deserialized objects.</span></span> <span data-ttu-id="252b9-118">L’intégralité du pipeline est exécutée dans Windows PowerShell et seul le résultat final est retourné.</span><span class="sxs-lookup"><span data-stu-id="252b9-118">The entire pipeline is executed in Windows PowerShell and only the final result is returned.</span></span> <span data-ttu-id="252b9-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="252b9-119">For example:</span></span>

```powershell
$s = Get-PSSession -Name WinPSCompatSession
Invoke-Command -Session $s -ScriptBlock {
  "Running in Windows PowerShell version $($PSVersionTable.PSVersion)"
}
```

<span data-ttu-id="252b9-120">La fonctionnalité de compatibilité peut être appelée de deux manières :</span><span class="sxs-lookup"><span data-stu-id="252b9-120">The Compatibility feature can be invoked in two ways:</span></span>

- <span data-ttu-id="252b9-121">Explicitement en important un module à l’aide du paramètre **UseWindowsPowerShell**</span><span class="sxs-lookup"><span data-stu-id="252b9-121">Explicitly by importing a module using the **UseWindowsPowerShell** parameter</span></span>

   ```powershell
   Import-Module -Name ScheduledTasks -UseWindowsPowerShell
   ```

- <span data-ttu-id="252b9-122">Implicitement en important un module Windows PowerShell par nom de module, chemin d’accès ou chargement automatique via la découverte de commande.</span><span class="sxs-lookup"><span data-stu-id="252b9-122">Implicitly by importing a Windows PowerShell module by module name, path, or autoloading via command discovery.</span></span>

   ```powershell
   Import-Module -Name ServerManager
   Get-AppLockerPolicy -Local
   ```

   <span data-ttu-id="252b9-123">S’il n’est pas déjà chargé, le module AppLocker est chargé lors de l’exécution de  `Get-AppLockerPolicy` .</span><span class="sxs-lookup"><span data-stu-id="252b9-123">If not already loaded, the AppLocker module is autoloaded when you run  `Get-AppLockerPolicy`.</span></span>

<span data-ttu-id="252b9-124">La compatibilité Windows PowerShell bloque le chargement des modules répertoriés dans le `WindowsPowerShellCompatibilityModuleDenyList` paramètre du fichier de configuration PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-124">Windows PowerShell Compatibility blocks loading of modules that are listed in the `WindowsPowerShellCompatibilityModuleDenyList` setting in PowerShell configuration file.</span></span>

<span data-ttu-id="252b9-125">La valeur par défaut de ce paramètre est :</span><span class="sxs-lookup"><span data-stu-id="252b9-125">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityModuleDenyList":  [
   "PSScheduledJob","BestPractices","UpdateServices"
]
```

### <a name="managing-implicit-module-loading"></a><span data-ttu-id="252b9-126">Gestion du chargement de modules implicites</span><span class="sxs-lookup"><span data-stu-id="252b9-126">Managing implicit module loading</span></span>

<span data-ttu-id="252b9-127">Pour désactiver le comportement d’importation implicite de la fonctionnalité de compatibilité Windows PowerShell, utilisez le `DisableImplicitWinCompat` paramètre dans un fichier de configuration PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-127">To disable implicit import behavior of the Windows PowerShell Compatibility feature, use the `DisableImplicitWinCompat` setting in a PowerShell configuration file.</span></span> <span data-ttu-id="252b9-128">Ce paramètre peut être ajouté au `powershell.config.json` fichier.</span><span class="sxs-lookup"><span data-stu-id="252b9-128">This setting can be added to the `powershell.config.json` file.</span></span> <span data-ttu-id="252b9-129">Pour plus d’informations, consultez [about_powershell_config](about_powershell_config.md).</span><span class="sxs-lookup"><span data-stu-id="252b9-129">For more information, see [about_powershell_config](about_powershell_config.md).</span></span>

<span data-ttu-id="252b9-130">Cet exemple montre comment créer un fichier de configuration qui désactive la fonctionnalité de chargement de module implicite de compatibilité Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-130">This example shows how to create a configuration file that disables the implicit module-loading feature of Windows PowerShell Compatibility.</span></span>

```powershell
$ConfigPath = "$PSHOME\DisableWinCompat.powershell.config.json"
$ConfigJSON = ConvertTo-Json -InputObject @{
  "DisableImplicitWinCompat" = $true
  "Microsoft.PowerShell:ExecutionPolicy" = "RemoteSigned"
}
$ConfigJSON | Out-File -Force $ConfigPath
pwsh -settingsFile $ConfigPath
```

<span data-ttu-id="252b9-131">Pour plus d’informations sur la compatibilité des modules, consultez la liste de [compatibilité des modules PowerShell 7](https://aka.ms/PSModuleCompat) .</span><span class="sxs-lookup"><span data-stu-id="252b9-131">For more the latest information about module compatibility, see the [PowerShell 7 module compatibility](https://aka.ms/PSModuleCompat) list.</span></span>

### <a name="managing-cmdlet-clobbering"></a><span data-ttu-id="252b9-132">Gestion des applets de commande effacer</span><span class="sxs-lookup"><span data-stu-id="252b9-132">Managing cmdlet clobbering</span></span>

<span data-ttu-id="252b9-133">La fonctionnalité de compatibilité Windows PowerShell utilise la communication à distance implicite pour charger les modules en mode de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="252b9-133">The Windows PowerShell Compatibility feature uses implicit remoting to load modules in compatibility mode.</span></span> <span data-ttu-id="252b9-134">En conséquence, les commandes exportées par le module sont prioritaires sur les commandes du même nom dans la session PowerShell 7 actuelle.</span><span class="sxs-lookup"><span data-stu-id="252b9-134">The result is that commands exported by the module take precedence over commands of the same name in the current PowerShell 7 session.</span></span> <span data-ttu-id="252b9-135">Dans PowerShell 7.0.0, cela comprenait les modules principaux fournis avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-135">In the PowerShell 7.0.0 release, this included the core modules that ship with PowerShell.</span></span>

<span data-ttu-id="252b9-136">Dans PowerShell 7,1, le comportement a été modifié, de sorte que les modules PowerShell de base suivants ne sont pas écrasé :</span><span class="sxs-lookup"><span data-stu-id="252b9-136">In PowerShell 7.1, the behavior was changed so that the following core PowerShell modules are not clobbered:</span></span>

- <span data-ttu-id="252b9-137">Microsoft. PowerShell. ConsoleHost</span><span class="sxs-lookup"><span data-stu-id="252b9-137">Microsoft.PowerShell.ConsoleHost</span></span>
- <span data-ttu-id="252b9-138">Microsoft.PowerShell.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="252b9-138">Microsoft.PowerShell.Diagnostics</span></span>
- <span data-ttu-id="252b9-139">Microsoft.PowerShell.Host</span><span class="sxs-lookup"><span data-stu-id="252b9-139">Microsoft.PowerShell.Host</span></span>
- <span data-ttu-id="252b9-140">Microsoft.PowerShell.Management</span><span class="sxs-lookup"><span data-stu-id="252b9-140">Microsoft.PowerShell.Management</span></span>
- <span data-ttu-id="252b9-141">Microsoft.PowerShell.Security</span><span class="sxs-lookup"><span data-stu-id="252b9-141">Microsoft.PowerShell.Security</span></span>
- <span data-ttu-id="252b9-142">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="252b9-142">Microsoft.PowerShell.Utility</span></span>
- <span data-ttu-id="252b9-143">Microsoft.WSMan.Management</span><span class="sxs-lookup"><span data-stu-id="252b9-143">Microsoft.WSMan.Management</span></span>

<span data-ttu-id="252b9-144">PowerShell 7,1 a également ajouté la possibilité de répertorier des modules supplémentaires qui ne doivent pas être écrasé par le mode de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="252b9-144">PowerShell 7.1 also added the ability to list additional modules that should not be clobbered by compatibility mode.</span></span>

<span data-ttu-id="252b9-145">Vous pouvez ajouter le `WindowsPowerShellCompatibilityNoClobberModuleList` paramètre au fichier de configuration PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252b9-145">You can add the `WindowsPowerShellCompatibilityNoClobberModuleList` setting to PowerShell configuration file.</span></span> <span data-ttu-id="252b9-146">La valeur de ce paramètre est une liste de noms de module séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="252b9-146">The value of this setting is a comma-separated list of module names.</span></span> <span data-ttu-id="252b9-147">La valeur par défaut de ce paramètre est :</span><span class="sxs-lookup"><span data-stu-id="252b9-147">The default value of this setting is:</span></span>

```json
"WindowsPowerShellCompatibilityNoClobberModuleList": [ ]
```

## <a name="limitations"></a><span data-ttu-id="252b9-148">Limites</span><span class="sxs-lookup"><span data-stu-id="252b9-148">Limitations</span></span>

<span data-ttu-id="252b9-149">La fonctionnalité de compatibilité de Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="252b9-149">The Windows PowerShell Compatibility functionality:</span></span>

1. <span data-ttu-id="252b9-150">Fonctionne uniquement localement sur les ordinateurs Windows</span><span class="sxs-lookup"><span data-stu-id="252b9-150">Only works locally on Windows computers</span></span>
1. <span data-ttu-id="252b9-151">Requiert Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="252b9-151">Requires that Windows PowerShell 5.1</span></span>
1. <span data-ttu-id="252b9-152">Fonctionne sur les paramètres et les valeurs de retour de l’applet de commande sérialisés, et non sur les objets actifs</span><span class="sxs-lookup"><span data-stu-id="252b9-152">Operates on serialized cmdlet parameters and return values, not on live objects</span></span>
1. <span data-ttu-id="252b9-153">Tous les modules importés dans la session de communication à distance Windows PowerShell partagent la même instance d’exécution.</span><span class="sxs-lookup"><span data-stu-id="252b9-153">All modules imported into the Windows PowerShell remoting session share the same runspace.</span></span>

## <a name="keywords"></a><span data-ttu-id="252b9-154">Mots clés</span><span class="sxs-lookup"><span data-stu-id="252b9-154">Keywords</span></span>

<span data-ttu-id="252b9-155">about_Windows_PowerShell_Compatibility</span><span class="sxs-lookup"><span data-stu-id="252b9-155">about_Windows_PowerShell_Compatibility</span></span>

## <a name="see-also"></a><span data-ttu-id="252b9-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="252b9-156">See also</span></span>

[<span data-ttu-id="252b9-157">about_Modules</span><span class="sxs-lookup"><span data-stu-id="252b9-157">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="252b9-158">Module d’importation</span><span class="sxs-lookup"><span data-stu-id="252b9-158">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
