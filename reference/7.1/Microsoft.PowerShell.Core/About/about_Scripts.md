---
description: Décrit comment exécuter et écrire des scripts dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: c877627f8caeab8309326826caa4ec13d65d5d9d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206709"
---
# <a name="about-scripts"></a>À propos des scripts

## <a name="short-description"></a>Description courte
Décrit comment exécuter et écrire des scripts dans PowerShell.

## <a name="long-description"></a>Description longue

Un script est un fichier texte brut qui contient une ou plusieurs commandes PowerShell.
Les scripts PowerShell ont une `.ps1` extension de fichier.

L’exécution d’un script ressemble beaucoup à l’exécution d’une applet de commande. Vous tapez le chemin d’accès et le nom de fichier du script et utilisez des paramètres pour envoyer des données et définir des options. Vous pouvez exécuter des scripts sur votre ordinateur ou dans une session à distance sur un autre ordinateur.

L’écriture d’un script enregistre une commande en vue d’une utilisation ultérieure et facilite le partage avec d’autres utilisateurs. Plus important encore, il vous permet d’exécuter les commandes simplement en tapant le chemin d’accès du script et le nom de fichier. Les scripts peuvent être aussi simples qu’une seule commande dans un fichier ou aussi étendu qu’un programme complexe.

Les scripts ont des fonctionnalités supplémentaires, telles que le `#Requires` commentaire spécial, l’utilisation de paramètres, la prise en charge des sections de données et la signature numérique pour la sécurité.
Vous pouvez également écrire des rubriques d’aide pour les scripts et pour toutes les fonctions du script.

## <a name="how-to-run-a-script"></a>Comment exécuter un script

Avant de pouvoir exécuter un script sur Windows, vous devez modifier la stratégie d’exécution PowerShell par défaut. La stratégie d’exécution ne s’applique pas à PowerShell s’exécutant sur des plateformes non-Windows.

La stratégie d’exécution par défaut, `Restricted` , empêche l’exécution de tous les scripts, y compris les scripts que vous écrivez sur l’ordinateur local. Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md).

La stratégie d’exécution étant enregistrée dans le registre, vous ne devez la modifier qu’une seule fois sur chaque ordinateur.

Pour modifier la stratégie d’exécution, utilisez la procédure suivante.

À l’invite de commandes, tapez :

```powershell
Set-ExecutionPolicy AllSigned
```

ou

```powershell
Set-ExecutionPolicy RemoteSigned
```

La modification prend effet immédiatement.

Pour exécuter un script, tapez le nom complet et le chemin d’accès complet au fichier de script.

Par exemple, pour exécuter le script Get-ServiceLog.ps1 dans le répertoire C:\Scripts, tapez :

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

