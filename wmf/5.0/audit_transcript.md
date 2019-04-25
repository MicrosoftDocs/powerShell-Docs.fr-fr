---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: f655cd7aa9b14bd38924d55c8f1246b55ef83756
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085847"
---
# <a name="enhanced-transcription-options"></a><span data-ttu-id="6ae19-102">Options de transcription améliorées</span><span class="sxs-lookup"><span data-stu-id="6ae19-102">Enhanced Transcription Options</span></span>

<span data-ttu-id="6ae19-103">La transcription Windows PowerShell a été améliorée pour s’appliquer à toutes les applications d’hébergement (telles que Windows PowerShell ISE), et pas simplement à l’hôte de la console (powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="6ae19-103">Windows PowerShell transcription has been improved to apply to all hosting applications (such as Windows PowerShell ISE) rather than just the console host (powershell.exe).</span></span>

<span data-ttu-id="6ae19-104">Outre l’extension de la transcription, la fonctionnalité de transcription proprement dite a été mise à jour pour prendre en charge l’imbrication arbitraire des transcriptions, des métadonnées supplémentaires dans l’en-tête de transcription résultant, et la définition d’un répertoire de sortie de transcription (pour prendre en charge la collecte de journaux centralisée).</span><span class="sxs-lookup"><span data-stu-id="6ae19-104">In addition to extending for transcripting, the transcripting functionality itself has been updated to support arbitrary nesting of transcripts, additional metadata in the resulting transcript header, and setting a transcription output directory (to support centralized log collection).</span></span>

<span data-ttu-id="6ae19-105">Vous pouvez configurer les options de transcription (notamment activer une transcription à l’échelle du système) avec le paramètre stratégie de groupe **Activer la transcription PowerShell** (Modèles d’administration -> Composants Windows -> Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="6ae19-105">Transcription options (including enabling a system-wide transcript) can be configured with the **Turn on PowerShell Transcription** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>
