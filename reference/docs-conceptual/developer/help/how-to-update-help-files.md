---
title: Guide pratique pour mettre à jour les fichiers d’aide
ms.date: 09/12/2016
ms.openlocfilehash: 80f7c8865729515de98648765fa36ce540e00162
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892946"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="4b4bb-102">Guide pratique pour mettre à jour les fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="4b4bb-102">How to Update Help Files</span></span>

<span data-ttu-id="4b4bb-103">Cette rubrique explique comment mettre à jour les fichiers d’aide d’un module qui prend en charge l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="4b4bb-104">Mise à jour des fichiers d’aide</span><span class="sxs-lookup"><span data-stu-id="4b4bb-104">Updating Help Files</span></span>

<span data-ttu-id="4b4bb-105">Il existe de nombreuses raisons de mettre à jour les fichiers d’aide, tels que la correction des erreurs, la clarification d’un concept, la réponse à une question fréquemment posée, l’ajout de nouveaux fichiers ou l’ajout de nouveaux et de meilleurs exemples.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="4b4bb-106">Pour mettre à jour un fichier d’aide :</span><span class="sxs-lookup"><span data-stu-id="4b4bb-106">To update a help file:</span></span>

1. <span data-ttu-id="4b4bb-107">Modifiez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-107">Change the files.</span></span>
1. <span data-ttu-id="4b4bb-108">Traduisez les fichiers dans d’autres cultures d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-108">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="4b4bb-109">Collecter tous les fichiers d’aide (nouveaux, modifiés et inchangés) pour le module dans chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="4b4bb-110">Validez les fichiers par rapport au schéma XML.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-110">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="4b4bb-111">Régénérez les fichiers CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-111">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="4b4bb-112">Dans le fichier XML HelpInfo, incrémentez les numéros de version du fichier CAB pour chaque culture d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="4b4bb-113">Chargez les nouveaux fichiers CAB à l’emplacement spécifié par la valeur de l’élément **HelpContentUri** dans le fichier XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="4b4bb-114">Remplacez les anciens fichiers CAB par les nouveaux fichiers CAB.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-114">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="4b4bb-115">Téléchargez le fichier XML HelpInfo mis à jour à l’emplacement spécifié par la clé **HelpInfoUri** dans le manifeste de module.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="4b4bb-116">Remplacez l’ancien fichier XML HelpInfo par le nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="4b4bb-116">Replace the older HelpInfo XML file with the new file.</span></span>
