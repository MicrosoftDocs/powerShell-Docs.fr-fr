---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Liste de vérification de création de ressources
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401563"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="a9aab-103">Liste de vérification de création de ressources</span><span class="sxs-lookup"><span data-stu-id="a9aab-103">Resource authoring checklist</span></span>

<span data-ttu-id="a9aab-104">Cette liste de vérification est une liste de bonnes pratiques lors de la création d’une ressource DSC.</span><span class="sxs-lookup"><span data-stu-id="a9aab-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="a9aab-105">Le module de ressources contient le fichier .psd1 et schema.mof pour chaque ressource</span><span class="sxs-lookup"><span data-stu-id="a9aab-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="a9aab-106">Vérifiez que votre ressource a une structure correcte et qu’elle contient tous les fichiers nécessaires.</span><span class="sxs-lookup"><span data-stu-id="a9aab-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="a9aab-107">Chaque module de ressources doit contenir un fichier .psd1 et toutes les ressources non composites doivent avoir un fichier schema.mof.</span><span class="sxs-lookup"><span data-stu-id="a9aab-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="a9aab-108">Les ressources qui ne contiennent pas de schéma ne seront pas répertoriées par `Get-DscResource` et les utilisateurs ne pourront pas utiliser Intellisense lors de l’écriture de code impliquant ces modules dans ISE.</span><span class="sxs-lookup"><span data-stu-id="a9aab-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="a9aab-109">La structure de répertoires de la ressource xRemoteFile, qui fait partie du [module de ressources xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9aab-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="a9aab-110">La ressource et le schéma sont corrects</span><span class="sxs-lookup"><span data-stu-id="a9aab-110">Resource and schema are correct</span></span>

<span data-ttu-id="a9aab-111">Vérifiez le fichier de schéma de ressource (\*.schema.mof).</span><span class="sxs-lookup"><span data-stu-id="a9aab-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="a9aab-112">Vous pouvez utiliser le [Concepteur de ressources DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) pour développer et tester votre schéma.</span><span class="sxs-lookup"><span data-stu-id="a9aab-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="a9aab-113">Vérifiez que :</span><span class="sxs-lookup"><span data-stu-id="a9aab-113">Make sure that:</span></span>

