---
title: Création d’un Workflow à l’aide d’un Script PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853045"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Création d’un workflow avec un script Windows PowerShell

Vous pouvez créer un flux de travail en écrivant un script Windows PowerShell. Pour créer un flux de travail, utilisez le mot clé de flux de travail suivi d’un nom pour le flux de travail avant le corps du script. Par exemple :

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Le flux de travail se trouvent dans la même façon que vous le feriez pour toute autre commande Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implémentation de Parallel et Sequence

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) prend en charge l’exécution des activités en parallèle. Pour implémenter cette fonctionnalité dans un script Windows PowerShell, utilisez le `parallel` mot-clé devant un bloc de script. Vous pouvez également utiliser le `foreach -parallel` construction pour itérer une collection d’objets en parallèle. Pour exécuter un groupe d’activités dans un ordre séquentiel au sein d’un bloc parallèle, placez ce groupe d’activités dans un bloc de script et faites précéder le bloc avec le mot clé de séquence.

## <a name="joining-computers-to-a-domain"></a>Joindre des ordinateurs à un domaine

Le script suivant crée un flux de travail qui vérifie l’état du domaine d’un groupe d’ordinateurs spécifié par l’utilisateur, les joint à un domaine s’ils ne sont pas déjà joint, puis vérifie à nouveau l’état. Il s’agit d’une version de script du flux de travail XAML expliqué dans [création d’un flux de travail avec Windows PowerShell activités](./creating-a-workflow-with-windows-powershell-activities.md).

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