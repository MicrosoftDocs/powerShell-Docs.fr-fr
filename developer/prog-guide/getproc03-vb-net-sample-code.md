---
title: GetProc03 (VB.NET) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854635"
---
# <a name="getproc03-vbnet-sample-code"></a>Exemple de code GetProc03 (VB.NET)

Le code suivant illustre l’implémentation d’un `Get-Process` entrée en pipeline l’applet de commande qui peut accepter. Cette implémentation définit un `Name` paramètre qui accepte les entrées de pipeline, récupère les informations de processus à partir de l’ordinateur local selon les noms fournis et utilise ensuite la [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) méthode en tant que le mécanisme de sortie pour envoyer des objets dans le pipeline.

## <a name="code-sample"></a>Exemple de code

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->