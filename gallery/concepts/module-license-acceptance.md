---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Modules exigeant l’acceptation de la licence
ms.openlocfilehash: 93f92f6e83bcf18a40c3d89eb39a154e16ca5063
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893108"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="6edff-103">Modules exigeant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="6edff-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="6edff-104">SYNOPSIS</span></span>

<span data-ttu-id="6edff-105">Les services juridiques de certains éditeurs de modules exigent que les clients acceptent explicitement la licence avant d’installer leur module à partir de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6edff-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="6edff-106">Si un utilisateur installe, met à jour ou enregistre un module à l’aide de PowerShellGet, directement ou en dépendance avec un autre élément, et que ce module oblige l’utilisateur à accepter une licence, l’utilisateur doit indiquer qu’il accepte la licence, faute de quoi l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="6edff-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="6edff-107">Publier la configuration requise pour les modules</span><span class="sxs-lookup"><span data-stu-id="6edff-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="6edff-108">Les modules demandant aux utilisateurs d’accepter une licence doivent répondre aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="6edff-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="6edff-109">La section PSData du manifeste de module doit inclure RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="6edff-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="6edff-110">Le module doit contenir le fichier license.txt dans le répertoire racine.</span><span class="sxs-lookup"><span data-stu-id="6edff-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="6edff-111">Le manifeste de module doit contenir l’Uri de la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="6edff-112">Le module doit être publié avec PowerShellGet Format, version 2.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6edff-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="6edff-113">Impact sur Install/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="6edff-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="6edff-114">Les applets de commande Install/Save/Update prendront en charge un nouveau paramètre (AcceptLicense), qui se comportera comme si l’utilisateur avait vu la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="6edff-115">Si RequiredLicenseAcceptance est défini sur True qu’AcceptLicense n’est pas spécifié, l’utilisateur verra le fichier license.txt et sera invité à répondre à la question suivante : &quot;Acceptez-vous les termes du contrat de licence ? (Oui/Non/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="6edff-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="6edff-116">Si la licence est acceptée</span><span class="sxs-lookup"><span data-stu-id="6edff-116">If the license is accepted</span></span>
    - <span data-ttu-id="6edff-117">**Save-Module :** le module sera copié sur le système utilisateur&#39;s</span><span class="sxs-lookup"><span data-stu-id="6edff-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="6edff-118">**Install-Module :** le module sera copié dans le bon dossier du système utilisateur&#39; (basé sur l’étendue)</span><span class="sxs-lookup"><span data-stu-id="6edff-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="6edff-119">**Update-Module :** le module sera mis à jour.</span><span class="sxs-lookup"><span data-stu-id="6edff-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="6edff-120">Si la licence a été refusée.</span><span class="sxs-lookup"><span data-stu-id="6edff-120">If the license is declined.</span></span>
    - <span data-ttu-id="6edff-121">L’opération sera annulée.</span><span class="sxs-lookup"><span data-stu-id="6edff-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="6edff-122">Vérifie toutes les applets de commande pour les métadonnées (requireLicenseAcceptance et version du Format) qui indiquent que l’acceptation d’une licence est nécessaire</span><span class="sxs-lookup"><span data-stu-id="6edff-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="6edff-123">Si la version de format est antérieure à 2.0, l’opération échouera et l’utilisateur sera invité à mettre à jour le client.</span><span class="sxs-lookup"><span data-stu-id="6edff-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="6edff-124">Si le module a été publié avec une version de format antérieure à 2.0, l’indicateur LicenseAcceptance sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="6edff-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="6edff-125">Dépendances du module</span><span class="sxs-lookup"><span data-stu-id="6edff-125">Module Dependencies</span></span>

- <span data-ttu-id="6edff-126">Pendant l’opération d’installation/d’enregistrement/de mise à jour, si un module dépendant (quelque chose d’autre dépend du module) nécessite une acceptation de licence, le comportement d’acceptation de licence (ci-dessus) sera requis.</span><span class="sxs-lookup"><span data-stu-id="6edff-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="6edff-127">Si la version du module est déjà répertoriée dans le catalogue local comme étant installée sur le système, nous contournerons la vérification de la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="6edff-128">Au cours de l’opération d’installation/d’enregistrement/de mise à jour, si un module dépendant requiert une licence et que l’acceptation de la licence n’a pas lieu, l’opération échouera et suivra le processus normal d’échec de l’installation/l’enregistrement/la mise à jour de l’élément.</span><span class="sxs-lookup"><span data-stu-id="6edff-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="6edff-129">Impact sur Force</span><span class="sxs-lookup"><span data-stu-id="6edff-129">Impact on -Force</span></span>

<span data-ttu-id="6edff-130">La spécification de `–Force` n’est PAS suffisante pour accepter une licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="6edff-131">`–AcceptLicense` est obligatoire pour autoriser l’installation.</span><span class="sxs-lookup"><span data-stu-id="6edff-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="6edff-132">Si `–Force` est spécifié, que RequiredLicenseAcceptance a la valeur True et qu’`–AcceptLicense` n’est PAS spécifié, l’opération échouera.</span><span class="sxs-lookup"><span data-stu-id="6edff-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="6edff-133">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="6edff-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="6edff-134">Exemple 1 : mise à jour du manifeste de module pour exiger l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="6edff-135">Cette commande met à jour le fichier de manifeste et définit l’indicateur RequireLicenseAcceptance sur true.</span><span class="sxs-lookup"><span data-stu-id="6edff-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="6edff-136">Exemple 2 : installation d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="6edff-137">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="6edff-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6edff-138">Exemple 3 : installation d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6edff-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="6edff-139">Le module est installé sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="6edff-140">Exemple 4 : installation d’un module nécessitant l’acceptation de la licence avec -Force</span><span class="sxs-lookup"><span data-stu-id="6edff-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="6edff-141">Exemple 5 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="6edff-142">Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="6edff-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="6edff-143">L’utilisateur est invité à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="6edff-144">Exemple 6 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence et AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6edff-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="6edff-145">Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="6edff-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="6edff-146">L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.</span><span class="sxs-lookup"><span data-stu-id="6edff-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="6edff-147">Exemple 7 : installation d’un module nécessitant l’acceptation de la licence sur un client antérieure à PSGetFormatVersion 2.0</span><span class="sxs-lookup"><span data-stu-id="6edff-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="6edff-148">Exemple 8 : enregistrement d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

<span data-ttu-id="6edff-149">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="6edff-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6edff-150">Exemple 9 : enregistrement d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6edff-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="6edff-151">Le module est enregistré sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="6edff-152">Exemple 10 : mise à jour d’un module nécessitant l’acceptation de la licence</span><span class="sxs-lookup"><span data-stu-id="6edff-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="6edff-153">Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.</span><span class="sxs-lookup"><span data-stu-id="6edff-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="6edff-154">Exemple 11 : mise à jour d’un module nécessitant l’acceptation de la licence avec AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="6edff-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="6edff-155">Le module est mis à jour sans invitation à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="6edff-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="6edff-156">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="6edff-156">More details</span></span>

[<span data-ttu-id="6edff-157">Exiger l’acceptation de la licence pour les scripts</span><span class="sxs-lookup"><span data-stu-id="6edff-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="6edff-158">Exiger la prise en charge de l’acceptation de licence sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="6edff-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)

[<span data-ttu-id="6edff-159">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="6edff-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)