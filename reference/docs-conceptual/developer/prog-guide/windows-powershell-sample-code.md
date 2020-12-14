---
ms.date: 09/13/2016
ms.topic: reference
title: Exemple de code Windows PowerShell
description: Exemple de code Windows PowerShell
ms.openlocfilehash: da916fa3557f44ecc9126ecef38235109aa391ec
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390131"
---
# <a name="windows-powershell-sample-code"></a>Exemple de code Windows PowerShell

&reg;Les exemples Windows PowerShell sont disponibles via le SDK Windows. Cette section contient l’exemple de code contenu dans les exemples de SDK Windows.

> [!NOTE]
> Lorsque le SDK Windows est installé, un répertoire d' **exemples** est créé dans lequel tous les exemples Windows PowerShell sont disponibles. Le répertoire d’installation par défaut est **C:\Program Files\Microsoft SDKs\Windows\v6.0**. Démarrez Windows PowerShell et tapez **« CD Samples\SysMgmt\PowerShell »** pour rechercher le répertoire d’exemples Windows PowerShell. Dans ce document, le répertoire des exemples Windows PowerShell est appelé **\<PowerShell Samples>** .

## <a name="sample-code-listing"></a>Exemple de liste de code

|                                    Exemple de code                                    |                                                                                                                                           Description                                                                                                                                           |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Exemple de code AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).                                                                                                                                                            |
| [Exemple de code AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).                                                                                                                                                            |
| [Exemple de code AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur d’éléments Windows PowerShell](./creating-a-windows-powershell-item-provider.md).                                                                                                                                                              |
| [Exemple de code AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).                                                                                                                                                    |
| [Exemple de code AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur de navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).                                                                                                                                                  |
| [Exemple de code AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md) | Il s’agit du fournisseur décrit dans [création d’un fournisseur de contenu Windows PowerShell](./creating-a-windows-powershell-content-provider.md).                                                                                                                                                        |
| [Exemples de code GetProc01](./getproc01-code-samples.md)                             | Il s’agit de l' `Get-Process` exemple d’applet de commande de base décrit dans [création de votre première applet](../cmdlet/creating-a-cmdlet-without-parameters.md)de commande.                                                                                                                                                     |
| [Exemples de code GetProc02](./getproc02-code-samples.md)                             | Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de paramètres qui traitent Command-Line entrée](../cmdlet/adding-parameters-that-process-command-line-input.md).                                                                                                                       |
| [Exemples de code GetProc03](./getproc03-code-samples.md)                             | Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de paramètres qui traitent l’entrée de pipeline](../cmdlet/adding-parameters-that-process-pipeline-input.md).                                                                                                                               |
| [Exemples de code GetProc04](./getproc04-code-samples.md)                             | Il s’agit de l' `Get-Process` exemple d’applet de commande décrit dans [Ajout de rapports d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande.                                                                                                                |
| [Exemples de code GetProc05](./getproc05-code-samples.md)                             | Cette `Get-Process` applet de commande est similaire à l’applet de commande décrite dans [Ajout d’un rapport d’erreurs de non-terminaison à votre applet de](../cmdlet/adding-non-terminating-error-reporting-to-your-cmdlet.md)commande.                                                                                                     |
| [Exemples de code StopProc01](./stopproc01-code-samples.md)                           | Il s’agit de l' `Stop-Process` exemple d’applet de commande décrit dans [création d’une applet de commande qui modifie le système](../cmdlet/creating-a-cmdlet-that-modifies-the-system.md).                                                                                                                                    |
| [Exemples de code StopProcessSample04](./stopprocesssample04-code-samples.md)         | Il s’agit de l' `Stop-Process` exemple d’applet de commande décrit dans [Ajout de jeux de paramètres à une applet de](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)commande.                                                                                                                                                      |
| [Exemples de code Runspace01](./runspace01-code-samples.md)                           | Voici les exemples de code pour l’instance d’exécution décrite dans [création d’une application console qui exécute une commande spécifiée](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).                                                                                      |
| [Exemples de code Runspace02](./runspace02-code-samples.md)                           | Cet exemple utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter l’applet de commande de `Get-Process` façon synchrone.                                                                                                            |
| [Exemples de code RunSpace03](./runspace03-code-samples.md)                           | Voici les exemples de code pour l’instance d’exécution décrite dans « création d’une application console qui exécute un script spécifié ».                                                                                                                                                                         |
| [Exemples de code RunSpace04](./runspace04-code-samples.md)                           | Il s’agit d’un exemple de code pour une instance d’exécution qui utilise la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) pour exécuter un script qui génère une erreur avec fin d’exécution.                                                                         |
| [Exemple de code RunSpace05](./runspace05-code-sample.md)                             |                                                                                                            |
| [Exemple de code RunSpace06](./runspace06-code-sample.md)                             |                                                                                                     |
| [Exemple de code RunSpace07](./runspace07-code-sample.md)                             |                                                                                               |
| [Exemple de code RunSpace08](./runspace08-code-sample.md)                             |                                                                                              |
| [Exemple de code RunSpace09](./runspace09-code-sample.md)                             |                                                                                       |
| [Exemple de code RunSpace10](./runspace10-code-sample.md)                             | Il s’agit du code source de l’exemple Runspace10, qui ajoute une applet de commande à [System. Management. Automation. instances d’exécution. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) , puis utilise les informations de configuration modifiées pour créer l’instance d’exécution. |

## <a name="see-also"></a>Voir aussi

[Guide de programmation pour Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
