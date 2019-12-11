---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Modules exigeant l’acceptation de la licence
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328520"
---
# <a name="modules-requiring-license-acceptance"></a>Modules exigeant l’acceptation de la licence

## <a name="synopsis"></a>SYNOPSIS

Les services juridiques de certains éditeurs de modules exigent que les clients acceptent explicitement la licence avant d’installer leur module à partir de PowerShell Gallery. Si un utilisateur installe, met à jour ou enregistre un module avec PowerShellGet, directement ou dans une relation de dépendance avec un autre package, et que ce module exige que l’utilisateur accepte une licence, l’utilisateur doit indiquer qu’il accepte la licence, faute de quoi l’opération échoue.

## <a name="publish-requirements-for-modules"></a>Publier la configuration requise pour les modules

Les modules demandant aux utilisateurs d’accepter une licence doivent répondre aux conditions suivantes :

- La section PSData du manifeste de module doit inclure RequireLicenseAcceptance = $True.
- Le module doit contenir le fichier license.txt dans le répertoire racine.
- Le manifeste de module doit contenir l’Uri de la licence.
- Le module doit être publié avec PowerShellGet Format, version 2.0 et versions ultérieures.

## <a name="impact-on-installsaveupdate-module"></a>Impact sur Install/Save/Update-Module

- Les applets de commande Install/Save/Update prendront en charge un nouveau paramètre (AcceptLicense), qui se comportera comme si l’utilisateur avait vu la licence.
- Si RequiredLicenseAcceptance est défini sur True qu’AcceptLicense n’est pas spécifié, l’utilisateur verra le fichier license.txt et sera invité à répondre à la question suivante : &quot;Acceptez-vous les termes du contrat de licence ? (Oui/Non/YesToAll/NoToAll)&quot;.
  - Si la licence est acceptée
    - **Save-Module :** le module sera copié sur le système utilisateur&#39;s
    - **Install-Module :** le module sera copié dans le bon dossier du système utilisateur&#39; (basé sur l’étendue)
    - **Update-Module :** le module sera mis à jour.
  - Si la licence a été refusée.
    - L’opération sera annulée.
    - Vérifie toutes les applets de commande pour les métadonnées (requireLicenseAcceptance et version du Format) qui indiquent que l’acceptation d’une licence est nécessaire
    - Si la version de format est antérieure à 2.0, l’opération échouera et l’utilisateur sera invité à mettre à jour le client.
    - Si le module a été publié avec une version de format antérieure à 2.0, l’indicateur LicenseAcceptance sera ignoré.

## <a name="module-dependencies"></a>Dépendances du module

- Pendant l’opération d’installation/d’enregistrement/de mise à jour, si un module dépendant (quelque chose d’autre dépend du module) nécessite une acceptation de licence, le comportement d’acceptation de licence (ci-dessus) sera requis.
- Si la version du module est déjà répertoriée dans le catalogue local comme étant installée sur le système, nous contournerons la vérification de la licence.
- Si, au cours de l’opération d’installation/d’enregistrement/de mise à jour, un module dépendant exige une licence et que l’acceptation de cette licence n’a pas lieu, l’opération échoue et suit les processus normaux d’échec de l’installation/l’enregistrement/la mise à jour du package.

## <a name="impact-on--force"></a>Impact sur Force

La spécification de `–Force` n’est PAS suffisante pour accepter une licence. `–AcceptLicense` est obligatoire pour autoriser l’installation. Si `–Force` est spécifié, que RequiredLicenseAcceptance a la valeur True et qu’`–AcceptLicense` n’est PAS spécifié, l’opération échouera.

## <a name="examples"></a>EXEMPLES

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exemple 1 : mise à jour du manifeste de module pour exiger l’acceptation de la licence

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Cette commande met à jour le fichier de manifeste et définit l’indicateur RequireLicenseAcceptance sur true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Exemple 2 : installation d’un module nécessitant l’acceptation de la licence

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

Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exemple 3 : installation d’un module nécessitant l’acceptation de la licence avec AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Le module est installé sans invitation à accepter la licence.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exemple 4 : installation d’un module nécessitant l’acceptation de la licence avec -Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exemple 5 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence

Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'. L’utilisateur est invité à accepter la licence.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemple 6 : installation d’un module avec des dépendances nécessitant l’acceptation de la licence et AcceptLicense

Le module 'ModuleWithDependency' dépend du module 'ModuleRequireLicenseAcceptance'. L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exemple 7 : installation d’un module nécessitant l’acceptation de la licence sur un client antérieure à PSGetFormatVersion 2.0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Exemple 8 : enregistrement d’un module nécessitant l’acceptation de la licence

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

Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exemple 9 : enregistrement d’un module nécessitant l’acceptation de la licence avec AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Le module est enregistré sans invitation à accepter la licence.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exemple 10 : mise à jour d’un module nécessitant l’acceptation de la licence

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

Cette commande affiche la licence du fichier license.txt et invite l’utilisateur à l’accepter.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exemple 11 : mise à jour d’un module nécessitant l’acceptation de la licence avec AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Le module est mis à jour sans invitation à accepter la licence.

## <a name="more-details"></a>Plus d’informations

[Exiger l’acceptation de la licence pour les scripts](./script-license-acceptance.md)

[Exiger la prise en charge de l’acceptation de licence sur PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Exiger l’acceptation de la licence lors du déploiement sur Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
