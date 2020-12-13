---
ms.date: 02/03/2020
ms.topic: reference
title: Importation d’un module PowerShell
description: Importation d’un module PowerShell
ms.openlocfilehash: 688509c0943a9a0289e75b80543f278e16cfedfe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658784"
---
# <a name="importing-a-powershell-module"></a>Importation d’un module PowerShell

Une fois que vous avez installé un module sur un système, vous souhaiterez probablement importer le module. L’importation est le processus qui charge le module dans la mémoire active, afin qu’un utilisateur puisse accéder à ce module dans sa session PowerShell. Dans PowerShell 2,0, vous pouvez importer un module PowerShell nouvellement installé à l’aide d’un appel à l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) . Dans PowerShell 3,0, PowerShell est en mesure d’importer implicitement un module lorsque l’une des fonctions ou applets de commande du module est appelée par un utilisateur. Notez que les deux versions supposent que vous installez votre module à un emplacement où PowerShell peut le trouver. Pour plus d’informations, consultez [installation d’un module PowerShell](./installing-a-powershell-module.md).
Vous pouvez utiliser un manifeste de module pour limiter les parties de votre module qui sont exportées, et vous pouvez utiliser les paramètres de l' `Import-Module` appel pour limiter les parties qui sont importées.

## <a name="importing-a-snap-in-powershell-10"></a>Importation d’un Snap-In (PowerShell 1,0)

Les modules n’existaient pas dans PowerShell 1,0 : vous deviez donc inscrire et utiliser les composants logiciels enfichables. Toutefois, il n’est pas recommandé d’utiliser cette technologie à ce stade, car les modules sont généralement plus faciles à installer et à importer. Pour plus d’informations, consultez [comment créer un composant logiciel enfichable Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importation d’un module avec Import-Module (PowerShell 2,0)

PowerShell 2,0 utilise l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) correctement nommée pour importer des modules. Lorsque cette applet de commande est exécutée, Windows PowerShell recherche le module spécifié dans les répertoires spécifiés dans la `PSModulePath` variable. Lorsque le répertoire spécifié est trouvé, Windows PowerShell recherche les fichiers dans l’ordre suivant : fichiers manifeste de module (. psd1), fichiers de module de script (. psm1), fichiers de module binaire (. dll). Pour plus d’informations sur l’ajout de répertoires à la recherche, consultez [modification du chemin d’installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md).
Le code suivant décrit comment importer un module :

```powershell
Import-Module myModule
```

En supposant que myModule se trouvait dans le `PSModulePath` , PowerShell chargera la mémoire active de MyModule. Si myModule n’a pas été trouvé dans un `PSModulePath` chemin d’accès, vous pouvez toujours indiquer explicitement à PowerShell où le trouver :

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Vous pouvez également utiliser le `-Verbose` paramètre pour identifier ce qui est exporté à partir du module et ce qui est importé dans la mémoire active. Les exportations et les importations restreignent ce qui est exposé à l’utilisateur : la différence est qui contrôle la visibilité. Fondamentalement, les exportations sont contrôlées par le code dans le module. En revanche, les importations sont contrôlées par l' `Import-Module` appel. Pour plus d’informations, consultez **restriction des membres qui sont importés**, ci-dessous.

## <a name="implicitly-importing-a-module-powershell-30"></a>Importation implicite d’un module (PowerShell 3,0)

À partir de Windows PowerShell 3.0, les modules sont importés automatiquement lorsqu’une applet de commande ou une fonction dans le module est utilisée dans une commande. Cette fonctionnalité fonctionne sur n’importe quel module d’un répertoire inclus dans la valeur de la variable d’environnement **PSModulePath** . Toutefois, si vous n’enregistrez pas votre module dans un chemin d’accès valide, vous pouvez toujours le charger à l’aide de l’option [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) explicite, décrite ci-dessus.

Les actions suivantes déclenchent l’importation automatique d’un module, également appelé « chargement automatique de module ».

- Utilisation d’une applet de commande dans une commande. Par exemple, `Get-ExecutionPolicy` la saisie importe le module Microsoft. PowerShell. Security qui contient l’applet de commande `Get-ExecutionPolicy` .

- Utilisation de l’applet de commande [« obtient-Command »](/powershell/module/Microsoft.PowerShell.Core/Get-Command) pour accéder à la commande. Par exemple, en tapant `Get-Command Get-JobTrigger` importe le module **PSScheduledJob** qui contient l’applet de commande `Get-JobTrigger` . Une `Get-Command` commande qui comprend des caractères génériques est considérée comme étant découverte et ne déclenche pas l’importation d’un module.

- Utilisation de l’applet de commande [obtenir-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) pour obtenir de l’aide pour une applet de commande. Par exemple, tapez `Get-Help Get-WinEvent` importe le module Microsoft. PowerShell. Diagnostics qui contient l' `Get-WinEvent` applet de commande.

Pour prendre en charge l’importation automatique de modules, l’applet de commande `Get-Command` obtient toutes les applets de commande et fonctions de tous les modules installés, même si le module n’est pas importé dans la session. Pour plus d’informations, consultez la rubrique d’aide de l’applet de [commande obtenir-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) .

## <a name="the-importing-process"></a>Processus d’importation

Quand un module est importé, un nouvel état de session est créé pour le module et un objet [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) est créé en mémoire. Un état de session est créé pour chaque module importé (y compris le module racine et tous les modules imbriqués). Les membres qui sont exportés à partir du module racine, y compris tous les membres qui ont été exportés dans le module racine par tous les modules imbriqués, sont ensuite importés dans l’état de session de l’appelant.

Les métadonnées des membres exportés à partir d’un module ont une propriété ModuleName. Cette propriété est remplie avec le nom du module qui les a exportés.

> [!WARNING]
> Si le nom d’un membre exporté utilise un verbe non approuvé ou si le nom du membre utilise des caractères restreints, un avertissement s’affiche lors de l’exécution de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .

Par défaut, l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) ne retourne aucun objet au pipeline. Toutefois, l’applet de commande prend en charge un paramètre **PassThru** qui peut être utilisé pour retourner un objet [System. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) pour chaque module importé. Pour envoyer la sortie à l’hôte, les utilisateurs doivent exécuter l’applet de commande [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) .

## <a name="restricting--the-members-that-are-imported"></a>Restriction des membres importés

Quand un module est importé à l’aide de l’applet de commande [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , par défaut, tous les membres de module exportés sont importés dans la session, y compris les commandes exportées dans le module par un module imbriqué. Par défaut, les variables et les alias ne sont pas exportés. Pour restreindre les membres exportés, utilisez un [manifeste de module](./how-to-write-a-powershell-module-manifest.md).
Pour restreindre les membres qui sont importés, utilisez les paramètres suivants de l’applet de commande `Import-Module` .

- **Fonction**: ce paramètre restreint les fonctions exportées. (Si vous utilisez un manifeste de module, consultez la clé FunctionsToExport.)

- `**Applet** de commande : ce paramètre restreint les applets de commande exportées (si vous utilisez un manifeste de module, consultez la clé CmdletsToExport.)

- **Variable**: ce paramètre restreint les variables exportées (si vous utilisez un manifeste de module, consultez la clé VariablesToExport.)

- **Alias**: ce paramètre restreint les alias exportés (si vous utilisez un manifeste de module, consultez la clé AliasesToExport.)

## <a name="see-also"></a>Voir aussi

[Écriture d’un module Windows PowerShell](./writing-a-windows-powershell-module.md)
