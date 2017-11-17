---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,configuration
ms.openlocfilehash: f39328b240a36deb40d484c4aedb889cee91dc8d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="9a853-102">Problèmes connus liés à la Configuration d’état souhaité (DSC)</span><span class="sxs-lookup"><span data-stu-id="9a853-102">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

<a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="9a853-103">Modification avec rupture : les certificats utilisés pour chiffrer/déchiffrer les mots de passe dans les configurations DSC peuvent ne pas fonctionner après l’installation de WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="9a853-103">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9a853-104">Dans les versions WMF 4.0 et WMF 5.0 Preview, DSC n’autorisait pas les mots de passe de plus de 121 caractères dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="9a853-104">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="9a853-105">DSC forçait l’utilisation de mots de passe courts même si des mots de passe forts et longs étaient souhaités.</span><span class="sxs-lookup"><span data-stu-id="9a853-105">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="9a853-106">Cette modification avec rupture autorise les mots de passe de longueur arbitraire dans la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="9a853-106">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="9a853-107">**Résolution :** Recréez le certificat avec l’attribut Data Encipherment ou Key Encipherment Key Usage, et avec l’attribut Document Encryption Enhanced Key Usage (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="9a853-107">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="9a853-108">L’article TechNet <https://technet.microsoft.com/en-us/library/dn807171.aspx> contient des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9a853-108">Technet article <https://technet.microsoft.com/en-us/library/dn807171.aspx> has more information.</span></span>


<a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="9a853-109">Les applets de commande DSC peuvent échouer après l’installation de WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="9a853-109">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>
------------------------------------------------------------------------------------
<span data-ttu-id="9a853-110">Start-DscConfiguration et d’autres applets de commande DSC peuvent échouer après l’installation de WMF 5.0 RTM avec l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="9a853-110">Start-DscConfiguration and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

<span data-ttu-id="9a853-111">**Résolution :** Supprimez DSCEngineCache.mof en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="9a853-111">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>
    
```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```


