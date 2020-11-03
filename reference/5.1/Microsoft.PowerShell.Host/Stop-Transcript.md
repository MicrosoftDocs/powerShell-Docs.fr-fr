---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 22298a898bd45a9be5eaf98d4963b98ab1bf063b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200782"
---
# <span data-ttu-id="a1987-103">Stop-Transcript</span><span class="sxs-lookup"><span data-stu-id="a1987-103">Stop-Transcript</span></span>

## <span data-ttu-id="a1987-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a1987-104">SYNOPSIS</span></span>
<span data-ttu-id="a1987-105">Arrête une transcription.</span><span class="sxs-lookup"><span data-stu-id="a1987-105">Stops a transcript.</span></span>

## <span data-ttu-id="a1987-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1987-106">SYNTAX</span></span>

```
Stop-Transcript [<CommonParameters>]
```

## <span data-ttu-id="a1987-107">Description</span><span class="sxs-lookup"><span data-stu-id="a1987-107">DESCRIPTION</span></span>
<span data-ttu-id="a1987-108">L' `Stop-Transcript` applet de commande arrête une transcription qui a été démarrée par l’applet de commande `Start-Transcript` .</span><span class="sxs-lookup"><span data-stu-id="a1987-108">The `Stop-Transcript` cmdlet stops a transcript that was started by the `Start-Transcript` cmdlet.</span></span>
<span data-ttu-id="a1987-109">Vous pouvez également mettre fin à une session pour arrêter une transcription.</span><span class="sxs-lookup"><span data-stu-id="a1987-109">Alternatively, you can end a session to stop a transcript.</span></span>

## <span data-ttu-id="a1987-110">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a1987-110">EXAMPLES</span></span>

### <span data-ttu-id="a1987-111">Exemple 1 : arrêter toutes les transcriptions</span><span class="sxs-lookup"><span data-stu-id="a1987-111">Example 1: Stop all transcripts</span></span>

```powershell
Stop-Transcript
```

<span data-ttu-id="a1987-112">Cette commande arrête toutes les transcriptions.</span><span class="sxs-lookup"><span data-stu-id="a1987-112">This command stops all transcripts.</span></span>

## <span data-ttu-id="a1987-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a1987-113">PARAMETERS</span></span>

### <span data-ttu-id="a1987-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1987-114">CommonParameters</span></span>
<span data-ttu-id="a1987-115">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a1987-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a1987-116">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a1987-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a1987-117">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a1987-117">INPUTS</span></span>

### <span data-ttu-id="a1987-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="a1987-118">None</span></span>
<span data-ttu-id="a1987-119">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a1987-119">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a1987-120">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a1987-120">OUTPUTS</span></span>

### <span data-ttu-id="a1987-121">System.String</span><span class="sxs-lookup"><span data-stu-id="a1987-121">System.String</span></span>
<span data-ttu-id="a1987-122">Cette applet de commande retourne une chaîne qui contient un message d’État et le chemin d’accès au fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="a1987-122">This cmdlet returns a string that contains a status message and the path to the output file.</span></span>

## <span data-ttu-id="a1987-123">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a1987-123">NOTES</span></span>

* <span data-ttu-id="a1987-124">Si une transcription n'a pas été démarrée, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="a1987-124">If a transcript has not been started, the command fails.</span></span>

*

## <span data-ttu-id="a1987-125">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a1987-125">RELATED LINKS</span></span>

[<span data-ttu-id="a1987-126">Start-Transcript</span><span class="sxs-lookup"><span data-stu-id="a1987-126">Start-Transcript</span></span>](Start-Transcript.md)
