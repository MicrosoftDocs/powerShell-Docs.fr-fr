---
description: Décrit les composants logiciels enfichables Windows PowerShell et explique comment les utiliser et les gérer.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: 494b3275e4fe8a3aacdc358317950542962957cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388890"
---
# <a name="about-pssnapins"></a>À propos de PSSnapins

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les composants logiciels enfichables Windows PowerShell et explique comment les utiliser et les gérer.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Un composant logiciel enfichable Windows PowerShell est un assembly d’infrastructure Microsoft .NET qui contient des fournisseurs et des applets de commande Windows PowerShell \/ . Windows PowerShell comprend un ensemble de composants logiciels enfichables de base, mais vous pouvez étendre la puissance et la valeur de Windows PowerShell en ajoutant des composants logiciels enfichables qui contiennent des fournisseurs et des applets de commande que vous créez ou récupérez d’autres.

Lorsque vous ajoutez un composant logiciel enfichable, les applets de commande et les fournisseurs qu’il contient sont immédiatement disponibles pour une utilisation dans la session active, mais la modification affecte uniquement la session active.

Pour ajouter le composant logiciel enfichable à toutes les sessions ultérieures, enregistrez-le dans votre profil Windows PowerShell. Vous pouvez également utiliser l’applet de commande Export-Console pour enregistrer les noms des composants logiciels enfichables dans un fichier de console, puis les utiliser dans les sessions ultérieures. Vous pouvez même enregistrer plusieurs fichiers de console, chacun avec un ensemble différent de composants logiciels enfichables.

