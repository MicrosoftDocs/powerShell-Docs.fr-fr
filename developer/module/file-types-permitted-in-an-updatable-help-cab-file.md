---
title: Fichier CAB d’aider à des Types de fichiers autorisés dans un actualisable | Microsoft Docs
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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794244"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="3e5f1-102">Types de fichiers autorisés dans un fichier CAB d’aide actualisable</span><span class="sxs-lookup"><span data-stu-id="3e5f1-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="3e5f1-103">Cette rubrique répertorie et décrit les exigences de contenu pour les fichiers CAB de vous aider à être mise à jour.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="3e5f1-104">Configuration requise du fichier CAB aide actualisable</span><span class="sxs-lookup"><span data-stu-id="3e5f1-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="3e5f1-105">Contenu du fichier CAB non compressé est limité à 1 Go par défaut.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="3e5f1-106">Pour contourner cette limite, les utilisateurs doivent utiliser le **Force** paramètre de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) et [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) applets de commande.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="3e5f1-107">Afin de garantir la sécurité des fichiers d’aide qui sont téléchargés à partir d’Internet, un fichier CAB d’aide actualisable peut inclure uniquement les types de fichiers répertoriés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="3e5f1-108">Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) applet de commande valide tous les fichiers par rapport aux schémas de la rubrique d’aide.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="3e5f1-109">Si le `Update-Help` applet de commande rencontre un fichier qui n’est pas valide ou n’est pas un type autorisé, il n’installe pas le fichier non valide et arrête l’installation des fichiers du fichier cab sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="3e5f1-110">Rubriques d’aide basé sur XML pour les applets de commande.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="3e5f1-111">Rubriques d’aide basé sur XML pour les scripts et fonctions.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="3e5f1-112">Rubriques d’aide basé sur XML pour les fournisseurs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="3e5f1-113">Textuel rubriques d’aide, telles que sur des sujets.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="3e5f1-114">Le [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) vérifie le contenu du fichier CAB lorsqu’il décompresse le fichier CAB.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="3e5f1-115">Si `Update-Help` recherche les types de fichier non conforme dans un fichier CAB d’aide actualisable, il génère une erreur avec fin d’exécution et arrête l’opération.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="3e5f1-116">Il n’installe pas les fichiers d’aide du fichier CAB, y compris celles des types de fichier compatible.</span><span class="sxs-lookup"><span data-stu-id="3e5f1-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>