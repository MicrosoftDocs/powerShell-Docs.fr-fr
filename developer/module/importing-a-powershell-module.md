---
title: Importation d’un Module PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854055"
---
# <a name="importing-a-powershell-module"></a>Importation d’un module PowerShell

Une fois votre avez installé un module sur un système, vous pouvez importer le module. L’importation d’est le processus qui charge le module dans la mémoire active, afin qu’un utilisateur puisse accéder à ce module dans leur session PowerShell. Dans PowerShell 2.0, vous pouvez importer un module PowerShell qui vient d’être installé avec un appel à [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande. Dans PowerShell 3.0, PowerShell est en mesure d’importer implicitement un module lorsque l’une des fonctions ou des applets de commande dans le module est appelée par un utilisateur. Notez que les deux versions supposent que vous installez votre module dans un emplacement où PowerShell peut s’avérer ; Pour plus d’informations, consultez [installation d’un PowerShell Module](./installing-a-powershell-module.md). Un manifeste de module permet de restreindre les parties de votre module sont exportées, et vous pouvez utiliser les paramètres de la `Import-Module` appel pour restreindre les parties sont importés.

## <a name="importing-a-snap-in-powershell-10"></a>Importation d’un composant logiciel enfichable (PowerShell 1.0)

Modules n’existait pas dans PowerShell 1.0 : au lieu de cela, vous deviez enregistrer et utiliser des composants logiciel enfichables. Toutefois, il est déconseillé que vous utilisez cette technologie à ce stade, comme les modules sont généralement plus faciles à installer et importer. Pour plus d’informations, consultez [comment créer un Windows PowerShell Snap-in](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importation d’un Module avec Import-Module (PowerShell 2.0)

PowerShell 2.0 utilise le nommé de manière adéquate [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande pour importer des modules. Lors de l’exécution de cette applet de commande, Windows PowerShell recherche le module spécifié dans les répertoires spécifiés dans le `PSModulePath` variable. Lorsque le répertoire spécifié est trouvé, Windows PowerShell recherche les fichiers dans l’ordre suivant : fichiers de manifeste de module (.psd1), fichiers de script module (.psm1), fichiers de module binaire (.dll). Pour plus d’informations sur l’ajout de répertoires à la recherche, consultez [modifier le chemin d’Installation de PSModulePath](./modifying-the-psmodulepath-installation-path.md). Le code suivant explique comment importer un module :

```powershell
Import-Module myModule
```

En supposant que myModule était située dans le `PSModulePath`, PowerShell chargerait myModule dans la mémoire active. Si myModule n’était pas situé sur un `PSModulePath` chemin d’accès, vous pouvez toujours explicitement demander PowerShell où les trouver :

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Vous pouvez également utiliser le paramètre - verbose pour identifier ce qui est en cours d’exportation hors du module, et ce qui est en cours d’importation dans la mémoire active. Exportations et importations limiter ce qui est exposé à l’utilisateur : la différence est qui contrôle la visibilité. Pour l’essentiel, les exportations sont contrôlées par le code dans le module. En revanche, les importations sont contrôlées par le `Import-Module` appeler. Pour plus d’informations, consultez **limitant les membres que sont importés**, ci-dessous.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implicitement l’importation d’un Module (PowerShell 3.0)

Modules à compter de Windows PowerShell 3.0, sont importés automatiquement lorsqu’une applet de commande ou une fonction dans le module est utilisée dans une commande. Cette fonctionnalité fonctionne sur n’importe quel module dans un répertoire inclus dans la valeur de la **PSModulePath** variable d’environnement. Si vous n’enregistrez pas toutefois de votre module sur un chemin d’accès valide, vous pouvez toujours charger à l’aide de la commande explicite [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) option, décrite ci-dessus.

Les actions suivantes déclenchent l’importation automatique d’un module, également appelé « module de chargement automatique. »

- À l’aide d’une applet de commande dans une commande. Par exemple, si vous saisissez `Get-ExecutionPolicy` importe le module Microsoft.PowerShell.Security qui contient le `Get-ExecutionPolicy` applet de commande.

- À l’aide de la [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) pour obtenir la commande.  Par exemple, si vous saisissez `Get-Command Get-JobTrigger` importe le **PSScheduledJob** module qui contient le `Get-JobTrigger` applet de commande. Un `Get-Command` commande qui inclut des caractères génériques est considéré comme étant la découverte et ne déclenche pas l’importation d’un module.

- À l’aide de la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) applet de commande pour obtenir de l’aide pour une applet de commande. Par exemple, si vous saisissez `Get-Help Get-WinEvent` importe le module Microsoft.PowerShell.Diagnostics qui contient le `Get-WinEvent` applet de commande.

Pour prendre en charge l’importation automatique des modules, la `Get-Command` applet de commande Obtient toutes les applets de commande et fonctions dans tous les modules installés, même si le module n’est pas importé dans la session. Pour plus d’informations, consultez la rubrique d’aide pour le [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) applet de commande.

## <a name="the-importing-process"></a>Le processus d’importation

Lorsqu’un module est importé, un état de nouvelle session est créé pour le module et un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objet est créé en mémoire. Un état de session est créé pour chaque module est importé (Cela inclut le module racine et tous les modules imbriqués). Les membres qui sont exportés à partir du module racine, y compris tous les membres qui ont été exportées vers le module racine par tous les modules imbriqués, sont ensuite importés dans l’état de session de l’appelant.

Les métadonnées des membres qui sont exportés à partir d’un module ont une propriété de nom du module. Cette propriété est remplie avec le nom du module qui les exporté.

> [!WARNING]
> Si le nom d’un membre exporté utilise un verbe non approuvé ou si le nom du membre utilise des caractères interdits, un avertissement s’affiche lorsque le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande est exécutée.

Par défaut, le [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande ne retourne pas d’objets dans le pipeline. Toutefois, l’applet de commande prend en charge un `PassThru` paramètre qui peut être utilisée pour retourner un [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objet pour chaque module est importé. Pour envoyer la sortie à l’hôte, les utilisateurs doivent exécuter la [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) applet de commande.

## <a name="restricting--the-members-that-are-imported"></a>Limiter les membres qui sont importés

Lorsqu’un module est importé à l’aide de la [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) applet de commande, par défaut, tous les modules exportés membres sont importés dans la session, y compris toutes les commandes exportées vers le module par un module imbriqué. Par défaut, les variables et les alias ne sont pas exportés. Pour limiter les membres qui sont exportées, utilisez un [manifeste de module](./how-to-write-a-powershell-module-manifest.md). Pour restreindre les membres qui sont importés, utilisez les paramètres suivants de la `Import-Module` applet de commande.

- `Function` : Ce paramètre limite les fonctions qui sont exportées. (Si vous utilisez un manifeste de module, consultez la clé de FunctionsToExport.)

- `Cmdlet` : Ce paramètre limite les applets de commande qui sont exportés (si vous utilisez un manifeste, voir module la clé de CmdletsToExport.)

- `Variable` : Ce paramètre limite les variables qui sont exportés (si vous utilisez un manifeste, voir module la clé VariablesToExport.)

- `Alias` : Ce paramètre limite les alias qui sont exportés (si vous utilisez un manifeste, voir module la clé AliasesToExport.)

## <a name="see-also"></a>Voir aussi

[Écrire un Module PowerShell de Windows](./writing-a-windows-powershell-module.md)
