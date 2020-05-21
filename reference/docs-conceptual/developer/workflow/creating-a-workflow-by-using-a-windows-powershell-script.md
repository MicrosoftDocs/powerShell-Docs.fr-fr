---
title: Création d’un flux de travail à l’aide d’un script Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: cc613240e056e8443b075019cbff6dd15da3716f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557446"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Création d’un workflow avec un script Windows PowerShell

Vous pouvez créer un flux de travail en écrivant un script Windows PowerShell. Pour créer un flux de travail, utilisez le mot clé Workflow suivi d’un nom pour le flux de travail avant le corps du script. Par exemple :

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Vous trouvez le flux de travail de la même façon que vous le feriez pour toute autre commande Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implémentation de Parallel et Sequence

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) prend en charge l’exécution des activités en parallèle. Pour implémenter cette fonctionnalité dans un script Windows PowerShell, utilisez le `parallel` mot clé devant un bloc de script. Vous pouvez également utiliser la `foreach -parallel` construction pour itérer au sein d’une collection d’objets en parallèle. Pour exécuter un groupe d’activités dans un ordre séquentiel dans un bloc parallèle, placez ce groupe d’activités dans un bloc de script et précédez le bloc avec le mot clé Sequence.

## <a name="joining-computers-to-a-domain"></a>Joindre des ordinateurs à un domaine

Le script suivant crée un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifiés par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joints, puis vérifie à nouveau l’État.
Il s’agit d’une version de script du flux de travail XAML expliquée dans [création d’un workflow avec des activités Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```
