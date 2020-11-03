---
description: Fournit une brève introduction à la fonctionnalité PowerShell Workflow.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207210"
---
# <a name="about-workflows"></a>À propos des workflows

## <a name="short-description"></a>Description courte

Fournit une brève introduction à la fonctionnalité PowerShell Workflow.

## <a name="long-description"></a>Description longue

PowerShell Workflow offre les avantages de l' [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) à PowerShell et vous permet d’écrire et d’exécuter des workflows.

PowerShell workflow a été introduit dans PowerShell 3,0 et le module est disponible jusqu’à PowerShell 5,1. Pour plus d’informations sur PowerShell workflow, consultez le [Guide des flux de travail](/previous-versions/powershell/scripting/components/workflows-guide) et l' [écriture d’un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).

## <a name="about-workflows"></a>À propos des workflows

Les flux de travail sont des commandes qui se composent d’une séquence ordonnée d’activités associées. En règle générale, elles s’exécutent pendant une période prolongée, en recueillant des données à partir de centaines d’ordinateurs et en les modifiant, souvent dans des environnements hétérogènes.

Les workflows peuvent être écrits en XAML, le langage utilisé dans Windows Workflow Foundation ou dans le langage PowerShell. Les flux de travail sont généralement empaquetés dans des modules et incluent des rubriques d’aide. Pour plus d’informations, consultez [vue d’ensemble du langage XAML (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

Les flux de travail sont essentiels dans un environnement informatique, car ils peuvent survivre aux redémarrages et à la récupération automatique à partir des défaillances courantes. Vous pouvez vous déconnecter et vous reconnecter des sessions et des ordinateurs qui exécutent des workflows sans interrompre le traitement des flux de travail, et interrompre et reprendre des flux de travail en toute transparence sans perte de données. Chaque activité d’un workflow peut être journalisée et auditée à des fins de référence.
Les workflows peuvent être exécutés en tant que travaux et peuvent être planifiés à l’aide de la fonctionnalité tâches planifiées de PowerShell.

L’État et les données d’un workflow sont enregistrés ou conservés au début et à la fin du workflow et aux points que vous spécifiez. Les points de persistance de workflow fonctionnent comme des instantanés de base de données ou des points de contrôle de programme pour protéger le flux de travail contre les effets des interruptions et des échecs. Si le flux de travail ne parvient pas à effectuer une récupération suite à une défaillance, vous pouvez utiliser les données persistantes et reprendre à partir du dernier point de persistance, au lieu de réexécuter un flux de travail complet depuis le début.

## <a name="workflow-requirements-and-configuration"></a>Configuration requise et configuration du flux de travail

Une configuration de workflow PowerShell se compose des éléments suivants :

- Ordinateur client qui exécute le flux de travail.
- Session de workflow, **PSSession** , sur l’ordinateur client ou sur un ordinateur distant.
- Nœuds gérés, ordinateurs cibles affectés par les activités de flux de travail.

La session de workflow n’est pas obligatoire, mais elle est recommandée. **Sessions PSSession** peut tirer parti des fonctionnalités robustes de récupération et de sessions déconnectées de PowerShell pour récupérer les sessions de workflow déconnectées. Pour plus d’informations, consultez [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)

Étant donné que l’ordinateur client et l’ordinateur sur lequel la session de workflow s’exécute peuvent être des nœuds gérés, vous pouvez exécuter un workflow sur un ordinateur unique qui assume tous les rôles.

L’ordinateur client et l’ordinateur sur lequel la session de workflow s’exécute doivent exécuter PowerShell 3,0. Tous les systèmes éligibles sont pris en charge, y compris les options d’installation minimale des systèmes d’exploitation Windows Server.

Pour exécuter des workflows qui incluent des applets de commande, les nœuds gérés doivent avoir Windows PowerShell 2,0 ou une version ultérieure. Les nœuds gérés ne requièrent pas PowerShell, sauf si le flux de travail comprend des applets de commande. Vous pouvez exécuter des workflows qui incluent des commandes Windows Management Instrumentation (WMI) et Common Information Model (CIM) sur des ordinateurs qui n’ont pas PowerShell.

## <a name="how-to-get-workflows"></a>Comment accéder aux flux de travail

Les flux de travail sont généralement empaquetés dans des modules. Pour importer le module qui comprend un flux de travail, utilisez une commande quelconque dans le module ou utilisez l’applet de commande `Import-Module` .
Les modules sont automatiquement importés lors de la première utilisation d’une commande dans le module.

Pour rechercher les workflows dans les modules installés sur votre ordinateur, utilisez le `Get-Command` paramètre **CommandType** de l’applet de commande.

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a>Comment exécuter des workflows

Pour exécuter un workflow, utilisez la procédure suivante.

1. Si le nœud géré est l’ordinateur local, cette étape n’est pas nécessaire.
   Dans le cas contraire, sur l’ordinateur client, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. Activez la communication à distance PowerShell sur l’ordinateur qui exécute la session de workflow et sur les nœuds gérés affectés par les workflows qui incluent des applets de commande.

   Vous ne devez effectuer cette étape qu’une seule fois sur chaque ordinateur participant.

   Cette étape est requise uniquement lors de l’exécution de flux de travail qui incluent des applets de commande. Vous n’avez pas besoin d’activer la communication à distance sur l’ordinateur client, sauf si la session workflows s’exécute sur l’ordinateur client ou sur des nœuds gérés qui exécutent PowerShell 3,0.

   Pour activer la communication à distance, utilisez l’applet de commande `Enable-PSRemoting` .

   ```powershell
   Enable-PSRemoting -Force
   ```

   Vous pouvez activer la communication à distance à l’aide du paramètre **activer l’exécution du Script** stratégie de groupe. Pour plus d’informations, consultez [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) et [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

1. Utilisez les `New-PSWorkflowSession` `New-PSSession` applets de commande ou pour créer la session de Workflow.

   L' `New-PSWorkflowSession` applet de commande démarre une session qui utilise la configuration de session **Microsoft. PowerShell. Workflow** intégrée sur l’ordinateur de destination. Cette configuration de session comprend des scripts, des fichiers de type et de mise en forme, ainsi que des options conçues pour les flux de travail.

   Ou utilisez l’applet de commande `New-PSSession` . Utilisez le paramètre **ConfigurationName** pour spécifier la configuration de session **Microsoft. PowerShell. Workflow** . Cette commande est identique à l’utilisation de l’applet de commande `New-PSWorkflowSession` .

   Une alternative consiste à utiliser l' `New-PSSession` applet de commande. Utilisez le paramètre **ConfigurationName** pour spécifier la configuration de session **Microsoft. PowerShell. Workflow** .

   Sur l’ordinateur local :

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   Sur un ordinateur distant :

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   Si vous êtes administrateur sur l’ordinateur de la session de workflow, vous pouvez utiliser l' `New-PSWorkflowExecutionOption` applet de commande pour créer des paramètres d’option personnalisés pour la configuration de session de Workflow. Utilisez l' `Set-PSSessionConfiguration` applet de commande pour modifier la configuration de session.

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. Exécutez le workflow dans la session de Workflow. Pour spécifier les noms des nœuds gérés, les ordinateurs cibles, utilisez le paramètre commun de workflow **PSComputerName** .

   Les exemples suivants exécutent le workflow nommé **test-Workflow** .

   Où le nœud géré est l’ordinateur qui héberge la session de workflow :

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   Où les nœuds gérés sont des ordinateurs distants.

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   L’exemple suivant exécute **test-Workflow** sur des centaines d’ordinateurs. L' `Get-Content` applet de commande obtient les noms d’ordinateur à partir d’un fichier texte et les enregistre dans la `$Servers` variable sur l’ordinateur local.

   `Invoke-Command` utilise le `$Using` modificateur de portée pour définir la `$Servers` variable dans la session locale. Pour plus d’informations sur le `$Using` modificateur d’étendue, consultez [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a>Utilisation des paramètres communs de workflow

Les paramètres communs de workflow sont un ensemble de paramètres que PowerShell ajoute automatiquement à tous les flux de travail. PowerShell ajoute les paramètres communs de l’applet de commande à tous les flux de travail, même si le workflow n’utilise pas l’attribut **CmdletBinding** .

Par exemple, le workflow suivant ne définit aucun paramètre. Toutefois, lorsque vous exécutez le workflow, il a à la fois les types **paramètres_courants** et **WorkflowCommonParameters** .

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

Les paramètres communs de workflow incluent plusieurs paramètres qui sont essentiels à l’exécution de flux de travail. Par exemple, le paramètre commun **PSComputerName** spécifie les nœuds gérés affectés par le flux de travail.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

Le paramètre commun de workflow **PSPersist** détermine le moment où les données de workflow sont conservées. Elle vous permet d’ajouter un point de persistance entre les activités aux flux de travail qui ne définissent pas de points de persistance.

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

D’autres paramètres communs de workflow vous permettent de spécifier les caractéristiques de la connexion à distance aux nœuds gérés. Leurs noms et leurs fonctionnalités sont similaires aux paramètres des applets de commande de communication à distance, y compris `Invoke-Command` .

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

Veillez à distinguer les paramètres de communication à distance qui définissent la connexion pour la session de workflow des paramètres communs de flux de travail du **préfixe PS** qui définissent la connexion aux nœuds gérés.

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

Certains paramètres communs de workflow sont propres aux workflows, tels que le paramètre **PSParameterCollection** qui vous permet de spécifier des valeurs de paramètres communes de workflow différentes pour différents nœuds distants. Pour obtenir une liste et une description des paramètres communs de workflow, consultez [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).

## <a name="see-also"></a>Voir aussi

[Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

Applets de commande [PSWorkflow](xref:PSWorkflow)

[Guide des workflows](/previous-versions/powershell/scripting/components/workflows-guide)

[Écriture d'un workflow Windows PowerShell](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
