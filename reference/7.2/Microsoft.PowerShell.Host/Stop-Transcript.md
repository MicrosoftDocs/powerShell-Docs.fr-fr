---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597333"
---
# <span data-ttu-id="700f8-102">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="700f8-102">Stop-Transcript</span></span>

## <span data-ttu-id="700f8-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="700f8-103">SYNOPSIS</span></span>
<span data-ttu-id="700f8-104">Arrête une transcription.</span><span class="sxs-lookup"><span data-stu-id="700f8-104">Stops a transcript.</span></span>

## <span data-ttu-id="700f8-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="700f8-105">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="700f8-106">Description</span><span class="sxs-lookup"><span data-stu-id="700f8-106">DESCRIPTION</span></span>

<span data-ttu-id="700f8-107">L' `Stop-Transcript` applet de commande arrête une transcription qui a été démarrée par l’applet de commande `Start-Transcript` .</span><span class="sxs-lookup"><span data-stu-id="700f8-107">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="700f8-108">Vous pouvez également mettre fin à une session pour arrêter une transcription.</span><span class="sxs-lookup"><span data-stu-id="700f8-108">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="700f8-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="700f8-109">EXAMPLES</span></span>

### <span data-ttu-id="700f8-110">Exemple 1 : arrêter toutes les transcriptions</span><span class="sxs-lookup"><span data-stu-id="700f8-110">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="700f8-111">Cette commande arrête toutes les transcriptions.</span><span class="sxs-lookup"><span data-stu-id="700f8-111">This command stops all transcripts.</span></span>

## <span data-ttu-id="700f8-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="700f8-112">PARAMETERS</span></span>

### <span data-ttu-id="700f8-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="700f8-113">CommonParameters</span></span>

<span data-ttu-id="700f8-114">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="700f8-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="700f8-115">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="700f8-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="700f8-116">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="700f8-116">INPUTS</span></span>

### <span data-ttu-id="700f8-117">None</span><span class="sxs-lookup"><span data-stu-id="700f8-117">None</span></span>

<span data-ttu-id="700f8-118">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="700f8-118">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="700f8-119">SORTIES</span><span class="sxs-lookup"><span data-stu-id="700f8-119">OUTPUTS</span></span>

### <span data-ttu-id="700f8-120">System.String</span><span class="sxs-lookup"><span data-stu-id="700f8-120">System.String</span></span>

<span data-ttu-id="700f8-121">Cette applet de commande retourne une chaîne qui contient un message d’État et le chemin d’accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="700f8-121">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="700f8-122">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="700f8-122">NOTES</span></span>

* <span data-ttu-id="700f8-123">Si une transcription n'a pas été démarrée, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="700f8-123">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="700f8-124">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="700f8-124">RELATED LINKS</span></span>

[<span data-ttu-id="700f8-125">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="700f8-125">Start-Transcript</span></span>](Start-Transcript.md)

