---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Appliquer, obtenir et tester des configurations sur un nœud
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401725"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a><span data-ttu-id="561b5-103">Appliquer, obtenir et tester des configurations sur un nœud</span><span class="sxs-lookup"><span data-stu-id="561b5-103">Apply, Get, and Test Configurations on a Node</span></span>

<span data-ttu-id="561b5-104">Ce guide vous explique comment travailler avec des Configurations sur une nœud cible.</span><span class="sxs-lookup"><span data-stu-id="561b5-104">This guide will show you how to work with Configurations on a target Node.</span></span> <span data-ttu-id="561b5-105">Ce guide est divisé en les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="561b5-105">This guide is broken up into the following steps:</span></span>

## <a name="apply-a-configuration"></a><span data-ttu-id="561b5-106">Appliquer une Configuration</span><span class="sxs-lookup"><span data-stu-id="561b5-106">Apply a Configuration</span></span>

<span data-ttu-id="561b5-107">Pour appliquer et gérer une Configuration, nous devons générer un fichier « .mof ».</span><span class="sxs-lookup"><span data-stu-id="561b5-107">In order to apply and manage a Configuration, we need to generate a ".mof" file.</span></span> <span data-ttu-id="561b5-108">Le code suivant représente une Configuration simple qui sera utilisée tout au long de ce guide.</span><span class="sxs-lookup"><span data-stu-id="561b5-108">The following code will represent a simple Configuration that will be used throughout this guide.</span></span>

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

<span data-ttu-id="561b5-109">Compilation de cette configuration génère deux fichiers « .mof ».</span><span class="sxs-lookup"><span data-stu-id="561b5-109">Compiling this configuration will yield two ".mof" files.</span></span>

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

<span data-ttu-id="561b5-110">Pour appliquer une Configuration, utilisez le [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) applet de commande.</span><span class="sxs-lookup"><span data-stu-id="561b5-110">To apply a Configuration, use the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="561b5-111">Le `-Path` paramètre spécifie un répertoire où se trouvent les fichiers « .mof ».</span><span class="sxs-lookup"><span data-stu-id="561b5-111">The `-Path` parameter specifies a directory where ".mof" files reside.</span></span> <span data-ttu-id="561b5-112">Si aucun `-Computername` est spécifié, `Start-DSCConfiguration` tentera d’appliquer chaque Configuration pour le nom d’ordinateur spécifié par le nom du fichier « .mof » (\<computername\>.mof).</span><span class="sxs-lookup"><span data-stu-id="561b5-112">If no `-Computername` is specified, `Start-DSCConfiguration` will attempt to apply each Configuration to the computer name specified by the name of the '.mof' file (\<computername\>.mof).</span></span> <span data-ttu-id="561b5-113">Spécifiez `-Verbose` à `Start-DSCConfiguration` pour voir une sortie plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="561b5-113">Specify `-Verbose` to `Start-DSCConfiguration` to see more verbose output.</span></span>

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

<span data-ttu-id="561b5-114">Si `-Wait` n’est pas spécifié, vous voyez un travail créé.</span><span class="sxs-lookup"><span data-stu-id="561b5-114">If `-Wait` is not specified, you see one job created.</span></span> <span data-ttu-id="561b5-115">Le travail créé aura une **ChildJob** pour chaque fichier « .mof » traitées par `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="561b5-115">The job created will have one **ChildJob** for each ".mof" file processed by `Start-DSCConfiguration`.</span></span>

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

<span data-ttu-id="561b5-116">Si une Configuration est trop de temps et que vous souhaitez l’arrêter, vous pouvez utiliser [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) à arrêter l’application sur le nœud local.</span><span class="sxs-lookup"><span data-stu-id="561b5-116">If a Configuration is taking a long time and you want to stop it, you can use [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) to stop application on the local Node.</span></span>

```powershell
Stop-DSCConfiguration -Force
```

<span data-ttu-id="561b5-117">Une fois terminé, vous pouvez afficher l’état des tâches via l’objet de tâche retourné par [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span><span class="sxs-lookup"><span data-stu-id="561b5-117">Once complete, you can view the status of the jobs through the job object returned by [Get-Job](/powershell/module/microsoft.powershell.core/get-job).</span></span>

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

<span data-ttu-id="561b5-118">Pour voir les **Verbose** de sortie, utilisez les commandes suivantes pour afficher le **Verbose** stream pour chaque **ChildJob**.</span><span class="sxs-lookup"><span data-stu-id="561b5-118">To see the **Verbose** output, use the following commands to view the **Verbose** stream for each **ChildJob**.</span></span> <span data-ttu-id="561b5-119">Pour plus d’informations sur les tâches PowerShell, consultez [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span><span class="sxs-lookup"><span data-stu-id="561b5-119">For more about PowerShell jobs, see [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).</span></span>

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="561b5-120">À compter de PowerShell 5.0, le `-UseExisting` paramètre a été ajouté à `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="561b5-120">Beginning in PowerShell 5.0, the `-UseExisting` parameter was added to `Start-DSCConfiguration`.</span></span> <span data-ttu-id="561b5-121">En spécifiant `-UseExisting`, vous demander à l’applet de commande à utiliser la Configuration appliquée existante au lieu de celle spécifiée par la `-Path` paramètre.</span><span class="sxs-lookup"><span data-stu-id="561b5-121">By specifying `-UseExisting`, you instruct the cmdlet to use the existing applied Configuration instead of one specified by the `-Path` parameter.</span></span>

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a><span data-ttu-id="561b5-122">Tester une Configuration</span><span class="sxs-lookup"><span data-stu-id="561b5-122">Test a Configuration</span></span>