- <span data-ttu-id="a9aab-114">Les types de propriétés sont corrects (par exemple, n’utilisez pas String pour les propriétés qui acceptent des valeurs numériques ; utilisez plutôt UInt32 ou d’autres types numériques).</span><span class="sxs-lookup"><span data-stu-id="a9aab-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="a9aab-115">Les attributs de propriétés sont spécifiés correctement en tant que ([key], [required], [write], [read])</span><span class="sxs-lookup"><span data-stu-id="a9aab-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="a9aab-116">Au moins un paramètre dans le schéma doit être marqué comme [key].</span><span class="sxs-lookup"><span data-stu-id="a9aab-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="a9aab-117">La propriété [read] ne coexiste pas avec [required], [key] ni [write]</span><span class="sxs-lookup"><span data-stu-id="a9aab-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="a9aab-118">Si plusieurs qualificateurs sont spécifiés, à l’exception de [read], [key] est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="a9aab-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="a9aab-119">Si [write] et [required] sont spécifiés, [required] est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="a9aab-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="a9aab-120">ValueMap est spécifié, le cas échéant. Exemple :</span><span class="sxs-lookup"><span data-stu-id="a9aab-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="a9aab-121">Le nom convivial est spécifié et conforme aux conventions d’affectation de noms DSC.</span><span class="sxs-lookup"><span data-stu-id="a9aab-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="a9aab-122">Exemple : `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="a9aab-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="a9aab-123">Chaque champ a une description explicite.</span><span class="sxs-lookup"><span data-stu-id="a9aab-123">Every field has meaningful description.</span></span> <span data-ttu-id="a9aab-124">Le dépôt GitHub de PowerShell présente des exemples intéressants, tel que [le fichier .schema.mof pour xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="a9aab-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="a9aab-125">Vous devez aussi utiliser les applets de commande **Test-xDscResource** et **Test-xDscSchema** à partir du [Concepteur de ressources DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) pour vérifier automatiquement la ressource et le schéma :</span><span class="sxs-lookup"><span data-stu-id="a9aab-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="a9aab-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a9aab-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="a9aab-127">La ressource se charge sans erreur</span><span class="sxs-lookup"><span data-stu-id="a9aab-127">Resource loads without errors</span></span>

<span data-ttu-id="a9aab-128">Vérifiez si le module de ressources peut être chargé.</span><span class="sxs-lookup"><span data-stu-id="a9aab-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="a9aab-129">Vous pouvez le faire soit manuellement, en exécutant `Import-Module <resource_module> -force` et en vérifiant qu’aucune erreur ne s’est produite, soit en écrivant une automatisation de test.</span><span class="sxs-lookup"><span data-stu-id="a9aab-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="a9aab-130">Dans le deuxième cas, vous pouvez suivre cette structure dans votre cas de test :</span><span class="sxs-lookup"><span data-stu-id="a9aab-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="a9aab-131">La ressource est idempotent dans le cas positif</span><span class="sxs-lookup"><span data-stu-id="a9aab-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="a9aab-132">Une des caractéristiques fondamentales des ressources de DSC est l’idempotence.</span><span class="sxs-lookup"><span data-stu-id="a9aab-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="a9aab-133">Cela signifie que l’application d’une configuration DSC contenant cette ressource plusieurs fois aboutit toujours au même résultat.</span><span class="sxs-lookup"><span data-stu-id="a9aab-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="a9aab-134">Par exemple, si nous créons une configuration qui contient la ressource de fichier suivante :</span><span class="sxs-lookup"><span data-stu-id="a9aab-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="a9aab-135">Après une première application, le fichier test.txt doit apparaître dans le dossier `C:\test`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="a9aab-136">Toutefois, les exécutions suivantes de la même configuration ne doivent pas changer l’état de l’ordinateur (par exemple, aucune copie du fichier `test.txt` ne doit être créée).</span><span class="sxs-lookup"><span data-stu-id="a9aab-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="a9aab-137">Pour vérifier qu’une ressource est idempotente, vous pouvez appeler `Set-TargetResource` à plusieurs reprises lors de tests directs de la ressource, ou appeler `Start-DscConfiguration` à plusieurs reprises lors de tests de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="a9aab-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="a9aab-138">Le résultat doit être le même après chaque exécution.</span><span class="sxs-lookup"><span data-stu-id="a9aab-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="a9aab-139">Scénario de modification par l’utilisateur de test</span><span class="sxs-lookup"><span data-stu-id="a9aab-139">Test user modification scenario</span></span>

<span data-ttu-id="a9aab-140">En changeant l’état de l’ordinateur, puis en réexécutant DSC, vous pouvez vérifier que `Set-TargetResource` et `Test-TargetResource` fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="a9aab-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="a9aab-141">Voici les étapes à suivre :</span><span class="sxs-lookup"><span data-stu-id="a9aab-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="a9aab-142">Commencez avec la ressource qui n’est pas à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a9aab-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="a9aab-143">Exécutez la configuration avec votre ressource.</span><span class="sxs-lookup"><span data-stu-id="a9aab-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="a9aab-144">Vérifiez que `Test-DscConfiguration` retourne la valeur True.</span><span class="sxs-lookup"><span data-stu-id="a9aab-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="a9aab-145">Modifiez l’élément configuré pour qu’il ne soit plus dans l’état souhaité</span><span class="sxs-lookup"><span data-stu-id="a9aab-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="a9aab-146">Vérifiez que `Test-DscConfiguration` retourne la valeur False.</span><span class="sxs-lookup"><span data-stu-id="a9aab-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="a9aab-147">Voici un exemple plus concret à l’aide de la ressource de Registre :</span><span class="sxs-lookup"><span data-stu-id="a9aab-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="a9aab-148">Commencez avec la clé de Registre qui n’est pas à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a9aab-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="a9aab-149">Exécutez `Start-DscConfiguration` avec une configuration pour la faire basculer à l’état souhaité et vérifiez que l’opération réussit.</span><span class="sxs-lookup"><span data-stu-id="a9aab-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="a9aab-150">Exécutez `Test-DscConfiguration` et vérifiez qu’elle retourne la valeur True.</span><span class="sxs-lookup"><span data-stu-id="a9aab-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="a9aab-151">Modifiez la valeur de la clé pour qu’elle ne soit pas à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a9aab-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="a9aab-152">Exécutez `Test-DscConfiguration` et vérifiez qu’elle retourne la valeur False.</span><span class="sxs-lookup"><span data-stu-id="a9aab-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="a9aab-153">La fonctionnalité `Get-TargetResource` a été vérifiée à l’aide de `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="a9aab-154">`Get-TargetResource` doit retourner des détails sur l’état actuel de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a9aab-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="a9aab-155">Testez-la en appelant `Get-DscConfiguration` après avoir appliqué la configuration et en vérifiant que la sortie reflète fidèlement l’état actuel de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a9aab-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="a9aab-156">Il est important de la tester séparément, car les problèmes dans cette zone ne s’affichent pas lors de l’appel de `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="a9aab-157">Appelez les fonctions **Get/Set/Test-TargetResource** directement</span><span class="sxs-lookup"><span data-stu-id="a9aab-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="a9aab-158">Testez les fonctions **Get/Set/Test-TargetResource** implémentées dans votre ressource en les appelant directement et en vérifiant qu’elles fonctionnent comme prévu.</span><span class="sxs-lookup"><span data-stu-id="a9aab-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="a9aab-159">Effectuez une vérification de bout en bout à l’aide de **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="a9aab-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="a9aab-160">Le test des fonctions **Get/Set/Test-TargetResource** en les appelant directement est important, mais les problèmes ne sont pas tous découverts de cette façon.</span><span class="sxs-lookup"><span data-stu-id="a9aab-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="a9aab-161">Vous devez axer une partie importante de vos tests sur l’utilisation de `Start-DscConfiguration` ou du serveur collecteur.</span><span class="sxs-lookup"><span data-stu-id="a9aab-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="a9aab-162">En fait, c’est de cette manière que les utilisateurs se serviront de la ressource. Ne sous-estimez donc pas l’importance de ce type de test.</span><span class="sxs-lookup"><span data-stu-id="a9aab-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="a9aab-163">Types de problèmes possibles :</span><span class="sxs-lookup"><span data-stu-id="a9aab-163">Possible types of issues:</span></span>

- <span data-ttu-id="a9aab-164">Les informations d’identification ou la session peuvent se comporter différemment, car l’agent DSC s’exécute en tant que service.</span><span class="sxs-lookup"><span data-stu-id="a9aab-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="a9aab-165">Veillez à tester ici toutes les fonctionnalités de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="a9aab-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="a9aab-166">Les erreurs générées par `Start-DscConfiguration` peuvent être différentes de celles affichées quand vous appelez directement la fonction `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="a9aab-167">Compatibilité des tests sur toutes les plateformes prises en charge DSC</span><span class="sxs-lookup"><span data-stu-id="a9aab-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="a9aab-168">La ressource doit fonctionner sur toutes les plateformes prises en charge par DSC (Windows Server 2008 R2 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="a9aab-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="a9aab-169">Installez la dernière version de WMF (Windows Management Framework) sur votre système d’exploitation pour obtenir la dernière version de DSC.</span><span class="sxs-lookup"><span data-stu-id="a9aab-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="a9aab-170">Si la ressource ne fonctionne pas sur certaines de ces plateformes de par sa conception, un message d’erreur spécifique doit être retourné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="a9aab-171">Veillez aussi à ce que votre ressource vérifie si les applets de commande que vous appelez sont présentes sur un ordinateur particulier.</span><span class="sxs-lookup"><span data-stu-id="a9aab-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="a9aab-172">Windows Server 2012 a ajouté un grand nombre de nouvelles applets de commande qui ne sont pas disponibles sur Windows Server 2008 R2, même avec WMF installé.</span><span class="sxs-lookup"><span data-stu-id="a9aab-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="a9aab-173">Effectuez une vérification sur le client Windows (le cas échéant)</span><span class="sxs-lookup"><span data-stu-id="a9aab-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="a9aab-174">L’une des erreurs courantes lors des tests consiste à vérifier la ressource uniquement sur les versions de Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a9aab-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="a9aab-175">De nombreuses ressources sont également conçues pour fonctionner sur des références (SKU) clientes. Si cela vous concerne, n’oubliez pas de les tester également sur ces plateformes.</span><span class="sxs-lookup"><span data-stu-id="a9aab-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="a9aab-176">Get-DSCResource répertorie la ressource</span><span class="sxs-lookup"><span data-stu-id="a9aab-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="a9aab-177">Après le déploiement du module, un appel à `Get-DscResource` doit répertorier votre ressource parmi les autres.</span><span class="sxs-lookup"><span data-stu-id="a9aab-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="a9aab-178">Si votre ressource ne figure pas dans la liste, vérifiez que le fichier schema.mof correspondant à cette ressource existe.</span><span class="sxs-lookup"><span data-stu-id="a9aab-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="a9aab-179">Le module de ressource contient des exemples</span><span class="sxs-lookup"><span data-stu-id="a9aab-179">Resource module contains examples</span></span>

