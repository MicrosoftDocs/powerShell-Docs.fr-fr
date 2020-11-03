---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: a221c6126bbbf22dffb493828f759bcbd4cfe759
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "93205817"
---
# Start-Process

## SYNOPSIS
Démarre un ou plusieurs processus sur l'ordinateur local.

## SYNTAX

### Valeur par défaut (par défaut)

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UseShellExecute

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Start-Process` applet de commande démarre un ou plusieurs processus sur l’ordinateur local. Par défaut, `Start-Process` crée un nouveau processus qui hérite de toutes les variables d’environnement définies dans le processus actuel.

Pour spécifier le programme qui s'exécute dans le processus, entrez un fichier exécutable, un fichier de script ou un fichier qui peut s'ouvrir à l'aide d'un programme sur l'ordinateur. Si vous spécifiez un fichier non exécutable, `Start-Process` démarre le programme associé au fichier, similaire à l’applet de commande `Invoke-Item` .

Vous pouvez utiliser les paramètres de `Start-Process` pour spécifier des options, telles que le chargement d’un profil utilisateur, le démarrage du processus dans une nouvelle fenêtre ou l’utilisation d’autres informations d’identification.

## EXEMPLES

### Exemple 1 : démarrer un processus qui utilise des valeurs par défaut

Cet exemple démarre un processus qui utilise le `Sort.exe` fichier dans le dossier actif. La commande utilise toutes les valeurs par défaut, y compris le style de fenêtre par défaut, le dossier de travail et les informations d’identification.

```powershell
Start-Process -FilePath "sort.exe"
```

### Exemple 2 : imprimer un fichier texte

Cet exemple démarre un processus qui imprime le `C:\PS-Test\MyFile.txt` fichier.

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### Exemple 3 : démarrer un processus pour trier des éléments dans un nouveau fichier

Cet exemple démarre un processus qui trie des éléments dans le `Testsort.txt` fichier et retourne les éléments triés dans les `Sorted.txt` fichiers. Toutes les erreurs sont écrites dans le `SortError.txt` fichier.

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

Le paramètre **UseNewEnvironment** spécifie que le processus s’exécute avec ses propres variables d’environnement.

### Exemple 4 : démarrer un processus dans une fenêtre agrandie

Cet exemple démarre le `Notepad.exe` processus. Elle agrandit la fenêtre et la conserve tant que l'exécution du processus n'est pas terminée.

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### Exemple 5 : Démarrer PowerShell en tant qu’administrateur

Cet exemple démarre PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### Exemple 6 : utilisation de différents verbes pour démarrer un processus

Cet exemple montre comment trouver les verbes qui peuvent être utilisés lors du démarrage d’un processus. Les verbes disponibles sont déterminés par l’extension de nom de fichier du fichier qui s’exécute dans le processus.

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

L’exemple utilise `New-Object` pour créer un objet **System. Diagnostics. ProcessStartInfo** pour **PowerShell.exe** , le fichier qui s’exécute dans le processus PowerShell. La propriété **Verbs** de l’objet **ProcessStartInfo** montre que vous pouvez utiliser les verbes **Open** et **runas** avec `PowerShell.exe` , ou avec n’importe quel processus qui exécute un `.exe` fichier.

### Exemple 7 : spécification d’arguments pour le processus

Les deux commandes démarrent l’interpréteur de commandes Windows, en émettant une `dir` commande sur le `Program Files` dossier. Étant donné que ce NomDossier contient un espace, la valeur doit être entourée de guillemets avec séquence d’échappement.
Notez que la première commande spécifie une chaîne en tant que **argumentlist** . La deuxième commande est un tableau de chaînes.

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## PARAMETERS

### -ArgumentList

Spécifie des paramètres ou des valeurs de paramètre à utiliser lorsque cette applet de commande démarre le processus. Les arguments peuvent être acceptés comme une chaîne unique avec les arguments séparés par des espaces, ou comme un tableau de chaînes séparées par des virgules.

Si des paramètres ou des valeurs de paramètre contiennent un espace, ils doivent être placés entre guillemets doubles. Pour plus d’informations, consultez [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action. Par défaut, l'applet de commande utilise les informations d'identification de l'utilisateur actuel.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Spécifie le chemin d’accès et le nom de fichier facultatifs du programme qui s’exécute dans le processus. Entrez le nom d’un fichier exécutable ou d’un document, tel qu’un `.txt` fichier ou `.doc` , associé à un programme sur l’ordinateur. Ce paramètre est obligatoire.

Si vous spécifiez uniquement un nom de fichier, utilisez le paramètre **WorkingDirectory** pour spécifier le chemin d’accès.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LoadUserProfile

Indique que cette applet de commande charge le profil utilisateur Windows stocké dans la `HKEY_USERS` clé de registre de l’utilisateur actuel. Le paramètre ne s’applique pas aux systèmes non-Windows.

Ce paramètre n’affecte pas les profils PowerShell. Pour plus d’informations, consultez [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewWindow

Démarrez le nouveau processus dans la fenêtre de console active. Par défaut sur Windows, PowerShell ouvre une nouvelle fenêtre. Sur les systèmes non-Windows, vous n’accédez jamais à une nouvelle fenêtre de terminal.

Vous ne pouvez pas utiliser les paramètres **NoNewWindow** et **WindowStyle** dans la même commande.

Le paramètre ne s’applique pas aux systèmes non-Windows.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourne un objet processus pour chaque processus démarré par l'applet de commande. Par défaut, cette applet de commande ne génère aucun résultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardError

Spécifie un fichier. Cette applet de commande envoie toutes les erreurs générées par le processus à un fichier que vous spécifiez.
Entrez le chemin d’accès et le nom de fichier. Par défaut, les erreurs s'affichent dans la console.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardInput

Spécifie un fichier. Cette applet de commande lit les entrées du fichier spécifié. Entrez le chemin d’accès et le nom du fichier d’entrée. Par défaut, le processus obtient son entrée à partir du clavier.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardOutput

Spécifie un fichier. Cette applet de commande envoie la sortie générée par le processus à un fichier que vous spécifiez.
Entrez le chemin d’accès et le nom de fichier. Par défaut, la sortie s'affiche dans la console.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewEnvironment

Indique que cette applet de commande utilise les nouvelles variables d’environnement spécifiées pour le processus. Par défaut, le processus démarré s’exécute avec les variables d’environnement héritées du processus parent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verbe

Spécifie un verbe à utiliser lorsque cette applet de commande démarre le processus. Les verbes disponibles sont déterminés par l’extension de nom de fichier du fichier qui s’exécute dans le processus.

Le tableau suivant répertorie les verbes pour quelques types de fichiers de processus courants.

| Type de fichier |                Verbes et adverbes                |
| --------- | ----------------------------------- |
| .cmd      | Modifier, ouvrir, imprimer, RunAs, nom_d’emprunt |
| .exe      | Open, RunAs, RunAsUser              |
| .txt      | Ouvrir, imprimer, PrintTo                |
| .wav      | Ouvrir, lire                          |

Pour trouver les verbes qui peuvent être utilisés avec le fichier qui s’exécute dans un processus, utilisez l' `New-Object` applet de commande pour créer un objet **System. Diagnostics. ProcessStartInfo** pour le fichier. Les verbes disponibles se trouvent dans la propriété **Verbs** de l’objet **ProcessStartInfo** . Pour plus de détails, consultez les exemples.

Le paramètre ne s’applique pas aux systèmes non-Windows.

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

Indique que cette applet de commande attend que le processus spécifié et ses descendants se terminent avant d’accepter une autre entrée. Ce paramètre supprime l’invite de commandes ou conserve la fenêtre jusqu’à ce que les processus se terminent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WindowStyle

Spécifie l'état de la fenêtre utilisée pour le nouveau processus. Les valeurs acceptables pour ce paramètre sont les suivantes : **normal** , **masqué** , **réduit** et **agrandi** . La valeur par défaut est **normal** .

Vous ne pouvez pas utiliser les paramètres **WindowStyle** et **NoNewWindow** dans la même commande.

Le paramètre ne s’applique pas aux systèmes non-Windows.

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkingDirectory

Spécifie l’emplacement dans lequel le nouveau processus doit commencer. La valeur par défaut est l’emplacement du fichier exécutable ou du document en cours de démarrage. Les caractères génériques ne sont pas pris en charge. Le nom du chemin d’accès ne doit pas contenir de caractères qui seraient interprétés comme des caractères génériques.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

Ce paramètre a été introduit dans PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### Aucun

Vous ne pouvez pas diriger d'entrée vers cette applet de commande.

## SORTIES

### Aucun, System. Diagnostics. Process

Cette applet de commande génère un objet **System. Diagnostics. Process** , si vous spécifiez le paramètre **PassThru** . Sinon, cette applet de commande ne retourne aucune sortie.

## REMARQUES

- Cette applet de commande est implémentée à l’aide de la méthode **Start** de la classe **System. Diagnostics. Process** . Pour plus d’informations sur cette méthode, consultez [méthode Process. Start](/dotnet/api/system.diagnostics.process.start#overloads).

- Sur Windows, quand vous utilisez **UseNewEnvironment** , le nouveau processus démarre uniquement les variables d’environnement par défaut définies pour la portée de l' **ordinateur** . Cela a pour effet d’affecter la `$env:USERNAME` valeur **système** à. Aucune des variables de l’étendue de l' **utilisateur** n’est incluse.

- Sur Windows, le cas d’utilisation le plus courant de `Start-Process` est d’utiliser le paramètre **Wait** pour bloquer la progression jusqu’à ce que le nouveau processus se termine. Sur un système non-Windows, cela est rarement nécessaire, car le comportement par défaut pour les applications en ligne de commande est équivalent à `Start-Process -Wait` .

- Si `Start-Process` vous utilisez sur des systèmes autres que Windows, vous n’avez jamais une nouvelle fenêtre de terminal.

## LIENS CONNEXES

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Service](Start-Service.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
