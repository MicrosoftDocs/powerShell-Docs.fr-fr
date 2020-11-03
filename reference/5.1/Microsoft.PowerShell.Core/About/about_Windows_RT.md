---
description: Explique les limitations de Windows PowerShell 4,0 sur Windows RT 8,1.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207505"
---
# <a name="about-windows-rt"></a><span data-ttu-id="354d8-104">À propos de Windows RT</span><span class="sxs-lookup"><span data-stu-id="354d8-104">About Windows RT</span></span>

## <a name="short-description"></a><span data-ttu-id="354d8-105">DESCRIPTION COURTE</span><span class="sxs-lookup"><span data-stu-id="354d8-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="354d8-106">Explique les limitations de Windows PowerShell 4,0 sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-106">Explains limitations of  Windows PowerShell 4.0 on Windows RT 8.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="354d8-107">DESCRIPTION DÉTAILLÉE</span><span class="sxs-lookup"><span data-stu-id="354d8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="354d8-108">Le système d’exploitation Windows RT 8,1 est installé sur les ordinateurs et les périphériques (tels que Microsoft Surface 2, sur lequel il s’agit du système d’exploitation fourni avec l’ordinateur) qui utilisent des processeurs ARM (Advanced RISC machine).</span><span class="sxs-lookup"><span data-stu-id="354d8-108">The Windows RT 8.1 operating system is installed on computers and devices (such as Microsoft Surface 2, on which it is the operating system that ships with the computer) that use Advanced RISC Machine (ARM) processors.</span></span>

<span data-ttu-id="354d8-109">Windows PowerShell 4,0 est inclus dans Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-109">Windows PowerShell 4.0 is included in Windows RT 8.1.</span></span> <span data-ttu-id="354d8-110">Toutes les applets de commande, tous les fournisseurs et tous les modules, ainsi que la plupart des scripts conçus pour Windows PowerShell 2,0 et versions ultérieures, s’exécutent sur Windows RT 8,1 sans aucune modification.</span><span class="sxs-lookup"><span data-stu-id="354d8-110">All cmdlets, providers, and modules, and most scripts designed for Windows PowerShell 2.0 and later releases run on Windows RT 8.1 without changes.</span></span>

<span data-ttu-id="354d8-111">Étant donné que Windows RT 8,1 n’inclut pas toutes les fonctionnalités de Windows, certaines fonctionnalités de Windows PowerShell fonctionnent différemment ou ne fonctionnent pas sur les périphériques basés sur Windows RT.</span><span class="sxs-lookup"><span data-stu-id="354d8-111">Because Windows RT 8.1 does not include all Windows features, some Windows PowerShell features work differently or do not work on Windows RT-based devices.</span></span> <span data-ttu-id="354d8-112">La liste suivante explique les différences.</span><span class="sxs-lookup"><span data-stu-id="354d8-112">The following list explains the differences.</span></span>

- <span data-ttu-id="354d8-113">Windows PowerShell ISE n’est pas inclus dans et ne peut pas s’exécuter sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-113">Windows PowerShell ISE is not included in and cannot run on Windows RT 8.1.</span></span>
  <span data-ttu-id="354d8-114">Windows PowerShell ISE nécessite Windows Presentation Foundation, qui n’est pas inclus dans Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-114">Windows PowerShell ISE requires Windows Presentation Foundation, which is not included in Windows RT 8.1.</span></span>

- <span data-ttu-id="354d8-115">La communication à distance Windows PowerShell et le service WinRM sont désactivés par défaut.</span><span class="sxs-lookup"><span data-stu-id="354d8-115">Windows PowerShell remoting and the WinRM service are disabled by default.</span></span>
  <span data-ttu-id="354d8-116">Pour activer la communication à distance, exécutez l’applet de commande Enable-PSRemoting.</span><span class="sxs-lookup"><span data-stu-id="354d8-116">To enable remoting, run the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="354d8-117">Exécutez également l’applet de commande Set-Service pour définir le type de démarrage du service WinRM sur automatique ou automatique (début différé).</span><span class="sxs-lookup"><span data-stu-id="354d8-117">Also, run the Set-Service cmdlet to set the startup type of the WinRM service to Automatic, or Automatic (Delayed Start).</span></span>

  <span data-ttu-id="354d8-118">Alors que la communication à distance est désactivée, vous pouvez utiliser la communication à distance Windows PowerShell pour exécuter des commandes sur d’autres ordinateurs, mais les autres ordinateurs ne peuvent pas exécuter de commandes sur l’appareil Windows RT.</span><span class="sxs-lookup"><span data-stu-id="354d8-118">While remoting is disabled, you can use Windows PowerShell remoting to run commands on other computers, but other computers cannot run commands on the Windows RT device.</span></span> <span data-ttu-id="354d8-119">En outre, la communication à distance implicite, c’est-à-dire la communication à distance qui est intégrée à une applet de commande ou à un script, et qui n’est pas explicitement demandée avec des paramètres ajoutés</span><span class="sxs-lookup"><span data-stu-id="354d8-119">Also, implicit remoting - that is, remoting that is built in to a cmdlet or script, and not explicitly requested with added parameters</span></span>
  - <span data-ttu-id="354d8-120">ne fonctionne pas dans Windows PowerShell s’exécutant sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-120">does not work in Windows PowerShell running on Windows RT 8.1.</span></span>

