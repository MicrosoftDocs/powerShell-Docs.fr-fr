---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: f4aec907a41378bbf49f744b66c5662aa3404beb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599142"
---
# Update-Help

## SYNOPSIS
Télécharge et installe les derniers fichiers d'aide sur votre ordinateur.

## SYNTAXE

### Chemin d’accès (par défaut)

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### LiteralPath

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## Description

L' `Update-Help` applet de commande télécharge les fichiers d’aide les plus récents pour les modules PowerShell et les installe sur votre ordinateur. Vous n’avez pas besoin de redémarrer PowerShell pour que le changement prenne effet. Vous pouvez utiliser l' `Get-Help` applet de commande pour afficher les nouveaux fichiers d’aide immédiatement.

`Update-Help` vérifie la version des fichiers d’aide sur votre ordinateur. Si vous n’avez pas de fichiers d’aide pour un module ou si vos fichiers d’aide sont obsolètes, `Update-Help` télécharge les fichiers d’aide les plus récents. Les fichiers d’aide peuvent être téléchargés et installés à partir d’Internet ou d’un partage de fichiers.

Sans paramètres, `Update-Help` met à jour les fichiers d’aide pour les modules de la session et pour tous les modules installés qui prennent en charge l’aide actualisable. Les modules installés mais non chargés dans la session active sont inclus. Les modules PowerShell sont stockés dans un emplacement répertorié dans la `$env:PSModulePath` variable d’environnement. Pour plus d’informations, voir [about_Updatable_Help](./About/about_Updatable_Help.md).

Vous pouvez utiliser le paramètre **module** pour mettre à jour les fichiers d’aide d’un module particulier. Utilisez le paramètre **UICulture** pour télécharger les fichiers d’aide dans plusieurs langues et paramètres régionaux.

Vous pouvez également utiliser `Update-Help` sur des ordinateurs qui ne sont pas connectés à Internet. Tout d’abord, utilisez la `Save-Help` cmdlet pour télécharger les fichiers d’aide à partir d’Internet et enregistrez-les dans un dossier partagé accessible au système qui n’est pas connecté à Internet. Utilisez ensuite le paramètre **SourcePath** de `Update-Help` pour télécharger les fichiers d’aide mis à jour à partir du partagé et les installer sur l’ordinateur.

Vous pouvez automatiser les mises à jour de l’aide en ajoutant l' `Update-Help` applet de commande à votre profil PowerShell. Par défaut, `Update-Help` s’exécute une seule fois par jour sur chaque ordinateur. Pour remplacer la limite d'une fois par jour, utilisez le paramètre **Force**.

L' `Update-Help` applet de commande a été introduite dans Windows PowerShell 3,0.

> [!IMPORTANT]
> `Update-Help` requiert des privilèges d’administrateur dans PowerShell 6,0 et versions antérieures.
> PowerShell 6,1 et versions ultérieures définissent l' **étendue** par défaut sur `CurrentUser` .
> Avant PowerShell 6,1, le paramètre d' **étendue** n’était pas disponible.
>
> Vous devez être membre du groupe Administrateurs sur l’ordinateur pour mettre à jour les fichiers d’aide pour les modules PowerShell Core.
>
> Pour télécharger ou mettre à jour les fichiers d’aide pour les modules dans le répertoire d’installation de PowerShell ( `$PSHOME\Modules` ), y compris les modules PowerShell Core, démarrez PowerShell à l’aide de l’option **exécuter en tant qu’administrateur** .
> Par exemple, `Start-Process pwsh.exe -Verb RunAs`.

## EXEMPLES

### Exemple 1 : mettre à jour les fichiers d’aide de tous les modules

L' `Update-Help` applet de commande met à jour les fichiers d’aide pour les modules installés qui prennent en charge l’aide actualisable. La langue de la culture de l’interface utilisateur (IU) est définie dans le système d’exploitation.

```powershell
Update-Help
```

### Exemple 2 : mettre à jour les fichiers d’aide pour les modules spécifiés

