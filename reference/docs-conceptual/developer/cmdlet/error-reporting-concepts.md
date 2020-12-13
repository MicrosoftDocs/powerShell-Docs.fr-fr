---
ms.date: 09/13/2016
ms.topic: reference
title: Concepts des rapports d’erreurs
description: Concepts des rapports d’erreurs
ms.openlocfilehash: 353e628c63667a2db010556b2ed9169809b742f4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653038"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="b2971-103">Concepts des rapports d’erreurs</span><span class="sxs-lookup"><span data-stu-id="b2971-103">Error Reporting Concepts</span></span>

<span data-ttu-id="b2971-104">Windows PowerShell fournit deux mécanismes pour signaler les erreurs : un mécanisme pour mettre *fin aux erreurs* et un autre mécanisme pour les *Erreurs sans fin d’achèvement*.</span><span class="sxs-lookup"><span data-stu-id="b2971-104">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="b2971-105">Il est important que votre applet de commande signale les erreurs correctement pour que l’application hôte qui exécute vos applets de commande puisse réagir de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="b2971-105">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="b2971-106">Votre applet de commande doit appeler la méthode [System. Management. Automation. applet de commande. ThrowTerminatingError \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) lorsqu’une erreur qui n’est pas ou ne doit pas permettre à l’applet de commande de continuer à traiter ses objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b2971-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="b2971-107">Votre applet de commande doit appeler la méthode [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) pour signaler les erreurs sans fin d’exécution lorsque l’applet de commande peut poursuivre le traitement des objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b2971-107">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="b2971-108">Les deux méthodes fournissent un enregistrement d’erreur que l’application hôte peut utiliser pour rechercher la cause de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="b2971-108">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="b2971-109">Utilisez les instructions suivantes pour déterminer si une erreur est une erreur de fin ou sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="b2971-109">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="b2971-110">Une erreur est une erreur de fin si elle empêche votre applet de commande de continuer à traiter l’objet actuel ou de traiter correctement les autres objets d’entrée, quel que soit leur contenu.</span><span class="sxs-lookup"><span data-stu-id="b2971-110">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="b2971-111">Une erreur est une erreur de fin si vous ne souhaitez pas que votre applet de commande continue à traiter l’objet en cours ou tout autre objet d’entrée, quel que soit son contenu.</span><span class="sxs-lookup"><span data-stu-id="b2971-111">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="b2971-112">Une erreur se termine par une erreur si elle se produit dans une applet de commande qui n’accepte pas ou ne retourne pas d’objet ou si elle se produit dans une applet de commande qui accepte ou retourne un seul objet.</span><span class="sxs-lookup"><span data-stu-id="b2971-112">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="b2971-113">Une erreur est une erreur sans fin d’exécution si vous souhaitez que votre applet de commande continue à traiter l’objet actuel et tous les autres objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b2971-113">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="b2971-114">Une erreur est une erreur sans fin d’opération si elle est liée à un objet d’entrée spécifique ou à un sous-ensemble d’objets d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b2971-114">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2971-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2971-115">See Also</span></span>

[<span data-ttu-id="b2971-116">System. Management. Automation. applet de commande. ThrowTerminatingError \*</span><span class="sxs-lookup"><span data-stu-id="b2971-116">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="b2971-117">System. Management. Automation. applet de commande. WriteError</span><span class="sxs-lookup"><span data-stu-id="b2971-117">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="b2971-118">Enregistrements d’erreurs Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2971-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="b2971-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2971-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