- <span data-ttu-id="354d8-121">L’informatique jointe à un domaine et l’authentification Kerberos ne sont pas prises en charge sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-121">Domain-joined computing and Kerberos authentication are not supported on Windows RT 8.1.</span></span> <span data-ttu-id="354d8-122">Vous ne pouvez pas utiliser Windows PowerShell pour ajouter ou gérer ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="354d8-122">You cannot use Windows PowerShell to add or manage these features.</span></span>

- <span data-ttu-id="354d8-123">Les classes Microsoft .NET Framework qui ne sont pas prises en charge sur Windows RT 8,1 ne sont pas non plus prises en charge par Windows PowerShell sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-123">Microsoft .NET Framework classes that are not supported on Windows RT 8.1 are also not supported by Windows PowerShell on Windows RT 8.1.</span></span>

- <span data-ttu-id="354d8-124">Les transactions ne sont pas activées sur Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="354d8-124">Transactions are not enabled on Windows RT 8.1.</span></span> <span data-ttu-id="354d8-125">Les applets de commande de transaction, telles que start-transaction et les paramètres de transaction, tels que UseTransaction, ne fonctionnent pas correctement.</span><span class="sxs-lookup"><span data-stu-id="354d8-125">Transaction cmdlets, such as Start-Transaction, and transaction parameters, such as UseTransaction, do not work properly.</span></span>

- <span data-ttu-id="354d8-126">Toutes les sessions Windows PowerShell sur les périphériques Windows RT 8,1 utilisent le mode de langage ConstrainedLanguage.</span><span class="sxs-lookup"><span data-stu-id="354d8-126">All Windows PowerShell sessions on Windows RT 8.1 devices use the ConstrainedLanguage language mode.</span></span> <span data-ttu-id="354d8-127">Le mode ConstrainedLanguage Language est un complément de l’intégrité du code du mode utilisateur (UMCI).</span><span class="sxs-lookup"><span data-stu-id="354d8-127">ConstrainedLanguage language mode is a companion to User Mode Code Integrity (UMCI).</span></span> <span data-ttu-id="354d8-128">Il autorise toutes les applets de commande Windows et les éléments de langage Windows PowerShell, mais limite les types pour s’assurer que les utilisateurs ne peuvent pas utiliser Windows PowerShell pour contourner ou violer les protections UMCI.</span><span class="sxs-lookup"><span data-stu-id="354d8-128">It permits all Windows cmdlets and Windows PowerShell language elements, but restricts types to ensure that users cannot use Windows PowerShell to circumvent or violate the UMCI protections.</span></span>

<span data-ttu-id="354d8-129">Pour plus d’informations sur le mode de langage ConstrainedLanguage, consultez [about_Language_Modes](about_Language_Modes.md).</span><span class="sxs-lookup"><span data-stu-id="354d8-129">For more information about ConstrainedLanguage language mode, see [about_Language_Modes](about_Language_Modes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="354d8-130">VOIR AUSSI</span><span class="sxs-lookup"><span data-stu-id="354d8-130">SEE ALSO</span></span>

[<span data-ttu-id="354d8-131">about_Language_Modes</span><span class="sxs-lookup"><span data-stu-id="354d8-131">about_Language_Modes</span></span>](about_Language_Modes.md)

[<span data-ttu-id="354d8-132">about_Remote</span><span class="sxs-lookup"><span data-stu-id="354d8-132">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="354d8-133">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="354d8-133">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)