<span data-ttu-id="a9aab-180">La création d’exemples de qualité aidera les autres à comprendre comment l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a9aab-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="a9aab-181">C’est crucial, surtout quand on sait que de nombreux utilisateurs traitent les exemples de code comme de la documentation.</span><span class="sxs-lookup"><span data-stu-id="a9aab-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="a9aab-182">Tout d’abord, vous devez déterminer les exemples qui seront inclus dans le module : au minimum, vous devez couvrir les cas d’usage les plus importants pour votre ressource :</span><span class="sxs-lookup"><span data-stu-id="a9aab-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="a9aab-183">Si votre module contient plusieurs ressources qui doivent fonctionner ensemble pour un scénario de bout en bout, l’exemple de bout en bout de base doit, dans l’idéal, être le premier.</span><span class="sxs-lookup"><span data-stu-id="a9aab-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="a9aab-184">Les exemples initiaux doivent être très simples : prise en main de vos ressources en petits segments gérables (par exemple création d’un disque dur virtuel).</span><span class="sxs-lookup"><span data-stu-id="a9aab-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="a9aab-185">Les exemples suivants doivent reposer sur ces exemples (création d’une machine virtuelle à partir d’un disque dur virtuel, suppression de machine virtuelle, modification de machines virtuelles, etc.) et illustrer les fonctionnalités avancées (comme la création d’une machine virtuelle avec mémoire dynamique).</span><span class="sxs-lookup"><span data-stu-id="a9aab-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="a9aab-186">Les exemples de configuration doivent être paramétrés (toutes les valeurs doivent être passées à la configuration comme paramètres et il ne doit y avoir aucune valeur codée en dur) :</span><span class="sxs-lookup"><span data-stu-id="a9aab-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="a9aab-187">Il est recommandé d’inclure un exemple (en commentaire) illustrant comment appeler la configuration avec les valeurs réelles à la fin de l’exemple de script.</span><span class="sxs-lookup"><span data-stu-id="a9aab-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="a9aab-188">Par exemple, dans la configuration ci-dessus, il n’est pas évident pour tout le monde que le meilleur moyen de spécifier UserAgent est :</span><span class="sxs-lookup"><span data-stu-id="a9aab-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="a9aab-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Dans ce cas, un commentaire peut clarifier l’exécution prévue de la configuration :</span><span class="sxs-lookup"><span data-stu-id="a9aab-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="a9aab-190">Pour chaque exemple, rédigez une brève description qui explique ce qu’il fait et la signification des paramètres.</span><span class="sxs-lookup"><span data-stu-id="a9aab-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="a9aab-191">Vérifiez que les exemples couvrent la plupart des principaux scénarios pour votre ressource et, si aucun élément ne manque, vérifiez qu’ils s’exécutent tous et qu’ils placent l’ordinateur à l’état souhaité.</span><span class="sxs-lookup"><span data-stu-id="a9aab-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="a9aab-192">Les messages d’erreur sont faciles à comprendre et aident les utilisateurs à résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="a9aab-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="a9aab-193">Pour être efficaces, les messages d’erreur doivent être :</span><span class="sxs-lookup"><span data-stu-id="a9aab-193">Good error messages should be:</span></span>

