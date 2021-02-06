---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598353"
---
# <span data-ttu-id="cec8a-102">Module PSReadLine</span><span class="sxs-lookup"><span data-stu-id="cec8a-102">PSReadLine Module</span></span>

## <span data-ttu-id="cec8a-103">Description</span><span class="sxs-lookup"><span data-stu-id="cec8a-103">Description</span></span>

<span data-ttu-id="cec8a-104">Le module PSReadLine contient des applets de commande qui vous permettent de personnaliser l’environnement d’édition de ligne de commande dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cec8a-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="cec8a-105">Ces articles documentent PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="cec8a-105">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="cec8a-106">Cette version est fournie dans PowerShell V6 et la mise à jour 2018 de Windows 10 octobre (Build 1809).</span><span class="sxs-lookup"><span data-stu-id="cec8a-106">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="cec8a-107">À compter de PowerShell 7,0, PowerShell ignore le chargement automatique de PSReadLine sur Windows si un programme de lecture d’écran est détecté.</span><span class="sxs-lookup"><span data-stu-id="cec8a-107">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="cec8a-108">Actuellement, PSReadLine ne fonctionne pas correctement avec les lecteurs d’écran.</span><span class="sxs-lookup"><span data-stu-id="cec8a-108">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="cec8a-109">Le rendu et la mise en forme par défaut de PowerShell 7,0 sur Windows fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="cec8a-109">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="cec8a-110">Vous pouvez charger le module manuellement, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="cec8a-110">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="cec8a-111">Applets de commande PSReadLine</span><span class="sxs-lookup"><span data-stu-id="cec8a-111">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="cec8a-112">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="cec8a-112">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="cec8a-113">Point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="cec8a-113">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="cec8a-114">PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cec8a-114">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="cec8a-115">Obtient les fonctions de clé liées pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="cec8a-115">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="cec8a-116">PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="cec8a-116">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="cec8a-117">Obtient des valeurs pour les options qui peuvent être configurées.</span><span class="sxs-lookup"><span data-stu-id="cec8a-117">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="cec8a-118">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="cec8a-118">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="cec8a-119">Cette fonction est le point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="cec8a-119">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="cec8a-120">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cec8a-120">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="cec8a-121">Supprime une combinaison de touches.</span><span class="sxs-lookup"><span data-stu-id="cec8a-121">Removes a key binding.</span></span>

### [<span data-ttu-id="cec8a-122">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="cec8a-122">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="cec8a-123">Lie des clés à des fonctions de gestionnaire de clés définies par l’utilisateur ou PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="cec8a-123">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="cec8a-124">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="cec8a-124">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="cec8a-125">Personnalise le comportement de la modification de la ligne de commande dans **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="cec8a-125">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

