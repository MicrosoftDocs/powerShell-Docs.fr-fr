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
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811648"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="28971-102">Guide pratique pour mettre à jour les fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="28971-102">How to Update Help Files</span></span>

<span data-ttu-id="28971-103">Cette rubrique explique comment mettre à jour les fichiers d’aide d’un module qui prend en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="28971-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="28971-104">Mise à jour des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="28971-104">Updating Help Files</span></span>

<span data-ttu-id="28971-105">Il existe de nombreuses raisons de mettre à jour les fichiers d’aide, tels que la correction des erreurs, la clarification d’un concept, la réponse à une question fréquemment posée, l’ajout de nouveaux fichiers ou l’ajout de nouveaux et de meilleurs exemples.</span><span class="sxs-lookup"><span data-stu-id="28971-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="28971-106">Pour mettre à jour un fichier d’aide :</span><span class="sxs-lookup"><span data-stu-id="28971-106">To update a help file:</span></span>

1. <span data-ttu-id="28971-107">Modifiez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="28971-107">Change the files.</span></span>

2. <span data-ttu-id="28971-108">Traduisez les fichiers dans d’autres cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="28971-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="28971-109">Collecter tous les fichiers d’aide (nouveaux, modifiés et inchangés) pour le module dans chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="28971-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="28971-110">Validez les fichiers par rapport au schéma XML.</span><span class="sxs-lookup"><span data-stu-id="28971-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="28971-111">Régénérez les fichiers CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="28971-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="28971-112">Dans le fichier XML HelpInfo, incrémentez les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="28971-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="28971-113">Chargez les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de l’élément **HelpContentUri** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="28971-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="28971-114">Remplacez les anciens fichiers CAB par les nouveaux fichiers CAB.</span><span class="sxs-lookup"><span data-stu-id="28971-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="28971-115">Téléchargez le fichier XML HelpInfo mis à jour à l’emplacement spécifié par la clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="28971-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="28971-116">Remplacez l’ancien fichier XML HelpInfo par le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="28971-116">Replace the older HelpInfo XML file with the new file.</span></span>
