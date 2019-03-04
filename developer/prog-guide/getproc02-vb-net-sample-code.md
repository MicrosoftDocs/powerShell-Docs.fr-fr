---
title: GetProc02 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 5b5cefae1be3ccf6aec819df83363b7161955b0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860185"
---
# <a name="getproc02-vbnet-sample-code"></a>Exemple de code GetProc02 (VB.NET)

Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui accepte les entrées de ligne de commande. Notez que cette implémentation définit un `Name` paramètre pour autoriser l’entrée de ligne de commande et il utilise le [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) méthode comme sortie mécanisme pour envoyer la sortie des objets au pipeline.

## <a name="code-sample"></a>Exemple de code

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a>Voir aussi

[Windows PowerShell SDK](../windows-powershell-reference.md)