<a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="9a853-112">Les applets de commande DSC peuvent ne pas fonctionner si WMF 5.0 RTM est installé sur WMF 5.0 Production Preview</span><span class="sxs-lookup"><span data-stu-id="9a853-112">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>
------------------------------------------------------
<span data-ttu-id="9a853-113">**Résolution :** Exécutez la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="9a853-113">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```


<a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="9a853-114">Le gestionnaire de configuration local peut basculer dans un état instable lors de l’utilisation de Get-DscConfiguration en DebugMode</span><span class="sxs-lookup"><span data-stu-id="9a853-114">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>
-------------------------------------------------------------------------------

<span data-ttu-id="9a853-115">Si le gestionnaire de configuration local est en DebugMode, une pression sur Ctrl+C pour arrêter le traitement de Get-DscConfiguration peut provoquer son basculement dans un état instable où la plupart des applets de commande DSC ne fonctionneront pas.</span><span class="sxs-lookup"><span data-stu-id="9a853-115">If LCM is in DebugMode, pressing CTRL+C to stop the processing of Get-DscConfiguration can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="9a853-116">**Résolution :** N’appuyez pas sur Ctrl+C lors du débogage de l’applet de commande Get-DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="9a853-116">**Resolution:** Don’t press CTRL+C while debugging Get-DscConfiguration cmdlet.</span></span>


<a name="stop-dscconfiguration-may-hang-in-debugmode"></a><span data-ttu-id="9a853-117">Stop-DscConfiguration peut se bloquer en DebugMode</span><span class="sxs-lookup"><span data-stu-id="9a853-117">Stop-DscConfiguration may hang in DebugMode</span></span>
------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="9a853-118">Si le gestionnaire de configuration local est en DebugMode, Stop-DscConfiguration peut se bloquer lors d’une tentative d’arrêt d’une opération démarrée par Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="9a853-118">If LCM is in DebugMode, Stop-DscConfiguration may hang while trying to stop an operation started by Get-DscConfiguration</span></span>

<span data-ttu-id="9a853-119">**Résolution :** terminez le débogage de l’opération démarrée par Get-DscConfiguration comme décrit dans la section « [Débogage des ressources DSC](https://msdn.microsoft.com/powershell/dsc/debugresource) ».</span><span class="sxs-lookup"><span data-stu-id="9a853-119">**Resolution:** Finish the debugging of the operation started by Get-DscConfiguration as outlined in section ‘[Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource)’.</span></span>


<a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="9a853-120">Aucun message d’erreur détaillé n’est affiché en DebugMode</span><span class="sxs-lookup"><span data-stu-id="9a853-120">No Verbose Error Messages are shown in DebugMode</span></span>
-----------------------------------------------------------------------------------
<span data-ttu-id="9a853-121">Si le gestionnaire de configuration local est en DebugMode, aucun message d’erreur détaillé n’est affiché à partir des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="9a853-121">If LCM is in DebugMode, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="9a853-122">**Résolution :** Désactivez *DebugMode* pour afficher les messages détaillés à partir de la ressource</span><span class="sxs-lookup"><span data-stu-id="9a853-122">**Resolution:** Disable *DebugMode* to see verbose messages from the resource</span></span>


<a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="9a853-123">Les opérations Invoke-DscResource ne peuvent pas être récupérées par l’applet de commande Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="9a853-123">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>
--------------------------------------------------------------------------------------
<span data-ttu-id="9a853-124">Après l’utilisation de l’applet de commande Invoke-DscResource pour appeler directement les méthodes d’une ressource quelconque, les enregistrements de cette opération ne peuvent pas être récupérés ultérieurement par Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="9a853-124">After using Invoke-DscResource cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through Get-DscConfigurationStatus at a later time.</span></span>

<span data-ttu-id="9a853-125">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-125">**Resolution:** None.</span></span>


<a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="9a853-126">Get-DscConfigurationStatus retourne les opérations de cycle d’extraction en tant que type *Consistency*</span><span class="sxs-lookup"><span data-stu-id="9a853-126">Get-DscConfigurationStatus returns pull cycle operations as type *Consistency*</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="9a853-127">Quand un nœud est configuré en mode d’actualisation par extraction, pour chaque opération d’extraction effectuée, l’applet de commande Get-DscConfigurationStatus indique que le type d’opération est *Consistency* au lieu de *Initial*</span><span class="sxs-lookup"><span data-stu-id="9a853-127">When a node is set to PULL refresh mode, for each pull operation performed, Get-DscConfigurationStatus cmdlet reports the operation type as *Consistency* instead of *Initial*</span></span>

<span data-ttu-id="9a853-128">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-128">**Resolution:** None.</span></span>

<a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="9a853-129">L’applet de commande Invoke-DscResource ne retourne pas les messages dans l’ordre dans lequel ils ont été générés</span><span class="sxs-lookup"><span data-stu-id="9a853-129">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>
---------------------------------------------------------------------------------
<span data-ttu-id="9a853-130">L’applet de commande Invoke-DscResource ne retourne pas les messages détaillés, d’avertissement et d’erreur dans l’ordre dans lequel ils ont été générés par le gestionnaire de configuration local ou la ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="9a853-130">The Invoke-DscResource cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="9a853-131">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-131">**Resolution:** None.</span></span>


<a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="9a853-132">Les ressources DSC ne peuvent pas être déboguées facilement en cas d’utilisation avec Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="9a853-132">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>
-----------------------------------------------------------------------
<span data-ttu-id="9a853-133">Quand le gestionnaire de configuration local s’exécute en mode débogage (pour plus de détails, consultez [Débogage des ressources DSC](https://msdn.microsoft.com/powershell/dsc/debugresource)), l’applet de commande Invoke-DscResource ne donne pas d’informations sur l’instance d’exécution à laquelle se connecter pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="9a853-133">When LCM is running in debug mode (see [Debugging DSC resources](https://msdn.microsoft.com/powershell/dsc/debugresource) for more details), Invoke-DscResource cmdlet does not give information about runspace to connect to for debugging.</span></span>
<span data-ttu-id="9a853-134">**Résolution :** Effectuez la découverte et la jonction à l’instance d’exécution à l’aide des applets de commande **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** et **Debug-Runspace** pour déboguer la ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="9a853-134">**Resolution:** Discover and attach to the runspace using cmdlets **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** and **Debug-Runspace** to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```