L' `Update-Help` applet de commande met à jour les fichiers d’aide uniquement pour les noms de modules qui commencent par **Microsoft. PowerShell**.

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### Exemple 3 : mettre à jour les fichiers d’aide pour différentes langues

L' `Update-Help` applet de commande met à jour les fichiers d’aide japonais (ja-JP) et anglais (en-US) pour tous les modules.

Si un module ne fournit pas de fichiers d’aide pour une culture d’interface utilisateur spécifiée, un message d’erreur s’affiche pour le module et la culture d’interface utilisateur. Dans cet exemple, le message d’erreur indique que les fichiers d’aide **ja-JP** sont introuvables pour le module **Microsoft. PowerShell. Utility**.

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### Exemple 4 : mettre à jour les fichiers d’aide sur plusieurs ordinateurs à partir d’un partage de fichiers

Dans cet exemple, les fichiers d’aide mis à jour sont téléchargés à partir d’Internet et enregistrés dans un partage de fichiers. Des informations d’identification de l’utilisateur sont nécessaires pour accéder au partage de fichiers et installer les mises à jour. Lorsqu’un partage de fichiers est utilisé, il est possible de mettre à jour les ordinateurs qui se trouvent derrière des pare-feu ou qui ne sont pas connectés à Internet.

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

La `Save-Help` commande télécharge les fichiers d’aide les plus récents pour tous les modules qui prennent en charge l’aide actualisable.
Le paramètre **DestinationPath** enregistre les fichiers dans le `\\Server01\Share\PSHelp` partage de fichiers. Le paramètre **Credential** spécifie un utilisateur qui a l’autorisation d’accéder au partage de fichiers.

L' `Invoke-Command` applet `Update-Help` de commande exécute des commandes à distance sur plusieurs ordinateurs. Le paramètre **ComputerName** obtient une liste d’ordinateurs distants à partir du fichier **Servers.txt** . Le paramètre **scriptblock** exécute la `Update-Help` commande et utilise le paramètre **SourcePath** pour spécifier le partage de fichiers qui contient les fichiers d’aide mis à jour. Le paramètre **Credential** spécifie un utilisateur qui peut accéder au partage de fichiers et exécuter la commande distante `Update-Help` .

### Exemple 5 : obtenir la liste des fichiers d’aide mis à jour

L' `Update-Help` applet de commande met à jour l’aide pour un module spécifié. L’applet de commande utilise le paramètre commun **Verbose** pour afficher la liste des fichiers d’aide qui ont été mis à jour. Vous pouvez utiliser **Verbose** pour afficher la sortie de tous les fichiers d’aide ou fichiers d’aide pour un module spécifique.

Sans le paramètre **Verbose** , `Update-Help` n’affiche pas les résultats de la commande. La sortie des paramètres **détaillés** est utile pour vérifier que les fichiers d’aide ont été mis à jour ou si la version la plus récente est installée.

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### Exemple 6 : Rechercher les modules qui prennent en charge l’aide actualisable

Cet exemple répertorie les modules qui prennent en charge l’aide actualisable. La commande utilise la propriété **HelpInfoUri** du module pour identifier les modules qui prennent en charge l’aide actualisable. La propriété **HelpInfoUri** contient une adresse qui est redirigée lorsque l' `Update-Help` applet de commande est exécutée.

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### Exemple 7 : inventaire des fichiers d’aide mis à jour

Dans cet exemple, le script `Get-UpdateHelpVersion.ps1` crée un inventaire des fichiers d’aide pouvant être mis à jour pour chaque module et de leurs numéros de version.

Le script identifie les modules qui prennent en charge l’aide actualisable à l’aide de la propriété **HelpInfoUri** des modules. Pour les modules qui prennent en charge l’aide actualisable, le script recherche et analyse le fichier d’informations d’aide (* helpinfo.xml) pour rechercher le numéro de version le plus récent.

Le script utilise la classe **PSCustomObject** et une table de hachage pour créer un objet de sortie personnalisé.

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## PARAMETERS

### -Credential

Spécifie les informations d’identification d’un utilisateur qui a l’autorisation d’accéder à l’emplacement du système de fichiers spécifié par **SourcePath**. Ce paramètre est valide uniquement quand le paramètre **SourcePath** ou **LiteralPath** est utilisé dans la commande.

