---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99595481"
---
# <span data-ttu-id="24ab5-102">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="24ab5-102">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="24ab5-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="24ab5-103">SYNOPSIS</span></span>
<span data-ttu-id="24ab5-104">Cette fonction est le point d’entrée principal pour PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="24ab5-104">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="24ab5-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="24ab5-105">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="24ab5-106">Description</span><span class="sxs-lookup"><span data-stu-id="24ab5-106">DESCRIPTION</span></span>

<span data-ttu-id="24ab5-107">`PSConsoleHostReadLine` est le point d’entrée principal pour le module PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="24ab5-107">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="24ab5-108">L’hôte de la console PowerShell charge automatiquement le module PSReadLine et appelle cette fonction.</span><span class="sxs-lookup"><span data-stu-id="24ab5-108">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="24ab5-109">Dans des conditions de fonctionnement normales, cette fonction n’est pas destinée à être utilisée à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="24ab5-109">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="24ab5-110">Le point `PSConsoleHostReadLine` d’extension est spécial pour l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="24ab5-110">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="24ab5-111">L’hôte appelle un alias, une fonction ou un script portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="24ab5-111">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="24ab5-112">PSReadLine définit cette fonction de manière à ce qu’elle soit appelée à partir de l’hôte de la console.</span><span class="sxs-lookup"><span data-stu-id="24ab5-112">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="24ab5-113">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="24ab5-113">EXAMPLES</span></span>

### <span data-ttu-id="24ab5-114">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="24ab5-114">Example 1</span></span>

<span data-ttu-id="24ab5-115">Cette fonction n’est pas destinée à être utilisée à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="24ab5-115">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="24ab5-116">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="24ab5-116">PARAMETERS</span></span>

## <span data-ttu-id="24ab5-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="24ab5-117">INPUTS</span></span>

### <span data-ttu-id="24ab5-118">None</span><span class="sxs-lookup"><span data-stu-id="24ab5-118">None</span></span>

## <span data-ttu-id="24ab5-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="24ab5-119">OUTPUTS</span></span>

### <span data-ttu-id="24ab5-120">None</span><span class="sxs-lookup"><span data-stu-id="24ab5-120">None</span></span>

## <span data-ttu-id="24ab5-121">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="24ab5-121">NOTES</span></span>

## <span data-ttu-id="24ab5-122">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="24ab5-122">RELATED LINKS</span></span>

[<span data-ttu-id="24ab5-123">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="24ab5-123">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

