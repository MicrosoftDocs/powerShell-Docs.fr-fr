---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Exiger l’acceptation de la licence pour les scripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048232"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="1e9a4-103">Exiger l’acceptation de la licence pour les scripts</span><span class="sxs-lookup"><span data-stu-id="1e9a4-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="1e9a4-104">L’acceptation de licence n’est pas prise en charge pour les scripts.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="1e9a4-105">Cependant, le scénario où un script dépend d’un module qui exige l’acceptation de la licence est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="1e9a4-106">Les commandes de scripts (Install-Script/Save-Script/Update-Script) prennent en charge un nouveau paramètre -AcceptLicense qui se comporte comme si l’utilisateur avait vu la licence.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="1e9a4-107">Si AcceptLicense n’est pas spécifié, l’utilisateur verra license.txt pour le module dépendant et sera invité à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="1e9a4-108">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1e9a4-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="1e9a4-109">Exemple 1 : installation d’un script avec des dépendances exigeant une acceptation de licence</span><span class="sxs-lookup"><span data-stu-id="1e9a4-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="1e9a4-110">Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1e9a4-111">L’utilisateur est invité à accepter la licence.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="1e9a4-112">Exemple 2 : installation d’un script avec des dépendances exigeant une acceptation de licence et AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1e9a4-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="1e9a4-113">Le script 'ScriptRequireLicenseAcceptance' dépend du module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1e9a4-114">L’utilisateur n’est pas invité à accepter la licence, puisqu’AcceptLicense est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1e9a4-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="1e9a4-115">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="1e9a4-115">More details</span></span>

- [<span data-ttu-id="1e9a4-116">Nécessitent la prise en charge de l’acceptation de licence pour les modules</span><span class="sxs-lookup"><span data-stu-id="1e9a4-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="1e9a4-117">Nécessitent la prise en charge de l’acceptation de licence sur PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="1e9a4-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="1e9a4-118">Exiger l’acceptation de la licence lors du déploiement sur Azure Automation</span><span class="sxs-lookup"><span data-stu-id="1e9a4-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)