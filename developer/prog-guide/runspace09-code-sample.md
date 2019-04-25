---
title: Exemple de Code RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081221"
---
# <a name="runspace09-code-sample"></a>Exemple de code RunSpace09

Voici le code source pour l’exemple Runspace09 décrit dans [création d’un Pipeline de façon asynchrone une Console Application qu’appelle](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Cet exemple d’application crée et ouvre une instance d’exécution, crée et appelle un pipeline de manière asynchrone, puis utilise les événements pour traiter de façon asynchrone le script de pipeline. Le script est exécuté par cette application crée les entiers entre 1 et 10 dans toutes les 0,5 secondes (500 ms).

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)