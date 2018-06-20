---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.topic: conceptual
title: exemple de modèle d’un problème ou limitation connu
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221933"
---
><span data-ttu-id="6a4f6-103">Remarque : fournir un titre descriptif proposé et une brève description</span><span class="sxs-lookup"><span data-stu-id="6a4f6-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="6a4f6-104">Exemples : erreurs ExecutionPolicy erronées</span><span class="sxs-lookup"><span data-stu-id="6a4f6-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="6a4f6-105">Sous Windows 7, l’utilisation de modules PowerShell et de ressources DSC peut générer des erreurs liées à ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="6a4f6-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="6a4f6-106">Solution</span><span class="sxs-lookup"><span data-stu-id="6a4f6-106">Resolution</span></span>

<span data-ttu-id="6a4f6-107">Pour résoudre le problème, affectez la valeur **RemoteSigned** à **ExecutionPolicy** en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="6a4f6-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
