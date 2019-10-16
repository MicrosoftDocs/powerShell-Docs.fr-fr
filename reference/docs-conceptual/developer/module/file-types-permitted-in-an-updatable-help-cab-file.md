---
title: Types de fichiers autorisés dans un fichier CAB d’aide pouvant être mis à jour | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367258"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="bc41d-102">Types de fichiers autorisés dans un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="bc41d-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="bc41d-103">Cette rubrique répertorie et décrit la configuration requise pour le contenu des fichiers CAB de l’aide actualisable.</span><span class="sxs-lookup"><span data-stu-id="bc41d-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="bc41d-104">Configuration requise pour le fichier CAB de l’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="bc41d-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="bc41d-105">Le contenu du fichier CAB non compressé est limité à 1 Go par défaut.</span><span class="sxs-lookup"><span data-stu-id="bc41d-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="bc41d-106">Pour contourner cette limite, les utilisateurs doivent utiliser le paramètre **force** des applets de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="bc41d-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="bc41d-107">Pour garantir la sécurité des fichiers d’aide téléchargés à partir d’Internet, un fichier CAB d’aide pouvant être mis à jour peut inclure uniquement les types de fichiers répertoriés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="bc41d-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="bc41d-108">L’applet de commande [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) valide tous les fichiers par rapport aux schémas de rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="bc41d-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="bc41d-109">Si l’applet de commande `Update-Help` rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, elle n’installe pas le fichier non valide et arrête l’installation des fichiers à partir du fichier CAB sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc41d-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="bc41d-110">Rubriques d’aide XML pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="bc41d-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="bc41d-111">Rubriques d’aide XML pour les scripts et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="bc41d-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="bc41d-112">Rubriques d’aide XML pour les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc41d-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="bc41d-113">Rubriques d’aide textuelles, telles que les rubriques à propos de.</span><span class="sxs-lookup"><span data-stu-id="bc41d-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="bc41d-114">La [mise à jour-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) vérifie le contenu du fichier CAB lorsqu’il décompresse le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="bc41d-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="bc41d-115">Si `Update-Help` trouve des types de fichiers non conformes dans un fichier CAB d’aide actualisable, il génère une erreur de fin et arrête l’opération.</span><span class="sxs-lookup"><span data-stu-id="bc41d-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="bc41d-116">Il n’installe pas les fichiers d’aide à partir du fichier CAB, même ceux des types de fichiers conformes.</span><span class="sxs-lookup"><span data-stu-id="bc41d-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>