- <span data-ttu-id="a9aab-194">Présents : Le plus gros problème avec les messages d’erreur est qu’ils n’existent pas souvent, assurez-vous qu’ils s’y.</span><span class="sxs-lookup"><span data-stu-id="a9aab-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="a9aab-195">Facile à comprendre : Codes d’erreur humaine de lisible, n’obscurs</span><span class="sxs-lookup"><span data-stu-id="a9aab-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="a9aab-196">Précise Décrire ce qu’est exactement le problème</span><span class="sxs-lookup"><span data-stu-id="a9aab-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="a9aab-197">Constructifs : Conseils pour résoudre le problème</span><span class="sxs-lookup"><span data-stu-id="a9aab-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="a9aab-198">Poli : Ne pas rendre responsable utilisateur ou rendre vous inquiétez pas</span><span class="sxs-lookup"><span data-stu-id="a9aab-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="a9aab-199">Vérifiez les erreurs dans les scénarios de bout en bout (à l’aide de `Start-DscConfiguration`), car elles peuvent différer de celles retournées lors de l’exécution directe des fonctions de ressources.</span><span class="sxs-lookup"><span data-stu-id="a9aab-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="a9aab-200">Les messages de journaux sont faciles à comprendre et informatifs (notamment les journaux –verbose, –debug et ETW)</span><span class="sxs-lookup"><span data-stu-id="a9aab-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="a9aab-201">Vérifiez que les journaux générés par la ressource sont faciles à comprendre et sont utiles à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9aab-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="a9aab-202">Les ressources doivent générer toutes les informations qui peuvent être utiles à l’utilisateur, mais il n’est pas toujours préférable de fournir davantage de journaux.</span><span class="sxs-lookup"><span data-stu-id="a9aab-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="a9aab-203">Vous devez éviter de créer des redondances et des données qui n’apportent rien de plus. Ne forcez pas un utilisateur à parcourir des centaines d’entrées de journaux pour trouver ce qu’il cherche.</span><span class="sxs-lookup"><span data-stu-id="a9aab-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="a9aab-204">Bien entendu, ne proposer aucun journal n’est pas non plus une solution acceptable pour ce problème.</span><span class="sxs-lookup"><span data-stu-id="a9aab-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="a9aab-205">Pendant les tests, vous devez aussi analyser les journaux détaillés et les journaux de débogage (en exécutant `Start-DscConfiguration` avec les commutateurs `–Verbose` et `–Debug` le cas échéant), ainsi que les journaux ETW.</span><span class="sxs-lookup"><span data-stu-id="a9aab-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="a9aab-206">Pour afficher les journaux ETW de DSC, accédez à l’Observateur d’événements et ouvrez le dossier suivant : Applications et Services Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="a9aab-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="a9aab-207">Par défaut le canal Opérationnel est activé, mais veillez à activer également les canaux Analyse et Débogage avant d’exécuter la configuration.</span><span class="sxs-lookup"><span data-stu-id="a9aab-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="a9aab-208">Pour activer les canaux Analyse/Débogage, vous pouvez exécuter le script ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a9aab-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="a9aab-209">L’implémentation de la ressource ne contient pas de chemins codés en dur</span><span class="sxs-lookup"><span data-stu-id="a9aab-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="a9aab-210">Vérifiez qu’il n’y a aucun chemin codé en dur dans l’implémentation de la ressource, en particulier s’ils définissent la langue (en-us) par supposition, ou quand des variables système peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="a9aab-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="a9aab-211">Si votre ressource a besoin d’accéder à des chemins spécifiques, utilisez des variables d’environnement au lieu de coder en dur le chemin, car il peut différer sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="a9aab-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="a9aab-212">Exemple :</span><span class="sxs-lookup"><span data-stu-id="a9aab-212">Example:</span></span>

