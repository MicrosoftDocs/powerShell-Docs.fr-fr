---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Notes de publication de WMF 5.1
ms.openlocfilehash: 61ca854cf8f26a9e96c6c5b5c06f6b54d08fb4ea
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795009"
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="24b93-103">Notes de publication de Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="24b93-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span>

<span data-ttu-id="24b93-104">WMF 5.1 comprend les composants PowerShell, WMI, WinRM et SIL (Journalisation de l’inventaire logiciel) qui ont été publiés avec Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="24b93-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="24b93-105">WMF 5.1 peut être installé sur Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 et 2012 R2, et fournit plusieurs améliorations par rapport à WMF 5.0 RTM, notamment :</span><span class="sxs-lookup"><span data-stu-id="24b93-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="24b93-106">Nouvelles applets de commande : groupes et utilisateurs locaux ; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="24b93-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="24b93-107">Améliorations de PowerShellGet avec l’utilisation imposée de modules signés et l’installation de modules JEA</span><span class="sxs-lookup"><span data-stu-id="24b93-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="24b93-108">Ajout de la prise en charge de PackageManagement pour les conteneurs, l’installation de CBS, l’installation basée sur des fichiers .exe et les packages CAB</span><span class="sxs-lookup"><span data-stu-id="24b93-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="24b93-109">Améliorations du débogage pour les classes DSC et PowerShell</span><span class="sxs-lookup"><span data-stu-id="24b93-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="24b93-110">Améliorations de la sécurité, notamment l’utilisation imposée de modules signés par le catalogue provenant du serveur collecteur et lors de l’utilisation des applets de commande PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="24b93-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="24b93-111">Réponses à plusieurs demandes et problèmes des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="24b93-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="24b93-112">**Remarques importantes :**</span><span class="sxs-lookup"><span data-stu-id="24b93-112">**Important notes:**</span></span>

- <span data-ttu-id="24b93-113">**WMF 5.1 nécessite le .NET Framework 4.5.2** (ou ultérieur).</span><span class="sxs-lookup"><span data-stu-id="24b93-113">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="24b93-114">L’installation réussit, mais des fonctionnalités clés échouent si le .NET Framework 4.5.2 (ou ultérieur) n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="24b93-114">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span> <span data-ttu-id="24b93-115">Des instructions sont disponibles dans la rubrique [Installer et configurer WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).</span><span class="sxs-lookup"><span data-stu-id="24b93-115">Instructions are available in the [Install and Configure WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="24b93-116">La préversion de WMF 5.1 doit être désinstallée avant d’installer la version WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="24b93-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="24b93-117">WMF 5.1 peut être installé directement sur WMF 5.0 ou WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="24b93-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="24b93-118">Il n’est __pas nécessaire__ d’installer WMF 4.0 avant d’installer WMF 5.1 sur Windows 7 et Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="24b93-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="24b93-119">C’était un problème lié à version 5.1 WMF qui a été résolu.</span><span class="sxs-lookup"><span data-stu-id="24b93-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>
