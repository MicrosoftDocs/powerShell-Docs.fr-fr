---
title: Exemple de code RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 2e9cd80f1869e0d859187eea89eca414a84cb4ab
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870578"
---
# <a name="runspace08-code-sample"></a>Exemple de code RunSpace08

Voici le code source de l’exemple Runspace08 décrit dans [création d’une application console qui ajoute des paramètres à une commande](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).
Cet exemple d’application crée une instance d’exécution, crée un pipeline, ajoute deux commandes au pipeline, ajoute deux paramètres à la deuxième commande, puis exécute le pipeline. Les commandes ajoutées au pipeline sont les applets de commande `Get-Process` et `Sort-Object`.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
