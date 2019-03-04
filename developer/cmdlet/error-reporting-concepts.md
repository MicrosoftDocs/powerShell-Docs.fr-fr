---
title: Concepts de signalement d’erreurs | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855075"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="52ca7-102">Concepts des rapports d’erreurs</span><span class="sxs-lookup"><span data-stu-id="52ca7-102">Error Reporting Concepts</span></span>

<span data-ttu-id="52ca7-103">Windows PowerShell fournit deux mécanismes pour signaler les erreurs : un mécanisme pour *arrêt erreurs* et un autre mécanisme pour *erreurs sans fin d’exécution*.</span><span class="sxs-lookup"><span data-stu-id="52ca7-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="52ca7-104">Il est important pour votre applet de commande pour signaler des erreurs correctement afin que l’application hôte qui exécute vos applets de commande peut réagir de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="52ca7-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="52ca7-105">Votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) méthode lorsqu’une erreur produit qui n’est pas ou ne doit pas autoriser l’applet de commande continuer à traiter ses objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52ca7-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="52ca7-106">Votre applet de commande doit appeler le [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler les erreurs sans fin d’exécution lors de l’applet de commande peut continuer à traiter les objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52ca7-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="52ca7-107">Les deux méthodes fournissent un enregistrement d’erreur que l’application hôte peut utiliser pour rechercher la cause de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="52ca7-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="52ca7-108">Utilisez les instructions suivantes pour déterminer si une erreur est une fin ou une erreur sans fin d’exécution.</span><span class="sxs-lookup"><span data-stu-id="52ca7-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="52ca7-109">Une erreur est une erreur avec fin si elle empêche votre applet de commande de continuer à traiter l’objet en cours ou de traiter correctement les objets davantage d’entrée, quel que soit leur contenu.</span><span class="sxs-lookup"><span data-stu-id="52ca7-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="52ca7-110">Une erreur est une erreur avec fin d’exécution si vous ne souhaitez pas votre applet de commande continuer le traitement de l’objet actuel ou tous les objets davantage d’entrée, quel que soit leur contenu.</span><span class="sxs-lookup"><span data-stu-id="52ca7-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="52ca7-111">Une erreur est une erreur avec fin s’il se produit dans une applet de commande qui ne pas accepter ou retourner un objet ou si elle se produit dans une applet de commande qui accepte ou retourne qu’un seul objet.</span><span class="sxs-lookup"><span data-stu-id="52ca7-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="52ca7-112">Une erreur est une erreur sans fin d’exécution si vous souhaitez que votre applet de commande pour continuer le traitement de l’objet actuel et tous les objets davantage d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52ca7-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="52ca7-113">Une erreur est une erreur sans fin d’exécution si elle est liée à un objet d’entrée spécifique ou un sous-ensemble d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="52ca7-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="52ca7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52ca7-114">See Also</span></span>

[<span data-ttu-id="52ca7-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="52ca7-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="52ca7-116">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="52ca7-116">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="52ca7-117">Windows PowerShell erreur enregistrements</span><span class="sxs-lookup"><span data-stu-id="52ca7-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="52ca7-118">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52ca7-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
