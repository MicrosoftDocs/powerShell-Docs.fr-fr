---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.topic: conceptual
title: exemple de modèle d’un problème ou limitation connu
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055545"
---
 ><span data-ttu-id="5b671-103">Remarque : fournir un titre descriptif proposé et une brève description</span><span class="sxs-lookup"><span data-stu-id="5b671-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="5b671-104">Exemple : erreurs ExecutionPolicy erronées</span><span class="sxs-lookup"><span data-stu-id="5b671-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="5b671-105">Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="5b671-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="5b671-106">Solution</span><span class="sxs-lookup"><span data-stu-id="5b671-106">Resolution</span></span>

<span data-ttu-id="5b671-107">Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="5b671-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
