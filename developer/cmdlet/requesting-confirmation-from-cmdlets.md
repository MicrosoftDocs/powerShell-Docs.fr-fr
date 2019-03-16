---
title: Demander la Confirmation des applets de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057399"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Demandes de confirmation des applets de commande

Applets de commande demande une confirmation lorsqu’ils sont sur le point d’apporter une modification au système qui se trouve en dehors de l’environnement Windows PowerShell. Par exemple, si une applet de commande est sur le point d’ajouter un compte d’utilisateur ou d’arrêter un processus, l’applet de commande doit nécessitent une confirmation de l’utilisateur avant de poursuivre. En revanche, si une applet de commande est sur le point de modifier une variable Windows PowerShell, l’applet de commande ne devez pas nécessitent une confirmation.

Pour effectuer une demande de confirmation, l’applet de commande doit indiquer qu’il prend en charge les demandes de confirmation, et il doit appeler la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) méthodes (facultatifs) pour afficher un message de demande de confirmation.

## <a name="supporting-confirmation-requests"></a>Prise en charge des demandes de Confirmation

Pour prendre en charge les demandes de confirmation, l’applet de commande doit définir le `SupportsShouldProcess` paramètre de l’attribut de l’applet de commande à `true`. Cela permet la `Confirm` et `WhatIf` paramètres d’applet de commande qui sont fournis par Windows PowerShell. Le `Confirm` paramètre permet à l’utilisateur de contrôler si la demande de confirmation s’affiche. Le `WhatIf` paramètre permet à l’utilisateur déterminer si l’applet de commande doit afficher un message ou exécuter son action. N’ajoutez pas manuellement la `Confirm` et `WhatIf` paramètres pour une applet de commande.

L’exemple suivant montre une déclaration d’attribut applet de commande qui prend en charge les demandes de confirmation.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Appel des méthodes de demande de Confirmation

Dans le code de l’applet de commande, appelez le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) méthode avant que l’opération qui modifie le système est effectuée. L’applet de commande de conception afin qu’en cas l’appel retourne une valeur de `false`, l’opération n’est pas effectuée et l’applet de commande traite l’opération suivante.

## <a name="calling-the-shouldcontinue-method"></a>Appel de la méthode ShouldContinue

La plupart des applets de commande demande confirmation à l’aide uniquement le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode). Toutefois, certains cas peuvent nécessiter de confirmation supplémentaire. Dans ce cas, vous devez compléter les [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) par un appel à la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode). Cela permet à l’applet de commande ou d’un fournisseur de contrôler plus précisément l’étendue de la **Oui pour tout** réponse à l’invite de confirmation.

Si une applet de commande appelle le [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (méthode), l’applet de commande doit également fournir un `Force` paramètre booléen. Si l’utilisateur spécifie `Force` lorsque l’utilisateur appelle l’applet de commande, l’applet de commande doit toujours appeler [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), mais il doit ignorer l’appel à [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) lève une exception lorsqu’elle est appelée à partir d’un environnement non interactif où l’utilisateur ne peut pas être invité. Ajout d’un `Force` paramètre garantit que la commande peut toujours être effectuée lorsqu’il est appelé dans un environnement non interactif.

L’exemple suivant montre comment appeler [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Le comportement d’un [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) appel peut varier en fonction de l’environnement dans lequel l’applet de commande est appelé. En suivant les recommandations précédentes afin de garantir que l’applet de commande se comporte de manière cohérente avec les autres applets de commande, quel que soit l’environnement hôte.

Pour obtenir un exemple de l’appel le [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), consultez [comment demander des Confirmations](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Spécifiez le niveau d’Impact

Lorsque vous créez l’applet de commande, spécifiez le niveau d’impact (la gravité) de la modification. Pour ce faire, définissez la valeur de la `ConfirmImpact` paramètre de l’attribut de l’applet de commande à élevé, moyen ou faible. Vous pouvez spécifier une valeur pour `ConfirmImpact` uniquement lorsque vous également spécifiez les `SupportsShouldProcess` paramètre pour l’applet de commande.

Pour la plupart des applets de commande, vous n’avez pas à spécifier explicitement `ConfirmImpact`.  Au lieu de cela, utilisez le paramètre par défaut du paramètre, qui est la moyenne. Si vous définissez `ConfirmImpact` élevé, l’opération sera confirmée par défaut. Réserver ce paramètre pour les actions hautement perturbatrices, telles que le reformatage d’un volume de disque dur.

## <a name="calling-non-confirmation-methods"></a>Appel de méthodes Non-Confirmation

Si l’applet de commande ou le fournisseur doit envoyer un message, mais pas demande confirmation, elle peut appeler le des trois méthodes suivantes. Évitez d’utiliser le [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) méthode pour envoyer des messages de ces types, car [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) le mélange de sortie avec la sortie normale de votre applet de commande ou d’un fournisseur, ce qui complique écriture de script.

- Pour l’attention de l’utilisateur et poursuivre l’opération, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) (méthode).

- Pour fournir des informations supplémentaires que l’utilisateur peut récupérer à l’aide de la `Verbose` paramètre, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) (méthode).

- Pour fournir les détails de niveau débogage à d’autres développeurs, ou pour la prise en charge du produit, l’applet de commande ou le fournisseur peut appeler le [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) (méthode). L’utilisateur peut récupérer cette information à l’aide de le `Debug` paramètre.

Applets de commande et des fournisseurs d’abord appellent les méthodes suivantes pour demande confirmation avant de tenter d’effectuer une opération qui modifie un système en dehors de Windows PowerShell :

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Ils le font en appelant le [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) (méthode), qui invite l’utilisateur à confirmer l’opération basée sur la façon dont l’utilisateur a appelé la commande.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
