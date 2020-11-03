---
description: Décrit comment les fonctions qui spécifient l' `CmdletBinding` attribut peuvent utiliser les méthodes et les propriétés disponibles pour les applets de commande compilées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 3dc5118076436ddb7fface16caa01bf4fcdec257
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207097"
---
# <a name="about-functions-advanced-methods"></a>À propos des méthodes avancées des fonctions

## <a name="short-description"></a>Description courte

Décrit comment les fonctions qui spécifient l' `CmdletBinding` attribut peuvent utiliser les méthodes et les propriétés disponibles pour les applets de commande compilées.

## <a name="long-description"></a>Description longue

Les fonctions qui spécifient l' `CmdletBinding` attribut peuvent accéder à un certain nombre de méthodes et de propriétés via la `$PSCmdlet` variable. Ces méthodes incluent les méthodes suivantes :

- Les méthodes de traitement d’entrée utilisées par les applets de commande pour effectuer leur travail.
- `ShouldProcess`Méthodes et `ShouldContinue` utilisées pour obtenir des commentaires de la part de l’utilisateur avant l’exécution d’une action.
- `ThrowTerminatingError`Méthode permettant de générer des enregistrements d’erreurs.
- Plusieurs `Write` méthodes qui retournent des types de sortie différents.

Toutes les méthodes et propriétés de la classe **PSCmdlet** sont disponibles pour les fonctions avancées. Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).

Pour plus d’informations sur l' `CmdletBinding` attribut, consultez [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).
Pour la classe **CmdletBindingAttribute** , consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdletbindingattribute)de commande. CmdletBindingAttribute.

### <a name="input-processing-methods"></a>Méthodes de traitement d’entrée

Les méthodes décrites dans cette section sont appelées méthodes de traitement d’entrée. Pour les fonctions, ces trois méthodes sont représentées par les `Begin` `Process` blocs, et `End` de la fonction. Vous n’êtes pas obligé d’utiliser ces blocs dans vos fonctions.

> [!NOTE]
> Ces blocs sont également disponibles pour les fonctions qui n’utilisent pas l' `CmdletBinding` attribut.

#### <a name="begin"></a>Début

Ce bloc est utilisé pour fournir un prétraitement unique facultatif pour la fonction.
Le runtime PowerShell utilise le code de ce bloc une fois pour chaque instance de la fonction dans le pipeline.

#### <a name="process"></a>Process

Ce bloc est utilisé pour fournir un traitement d’enregistrement par enregistrement pour la fonction. Vous pouvez utiliser un `Process` bloc sans définir les autres blocs. Le nombre d' `Process` exécutions de bloc dépend de la façon dont vous utilisez la fonction et de l’entrée que la fonction reçoit.

La variable automatique `$_` ou `$PSItem` contient l’objet actuel dans le pipeline à utiliser dans le `Process` bloc. La `$input` variable automatique contient un énumérateur qui est uniquement disponible pour les fonctions et les blocs de script.
Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

- L’appel de la fonction au début, ou à l’extérieur d’un pipeline, exécute le `Process` bloc une fois.
- Dans un pipeline, le `Process` bloc s’exécute une fois pour chaque objet d’entrée qui atteint la fonction.
- Si l’entrée de pipeline qui atteint la fonction est vide, le `Process` bloc ne s’exécute **pas** .
  - Les `Begin` `End` blocs et s’exécutent toujours.

> [!IMPORTANT]
> Si un paramètre de fonction est défini pour accepter l’entrée de pipeline et qu’un `Process` bloc n’est pas défini, le traitement d’enregistrement par enregistrement échoue. Dans ce cas, votre fonction ne s’exécutera qu’une seule fois, quelle que soit l’entrée.

#### <a name="end"></a>End

Ce bloc est utilisé pour fournir un traitement unique facultatif pour la fonction.

L’exemple suivant montre le plan d’une fonction qui contient un bloc pour le prétraitement à usage `Begin` unique, un `Process` bloc pour le traitement des enregistrements multiples et un `End` bloc pour le traitement unique à la fois.

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> `Begin`Si vous utilisez un `End` bloc ou, vous devez définir les trois blocs. Lorsque vous utilisez les trois blocs, tout le code PowerShell doit se trouver à l’intérieur de l’un des blocs.

### <a name="confirmation-methods"></a>Méthodes de confirmation

#### <a name="shouldprocess"></a>ShouldProcess

Cette méthode est appelée pour demander la confirmation de l’utilisateur avant que la fonction exécute une action qui modifie le système. La fonction peut continuer en fonction de la valeur booléenne retournée par la méthode. Cette méthode ne peut être appelée qu’à partir du `Process{}` bloc de la fonction. L' `CmdletBinding` attribut doit également déclarer que la fonction prend en charge `ShouldProcess` (comme indiqué dans l’exemple précédent).

