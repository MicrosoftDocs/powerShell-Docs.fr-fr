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
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="50799-103">Exiger l’acceptation de la licence pour les scripts</span><span class="sxs-lookup"><span data-stu-id="50799-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="50799-104">L’acceptation de licence n’est pas prise en charge pour les scripts.</span><span class="sxs-lookup"><span data-stu-id="50799-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="50799-105">Cependant, le scénario où un script dépend d’un module qui exige l’acceptation de la licence est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="50799-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="50799-106">Les commandes de script PowerShellGet prennent en charge le paramètre **AcceptLicense** qui se comporte comme si l’utilisateur avait vu la licence.</span><span class="sxs-lookup"><span data-stu-id="50799-106">The PowerShellGet script commands support the parameter **AcceptLicense** that behaves as though user saw the license.</span></span> <span data-ttu-id="50799-107">Si **AcceptLicense** n’est pas spécifié, l’utilisateur voit le fichier `license.txt` pour le module dépendant et est à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="50799-107">If **AcceptLicense** is not specified the user is shown the `license.txt` file for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="50799-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="50799-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="50799-109">Exemple 1 : installation d’un script avec des dépendances exigeant une acceptation de licence</span><span class="sxs-lookup"><span data-stu-id="50799-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="50799-110">Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="50799-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="50799-111">L’utilisateur est invité à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="50799-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="50799-112">Exemple 2 : installation d’un script avec des dépendances exigeant une acceptation de licence et AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="50799-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="50799-113">Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="50799-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="50799-114">L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.</span><span class="sxs-lookup"><span data-stu-id="50799-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="50799-115">Détails supplémentaires</span><span class="sxs-lookup"><span data-stu-id="50799-115">More details</span></span>

- [<span data-ttu-id="50799-116">Nécessitent la prise en charge de l’acceptation de licence pour les modules</span><span class="sxs-lookup"><span data-stu-id="50799-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="50799-117">Exiger la prise en charge de l’acceptation de licence sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="50799-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="50799-118">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="50799-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