<a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="9a853-135">Différents documents de configuration partielle pour le même nœud ne peuvent pas avoir des noms de ressources identiques</span><span class="sxs-lookup"><span data-stu-id="9a853-135">Various Partial Configuration documents for same node cannot have identical resource names</span></span>
------------------------------------------------------------------------------------------

<span data-ttu-id="9a853-136">Pour plusieurs configurations partielles déployées sur un même nœud, des noms de ressources identiques provoquent des erreurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9a853-136">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="9a853-137">**Résolution :** Utilisez des noms différents pour les mêmes ressources dans différentes configurations partielles.</span><span class="sxs-lookup"><span data-stu-id="9a853-137">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>


<a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="9a853-138">Start-DscConfiguration –UseExisting ne fonctionne pas avec -Credential</span><span class="sxs-lookup"><span data-stu-id="9a853-138">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>
------------------------------------------------------------------

<span data-ttu-id="9a853-139">Quand vous utilisez Start-DscConfiguration avec le paramètre –UseExisting, le paramètre –Credential est ignoré.</span><span class="sxs-lookup"><span data-stu-id="9a853-139">When using Start-DscConfiguration with –UseExisting parameter, the –Credential parameter is ignored.</span></span> <span data-ttu-id="9a853-140">DSC utilise l’identité de processus par défaut pour continuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="9a853-140">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="9a853-141">Cela provoque une erreur quand des informations d’identification différentes sont nécessaires pour continuer sur le nœud distant.</span><span class="sxs-lookup"><span data-stu-id="9a853-141">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="9a853-142">**Résolution :** Utilisez une session CIM pour les opérations DSC à distance :</span><span class="sxs-lookup"><span data-stu-id="9a853-142">**Resolution:** Use CIM session for remote DSC operations:</span></span>
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```


<a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="9a853-143">Adresses IPv6 en tant que noms de nœuds dans les configurations DSC</span><span class="sxs-lookup"><span data-stu-id="9a853-143">IPv6 Addresses as Node Names in DSC configurations</span></span>
--------------------------------------------------
<span data-ttu-id="9a853-144">Les adresses IPv6 en tant que noms de nœuds dans les scripts de configuration DSC ne sont pas prises en charge dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9a853-144">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="9a853-145">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-145">**Resolution:** None.</span></span>


<a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="9a853-146">Débogage des ressources DSC basées sur une classe</span><span class="sxs-lookup"><span data-stu-id="9a853-146">Debugging of Class-Based DSC Resources</span></span>
--------------------------------------
<span data-ttu-id="9a853-147">Le débogage des ressources DSC basées sur une classe n’est pas pris en charge dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9a853-147">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="9a853-148">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-148">**Resolution:** None.</span></span>


<a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="9a853-149">Les variables et fonctions définies dans l’étendue $script dans une ressource DSC basée sur une classe ne sont pas conservées entre les appels à une ressource DSC</span><span class="sxs-lookup"><span data-stu-id="9a853-149">Variables & Functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span> 
-------------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9a853-150">Plusieurs appels successifs à Start-DSCConfiguration échouent si la configuration utilise une ressource basée sur une classe qui a des variables ou des fonctions définies dans l’étendue $script.</span><span class="sxs-lookup"><span data-stu-id="9a853-150">Multiple consecutive calls to Start-DSCConfiguration will fail if configuration is using any class-based resource which has variables or functions defined in $script scope.</span></span>

<span data-ttu-id="9a853-151">**Résolution :** Définissez toutes les variables et fonctions dans la classe de ressource DSC proprement dite.</span><span class="sxs-lookup"><span data-stu-id="9a853-151">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="9a853-152">Aucune variable/fonction d’étendue $script.</span><span class="sxs-lookup"><span data-stu-id="9a853-152">No $script scope variables/functions.</span></span>


<a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="9a853-153">Débogage de ressources DSC quand une ressource utilise PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9a853-153">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>
----------------------------------------------------------------------
<span data-ttu-id="9a853-154">Le débogage de ressources DSC quand une ressource utilise la propriété *PSDscRunAsCredential* dans la configuration n’est pas pris en charge dans cette version.</span><span class="sxs-lookup"><span data-stu-id="9a853-154">DSC Resource debugging when a resource is using the *PSDscRunAsCredential* property in the configuration is not suported in this release.</span></span>

<span data-ttu-id="9a853-155">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-155">**Resolution:** None.</span></span>


<a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="9a853-156">PsDscRunAsCredential n’est pas pris en charge pour les ressources DSC composites</span><span class="sxs-lookup"><span data-stu-id="9a853-156">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>
----------------------------------------------------------------

<span data-ttu-id="9a853-157">**Résolution :** Utilisez si possible une propriété Credential.</span><span class="sxs-lookup"><span data-stu-id="9a853-157">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="9a853-158">Exemple de ServiceSet et WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="9a853-158">Example ServiceSet and WindowsFeatureSet</span></span>


<a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="9a853-159">*Get-DscResource -Syntax* ne reflète pas correctement PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9a853-159">*Get-DscResource -Syntax* does not reflect PsDscRunAsCredential correctly</span></span>
-------------------------------------------------------------------------
<span data-ttu-id="9a853-160">Get-DscResource -Syntax ne reflète pas correctement PsDscRunAsCredential quand la ressource la marque comme étant obligatoire ou ne la prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="9a853-160">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="9a853-161">**Résolution :** Aucune.</span><span class="sxs-lookup"><span data-stu-id="9a853-161">**Resolution:** None.</span></span> <span data-ttu-id="9a853-162">Cependant, la création de configuration dans ISE reflète les métadonnées correctes concernant la propriété PsDscRunAsCredential lors de l’utilisation d’IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="9a853-162">However, authoring configuration in ISE reflects correct metadata about PsDscRunAsCredential property when using IntelliSense.</span></span>


<a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="9a853-163">WindowsOptionalFeature n’est pas disponible dans Windows 7</span><span class="sxs-lookup"><span data-stu-id="9a853-163">WindowsOptionalFeature is not available in Windows 7</span></span>
-----------------------------------------------------

<span data-ttu-id="9a853-164">La ressource DSC WindowsOptionalFeature n’est pas disponible dans Windows 7.</span><span class="sxs-lookup"><span data-stu-id="9a853-164">The WindowsOptionalFeature DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="9a853-165">Cette ressource nécessite le module DISM et les applets de commande DISM qui sont disponibles à partir de Windows 8 et des versions plus récentes du système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="9a853-165">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

<a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="9a853-166">Pour les ressources DSC basées sur une classe, Import-DscResource -ModuleVersion peut ne pas fonctionner comme prévu</span><span class="sxs-lookup"><span data-stu-id="9a853-166">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>   
------------------------------------------------------------------------------------------
<span data-ttu-id="9a853-167">Si le nœud de compilation a plusieurs versions d’un module de ressource DSC basé sur une classe, `Import-DscResource -ModuleVersion` ne récupère pas la version spécifiée et génère l’erreur de compilation suivante.</span><span class="sxs-lookup"><span data-stu-id="9a853-167">If the compilation node has multiple version of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="9a853-168">**Résolution :** Importez la version requise en définissant l’objet *ModuleSpecification* sur `-ModuleName` avec la clé `RequiredVersion` spécifiée comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a853-168">**Resolution:** Import the required version by defining the *ModuleSpecification* object to the `-ModuleName` with `RequiredVersion` key specified as follows:</span></span>
``` PowerShell  
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}  
```  

<a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="9a853-169">Certaines ressources DSC comme une ressource du Registre peuvent commencer à prendre beaucoup de temps pour traiter la demande.</span><span class="sxs-lookup"><span data-stu-id="9a853-169">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>
--------------------------------------------------------------------------------------------------------------------------------

<span data-ttu-id="9a853-170">**Résolution 1 :** Créez une tâche planifiée qui nettoie le dossier suivant régulièrement.</span><span class="sxs-lookup"><span data-stu-id="9a853-170">**Resolution1:** Create a schedule task that cleans up the following folder periodically.</span></span>
``` PowerShell 
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis 
```

<span data-ttu-id="9a853-171">**Résolution 2 :** Modifiez la configuration DSC pour nettoyer le dossier *CommandAnalysis* à la fin de la configuration.</span><span class="sxs-lookup"><span data-stu-id="9a853-171">**Resolution2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>
``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config 
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```