<span data-ttu-id="a9aab-213">Au lieu de :</span><span class="sxs-lookup"><span data-stu-id="a9aab-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="a9aab-214">Vous pouvez écrire :</span><span class="sxs-lookup"><span data-stu-id="a9aab-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="a9aab-215">L’implémentation de ressource ne contient pas d’informations sur l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="a9aab-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="a9aab-216">Vérifiez que le code ne contient aucune adresse de messagerie, information de compte ou nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a9aab-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="a9aab-217">La ressource a été testée avec des informations d’identification valides ou non valides</span><span class="sxs-lookup"><span data-stu-id="a9aab-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="a9aab-218">Si votre ressource prend des informations d’identification en tant que paramètre :</span><span class="sxs-lookup"><span data-stu-id="a9aab-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="a9aab-219">Vérifiez que la ressource fonctionne quand Système local (ou le compte d’ordinateur pour les ressources distantes) n’a pas accès.</span><span class="sxs-lookup"><span data-stu-id="a9aab-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="a9aab-220">Vérifiez que la ressource fonctionne avec des informations d’identification spécifiées pour Get, Set et Test</span><span class="sxs-lookup"><span data-stu-id="a9aab-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="a9aab-221">Si votre ressource accède à des partages, testez toutes les variantes que vous devez prendre en charge, par exemple :</span><span class="sxs-lookup"><span data-stu-id="a9aab-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="a9aab-222">Partages Windows standard.</span><span class="sxs-lookup"><span data-stu-id="a9aab-222">Standard windows shares.</span></span>
  - <span data-ttu-id="a9aab-223">Partages DFS.</span><span class="sxs-lookup"><span data-stu-id="a9aab-223">DFS shares.</span></span>
  - <span data-ttu-id="a9aab-224">Partages SAMBA (si vous souhaitez prendre en charge Linux.)</span><span class="sxs-lookup"><span data-stu-id="a9aab-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="a9aab-225">La ressource ne nécessite pas d’entrée interactive</span><span class="sxs-lookup"><span data-stu-id="a9aab-225">Resource does not require interactive input</span></span>

