---
description: Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596752"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="30545-103">À propos de l’exécution avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="30545-103">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="30545-104">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="30545-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="30545-105">Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="30545-105">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="30545-106">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="30545-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="30545-107">À compter de Windows PowerShell 3,0, vous pouvez utiliser la fonctionnalité « exécuter avec PowerShell » pour exécuter des scripts à partir de l’Explorateur de fichiers dans Windows 8 et Windows Server 2012 et à partir de l’Explorateur Windows dans les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="30545-107">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="30545-108">La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="30545-108">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="30545-109">Lorsque vous utilisez la fonctionnalité « exécuter avec PowerShell », la fenêtre de console PowerShell s’affiche brièvement, si ce n’est le cas.</span><span class="sxs-lookup"><span data-stu-id="30545-109">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="30545-110">Vous ne pouvez pas interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="30545-110">You cannot interact with it.</span></span>

<span data-ttu-id="30545-111">Pour utiliser la fonctionnalité « exécuter avec PowerShell » :</span><span class="sxs-lookup"><span data-stu-id="30545-111">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="30545-112">Dans l’Explorateur de fichiers (ou l’Explorateur Windows), cliquez avec le bouton droit sur le nom du fichier de script, puis sélectionnez exécuter avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30545-112">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="30545-113">La fonctionnalité « exécuter avec PowerShell » démarre une session PowerShell qui a une stratégie d’exécution de contournement, exécute le script et ferme la session.</span><span class="sxs-lookup"><span data-stu-id="30545-113">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="30545-114">Il exécute une commande qui a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="30545-114">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="30545-115">« Exécuter avec PowerShell » définit la stratégie d’exécution de contournement uniquement pour la session (l’instance actuelle du processus PowerShell) dans laquelle le script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="30545-115">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="30545-116">Cette fonctionnalité ne modifie pas la stratégie d’exécution de l’ordinateur ou de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="30545-116">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="30545-117">La fonctionnalité « exécuter avec PowerShell » est uniquement affectée par la stratégie d’exécution AllSigned.</span><span class="sxs-lookup"><span data-stu-id="30545-117">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="30545-118">Si la stratégie d’exécution AllSigned est effective pour l’ordinateur ou l’utilisateur, « exécuter avec PowerShell » exécute uniquement les scripts signés.</span><span class="sxs-lookup"><span data-stu-id="30545-118">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="30545-119">« Exécuter avec PowerShell » n’est pas affecté par les autres stratégies d’exécution.</span><span class="sxs-lookup"><span data-stu-id="30545-119">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="30545-120">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="30545-120">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="30545-121">Remarque sur la résolution des problèmes : exécuter avec la commande PowerShell peut vous inviter à confirmer la modification de la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="30545-121">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="30545-122">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="30545-122">SEE ALSO</span></span>

[<span data-ttu-id="30545-123">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="30545-123">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="30545-124">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="30545-124">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="30545-125">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="30545-125">about_Scripts</span></span>](about_Scripts.md)

