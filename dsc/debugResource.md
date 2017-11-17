---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Débogage des ressources DSC"
ms.openlocfilehash: 944eca3d9f21d7e06d128caf19e4aebacc5c0b26
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="b0860-103">Débogage des ressources DSC</span><span class="sxs-lookup"><span data-stu-id="b0860-103">Debugging DSC resources</span></span>

> <span data-ttu-id="b0860-104">S’applique à : Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b0860-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b0860-105">Dans PowerShell 5.0, DSC contient une nouvelle fonctionnalité qui permet de déboguer une ressource DSC pendant qu’une configuration est appliquée.</span><span class="sxs-lookup"><span data-stu-id="b0860-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuraiton (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="b0860-106">Activation du débogage DSC</span><span class="sxs-lookup"><span data-stu-id="b0860-106">Enabling DSC debugging</span></span>
<span data-ttu-id="b0860-107">Avant de pouvoir déboguer une ressource, vous devez activer le débogage en appelant l’applet de commande [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0860-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx) cmdlet.</span></span> <span data-ttu-id="b0860-108">Cette applet de commande prend un paramètre obligatoire : **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="b0860-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span> 

<span data-ttu-id="b0860-109">Vous pouvez vérifier que le débogage a été activé en examinant le résultat d’un appel à [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0860-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).</span></span>

<span data-ttu-id="b0860-110">La sortie PowerShell suivante montre le résultat de l’activation du débogage :</span><span class="sxs-lookup"><span data-stu-id="b0860-110">The following PowerShell output shows the result of enabling debugging:</span></span>


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


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="b0860-111">Démarrage d’une configuration avec le débogage activé</span><span class="sxs-lookup"><span data-stu-id="b0860-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="b0860-112">Pour déboguer une ressource DSC, démarrez une configuration qui appelle cette ressource.</span><span class="sxs-lookup"><span data-stu-id="b0860-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span> <span data-ttu-id="b0860-113">Pour cet exemple, nous allons étudier une configuration simple qui appelle la ressource [WindowsFeature](windowsfeatureResource.md) pour vérifier que la fonctionnalité « WindowsPowerShellWebAccess » est bien installée :</span><span class="sxs-lookup"><span data-stu-id="b0860-113">For this example, we'll look at a simple configuration that calls the [WindowsFeature](windowsfeatureResource.md) resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

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
<span data-ttu-id="b0860-114">Après la compilation de la configuration, démarrez-la en appelant [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0860-114">After compiling the configuration, start it by calling [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx).</span></span> <span data-ttu-id="b0860-115">La configuration s’arrête quand le gestionnaire de configuration local appelle la première ressource de la configuration.</span><span class="sxs-lookup"><span data-stu-id="b0860-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span> <span data-ttu-id="b0860-116">Si vous utilisez les paramètres `-Verbose` et `-Wait`, la sortie affiche les lignes que vous devez entrer pour démarrer le débogage.</span><span class="sxs-lookup"><span data-stu-id="b0860-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

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
<span data-ttu-id="b0860-117">À ce stade, le gestionnaire de configuration local a appelé la ressource et arrive au premier point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b0860-117">At this point, the LCM has called the resource, and come to the first break point.</span></span> <span data-ttu-id="b0860-118">Les trois dernières lignes de la sortie vous montrent comment attacher au processus et commencer à déboguer le script de ressource.</span><span class="sxs-lookup"><span data-stu-id="b0860-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="b0860-119">Débogage du script de la ressource</span><span class="sxs-lookup"><span data-stu-id="b0860-119">Debugging the resource script</span></span>

<span data-ttu-id="b0860-120">Démarrez une nouvelle instance de PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b0860-120">Start a new instance of the PowerShell ISE.</span></span> <span data-ttu-id="b0860-121">Dans le volet de la console, entrez les trois dernières lignes de la sortie de la `Start-DscConfiguration` sous forme de commandes, en remplaçant `<credentials>` par des informations d’identification valides.</span><span class="sxs-lookup"><span data-stu-id="b0860-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span> <span data-ttu-id="b0860-122">Une invite du type suivant doit s’afficher :</span><span class="sxs-lookup"><span data-stu-id="b0860-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="b0860-123">Le script de ressources s’ouvre dans le volet de script et le débogueur s’arrête à la première ligne de la fonction **Test-TargetResource** (la méthode **Test()** d’une ressource de classe).</span><span class="sxs-lookup"><span data-stu-id="b0860-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="b0860-124">Vous pouvez désormais utiliser les commandes de débogage dans l’environnement ISE pour parcourir le script de ressources, examiner les valeurs des variables, afficher la pile des appels et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b0860-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="b0860-125">Pour plus d’informations sur le débogage dans PowerShell ISE, consultez [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx) (Comment déboguer des scripts dans Windows PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="b0860-125">For information about debugging in the PowerShell ISE, see [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx).</span></span> <span data-ttu-id="b0860-126">N’oubliez pas que chaque ligne du script de ressources (ou classe) est défini comme point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="b0860-126">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="b0860-127">Désactivation du débogage DSC</span><span class="sxs-lookup"><span data-stu-id="b0860-127">Disabling DSC debugging</span></span>

<span data-ttu-id="b0860-128">Après avoir appelé [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), tous les appels à [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) causeront des erreurs de configuration dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="b0860-128">After calling [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx), all calls to [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="b0860-129">Pour permettre aux configurations de s’exécuter normalement, vous devez désactiver le débogage en appelant l’applet de commande [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx).</span><span class="sxs-lookup"><span data-stu-id="b0860-129">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx) cmdlet.</span></span>

><span data-ttu-id="b0860-130">**Remarque :** le redémarrage ne modifie pas l’état de débogage du LCM.</span><span class="sxs-lookup"><span data-stu-id="b0860-130">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="b0860-131">Si le débogage est activé, le démarrage d’une configuration générera toujours des erreurs après un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="b0860-131">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>


## <a name="see-also"></a><span data-ttu-id="b0860-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0860-132">See Also</span></span>
- [<span data-ttu-id="b0860-133">Écriture d’une ressource DSC personnalisée avec MOF</span><span class="sxs-lookup"><span data-stu-id="b0860-133">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="b0860-134">Écriture d’une ressource DSC personnalisée avec les classes PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0860-134">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)

