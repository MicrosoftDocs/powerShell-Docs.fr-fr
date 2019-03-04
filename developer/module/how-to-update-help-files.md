---
title: Comment mettre à jour les fichiers d’aide | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855525"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="d5501-102">Guide pratique pour mettre à jour les fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="d5501-102">How to Update Help Files</span></span>

<span data-ttu-id="d5501-103">Cette rubrique explique comment mettre à jour les fichiers d’aide pour un module qui prend en charge de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="d5501-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="d5501-104">La mise à jour des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="d5501-104">Updating Help Files</span></span>

<span data-ttu-id="d5501-105">Il existe de nombreuses raisons pour mettre à jour les fichiers d’aide, telles que la correction des erreurs, clarifier un concept, répondre à une question fréquemment posées, ajout de nouveaux fichiers ou ajout d’exemples de nouvelles et meilleures.</span><span class="sxs-lookup"><span data-stu-id="d5501-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="d5501-106">Pour mettre à jour un fichier d’aide :</span><span class="sxs-lookup"><span data-stu-id="d5501-106">To update a help file:</span></span>

1. <span data-ttu-id="d5501-107">Modifier les fichiers.</span><span class="sxs-lookup"><span data-stu-id="d5501-107">Change the files.</span></span>

2. <span data-ttu-id="d5501-108">Traduire les fichiers dans les autres cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5501-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="d5501-109">Collecter tous les fichiers d’aide (nouvelles, modifiées et inchangées) pour le module dans chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5501-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="d5501-110">Validez les fichiers par rapport au schéma XML.</span><span class="sxs-lookup"><span data-stu-id="d5501-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="d5501-111">Reconstruire les fichiers CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5501-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="d5501-112">Dans le fichier XML HelpInfo, incrémenter les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d5501-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="d5501-113">Télécharger les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de la **HelpContentUri** élément dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="d5501-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="d5501-114">Remplacez les anciens fichiers CAB avec les nouveaux fichiers CAB.</span><span class="sxs-lookup"><span data-stu-id="d5501-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="d5501-115">Télécharger le fichier XML HelpInfo mis à jour à l’emplacement spécifié par le **HelpInfoUri** clés dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="d5501-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="d5501-116">Remplacez l’ancien fichier XML HelpInfo avec le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="d5501-116">Replace the older HelpInfo XML file with the new file.</span></span>