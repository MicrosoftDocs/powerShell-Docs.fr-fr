---
ms.date: 09/12/2016
ms.topic: reference
title: Exemple de code GetProc03 (VB.NET)
description: Exemple de code GetProc03 (VB.NET)
ms.openlocfilehash: fc70496178c85e101b380e68aacd64c8d1f350e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355559"
---
# <a name="getproc03-vbnet-sample-code"></a>Exemple de code GetProc03 (VB.NET)

Le code suivant illustre l’implémentation d’une `Get-Process` applet de commande qui peut accepter une entrée en pipeline. Cette implémentation définit un `Name` paramètre qui accepte l’entrée de pipeline, récupère des informations de processus à partir de l’ordinateur local en fonction des noms fournis, puis utilise la méthode [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) comme mécanisme de sortie pour envoyer des objets au pipeline.

## <a name="code-sample"></a>Exemple de code

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
