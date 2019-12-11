---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Exiger l’acceptation de la licence pour les scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328080"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Exiger l’acceptation de la licence pour les scripts

L’acceptation de licence n’est pas prise en charge pour les scripts. Cependant, le scénario où un script dépend d’un module qui exige l’acceptation de la licence est pris en charge.

Les commandes de scripts (Install-Script/Save-Script/Update-Script) prennent en charge un nouveau paramètre -AcceptLicense qui se comporte comme si l’utilisateur avait vu la licence. Si AcceptLicense n’est pas spécifié, l’utilisateur verra license.txt pour le module dépendant et sera invité à accepter la licence.

## <a name="examples"></a>EXEMPLES

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemple 1 : installation d’un script avec des dépendances exigeant une acceptation de licence

Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'. L’utilisateur est invité à accepter la licence.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemple 2 : installation d’un script avec des dépendances exigeant une acceptation de licence et AcceptLicense

Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'. L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Plus d’informations

- [Nécessitent la prise en charge de l’acceptation de licence pour les modules](module-license-acceptance.md)
- [Nécessitent la prise en charge de l’acceptation de licence sur PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Exiger l’acceptation de la licence lors du déploiement sur Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
