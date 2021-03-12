---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193911"
---
# <span data-ttu-id="c0040-102">Module PSReadLine</span><span class="sxs-lookup"><span data-stu-id="c0040-102">PSReadLine Module</span></span>

## <span data-ttu-id="c0040-103">Description</span><span class="sxs-lookup"><span data-stu-id="c0040-103">Description</span></span>

<span data-ttu-id="c0040-104">Le module PSReadLine contient des applets de commande qui vous permettent de personnaliser l’environnement d’édition de ligne de commande dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0040-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="c0040-105">Ces articles documentent la version bêta actuelle de PSReadLine v 2.2.0.</span><span class="sxs-lookup"><span data-stu-id="c0040-105">These articles document the current beta version of PSReadLine v2.2.0.</span></span>

> [!NOTE]
> <span data-ttu-id="c0040-106">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="c0040-106">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="c0040-107">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="c0040-107">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="c0040-108">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="c0040-108">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="c0040-109">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c0040-109">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="c0040-110">Applets de commande PSReadLine</span><span class="sxs-lookup"><span data-stu-id="c0040-110">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="c0040-111">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="c0040-111">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="c0040-112">Point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c0040-112">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="c0040-113">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c0040-113">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="c0040-114">Obtient les fonctions de clé liées pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c0040-114">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="c0040-115">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c0040-115">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="c0040-116">Obtient des valeurs pour les options qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="c0040-116">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="c0040-117">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="c0040-117">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="c0040-118">Cette fonction est le point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c0040-118">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="c0040-119">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c0040-119">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="c0040-120">Supprime une combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="c0040-120">Removes a key binding.</span></span>

### [<span data-ttu-id="c0040-121">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c0040-121">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="c0040-122">Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c0040-122">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="c0040-123">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c0040-123">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="c0040-124">Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c0040-124">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

