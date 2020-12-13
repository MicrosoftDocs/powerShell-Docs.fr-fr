---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour tester l’aide actualisable
description: Guide pratique pour tester l’aide actualisable
ms.openlocfilehash: 47873089bfa1b918ea9970915e829a22aa7254c5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667621"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="20908-103">Guide pratique pour tester l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="20908-103">How to Test Updatable Help</span></span>

<span data-ttu-id="20908-104">Cette rubrique décrit les approches de test de l’aide actualisable pour un module.</span><span class="sxs-lookup"><span data-stu-id="20908-104">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="20908-105">Utilisation de verbose pour détecter les erreurs</span><span class="sxs-lookup"><span data-stu-id="20908-105">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="20908-106">Après avoir chargé le fichier XML HelpInfo et les fichiers CAB de votre module, testez les fichiers en exécutant une commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) avec le paramètre **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="20908-106">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="20908-107">Le paramètre **Verbose** indique `Update-Help` à de signaler les étapes critiques dans ses actions, de la lecture de la clé **HelpInfoUri** dans le manifeste de module à la validation des types de fichiers dans le fichier CAB décompressé et de la mise en place des fichiers dans le répertoire de module spécifique à la langue.</span><span class="sxs-lookup"><span data-stu-id="20908-107">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="20908-108">Lorsque tous les messages détaillés sont résolus, exécutez une `Update-Help` commande avec le paramètre **Debug** .</span><span class="sxs-lookup"><span data-stu-id="20908-108">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="20908-109">Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide pouvant être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="20908-109">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