<span data-ttu-id="a9aab-226">Les fonctions **Get/Set/Test-TargetResource** doivent être exécutées automatiquement et ne doivent attendre une entrée utilisateur à aucun moment de l’exécution (par exemple, vous ne devez pas utiliser `Get-Credential` à l’intérieur de ces fonctions).</span><span class="sxs-lookup"><span data-stu-id="a9aab-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="a9aab-227">Si vous avez besoin de fournir une entrée utilisateur, vous devez la passer à la configuration en tant que paramètre pendant la phase de compilation.</span><span class="sxs-lookup"><span data-stu-id="a9aab-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="a9aab-228">La fonctionnalité de la ressource a été testée de manière approfondie</span><span class="sxs-lookup"><span data-stu-id="a9aab-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="a9aab-229">Cette liste de vérification contient des éléments qu’il est important de tester et/ou qui sont souvent oubliés.</span><span class="sxs-lookup"><span data-stu-id="a9aab-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="a9aab-230">Il y aura plusieurs séries de tests, principalement des tests fonctionnels propres à la ressource que vous testez et qui ne sont pas mentionnés ici.</span><span class="sxs-lookup"><span data-stu-id="a9aab-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="a9aab-231">N’oubliez pas les cas de tests négatifs.</span><span class="sxs-lookup"><span data-stu-id="a9aab-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="a9aab-232">Bonne pratique Module de ressources contient un dossier Tests avec un script ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="a9aab-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="a9aab-233">Il est conseillé de créer un dossier « Tests » à l’intérieur du module de ressources, de créer un fichier `ResourceDesignerTests.ps1` et d’ajouter des tests à l’aide de **Test-xDscResource** et **Test-xDscSchema** pour toutes les ressources d’un module donné.</span><span class="sxs-lookup"><span data-stu-id="a9aab-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="a9aab-234">De cette façon, vous pouvez valider rapidement les schémas de toutes les ressources des modules donnés et effectuer des tests d’intégrité avant la publication.</span><span class="sxs-lookup"><span data-stu-id="a9aab-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="a9aab-235">Pour xRemoteFile, `ResourceTests.ps1` pourrait être aussi simple que ceci :</span><span class="sxs-lookup"><span data-stu-id="a9aab-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="a9aab-236">Bonne pratique Dossier de ressources contient le script de Concepteur de ressources pour générer le schéma</span><span class="sxs-lookup"><span data-stu-id="a9aab-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="a9aab-237">Chaque ressource doit contenir un script de concepteur de ressources qui génère un schéma mof de la ressource.</span><span class="sxs-lookup"><span data-stu-id="a9aab-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="a9aab-238">Ce fichier doit être placé dans `<ResourceName>\ResourceDesignerScripts` et nommé Generate`<ResourceName>Schema.ps1`. Pour la ressource xRemoteFile, ce fichier se nommerait `GenerateXRemoteFileSchema.ps1` et contiendrait :</span><span class="sxs-lookup"><span data-stu-id="a9aab-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="a9aab-239">Bonne pratique Ressource prend en charge - WhatIf</span><span class="sxs-lookup"><span data-stu-id="a9aab-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="a9aab-240">Si votre ressource effectue des opérations « dangereuses », nous vous recommandons d’implémenter une fonctionnalité `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="a9aab-241">Une fois ceci effectué, vérifiez que la sortie `-WhatIf` décrit correctement les opérations qui auraient lieu si la commande était exécutée sans commutateur `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="a9aab-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="a9aab-242">Vérifiez également que les opérations ne s’exécutent pas (l’état du nœud n’est pas modifié) quand le commutateur `–WhatIf` est présent.</span><span class="sxs-lookup"><span data-stu-id="a9aab-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="a9aab-243">Par exemple, supposons que nous testons la ressource File.</span><span class="sxs-lookup"><span data-stu-id="a9aab-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="a9aab-244">Voici une configuration simple qui crée un fichier `test.txt` avec le contenu « test » :</span><span class="sxs-lookup"><span data-stu-id="a9aab-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="a9aab-245">Si nous compilons et exécutons la configuration avec le commutateur `-WhatIf`, la sortie nous indique exactement ce qui se passera si nous exécutons la configuration.</span><span class="sxs-lookup"><span data-stu-id="a9aab-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="a9aab-246">Toutefois, la configuration proprement dite n’a pas été exécutée (le fichier `test.txt` n’a pas été créé).</span><span class="sxs-lookup"><span data-stu-id="a9aab-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="a9aab-247">Cette liste n’est pas exhaustive, mais elle traite de nombreux problèmes importants qui peuvent se poser lors de la conception, du développement et des tests des ressources DSC.</span><span class="sxs-lookup"><span data-stu-id="a9aab-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
