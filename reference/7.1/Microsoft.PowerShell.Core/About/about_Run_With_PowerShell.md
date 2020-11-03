---
description: Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 83931fcfcc89340b1d4958e41cb182642a554737
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208145"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="48313-104">À propos de l’exécution avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="48313-104">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="48313-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="48313-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="48313-106">Explique comment utiliser la fonctionnalité exécuter avec PowerShell pour exécuter un script à partir d’un lecteur du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="48313-106">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="48313-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="48313-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="48313-108">À compter de Windows PowerShell 3,0, vous pouvez utiliser la fonctionnalité « exécuter avec PowerShell » pour exécuter des scripts à partir de l’Explorateur de fichiers dans Windows 8 et Windows Server 2012 et à partir de l’Explorateur Windows dans les versions antérieures de Windows.</span><span class="sxs-lookup"><span data-stu-id="48313-108">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="48313-109">La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="48313-109">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="48313-110">Lorsque vous utilisez la fonctionnalité « exécuter avec PowerShell », la fenêtre de console PowerShell s’affiche brièvement, si ce n’est le cas.</span><span class="sxs-lookup"><span data-stu-id="48313-110">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="48313-111">Vous ne pouvez pas interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="48313-111">You cannot interact with it.</span></span>

<span data-ttu-id="48313-112">Pour utiliser la fonctionnalité « exécuter avec PowerShell » :</span><span class="sxs-lookup"><span data-stu-id="48313-112">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="48313-113">Dans l’Explorateur de fichiers (ou l’Explorateur Windows), cliquez avec le bouton droit sur le nom du fichier de script, puis sélectionnez exécuter avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48313-113">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="48313-114">La fonctionnalité « exécuter avec PowerShell » démarre une session PowerShell qui a une stratégie d’exécution de contournement, exécute le script et ferme la session.</span><span class="sxs-lookup"><span data-stu-id="48313-114">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="48313-115">Il exécute une commande qui a le format suivant :</span><span class="sxs-lookup"><span data-stu-id="48313-115">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="48313-116">« Exécuter avec PowerShell » définit la stratégie d’exécution de contournement uniquement pour la session (l’instance actuelle du processus PowerShell) dans laquelle le script s’exécute.</span><span class="sxs-lookup"><span data-stu-id="48313-116">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="48313-117">Cette fonctionnalité ne modifie pas la stratégie d’exécution de l’ordinateur ou de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="48313-117">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="48313-118">La fonctionnalité « exécuter avec PowerShell » est uniquement affectée par la stratégie d’exécution AllSigned.</span><span class="sxs-lookup"><span data-stu-id="48313-118">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="48313-119">Si la stratégie d’exécution AllSigned est effective pour l’ordinateur ou l’utilisateur, « exécuter avec PowerShell » exécute uniquement les scripts signés.</span><span class="sxs-lookup"><span data-stu-id="48313-119">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="48313-120">« Exécuter avec PowerShell » n’est pas affecté par les autres stratégies d’exécution.</span><span class="sxs-lookup"><span data-stu-id="48313-120">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="48313-121">Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="48313-121">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="48313-122">Remarque sur la résolution des problèmes : exécuter avec la commande PowerShell peut vous inviter à confirmer la modification de la stratégie d’exécution.</span><span class="sxs-lookup"><span data-stu-id="48313-122">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="48313-123">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="48313-123">SEE ALSO</span></span>

[<span data-ttu-id="48313-124">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="48313-124">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="48313-125">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="48313-125">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="48313-126">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="48313-126">about_Scripts</span></span>](about_Scripts.md)

