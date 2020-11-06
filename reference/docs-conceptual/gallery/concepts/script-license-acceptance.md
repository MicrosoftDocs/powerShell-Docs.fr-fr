---
ms.date: 06/09/2017
title: Exiger l’acceptation de la licence pour les scripts
description: L’article explique comment utiliser les scripts publiés dans PowerShell Gallery, qui requièrent l’acceptation d’une licence utilisateur final.
ms.openlocfilehash: d82974810fd1e73ef8d9e5771fc430d0f7964e87
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656083"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Exiger l’acceptation de la licence pour les scripts

L’acceptation de licence n’est pas prise en charge pour les scripts. Cependant, le scénario où un script dépend d’un module qui exige l’acceptation de la licence est pris en charge.

Les commandes de script PowerShellGet prennent en charge le paramètre **AcceptLicense** qui se comporte comme si l’utilisateur avait vu la licence. Si **AcceptLicense** n’est pas spécifié, l’utilisateur voit le fichier `license.txt` pour le module dépendant et est à accepter la licence.

## <a name="examples"></a>EXEMPLES

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exemple 1 : installation d’un script avec des dépendances exigeant une acceptation de licence

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exemple 2 : installation d’un script avec des dépendances exigeant une acceptation de licence et AcceptLicense

Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'. L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Détails supplémentaires

- [Nécessitent la prise en charge de l’acceptation de licence pour les modules](module-license-acceptance.md)
- [Exiger la prise en charge de l’acceptation de licence sur PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Exiger l’acceptation de la licence lors du déploiement sur Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