Pour exécuter un script dans le répertoire actif, tapez le chemin d’accès au répertoire actif ou utilisez un point pour représenter le répertoire actif, suivi d’une barre oblique inverse ( `.\` ).

Par exemple, pour exécuter le script ServicesLog.ps1 dans le répertoire local, tapez :

```powershell
.\Get-ServiceLog.ps1
```

Si le script contient des paramètres, tapez les paramètres et les valeurs de paramètre après le nom de fichier du script.

Par exemple, la commande suivante utilise le paramètre ServiceName du script Get-ServiceLog pour demander un journal de l’activité du service WinRM.

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

En tant que fonctionnalité de sécurité, PowerShell n’exécute pas de scripts lorsque vous double-cliquez sur l’icône de script dans l’Explorateur de fichiers ou lorsque vous tapez le nom du script sans chemin d’accès complet, même si le script se trouve dans le répertoire actif. Pour plus d’informations sur l’exécution de commandes et de scripts dans PowerShell, consultez [about_Command_Precedence](about_Command_Precedence.md).

### <a name="run-with-powershell"></a>Exécuter avec PowerShell

À compter de PowerShell 3,0, vous pouvez exécuter des scripts à partir de l’Explorateur de fichiers.

Pour utiliser la fonctionnalité « exécuter avec PowerShell » :

Exécutez l’Explorateur de fichiers, cliquez avec le bouton droit sur le nom de fichier du script, puis sélectionnez exécuter avec PowerShell.

La fonctionnalité « exécuter avec PowerShell » est conçue pour exécuter des scripts qui n’ont pas de paramètres requis et ne renvoient pas de sortie à l’invite de commandes.

Pour plus d'informations, consultez [about_Run_With_PowerShell](about_Run_With_PowerShell.md).

### <a name="running-scripts-on-other-computers"></a>Exécution de scripts sur d’autres ordinateurs

Pour exécuter un script sur un ou plusieurs ordinateurs distants, utilisez le paramètre **filePath** de l’applet de commande `Invoke-Command` .

Entrez le chemin d’accès et le nom de fichier du script en tant que valeur du paramètre **filePath** . Le script doit résider sur l'ordinateur local ou dans un répertoire auquel celui-ci peut accéder.

La commande suivante exécute le `Get-ServiceLog.ps1` script sur les ordinateurs distants nommés SERVEUR01 et Server02.

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>Obtenir de l’aide pour les scripts

L’applet de commande Get-Help obtient les rubriques d’aide pour les scripts, ainsi que pour les applets de commande et autres types de commandes. Pour obtenir la rubrique d’aide d’un script, tapez `Get-Help` suivi du chemin d’accès et du nom de fichier du script. Si le chemin d’accès du script se trouve dans votre `Path` variable d’environnement, vous pouvez omettre le chemin d’accès.

Par exemple, pour obtenir de l’aide pour le script ServicesLog.ps1, tapez :

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>Comment écrire un script

Un script peut contenir toutes les commandes PowerShell valides, y compris les commandes uniques, les commandes qui utilisent le pipeline, les fonctions et les structures de contrôle telles que les instructions If et les boucles for.

Pour écrire un script, ouvrez un nouveau fichier dans un éditeur de texte, tapez les commandes et enregistrez-les dans un fichier avec un nom de fichier valide avec l' `.ps1` extension de fichier.

L’exemple suivant est un script simple qui obtient les services qui s’exécutent sur le système actuel et les enregistre dans un fichier journal. Le nom du fichier journal est créé à partir de la date actuelle.

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

Pour créer ce script, ouvrez un éditeur de texte ou un éditeur de script, tapez ces commandes, puis enregistrez-les dans un fichier nommé `ServiceLog.ps1` .

### <a name="parameters-in-scripts"></a>Paramètres dans les scripts

Pour définir des paramètres dans un script, utilisez une instruction param. L' `Param` instruction doit être la première instruction d’un script, à l’exception des commentaires et des `#Require` instructions.

Les paramètres de script fonctionnent comme les paramètres de fonction. Les valeurs des paramètres sont disponibles pour toutes les commandes dans le script. Toutes les fonctionnalités des paramètres de fonction, y compris l’attribut de paramètre et ses arguments nommés, sont également valides dans les scripts.

Lors de l’exécution du script, les utilisateurs de script tapent les paramètres après le nom du script.

L’exemple suivant montre un `Test-Remote.ps1` script qui a un paramètre **ComputerName** . Les deux fonctions de script peuvent accéder à la valeur du paramètre **ComputerName** .

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

Pour exécuter ce script, tapez le nom du paramètre après le nom du script. Par exemple :

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

Pour plus d’informations sur l’instruction param et les paramètres de fonction, consultez [about_Functions](about_Functions.md) et [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="writing-help-for-scripts"></a>Écriture de l’aide pour les scripts

Vous pouvez écrire une rubrique d’aide pour un script à l’aide de l’une des deux méthodes suivantes :

- Aide Comment-Based pour les scripts

  Créez une rubrique d’aide en utilisant des mots clés spéciaux dans les commentaires. Pour créer une aide basée sur des commentaires pour un script, les commentaires doivent être placés au début ou à la fin du fichier de script. Pour plus d’informations sur l’aide basée sur les commentaires, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md).

- Aide XML-Based pour les scripts

  Créez une rubrique d’aide XML, telle que le type qui est généralement créé pour les applets de commande. L’aide XML est requise si vous traduisez des rubriques d’aide en plusieurs langues.

Pour associer le script à la rubrique d’aide basée sur XML, utilisez le. Mot clé d’aide commentaire ExternalHelp. Pour plus d’informations sur le mot clé commentaire ExternalHelp, consultez [about_Comment_Based_Help](about_Comment_Based_Help.md). Pour plus d’informations sur l’aide XML, consultez [Comment écrire l’aide sur les applets de](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)commande.

### <a name="returning-an-exit-value"></a>Retour d’une valeur de sortie

Par défaut, les scripts ne retournent pas d’état de sortie lorsque le script se termine. Vous devez utiliser l' `exit` instruction pour retourner un code de sortie à partir d’un script. Par défaut, l' `exit` instruction retourne `0` . Vous pouvez fournir une valeur numérique pour retourner un état de sortie différent. Un code de sortie différent de zéro signale généralement un échec.

Sur Windows, toute valeur comprise entre `[int]::MinValue` et `[int]::MaxValue` est autorisée.

Sur UNIX, seuls les nombres positifs compris entre `[byte]::MinValue` (0) et `[byte]::MaxValue` (255) sont autorisés. Un nombre négatif dans la plage de `-1` par `-255` est automatiquement converti en nombre positif en ajoutant
256. Par exemple, `-2` est transformé en `254` .

Dans PowerShell, l' `exit` instruction définit la valeur de la `$LASTEXITCODE` variable. Dans l’interface de commande Windows (cmd.exe), l’instruction Exit définit la valeur de la `%ERRORLEVEL%` variable d’environnement.

Tout argument qui n’est pas numérique ou qui se trouve en dehors de la plage spécifique à la plateforme est traduit en valeur de `0` .

## <a name="script-scope-and-dot-sourcing"></a>Étendue de script et source de points

Chaque script s’exécute dans sa propre étendue. Les fonctions, les variables, les alias et les lecteurs créés dans le script existent uniquement dans l’étendue du script. Vous ne pouvez pas accéder à ces éléments ou à leurs valeurs dans l’étendue dans laquelle le script s’exécute.

Pour exécuter un script dans une autre étendue, vous pouvez spécifier une étendue, telle que global ou local, ou vous pouvez pointer le script à la source.

La fonctionnalité de source de points vous permet d’exécuter un script dans l’étendue actuelle plutôt que dans la portée du script. Quand vous exécutez un script qui a la forme d’un point, les commandes du script s’exécutent comme si vous les aviez tapées à l’invite de commandes. Les fonctions, les variables, les alias et les lecteurs créés par le script sont créés dans l’étendue dans laquelle vous travaillez. Une fois le script exécuté, vous pouvez utiliser les éléments créés et accéder à leurs valeurs dans votre session.

Pour un script de source de point, tapez un point (.) et un espace avant le chemin du script.

Par exemple :

```powershell
. C:\scripts\UtilityFunctions.ps1
```

or

```powershell
. .\UtilityFunctions.ps1
```

Une fois le `UtilityFunctions.ps1` script exécuté, les fonctions et les variables créées par le script sont ajoutées à l’étendue actuelle.

Par exemple, le `UtilityFunctions.ps1` script crée la `New-Profile` fonction et la `$ProfileName` variable.

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

Si vous exécutez le `UtilityFunctions.ps1` script dans sa propre étendue de script, la `New-Profile` fonction et la `$ProfileName` variable existent uniquement lorsque le script est en cours d’exécution. Lorsque le script se termine, la fonction et la variable sont supprimées, comme illustré dans l’exemple suivant.

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

Lorsque vous pointez le script source et que vous l’exécutez, le script crée la `New-Profile` fonction et la `$ProfileName` variable de votre session dans votre portée. Une fois le script exécuté, vous pouvez utiliser la `New-Profile` fonction dans votre session, comme illustré dans l’exemple suivant.

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

Pour plus d’informations sur l’étendue, consultez about_Scopes.

## <a name="scripts-in-modules"></a>Scripts dans les modules

Un module est un ensemble de ressources PowerShell associées qui peuvent être distribuées en tant qu’unité. Vous pouvez utiliser des modules pour organiser vos scripts, fonctions et autres ressources. Vous pouvez également utiliser des modules pour distribuer votre code à d’autres utilisateurs et pour récupérer du code à partir de sources approuvées.

Vous pouvez inclure des scripts dans vos modules, ou vous pouvez créer un module de script, qui est un module qui se compose entièrement ou principalement d’un script et de ressources de prise en charge. Un module de script est simplement un script avec une extension de fichier. psm1.

Pour plus d’informations sur les modules, consultez [about_Modules](about_Modules.md).

## <a name="other-script-features"></a>Autres fonctionnalités de script

PowerShell offre de nombreuses fonctionnalités utiles que vous pouvez utiliser dans les scripts.

- `#Requires` -Vous pouvez utiliser une `#Requires` instruction pour empêcher l’exécution d’un script sans modules ou composants logiciels enfichables spécifiés et une version spécifiée de PowerShell. Pour plus d’informations, consultez about_Requires.

- `$PSCommandPath` -Contient le chemin d’accès complet et le nom du script en cours d’exécution. Ce paramètre est valide dans tous les scripts. Cette variable automatique est introduite dans PowerShell 3,0.

- `$PSScriptRoot` -Contient le répertoire à partir duquel un script est en cours d’exécution. Dans PowerShell 2,0, cette variable est valide uniquement dans les modules de script ( `.psm1` ).
  À compter de PowerShell 3,0, il est valide dans tous les scripts.

- `$MyInvocation` -La `$MyInvocation` variable automatique contient des informations sur le script en cours, y compris des informations sur la façon dont il a été démarré ou « appelé ». Vous pouvez utiliser cette variable et ses propriétés pour obtenir des informations sur le script pendant son exécution. Par exemple, `$MyInvocation` . La variable MyCommand. Path contient le chemin d’accès et le nom de fichier du script. `$MyInvocation`. La ligne contient la commande qui a démarré le script, y compris tous les paramètres et les valeurs.

  À compter de PowerShell 3,0, `$MyInvocation` possède deux nouvelles propriétés qui fournissent des informations sur le script qui a appelé ou appelé le script actuel. Les valeurs de ces propriétés sont remplies uniquement lorsque le demandeur ou l’appelant est un script.

  - **PSCommandPath** contient le chemin d’accès complet et le nom du script qui a appelé ou appelé le script actuel.

  - **PSScriptRoot** contient le répertoire du script qui a appelé ou appelé le script actuel.

  Contrairement aux `$PSCommandPath` `$PSScriptRoot` variables automatiques et, qui contiennent des informations sur le script en cours, les propriétés **PSCommandPath** et **PSScriptRoot** de la `$MyInvocation` variable contiennent des informations sur le script qui a appelé le script actuel.

- Sections de données : vous pouvez utiliser le `Data` mot clé pour séparer les données de la logique dans les scripts. Les sections de données peuvent également faciliter la localisation. Pour plus d’informations, consultez [about_Data_Sections](about_Data_Sections.md) et [about_Script_Internationalization](about_Script_Internationalization.md).

- Signature de script : vous pouvez ajouter une signature numérique à un script. Selon la stratégie d’exécution, vous pouvez utiliser des signatures numériques pour limiter l’exécution de scripts pouvant inclure des commandes non sécurisées. Pour plus d’informations, consultez [about_Execution_Policies](about_Execution_Policies.md) et [about_Signing](about_Signing.md).

## <a name="see-also"></a>Voir aussi

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
