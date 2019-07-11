---
title: RunSpace03 (C#) exemple de Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: e1fc91174a959d6acc306330afb8d5c2e7a9a860
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735006"
---
# <a name="runspace03-c-code-sample"></a>Exemple de code RunSpace03 (C#)

Voici le C# code source pour l’application de console décrite dans [création d’une Console Application qui s’exécute un Script spécifié](fd). Cet exemple utilise le [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) classe pour exécuter un script qui Récupère traite les informations à l’aide de la liste des noms de processus passés dans le script. Il montre comment passer des objets d’entrée à un script et comment récupérer des objets d’erreur, ainsi que les objets de sortie.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (runspace03.cs) pour cet exemple en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution de Microsoft .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.

## <a name="code-sample"></a>Exemple de code

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Voir aussi

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)