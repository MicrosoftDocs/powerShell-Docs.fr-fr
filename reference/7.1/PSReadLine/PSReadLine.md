---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: a404461e2b92f269d581b18c3ebe7643aa86c3a4
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "93206482"
---
# <span data-ttu-id="97ba5-103">Module PSReadLine</span><span class="sxs-lookup"><span data-stu-id="97ba5-103">PSReadLine Module</span></span>

## <span data-ttu-id="97ba5-104">Description</span><span class="sxs-lookup"><span data-stu-id="97ba5-104">Description</span></span>

<span data-ttu-id="97ba5-105">Le module PSReadLine contient des applets de commande qui vous permettent de personnaliser l’environnement d’édition de ligne de commande dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97ba5-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="97ba5-106">Ces articles documentent PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="97ba5-106">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="97ba5-107">Cette version est fournie dans PowerShell V6 et la mise à jour 2018 de Windows 10 octobre (Build 1809).</span><span class="sxs-lookup"><span data-stu-id="97ba5-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="97ba5-108">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="97ba5-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="97ba5-109">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="97ba5-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="97ba5-110">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="97ba5-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="97ba5-111">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="97ba5-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="97ba5-112">Applets de commande PSReadLine</span><span class="sxs-lookup"><span data-stu-id="97ba5-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="97ba5-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="97ba5-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="97ba5-114">Point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="97ba5-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="97ba5-115">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="97ba5-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="97ba5-116">Obtient les fonctions de clé liées pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="97ba5-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="97ba5-117">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="97ba5-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="97ba5-118">Obtient des valeurs pour les options qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="97ba5-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="97ba5-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="97ba5-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="97ba5-120">Cette fonction est le point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="97ba5-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="97ba5-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="97ba5-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="97ba5-122">Supprime une combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="97ba5-122">Removes a key binding.</span></span>

### [<span data-ttu-id="97ba5-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="97ba5-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="97ba5-124">Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="97ba5-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="97ba5-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="97ba5-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="97ba5-126">Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine** .</span><span class="sxs-lookup"><span data-stu-id="97ba5-126">Customizes the behavior of command line editing in **PSReadLine** .</span></span>

