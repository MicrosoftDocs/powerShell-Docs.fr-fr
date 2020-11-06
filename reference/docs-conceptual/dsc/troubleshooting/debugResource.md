---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,installation
title: Débogage des ressources DSC
description: Cet article explique comment activer le débogage pour les configurations DSC.
ms.openlocfilehash: 5dda217e8dc9cc4b8699c82153c1a588d405d99e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654131"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="337bf-104">Débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="337bf-104">Debugging DSC resources</span></span>

> <span data-ttu-id="337bf-105">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="337bf-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="337bf-106">Dans PowerShell 5.0, DSC contient une nouvelle fonctionnalité qui permet de déboguer une ressource DSC pendant qu’une configuration est appliquée.</span><span class="sxs-lookup"><span data-stu-id="337bf-106">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="337bf-107">Activation du débogage DSC</span><span class="sxs-lookup"><span data-stu-id="337bf-107">Enabling DSC debugging</span></span>

<span data-ttu-id="337bf-108">Avant de pouvoir déboguer une ressource, vous devez activer le débogage en appelant l’applet de commande [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug).</span><span class="sxs-lookup"><span data-stu-id="337bf-108">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span> <span data-ttu-id="337bf-109">Cette applet de commande prend un paramètre obligatoire : **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="337bf-109">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="337bf-110">Vous pouvez vérifier que le débogage a été activé en examinant le résultat d’un appel à [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="337bf-110">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="337bf-111">La sortie PowerShell suivante montre le résultat de l’activation du débogage :</span><span class="sxs-lookup"><span data-stu-id="337bf-111">The following PowerShell output shows the result of enabling debugging:</span></span>

```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```

## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="337bf-112">Démarrage d’une configuration avec le débogage activé</span><span class="sxs-lookup"><span data-stu-id="337bf-112">Starting a configuration with debug enabled</span></span>

<span data-ttu-id="337bf-113">Pour déboguer une ressource DSC, démarrez une configuration qui appelle cette ressource.</span><span class="sxs-lookup"><span data-stu-id="337bf-113">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="337bf-114">Pour cet exemple, nous allons étudier une configuration simple qui appelle la ressource **WindowsFeature** pour vérifier que la fonctionnalité « WindowsPowerShellWebAccess » est bien installée :</span><span class="sxs-lookup"><span data-stu-id="337bf-114">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```

<span data-ttu-id="337bf-115">Après la compilation de la configuration, démarrez-la en appelant [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="337bf-115">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span> <span data-ttu-id="337bf-116">La configuration s’arrête quand le gestionnaire de configuration local appelle la première ressource de la configuration.</span><span class="sxs-lookup"><span data-stu-id="337bf-116">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="337bf-117">Si vous utilisez les paramètres `-Verbose` et `-Wait`, la sortie affiche les lignes que vous devez entrer pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="337bf-117">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```

<span data-ttu-id="337bf-118">À ce stade, le gestionnaire de configuration local a appelé la ressource et arrive au premier point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="337bf-118">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="337bf-119">Les trois dernières lignes de la sortie vous montrent comment attacher au processus et commencer à déboguer le script de ressource.</span><span class="sxs-lookup"><span data-stu-id="337bf-119">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="337bf-120">Débogage du script de la ressource</span><span class="sxs-lookup"><span data-stu-id="337bf-120">Debugging the resource script</span></span>

<span data-ttu-id="337bf-121">Démarrez une nouvelle instance de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="337bf-121">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="337bf-122">Dans le volet de la console, entrez les trois dernières lignes de la sortie de la `Start-DscConfiguration` sous forme de commandes, en remplaçant `<credentials>` par des informations d’identification valides.</span><span class="sxs-lookup"><span data-stu-id="337bf-122">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="337bf-123">Une invite du type suivant doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="337bf-123">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="337bf-124">Le script de ressources s’ouvre dans le volet de script et le débogueur s’arrête à la première ligne de la fonction **Test-TargetResource** (la méthode **Test()** d’une ressource de classe).</span><span class="sxs-lookup"><span data-stu-id="337bf-124">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span> <span data-ttu-id="337bf-125">Vous pouvez désormais utiliser les commandes de débogage dans l’environnement ISE pour parcourir le script de ressources, examiner les valeurs des variables, afficher la pile des appels et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="337bf-125">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="337bf-126">N’oubliez pas que chaque ligne du script de ressources (ou classe) est défini comme point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="337bf-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="337bf-127">Désactivation du débogage DSC</span><span class="sxs-lookup"><span data-stu-id="337bf-127">Disabling DSC debugging</span></span>

<span data-ttu-id="337bf-128">Après avoir appelé [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), tous les appels à [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) causeront des erreurs de configuration dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="337bf-128">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="337bf-129">Pour permettre aux configurations de s’exécuter normalement, vous devez désactiver le débogage en appelant l’applet de commande [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug).</span><span class="sxs-lookup"><span data-stu-id="337bf-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="337bf-130">Le redémarrage ne modifie pas l’état de débogage du Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="337bf-130">Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="337bf-131">Si le débogage est activé, le démarrage d’une configuration générera toujours des erreurs après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="337bf-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="337bf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="337bf-132">See Also</span></span>

- [<span data-ttu-id="337bf-133">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="337bf-133">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="337bf-134">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="337bf-134">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
