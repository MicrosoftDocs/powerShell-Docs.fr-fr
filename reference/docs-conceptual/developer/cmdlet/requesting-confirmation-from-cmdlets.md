---
ms.date: 09/13/2016
ms.topic: reference
title: Demandes de confirmation des applets de commande
description: Demandes de confirmation des applets de commande
ms.openlocfilehash: fd869d50b185cb4d38269640df58ec284a32da50
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646402"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Demandes de confirmation des applets de commande

Les applets de commande doivent demander confirmation lorsqu’elles sont sur le le du système qui se trouve en dehors de l’environnement Windows PowerShell. Par exemple, si une applet de commande est sur le point d’ajouter un compte d’utilisateur ou d’arrêter un processus, l’applet de commande doit demander confirmation à l’utilisateur avant de continuer. En revanche, si une applet de commande est sur le paragraphe de la modification d’une variable Windows PowerShell, l’applet de commande n’a pas besoin de demander de confirmation.

Pour effectuer une demande de confirmation, l’applet de commande doit indiquer qu’elle prend en charge les demandes de confirmation, et elle doit appeler les méthodes [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (facultatif) pour afficher un message de demande de confirmation.

## <a name="supporting-confirmation-requests"></a>Prise en charge des demandes de confirmation

Pour prendre en charge les demandes de confirmation, l’applet de commande doit définir le `SupportsShouldProcess` paramètre de l’attribut d’applet de commande sur `true` . Cela active les `Confirm` paramètres de l’applet de commande et `WhatIf` fournis par Windows PowerShell. Le `Confirm` paramètre permet à l’utilisateur de contrôler si la demande de confirmation est affichée. Le `WhatIf` paramètre permet à l’utilisateur de déterminer si l’applet de commande doit afficher un message ou exécuter son action. N’ajoutez pas manuellement les `Confirm` `WhatIf` paramètres et à une applet de commande.

L’exemple suivant montre une déclaration d’attribut d’applet de commande qui prend en charge les demandes de confirmation.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Appel des méthodes de demande de confirmation

Dans le code de l’applet de commande, appelez la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) avant l’opération qui modifie le système. Concevez l’applet de commande de sorte que si l’appel retourne la valeur `false` , l’opération n’est pas effectuée et l’applet de commande traite l’opération suivante.

## <a name="calling-the-shouldcontinue-method"></a>Appel de la méthode ShouldContinue

La plupart des applets de commande demandent une confirmation en utilisant uniquement la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Toutefois, certains cas peuvent nécessiter une confirmation supplémentaire. Dans ces cas-là, complétez l’appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) avec un appel à la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) de commande. ShouldContinue. Cela permet à l’applet de commande ou au fournisseur de contrôler plus précisément l’étendue de la réponse **Yes to all** à l’invite de confirmation.

Si une applet de commande appelle la méthode [System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , l’applet de commande doit également fournir un `Force` paramètre de commutateur. Si l’utilisateur spécifie `Force` quand l’utilisateur appelle l’applet de commande, l’applet de commande doit toujours appeler [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), mais il doit ignorer l’appel à [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)de commande. ShouldContinue.

[System. Management. Automation. applet de commande. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) lèvera une exception lorsqu’elle est appelée à partir d’un environnement non interactif où l’utilisateur ne peut pas être invité. L’ajout d’un `Force` paramètre permet de s’assurer que la commande peut toujours être exécutée quand elle est appelée dans un environnement non interactif.

L’exemple suivant montre comment appeler [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) et [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)de commande. ShouldContinue.

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Le comportement d’un appel [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) peut varier en fonction de l’environnement dans lequel l’applet de commande est appelée. L’utilisation des instructions précédentes permet de s’assurer que l’applet de commande se comporte de manière cohérente avec d’autres applets de commande, quel que soit l’environnement de l’hôte.

Pour obtenir un exemple d’appel de la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , consultez [Comment demander des confirmations](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Spécifier le niveau d’impact

Lorsque vous créez l’applet de commande, spécifiez le niveau d’impact (gravité) de la modification. Pour ce faire, définissez la valeur du `ConfirmImpact` paramètre de l’attribut d’applet de commande sur haute, moyenne ou faible. Vous pouvez spécifier une valeur pour `ConfirmImpact` uniquement lorsque vous spécifiez également le `SupportsShouldProcess` paramètre pour l’applet de commande.

Pour la plupart des applets de commande, vous n’avez pas à spécifier explicitement `ConfirmImpact` .  Au lieu de cela, utilisez le paramètre par défaut du paramètre, qui est moyen. Si vous définissez `ConfirmImpact` sur élevé, l’opération est confirmée par défaut. Réservez ce paramètre pour les actions très perturbatrices, telles que le reformatage d’un volume de disque dur.

## <a name="calling-non-confirmation-methods"></a>Appel de méthodes sans confirmation

Si l’applet de commande ou le fournisseur doit envoyer un message, mais pas demander de confirmation, il peut appeler les trois méthodes suivantes. Évitez d’utiliser la méthode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) pour envoyer des messages de ces types, car la sortie [System. Management. Automation. applet de commande. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) est mélangée avec la sortie normale de votre applet de commande ou fournisseur, ce qui complique l’écriture du script.

- Pour faire attention à l’utilisateur et poursuivre l’opération, l’applet de commande ou le fournisseur peut appeler la méthode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

- Pour fournir des informations supplémentaires que l’utilisateur peut récupérer à l’aide du `Verbose` paramètre, l’applet de commande ou le fournisseur peut appeler la méthode [System. Management. Automation. applet de commande. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

- Pour fournir des détails au niveau du débogage pour d’autres développeurs ou pour le support technique, l’applet de commande ou le fournisseur peut appeler la méthode [System. Management. Automation. applet](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) de commande. WriteDebug. L’utilisateur peut récupérer ces informations à l’aide du `Debug` paramètre.

Les applets de commande et les fournisseurs appellent d’abord les méthodes suivantes pour demander confirmation avant de tenter d’effectuer une opération qui modifie un système en dehors de Windows PowerShell :

- [System. Management. Automation. applet de commande. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Pour ce faire, ils appellent la méthode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , qui invite l’utilisateur à confirmer l’opération en fonction de la façon dont l’utilisateur a appelé la commande.

## <a name="see-also"></a>Voir aussi

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