Pour plus d’informations sur cette méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.shouldprocess)de commande. ShouldProcess.

Pour plus d’informations sur la demande de confirmation, consultez [demande de confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).

#### <a name="shouldcontinue"></a>ShouldContinue

Cette méthode est appelée pour demander un deuxième message de confirmation. Elle doit être appelée lorsque la `ShouldProcess` méthode retourne `$true` . Pour plus d’informations sur cette méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)de commande. ShouldContinue.

### <a name="error-methods"></a>Méthodes d’erreur

Les fonctions peuvent appeler deux méthodes différentes lorsque des erreurs se produisent. Lorsqu’une erreur sans fin d’exécution se produit, la fonction doit appeler la `WriteError` méthode, qui est décrite dans la `Write` section Méthodes. Lorsqu’une erreur se termine et que la fonction ne peut pas continuer, elle doit appeler la `ThrowTerminatingError` méthode. Vous pouvez également utiliser l' `Throw` instruction pour les erreurs de fin et l’applet de commande [write-error](xref:Microsoft.PowerShell.Utility.Write-Error) pour les erreurs sans fin d’arrêt.

Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)de commande. ThrowTerminatingError.

### <a name="write-methods"></a>Méthodes d’écriture

Une fonction peut appeler les méthodes suivantes pour retourner différents types de sortie.
Notez que tous les résultats ne sont pas transmis à la commande suivante dans le pipeline. Vous pouvez également utiliser les différentes `Write` applets de commande, telles que `Write-Error` .

#### <a name="writecommanddetail"></a>WriteCommandDetail

Pour plus d’informations sur la `WriteCommandDetails` méthode, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)de commande. WriteCommandDetail.

#### <a name="writedebug"></a>WriteDebug

Pour fournir des informations qui peuvent être utilisées pour résoudre les problèmes d’une fonction, faites en sorte que la fonction appelle la `WriteDebug` méthode. La `WriteDebug` méthode affiche des messages de débogage à l’utilisateur. Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writedebug)de commande. WriteDebug.

#### <a name="writeerror"></a>WriteError

Les fonctions doivent appeler cette méthode lorsque des erreurs sans fin d’exécution se produisent et que la fonction est conçue pour poursuivre le traitement des enregistrements. Pour plus d’informations, consultez [System. Management. Automation. applet](/dotnet/api/system.management.automation.cmdlet.writeerror)de commande. WriteError.

> [!NOTE]
> Si une erreur se termine, la fonction doit appeler la méthode [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) .

#### <a name="writeobject"></a>WriteObject

La `WriteObject` méthode permet à la fonction d’envoyer un objet à la commande suivante dans le pipeline. Dans la plupart des cas, `WriteObject` est la méthode à utiliser lorsque la fonction retourne des données. Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).

#### <a name="writeprogress"></a>WriteProgress

Pour les fonctions avec des actions dont l’exécution prend beaucoup de temps, cette méthode permet à la fonction d’appeler la `WriteProgress` méthode afin d’afficher les informations de progression. Par exemple, vous pouvez afficher le pourcentage effectué.
Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).

#### <a name="writeverbose"></a>WriteVerbose

Pour fournir des informations détaillées sur ce que fait la fonction, faites en sorte que la fonction appelle la `WriteVerbose` méthode pour afficher des messages détaillés à l’utilisateur. Par défaut, les messages détaillés ne sont pas affichés. Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).

#### <a name="writewarning"></a>WriteWarning

Pour fournir des informations sur les conditions qui peuvent entraîner des résultats inattendus, faites en sorte que la fonction appelle la méthode WriteWarning pour afficher des messages d’avertissement à l’utilisateur. Par défaut, les messages d’avertissement s’affichent. Pour plus d’informations, consultez [System. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).

> [!NOTE]
> Vous pouvez également afficher des messages d’avertissement en configurant la `$WarningPreference` variable ou à l’aide des `Verbose` options de ligne de commande et `Debug` . Pour plus d’informations sur la `$WarningPreference` variable, consultez [about_Preference_Variables](about_Preference_Variables.md).

### <a name="other-methods-and-properties"></a>Autres méthodes et propriétés

Pour plus d’informations sur les autres méthodes et propriétés accessibles via la `$PSCmdlet` variable, consultez [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).

Par exemple, la propriété [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) vous permet de voir le jeu de paramètres en cours d’utilisation. Les jeux de paramètres vous permettent de créer une fonction qui exécute différentes tâches en fonction des paramètres spécifiés lors de l’exécution de la fonction.

## <a name="see-also"></a>Voir aussi

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)
