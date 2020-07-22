---
title: Guide pratique pour tester l’aide actualisable
ms.date: 09/12/2016
ms.openlocfilehash: 0602349f853fddd0cadae545eaf0302c150e3a28
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892963"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="29e45-102">Guide pratique pour tester l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="29e45-102">How to Test Updatable Help</span></span>

<span data-ttu-id="29e45-103">Cette rubrique décrit les approches de test de l’aide actualisable pour un module.</span><span class="sxs-lookup"><span data-stu-id="29e45-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="29e45-104">Utilisation de verbose pour détecter les erreurs</span><span class="sxs-lookup"><span data-stu-id="29e45-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="29e45-105">Après avoir chargé le fichier XML HelpInfo et les fichiers CAB de votre module, testez les fichiers en exécutant une commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) avec le paramètre **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="29e45-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="29e45-106">Le paramètre **Verbose** indique `Update-Help` à de signaler les étapes critiques dans ses actions, de la lecture de la clé **HelpInfoUri** dans le manifeste de module à la validation des types de fichiers dans le fichier CAB décompressé et de la mise en place des fichiers dans le répertoire de module spécifique à la langue.</span><span class="sxs-lookup"><span data-stu-id="29e45-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="29e45-107">Lorsque tous les messages détaillés sont résolus, exécutez une `Update-Help` commande avec le paramètre **Debug** .</span><span class="sxs-lookup"><span data-stu-id="29e45-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span>
<span data-ttu-id="29e45-108">Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide pouvant être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="29e45-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
