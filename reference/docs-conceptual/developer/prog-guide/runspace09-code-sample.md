---
title: Exemple de code RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: 2f447fd0ce21c5bca8abe1fddb4e3c7025b70ef1
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870577"
---
# <a name="runspace09-code-sample"></a>Exemple de code RunSpace09

Voici le code source de l’exemple Runspace09 décrit dans [création d’une application console qui appelle un pipeline de manière asynchrone](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).
Cet exemple d’application crée et ouvre une instance d’exécution, crée et appelle de manière asynchrone un pipeline, puis utilise des événements de pipeline pour traiter le script de façon asynchrone. Le script exécuté par cette application crée les entiers de 1 à 10 en intervalles de 0,5 secondes (500 ms).

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace09.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)
