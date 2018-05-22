---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: af16ce7c5d97731581aa3393a70aba672244c9d8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="remove-dsc-documents"></a><span data-ttu-id="90469-102">Supprimer des documents DSC</span><span class="sxs-lookup"><span data-stu-id="90469-102">Remove DSC documents</span></span>

<span data-ttu-id="90469-103">Quand un document de configuration est remis à DSC, il passe par différentes phases (en attente, en cours, précédent).</span><span class="sxs-lookup"><span data-stu-id="90469-103">When a configuration document is delivered to DSC, the document goes through various stages (pending, current, previous).</span></span> <span data-ttu-id="90469-104">Nous avons ajouté une nouvelle applet de commande à DSC dans Windows PowerShell 4.0, `Remove-DscConfigurationDocument`, dans le cadre du [correctif cumulatif de novembre 2014 pour Windows RT 8.1, Windows 8.1 et Windows Server 2012 R2](https://support.microsoft.com/kb/3000850).</span><span class="sxs-lookup"><span data-stu-id="90469-104">We added a new cmdlet to DSC in Windows PowerShell 4.0, `Remove-DscConfigurationDocument`, as part of [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850).</span></span>