<span data-ttu-id="561b5-123">Vous pouvez tester une Configuration actuellement appliquée à l’aide [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="561b5-123">You can test a currently applied Configuration using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span> <span data-ttu-id="561b5-124">`Test-DSCConfiguration` retournera `True` si le nœud est conforme, et `False` si elle n’est pas.</span><span class="sxs-lookup"><span data-stu-id="561b5-124">`Test-DSCConfiguration` will return `True` if the Node is compliant, and `False` if it is not.</span></span>

```powershell
Test-DSCConfiguration
```

<span data-ttu-id="561b5-125">À compter de PowerShell 5.0, le `-Detailed` paramètre a été ajouté, qui retourne un objet avec des collections de **ResourcesInDesiredState** et **ResourcesNotInDesiredState**</span><span class="sxs-lookup"><span data-stu-id="561b5-125">Beginning in PowerShell 5.0, the `-Detailed` parameter was added which returns an object with collections for **ResourcesInDesiredState** and **ResourcesNotInDesiredState**</span></span>

```powershell
Test-DSCConfiguration -Detailed
```

<span data-ttu-id="561b5-126">À compter de PowerShell 5.0, vous pouvez tester une Configuration sans l’appliquer.</span><span class="sxs-lookup"><span data-stu-id="561b5-126">Beginning in PowerShell 5.0 you can test a Configuration without applying it.</span></span> <span data-ttu-id="561b5-127">Le `-ReferenceConfiguration` paramètre accepte le chemin d’accès d’un fichier « .mof » pour tester le nœud par rapport.</span><span class="sxs-lookup"><span data-stu-id="561b5-127">The `-ReferenceConfiguration` parameter accepts the path of a ".mof" file to test the Node against.</span></span> <span data-ttu-id="561b5-128">Ne **définir** actions sont effectuées sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="561b5-128">No **Set** actions are taken against the Node.</span></span> <span data-ttu-id="561b5-129">Dans PowerShell 4.0, il existe des solutions de contournement pour tester une Configuration sans l’appliquer, mais ils ne sont pas abordées ici.</span><span class="sxs-lookup"><span data-stu-id="561b5-129">In PowerShell 4.0, there are workarounds to test a Configuration without applying it, but they are not discussed here.</span></span>

## <a name="get-configuration-values"></a><span data-ttu-id="561b5-130">Obtenir les valeurs de Configuration</span><span class="sxs-lookup"><span data-stu-id="561b5-130">Get Configuration Values</span></span>

<span data-ttu-id="561b5-131">Le [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) applet de commande renvoie les valeurs actuelles de toutes les ressources configurées dans la Configuration actuellement appliquée.</span><span class="sxs-lookup"><span data-stu-id="561b5-131">The [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet returns the current values for any configured resources in the currently applied Configuration.</span></span>

```powershell
Get-DSCConfiguration
```

<span data-ttu-id="561b5-132">Sortie à partir de notre exemple de Configuration ressemblerait à ceci si appliquées avec succès.</span><span class="sxs-lookup"><span data-stu-id="561b5-132">Output from our sample Configuration would look like this if applied successfully.</span></span>

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a><span data-ttu-id="561b5-133">Obtenir l’état de Configuration</span><span class="sxs-lookup"><span data-stu-id="561b5-133">Get Configuration Status</span></span>

<span data-ttu-id="561b5-134">À compter de PowerShell 5.0 le [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) applet de commande vous permet de consulter l’historique des Configurations appliquées au nœud.</span><span class="sxs-lookup"><span data-stu-id="561b5-134">Beginning in PowerShell 5.0 the [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet allows you to see the history of applied Configurations to the node.</span></span> <span data-ttu-id="561b5-135">PowerShell DSC effectue le suivi des {{N}} dernières Configurations appliquées dans **Push** ou **extraire** mode.</span><span class="sxs-lookup"><span data-stu-id="561b5-135">PowerShell DSC keeps track of the last {{N}} Configurations applied in **Push** or **Pull** mode.</span></span> <span data-ttu-id="561b5-136">Cela inclut tous *cohérence* vérifications exécutées par le Gestionnaire de configuration local.</span><span class="sxs-lookup"><span data-stu-id="561b5-136">This includes any *consistency* checks executed by the LCM.</span></span> <span data-ttu-id="561b5-137">Par défaut, `Get-DSCConfigurationStatus` vous montre uniquement la dernière entrée de l’historique.</span><span class="sxs-lookup"><span data-stu-id="561b5-137">By default, `Get-DSCConfigurationStatus` shows you the last history entry only.</span></span>

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

<span data-ttu-id="561b5-138">Utilisez le `-All` paramètre pour afficher tous les historique d’état de la Configuration.</span><span class="sxs-lookup"><span data-stu-id="561b5-138">Use the `-All` parameter to see all Configuration Status history.</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-139">Sortie est tronquée par souci de concision.</span><span class="sxs-lookup"><span data-stu-id="561b5-139">Output is truncated for brevity.</span></span>

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a><span data-ttu-id="561b5-140">Gérer des Documents de Configuration</span><span class="sxs-lookup"><span data-stu-id="561b5-140">Manage Configuration Documents</span></span>

<span data-ttu-id="561b5-141">Le LCM gère la Configuration du nœud en travaillant avec **Documents de Configuration**.</span><span class="sxs-lookup"><span data-stu-id="561b5-141">The LCM manages the Configuration of the Node by working with **Configuration Documents**.</span></span> <span data-ttu-id="561b5-142">Ces fichiers « .mof » se trouvent dans le répertoire « C:\Windows\System32\Configuration ».</span><span class="sxs-lookup"><span data-stu-id="561b5-142">These ".mof" files reside in the "C:\Windows\System32\Configuration" directory.</span></span>

<span data-ttu-id="561b5-143">À compter de PowerShell 5.0 le [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) vous permet de supprimer les fichiers « .mof » pour arrêter les vérifications de cohérence futures ou de supprimer une Configuration qui comporte des erreurs lorsqu’il est appliqué.</span><span class="sxs-lookup"><span data-stu-id="561b5-143">Beginning in PowerShell 5.0 the [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) allows you to remove the ".mof" files to stop future consistency checks or remove a Configuration that has errors when applied.</span></span> <span data-ttu-id="561b5-144">Le `-Stage` paramètre permet de spécifier le fichier « .mof » que vous souhaitez supprimer.</span><span class="sxs-lookup"><span data-stu-id="561b5-144">The `-Stage` parameter allows you to specify which ".mof" file you want to remove.</span></span>

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> <span data-ttu-id="561b5-145">Dans PowerShell 4.0, vous pouvez toujours supprimer ces fichiers « .mof » directement à l’aide [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span><span class="sxs-lookup"><span data-stu-id="561b5-145">In PowerShell 4.0, you can still remove these ".mof" files directly using [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).</span></span>

## <a name="publish-configurations"></a><span data-ttu-id="561b5-146">Publier des Configurations</span><span class="sxs-lookup"><span data-stu-id="561b5-146">Publish Configurations</span></span>

<span data-ttu-id="561b5-147">À compter de PowerShell 5.0, le [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) applet de commande a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="561b5-147">Beginning in PowerShell 5.0, the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet was added.</span></span> <span data-ttu-id="561b5-148">Cette applet de commande vous permet de publier un fichier « .mof » à des ordinateurs distants sans l’appliquer.</span><span class="sxs-lookup"><span data-stu-id="561b5-148">This cmdlet allows you to publish a ".mof" file to remote computers, without applying it.</span></span>

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a><span data-ttu-id="561b5-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="561b5-149">See also</span></span>

- [<span data-ttu-id="561b5-150">Méthodes Get, Test et Set</span><span class="sxs-lookup"><span data-stu-id="561b5-150">Get, Test, and Set</span></span>](../resources/get-test-set.md)