Le paramètre **Credential** vous permet d’exécuter `Update-Help` des commandes avec le paramètre **SourcePath** sur des ordinateurs distants. En fournissant des informations d’identification explicites, vous pouvez exécuter la commande sur un ordinateur distant et accéder à un partage de fichiers sur un troisième ordinateur sans rencontrer une erreur d’accès refusé ou en utilisant l’authentification CredSSP pour déléguer les informations d’identification.

Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` . Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.

Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande ne suit pas la limite d’une fois par jour, ignore la vérification de version et télécharge les fichiers qui dépassent la limite de 1 Go.

Sans ce paramètre, `Update-Help` s’exécute une seule fois par période de 24 heures. Les téléchargements sont limités à 1 Go de contenu non compressé par module et les fichiers d’aide ne sont installés que s’ils sont plus récents que les fichiers existants sur l’ordinateur.

La limite d’une fois par jour protège les serveurs qui hébergent les fichiers d’aide et vous permet d’ajouter une `Update-Help` commande à votre profil PowerShell sans impliquer le coût des ressources des connexions ou des téléchargements répétés.

Pour mettre à jour l'aide d'un module dans plusieurs cultures d'interface utilisateur sans le paramètre **Force**, incluez toutes les cultures d'interface utilisateur dans la même commande, par exemple, comme ceci :

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### -FullyQualifiedModule

Spécifie les modules dont les noms sont spécifiés sous la forme d’objets **ModuleSpecification** .
Ces modules sont décrits dans la section Notes du [constructeur ModuleSpecification (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).

Par exemple, le paramètre **FullyQualifiedModule** accepte un nom de module qui est spécifié au format :

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

ou

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

**ModuleName** et **ModuleVersion** sont obligatoires, mais **Guid** est facultatif.

Vous ne pouvez pas spécifier le paramètre **FullyQualifiedModule** dans la même commande qu’un paramètre **module** .

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Spécifie le dossier pour les fichiers d’aide mis à jour au lieu de les télécharger à partir d’Internet. Utilisez ce paramètre ou **SourcePath** si vous avez utilisé l' `Save-Help` applet de commande pour télécharger les fichiers d’aide dans un répertoire.

Vous pouvez effectuer un pipeline d’un objet d’annuaire, tel que des `Get-Item` applets de commande ou `Get-ChildItem` , à `Update-Help` .

Contrairement à la valeur de **SourcePath**, la valeur de **LiteralPath** est utilisée exactement telle qu’elle est tapée. Aucun caractère n'est interprété en tant que caractère générique. Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples. Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

Met à jour l'aide pour les modules spécifiés. Entrez un ou plusieurs noms de module ou modèles de nom dans une liste séparée par des virgules, ou spécifiez un fichier qui répertorie un nom de module sur chaque ligne. Les caractères génériques sont autorisés. Vous pouvez effectuer le pipeline des modules de l' `Get-Module` applet de commande vers l’applet de commande `Update-Help` .

Les modules que vous spécifiez doivent être installés sur l’ordinateur, mais ils n’ont pas besoin d’être importés dans la session active. Vous pouvez spécifier n’importe quel module de la session ou tout module installé dans un emplacement figurant dans la `$env:PSModulePath` variable d’environnement.

La valeur `*` (All) tente de mettre à jour l’aide de tous les modules installés sur l’ordinateur.
Les modules qui ne prennent pas en charge l’aide actualisable sont inclus. Cette valeur peut générer des erreurs quand la commande rencontre des modules qui ne prennent pas en charge l’aide actualisable. Au lieu de cela, exécutez `Update-Help` sans paramètres.

Le paramètre **module** de l' `Update-Help` applet de commande n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module. Pour mettre à jour l’aide d’un module qui ne se trouve pas dans un `$env:PSModulePath` emplacement, importez le module dans la session active avant d’exécuter la `Update-Help` commande.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Recurse

Effectue une recherche récursive des fichiers d’aide dans le répertoire spécifié. Ce paramètre est valide uniquement lorsque la commande utilise le paramètre **SourcePath** .

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

### -Étendue

Spécifie l’étendue du système dans laquelle l’aide est mise à jour. Les mises à jour au niveau de l’étendue **ALLUSERS** requièrent des privilèges d’administrateur sur les systèmes Windows. Le `-Scope` paramètre a été introduit dans PowerShell Core version 6,1.

**CurrentUser** est l’étendue par défaut pour les fichiers d’aide dans PowerShell 6,1 et versions ultérieures. **ALLUSERS** peut être spécifié pour installer ou mettre à jour l’aide pour tous les utilisateurs. Sur les systèmes UNIX `sudo` , des privilèges sont requis pour mettre à jour l’aide pour tous les utilisateurs. Par exemple : `sudo pwsh -c Update-Help`

Les valeurs possibles sont :

- Utilisateur en cours
- AllUsers

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourcePath

Spécifie un dossier de système de fichiers dans lequel `Update-Help` les fichiers d’aide mis à jour, au lieu de les télécharger à partir d’Internet. Entrez le chemin d’accès à un dossier. Ne spécifiez pas un nom de fichier ou une extension de nom de fichier. Vous pouvez canaliser un dossier, tel que celui des `Get-Item` applets de commande ou `Get-ChildItem` , vers `Update-Help` .

Par défaut, `Update-Help` télécharge les fichiers d’aide mis à jour à partir d’Internet. Utilisez **SourcePath** lorsque vous avez utilisé l' `Save-Help` applet de commande pour télécharger les fichiers d’aide mis à jour dans un répertoire.

Pour spécifier une valeur par défaut pour **SourcePath**, accédez à **stratégie de groupe**, **Configuration ordinateur**, puis **Définissez le chemin source par défaut pour Update-Help**. Ce paramètre stratégie de groupe empêche les utilisateurs d’utiliser `Update-Help` pour télécharger des fichiers d’aide à partir d’Internet.
Pour plus d’informations, consultez [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

Spécifie les valeurs de culture d’interface utilisateur `Update-Help` utilisées par pour obtenir les fichiers d’aide mis à jour. Entrez un ou plusieurs codes de langue, tels que **es-es**, une variable qui contient des objets de culture ou une commande qui obtient des objets de culture, tels qu’une `Get-Culture` `Get-UICulture` commande ou. Les caractères génériques ne sont pas autorisés et vous ne pouvez pas envoyer un code de langue partielle, tel que **de**.

Par défaut, `Update-Help` obtient les fichiers d’aide dans la culture d’interface utilisateur définie pour le système d’exploitation. Si vous spécifiez le paramètre **UICulture** , `Update-Help` recherche uniquement de l’aide pour la culture d’interface utilisateur spécifiée.

> [!NOTE]
> Ubuntu 18,04 a modifié les paramètres régionaux par défaut en `C.UTF.8` , qui n’est pas une culture d’interface utilisateur reconnue. `Update-Help` ne parvient pas à télécharger l’aide en mode silencieux, sauf si vous utilisez ce paramètre avec des paramètres régionaux pris en charge, comme `en-US` . Cela peut se produire sur n’importe quelle plateforme qui utilise une valeur non prise en charge.

Les commandes qui utilisent le paramètre **UICulture** ne réussissent que si le module fournit les fichiers d'aide pour la culture d'interface utilisateur spécifiée. Si la commande échoue car la culture d’interface utilisateur spécifiée n’est pas prise en charge, un message d’erreur s’affiche.

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredentials

Indique que `Update-Help` exécute la commande, y compris le téléchargement Internet, à l’aide des informations d’identification de l’utilisateur actuel. Par défaut, la commande s'exécute sans informations d'identification explicites.

Ce paramètre est effectif uniquement quand le téléchargement Web utilise l’authentification NTLM (NT LAN Manager), Negotiate ou Kerberos.

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

### -Confirm

Vous demande une confirmation avant d’exécuter l’applet de commande.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande. L’applet de commande n’est pas exécutée.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable. Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## ENTRÉES

### System. IO. DirectoryInfo

Vous pouvez diriger un chemin d’accès de répertoire vers `Update-Help` .

### System. Management. Automation. PSModuleInfo

Vous pouvez diriger un objet de module de l’applet de commande `Get-Module` vers `Update-Help` .

## SORTIES

### None

`Update-Help` ne génère aucune sortie.

## REMARQUES

Pour mettre à jour l’aide pour les modules PowerShell Core, qui contiennent les commandes installées avec PowerShell, ou tout module dans l' `$PSHOME\Modules` annuaire, démarrez PowerShell avec l’option **exécuter en tant qu’administrateur**.

Seuls les membres du groupe Administrateurs sur l’ordinateur peuvent mettre à jour l’aide pour les modules PowerShell Core, les commandes qui sont installées avec PowerShell et les modules dans le `$PSHOME\Modules` dossier. Si vous n’avez pas l’autorisation de mettre à jour les fichiers d’aide, vous pouvez lire les fichiers d’aide en ligne. Par exemple, `Get-Help Update-Help -Online`.

Les modules sont la plus petite unité d'aide actualisable. Vous ne pouvez pas mettre à jour l’aide d’une applet de commande particulière. Pour rechercher le module qui contient une applet de commande particulière, utilisez la propriété **modulename** de l’applet de commande `Get-Command` , par exemple, `(Get-Command Update-Help).ModuleName` .

Étant donné que les fichiers d’aide sont installés dans le répertoire du module, l’applet de commande `Update-Help` peut installer le fichier d’aide mis à jour uniquement pour les modules qui sont installés sur l’ordinateur. Toutefois, l' `Save-Help` applet de commande peut enregistrer l’aide pour les modules qui ne sont pas installés sur l’ordinateur.

Si `Update-Help` ne peut pas trouver les fichiers d’aide mis à jour pour un module ou si l’aide mise à jour est introuvable dans la langue spécifiée, elle se poursuit en mode silencieux sans afficher de message d’erreur. Pour afficher l'état et les détails de la progression, utilisez le paramètre **Verbose**.

L' `Update-Help` applet de commande a été introduite dans Windows PowerShell 3,0. Il ne fonctionne pas dans les versions antérieures de PowerShell. Sur les ordinateurs qui ont à la fois Windows PowerShell 2,0 et Windows PowerShell 3,0, utilisez l' `Update-Help` applet de commande dans une session Windows powershell 3,0 pour télécharger et mettre à jour les fichiers d’aide. Les fichiers d’aide sont disponibles pour Windows PowerShell 2,0 et Windows PowerShell 3,0.

Les `Update-Help` `Save-Help` applets de commande et utilisent les ports suivants pour télécharger les fichiers d’aide : le port 80 pour http et le port 443 pour HTTPS.

`Update-Help` prend en charge tous les modules et les composants logiciels enfichables PowerShell Core. Elle ne prend en charge aucun autre composant logiciel enfichable.

Pour mettre à jour l’aide d’un module dans un emplacement qui n’est pas listé dans la `$env:PSModulePath` variable d’environnement, importez le module dans la session active, puis exécutez une `Update-Help` commande. Exécutez `Update-Help` sans paramètres ou utilisez le paramètre **module** pour spécifier le nom du module. Le paramètre **module** des `Update-Help` applets de commande et `Save-Help` n’accepte pas le chemin d’accès complet d’un fichier de module ou d’un fichier manifeste de module.

Tout module prend en charge de l'aide actualisable. Pour obtenir des instructions sur la prise en charge de l’aide actualisable dans les modules que vous créez, consultez [prise en charge de l’aide actualisable](/powershell/scripting/developer/module/supporting-updatable-help).

Les `Update-Help` applets de commande et ne `Save-Help` sont pas prises en charge sur environnement de préinstallation Windows (WinPE) (Windows PE).

## LIENS CONNEXES

[Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

[Get-Help](Get-Help.md)

[Get-Module](Get-Module.md)

[Get-UICulture](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[Start-Job](Start-Job.md)

[Save-Help](Save-Help.md)
