---
title: Comment tester l’aide actualisable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367148"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="e7971-102">Guide pratique pour tester l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="e7971-102">How to Test Updatable Help</span></span>

<span data-ttu-id="e7971-103">Cette rubrique décrit les approches de test de l’aide actualisable pour un module.</span><span class="sxs-lookup"><span data-stu-id="e7971-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="e7971-104">Utilisation de verbose pour détecter les erreurs</span><span class="sxs-lookup"><span data-stu-id="e7971-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="e7971-105">Après avoir chargé le fichier XML HelpInfo et les fichiers CAB de votre module, testez les fichiers en exécutant une commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) avec le paramètre **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="e7971-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="e7971-106">Le paramètre **Verbose** indique à `Update-Help` de signaler les étapes critiques dans ses actions, de la lecture de la clé **HelpInfoUri** dans le manifeste de module à la validation des types de fichiers dans le fichier CAB décompressé et de la mise en place des fichiers dans la langue spécifique au langage Répertoire du module.</span><span class="sxs-lookup"><span data-stu-id="e7971-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="e7971-107">Une fois tous les messages détaillés résolus, exécutez une commande `Update-Help` avec le paramètre **Debug** .</span><span class="sxs-lookup"><span data-stu-id="e7971-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="e7971-108">Ce paramètre doit détecter les problèmes restants avec les fichiers d’aide pouvant être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="e7971-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>