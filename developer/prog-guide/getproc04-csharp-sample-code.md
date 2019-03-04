---
title: GetProc04 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: 02b692047294879f885ca86d4598b0b0ab81808a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863285"
---
# <a name="getproc04-c-sample-code"></a>Exemple de code GetProc04 (C#)

Le code suivant illustre l’implémentation d’un `Get-Process` applet de commande qui signale les erreurs sans fin d’exécution. Cette implémentation appelle le [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) méthode pour signaler des erreurs sans fin d’exécution.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Vous pouvez télécharger le C# le fichier source (getprov04.cs) pour cette applet de commande Get-Process en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[GetProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)