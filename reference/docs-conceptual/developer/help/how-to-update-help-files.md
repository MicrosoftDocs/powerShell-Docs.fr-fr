---
ms.date: 09/12/2016
ms.topic: reference
title: Guide pratique pour mettre à jour les fichiers d’aide
description: Guide pratique pour mettre à jour les fichiers d’aide
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649594"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="3883d-103">Guide pratique pour mettre à jour les fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="3883d-103">How to Update Help Files</span></span>

<span data-ttu-id="3883d-104">Cette rubrique explique comment mettre à jour les fichiers d’aide d’un module qui prend en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="3883d-104">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="3883d-105">Mise à jour des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="3883d-105">Updating Help Files</span></span>

<span data-ttu-id="3883d-106">Il existe de nombreuses raisons de mettre à jour les fichiers d’aide, tels que la correction des erreurs, la clarification d’un concept, la réponse à une question fréquemment posée, l’ajout de nouveaux fichiers ou l’ajout de nouveaux et de meilleurs exemples.</span><span class="sxs-lookup"><span data-stu-id="3883d-106">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="3883d-107">Pour mettre à jour un fichier d’aide :</span><span class="sxs-lookup"><span data-stu-id="3883d-107">To update a help file:</span></span>

1. <span data-ttu-id="3883d-108">Modifiez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="3883d-108">Change the files.</span></span>
1. <span data-ttu-id="3883d-109">Traduisez les fichiers dans d’autres cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3883d-109">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="3883d-110">Collecter tous les fichiers d’aide (nouveaux, modifiés et inchangés) pour le module dans chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3883d-110">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="3883d-111">Validez les fichiers par rapport au schéma XML.</span><span class="sxs-lookup"><span data-stu-id="3883d-111">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="3883d-112">Régénérez les fichiers CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3883d-112">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="3883d-113">Dans le fichier XML HelpInfo, incrémentez les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3883d-113">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="3883d-114">Chargez les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de l’élément **HelpContentUri** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="3883d-114">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="3883d-115">Remplacez les anciens fichiers CAB par les nouveaux fichiers CAB.</span><span class="sxs-lookup"><span data-stu-id="3883d-115">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="3883d-116">Téléchargez le fichier XML HelpInfo mis à jour à l’emplacement spécifié par la clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="3883d-116">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="3883d-117">Remplacez l’ancien fichier XML HelpInfo par le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="3883d-117">Replace the older HelpInfo XML file with the new file.</span></span>
