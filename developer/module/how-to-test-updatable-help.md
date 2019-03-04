---
title: Le Test d’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854735"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="1326a-102">Guide pratique pour tester l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="1326a-102">How to Test Updatable Help</span></span>

<span data-ttu-id="1326a-103">Cette rubrique décrit les approches de test de l’aide actualisable pour un module.</span><span class="sxs-lookup"><span data-stu-id="1326a-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="1326a-104">À l’aide détaillée pour détecter les erreurs</span><span class="sxs-lookup"><span data-stu-id="1326a-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="1326a-105">Après avoir téléchargé le fichier XML HelpInfo et les fichiers CAB pour votre module, les fichiers de test en exécutant un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) commande avec le **Verbose** paramètre.</span><span class="sxs-lookup"><span data-stu-id="1326a-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="1326a-106">Le **Verbose** paramètre dirige `Update-Help` pour signaler les étapes critiques dans ses actions, de lire le **HelpInfoUri** clés dans le manifeste de module pour valider les types de fichiers dans le fichier CAB décompressé et placer les fichiers dans le répertoire de module spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="1326a-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>
<span data-ttu-id="1326a-107">Après avoir téléchargé le fichier XML HelpInfo et les fichiers CAB pour votre module, les fichiers de test en exécutant un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) commande avec le **Verbose** paramètre.</span><span class="sxs-lookup"><span data-stu-id="1326a-107">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="1326a-108">Le **Verbose** paramètre dirige `Update-Help` pour signaler les étapes critiques dans ses actions, de lire le **HelpInfoUri** clés dans le manifeste de module pour valider les types de fichiers dans le fichier CAB décompressé et placer les fichiers dans le répertoire de module spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="1326a-108">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="1326a-109">Quand tous les messages documentés sont résolues, exécutez une `Update-Help` commande avec le **déboguer** paramètre.</span><span class="sxs-lookup"><span data-stu-id="1326a-109">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="1326a-110">Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="1326a-110">This parameter should detect any remaining problems with the Updatable Help files.</span></span>