---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Modules exigeant l’acceptation de la licence
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048286"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="ff7fb-103">Modules exigeant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff7fb-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="ff7fb-104">SYNOPSIS</span></span>

<span data-ttu-id="ff7fb-105">Les services juridiques de certains éditeurs de modules exigent que les clients acceptent explicitement la licence avant d’installer leur module à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="ff7fb-106">Si un utilisateur installe, met à jour ou enregistre un module à l’aide de PowerShellGet, directement ou en dépendance avec un autre élément, et que ce module oblige l’utilisateur à accepter une licence, l’utilisateur doit indiquer qu’il accepte la licence, faute de quoi l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="ff7fb-107">Publier la configuration requise pour les modules</span><span class="sxs-lookup"><span data-stu-id="ff7fb-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="ff7fb-108">Les modules demandant aux utilisateurs d’accepter une licence doivent répondre aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff7fb-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="ff7fb-109">La section PSData du manifeste de module doit inclure RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="ff7fb-110">Le module doit contenir le fichier license.txt dans le répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="ff7fb-111">Le manifeste de module doit contenir l’Uri de la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="ff7fb-112">Le module doit être publié avec PowerShellGet Format, version 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="ff7fb-113">Impact sur Install/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="ff7fb-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="ff7fb-114">Les applets de commande Install/Save/Update prendront en charge un nouveau paramètre (AcceptLicense), qui se comportera comme si l’utilisateur avait vu la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="ff7fb-115">Si RequiredLicenseAcceptance est défini sur True qu’AcceptLicense n’est pas spécifié, l’utilisateur verra le fichier license.txt et sera invité à répondre à la question suivante : &quot;Acceptez-vous les termes du contrat de licence ? (Oui/Non/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="ff7fb-116">Si la licence est acceptée</span><span class="sxs-lookup"><span data-stu-id="ff7fb-116">If the license is accepted</span></span>
    - <span data-ttu-id="ff7fb-117">**Save-Module :** le module sera copié sur le système utilisateur&#39;s</span><span class="sxs-lookup"><span data-stu-id="ff7fb-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="ff7fb-118">**Install-Module :** le module sera copié dans le bon dossier du système utilisateur&#39; (basé sur l’étendue)</span><span class="sxs-lookup"><span data-stu-id="ff7fb-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="ff7fb-119">**Update-Module :** le module sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="ff7fb-120">Si la licence a été refusée.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-120">If the license is declined.</span></span>
    - <span data-ttu-id="ff7fb-121">L’opération sera annulée.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="ff7fb-122">Vérifie toutes les applets de commande pour les métadonnées (requireLicenseAcceptance et version du Format) qui indiquent que l’acceptation d’une licence est nécessaire</span><span class="sxs-lookup"><span data-stu-id="ff7fb-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="ff7fb-123">Si la version de format est antérieure à 2.0, l’opération échouera et l’utilisateur sera invité à mettre à jour le client.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="ff7fb-124">Si le module a été publié avec une version de format antérieure à 2.0, l’indicateur LicenseAcceptance sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="ff7fb-125">Dépendances du module</span><span class="sxs-lookup"><span data-stu-id="ff7fb-125">Module Dependencies</span></span>
- <span data-ttu-id="ff7fb-126">Pendant l’opération d’installation/d’enregistrement/de mise à jour, si un module dépendant (quelque chose d’autre dépend du module) nécessite une acceptation de licence, le comportement d’acceptation de licence (ci-dessus) sera requis.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="ff7fb-127">Si la version du module est déjà répertoriée dans le catalogue local comme étant installée sur le système, nous contournerons la vérification de la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="ff7fb-128">Au cours de l’opération d’installation/d’enregistrement/de mise à jour, si un module dépendant requiert une licence et que l’acceptation de la licence n’a pas lieu, l’opération échouera et suivra le processus normal d’échec de l’installation/l’enregistrement/la mise à jour de l’élément.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="ff7fb-129">Impact sur Force</span><span class="sxs-lookup"><span data-stu-id="ff7fb-129">Impact on -Force</span></span>

<span data-ttu-id="ff7fb-130">La spécification de Force n’est pas suffisante pour accepter une licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="ff7fb-131">AcceptLicense est requis pour autoriser l’installation.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="ff7fb-132">Si Force est spécifié, RequiredLicenseAcceptance défini sur True et qu’AcceptLicense n’est PAS spécifié, l’opération échouera.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="ff7fb-133">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="ff7fb-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="ff7fb-134">Exemple 1 : mise à jour du manifeste de module pour exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="ff7fb-135">Cette commande met à jour le fichier de manifeste et définit l’indicateur RequireLicenseAcceptance sur true.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="ff7fb-136">Exemple 2 : installation d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-136">Example 2: Install Module requiring license acceptance</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):

```

<span data-ttu-id="ff7fb-137">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="ff7fb-138">Exemple 3 : installation d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ff7fb-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="ff7fb-139">Le module est installé sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="ff7fb-140">Exemple 4 : installation d’un module nécessitant l’acceptation de la licence avec -Force</span><span class="sxs-lookup"><span data-stu-id="ff7fb-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="ff7fb-141">Exemple 5 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="ff7fb-142">Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ff7fb-143">L’utilisateur est invité à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-143">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Module -Name ModuleWithDependency

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="ff7fb-144">Exemple 6 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence et AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ff7fb-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="ff7fb-145">Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="ff7fb-146">L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="ff7fb-147">Exemple 7 : installation d’un module nécessitant l’acceptation de la licence sur un client antérieure à PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="ff7fb-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="ff7fb-148">Exemple 8 : enregistrement d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-148">Example 8: Save Module requiring license acceptance</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="ff7fb-149">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="ff7fb-150">Exemple 9 : enregistrement d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ff7fb-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="ff7fb-151">Le module est enregistré sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="ff7fb-152">Exemple 10 : mise à jour d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="ff7fb-152">Example 10: Update Module requiring license acceptance</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="ff7fb-153">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="ff7fb-154">Exemple 11 : mise à jour d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ff7fb-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="ff7fb-155">Le module est mis à jour sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="ff7fb-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="ff7fb-156">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="ff7fb-156">More details</span></span>

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[<span data-ttu-id="ff7fb-157">Exiger l’acceptation de la licence pour les scripts</span><span class="sxs-lookup"><span data-stu-id="ff7fb-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[<span data-ttu-id="ff7fb-158">Exiger la prise en charge de l’acceptation de licence sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="ff7fb-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[<span data-ttu-id="ff7fb-159">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="ff7fb-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)