Remarque : les composants logiciels enfichables Windows PowerShell (PSSnapins) peuvent être utilisés dans Windows PowerShell 3,0 et Windows PowerShell 2,0. Ils peuvent être modifiés ou non disponibles dans les versions ultérieures. Pour empaqueter les fournisseurs et applets de commande de Windows PowerShell, utilisez des modules. Pour plus d’informations sur la création de modules et la conversion de composants logiciels enfichables en modules, consultez [écriture d’un module Windows PowerShell](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

### <a name="finding-snap-ins"></a>RECHERCHE DE COMPOSANTS LOGICIELS ENFICHABLES

Pour obtenir la liste des composants logiciels enfichables Windows PowerShell sur votre ordinateur, tapez :

```powershell
Get-PSSnapin
```

Pour obtenir le composant logiciel enfichable pour chaque fournisseur Windows PowerShell, tapez :

```powershell
Get-PSProvider | Format-List name, pssnapin
```

Pour obtenir la liste des applets de commande dans un composant logiciel enfichable Windows PowerShell, tapez :

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a>INSTALLATION D’UN COMPOSANT LOGICIEL ENFICHABLE

Les composants logiciels enfichables intégrés sont enregistrés dans le système et ajoutés à la session par défaut lorsque vous démarrez Windows PowerShell. Toutefois, vous devez inscrire les composants logiciels enfichables que vous créez ou obtenez à partir d’autres, puis ajouter les composants logiciels enfichables à votre session.

### <a name="registering-a-snap-in"></a>INSCRIPTION D’UN COMPOSANT LOGICIEL ENFICHABLE

Un composant logiciel enfichable Windows PowerShell est un programme écrit dans un langage de .NET Framework qui est compilé dans un fichier. dll. Pour utiliser les fournisseurs et les applets de commande dans un composant logiciel enfichable, vous devez d’abord inscrire le composant logiciel enfichable (l’ajouter au registre).

La plupart des composants logiciels enfichables incluent un programme d’installation (un fichier. exe ou. msi) qui enregistre le fichier. dll pour vous. Toutefois, si vous recevez un composant logiciel enfichable sous la forme d’un fichier. dll, vous pouvez l’inscrire sur votre système. Pour plus d’informations, consultez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

Pour obtenir tous les composants logiciels enfichables inscrits sur votre système ou pour vérifier qu’un composant logiciel enfichable est inscrit, tapez :

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a>AJOUT DU COMPOSANT LOGICIEL ENFICHABLE À LA SESSION ACTIVE

Pour ajouter un composant logiciel enfichable inscrit à la session active, utilisez l’applet de commande Add-PsSnapin. Par exemple, pour ajouter le composant logiciel enfichable Microsoft SQL Server à la session, tapez :

```powershell
Add-PSSnapin sql
```

Une fois la commande terminée, les fournisseurs et les applets de commande du composant logiciel enfichable sont disponibles dans la session. Toutefois, elles ne sont disponibles que dans la session active, sauf si vous les enregistrez.

### <a name="saving-the-snap-ins"></a>ENREGISTREMENT DES COMPOSANTS LOGICIELS ENFICHABLES

Pour utiliser un composant logiciel enfichable dans de futures sessions Windows PowerShell, ajoutez la commande Add-PsSnapin à votre profil Windows PowerShell. Ou, exportez les noms des composants logiciels enfichables dans un fichier de console.

Si vous ajoutez la commande Add-PSSnapin à votre profil, elle est disponible dans toutes les futures sessions Windows PowerShell. Si vous exportez les noms des composants logiciels enfichables dans votre session, vous pouvez utiliser le fichier d’exportation uniquement lorsque vous avez besoin des composants logiciels enfichables.

Pour ajouter la commande Add-PsSnapin à votre profil Windows PowerShell, ouvrez votre profil, collez ou tapez la commande, puis enregistrez le profil. Pour plus d'informations, consultez about_Providers.

Pour enregistrer les composants logiciels enfichables à partir d’une session dans le fichier de console (. psc1), utilisez l’applet de commande Export-Console. Par exemple, pour enregistrer les composants logiciels enfichables dans la configuration de session active dans le fichier NewConsole. psc1 dans le répertoire actif, tapez :

```powershell
Export-Console NewConsole
```

Pour plus d’informations, consultez Export-Console.

### <a name="opening-windows-powershell-with-a-console-file"></a>OUVERTURE DE WINDOWS POWERSHELL AVEC UN FICHIER DE CONSOLE

Pour utiliser un fichier de console qui comprend le composant logiciel enfichable, démarrez Windows PowerShell (PowerShell.exe) à partir de l’invite de commandes dans Cmd.exe ou dans une autre session Windows PowerShell. Utilisez le paramètre PsConsoleFile pour spécifier le fichier de console qui contient le composant logiciel enfichable. Par exemple, la commande suivante démarre Windows PowerShell avec le fichier de console NewConsole. psc1 :

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

Les fournisseurs et les applets de commande du composant logiciel enfichable peuvent désormais être utilisés dans la session.

### <a name="removing-a-snap-in"></a>SUPPRESSION D’UN COMPOSANT LOGICIEL ENFICHABLE

Pour supprimer un composant logiciel enfichable Windows PowerShell de la session active, utilisez l’applet de commande Remove-PsSnapin. Par exemple, pour supprimer le composant logiciel enfichable SQL Server de la session active, tapez :

```powershell
Remove-PSSnapin sql
```

Cette applet de commande supprime le composant logiciel enfichable de la session. Le composant logiciel enfichable est toujours chargé, mais les fournisseurs et les applets de commande qu’il prend en charge ne sont plus disponibles.

### <a name="built-in-commands"></a>COMMANDES INTÉGRÉES

Dans Windows PowerShell 2,0 et dans les anciens programmes hôtes de Windows PowerShell 3,0 et versions ultérieures, les commandes intégrées qui sont installées avec Windows PowerShell sont empaquetées dans des composants logiciels enfichables qui sont ajoutés automatiquement à chaque session Windows PowerShell.

À compter de Windows PowerShell 3,0, dans les programmes hôtes de style plus récents, ceux qui démarrent des sessions à l’aide de la méthode InitialSessionState. CreateDefault2, les commandes intégrées sont empaquetées dans des modules. L’exception est Microsoft. PowerShell. Core, qui apparaît toujours comme un composant logiciel enfichable. Le composant logiciel enfichable principal est inclus dans chaque session par défaut. Les modules intégrés sont chargés automatiquement lors de la première utilisation.

Remarque : les sessions à distance, y compris les sessions qui sont démarrées à l’aide de l’applet de commande New-PSSession, sont des sessions de style plus anciennes dans lesquelles les commandes intégrées sont empaquetées dans des composants logiciels enfichables.

Les composants logiciels enfichables (ou modules) suivants sont installés avec Windows PowerShell.

- Microsoft. PowerShell. Core : contient les fournisseurs et les applets de commande utilisés pour gérer les fonctionnalités de base de Windows PowerShell. Il comprend le système de fichiers, le registre, les alias, l’environnement, la fonction et les fournisseurs de variables, ainsi que les applets de commande de base, telles que obtenir-aide, obtenir-commande et obtenir l’historique.

- Microsoft. PowerShell. Host-contient des applets de commande utilisées par l’hôte Windows PowerShell, telles que Start-Transcript et Stop-Transcript.

- Microsoft. PowerShell. Management : contient des applets de commande, telles que Get-Service et Get-ChildItem, qui sont utilisées pour gérer les fonctionnalités Windows.

- Microsoft. PowerShell. Security : contient le fournisseur de certificats et les applets de commande utilisés pour gérer la sécurité Windows PowerShell, tels que l’applet de commande, l’applet de commande, l’applet de commande, l’applet de commande et le contrôle ConvertTo-SecureString.

- Microsoft. PowerShell. Utility-contient des applets de commande qui permettent de manipuler des objets et des données, tels que l’applet de commande, l’accès en écriture et la liste de formats.

- Microsoft. WSMan. Management : contient le fournisseur WSMan et les applets de commande qui gèrent le service Windows Remote Management, comme Connect-WSMan et Enable-WSManCredSSP.

## <a name="logging-snap-in-events"></a>ÉVÉNEMENTS DU COMPOSANT LOGICIEL ENFICHABLE JOURNALISATION

À compter de Windows PowerShell 3,0, vous pouvez enregistrer les événements d’exécution des applets de commande dans les modules et les composants logiciels enfichables Windows PowerShell en affectant la valeur TRUE à la propriété LogPipelineExecutionDetails des modules et des composants logiciels enfichables. Pour plus d’informations, consultez [about_EventLogs](about_EventLogs.md).

## <a name="see-also"></a>VOIR AUSSI

[Add-PsSnapin](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[Obtient-PsSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[Remove-PsSnapin](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[Export-Console](xref:Microsoft.PowerShell.Core.Export-Console)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[about_Profiles](about_Profiles.md)

[about_Modules](about_Modules.md)

## <a name="keywords"></a>MOT

about_Snapins, about_Snap_ins, about_Snap-ins
