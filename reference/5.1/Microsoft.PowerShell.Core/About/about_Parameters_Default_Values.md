---
description: Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 5/31/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters_default_values?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters_Default_Values
ms.openlocfilehash: 286ffff28a88dbb29ce3ce83cea02b403eafd992
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207973"
---
# <a name="about-parameters-default-values"></a>À propos des valeurs par défaut des paramètres

## <a name="short-description"></a>Description courte

Décrit comment définir des valeurs par défaut personnalisées pour les paramètres d’applet de commande et les fonctions avancées.

## <a name="long-description"></a>Description longue

La `$PSDefaultParameterValues` variable de préférence vous permet de spécifier des valeurs par défaut personnalisées pour une applet de commande ou une fonction avancée. Les applets de commande et fonctions avancées utilisent la valeur par défaut personnalisée, sauf si vous spécifiez une autre valeur dans la commande.

Les auteurs des applets de commande et des fonctions avancées définissent les valeurs par défaut standard de leurs paramètres. En règle générale, les valeurs par défaut standard sont utiles, mais elles peuvent ne pas convenir à tous les environnements.

Cette fonctionnalité est particulièrement utile lorsque vous devez spécifier la même valeur de paramètre de remplacement presque chaque fois que vous utilisez la commande ou lorsqu’une valeur de paramètre particulière est difficile à mémoriser, par exemple un nom de serveur de messagerie ou un GUID de projet.

Si la valeur par défaut souhaitée varie de manière prévisible, vous pouvez spécifier un bloc de script qui fournit différentes valeurs par défaut pour un paramètre dans des conditions différentes.

`$PSDefaultParameterValues` a été introduit dans PowerShell 3,0.

## <a name="syntax"></a>Syntaxe

La `$PSDefaultParameterValues` variable est une table de hachage qui valide le format des clés en tant que type d’objet de **System. Management. Automation. DefaultParameterDictionary** . La table de hachage contient des paires **clé/valeur** . Une **clé** est au format `CmdletName:ParameterName` . Une **valeur** est le **DefaultValue** ou le **scriptblock** affecté à la clé.

La syntaxe de la `$PSDefaultParameterValues` variable de préférence est la suivante :

```
$PSDefaultParameterValues=@{"CmdletName:ParameterName"="DefaultValue"}

$PSDefaultParameterValues=@{ "CmdletName:ParameterName"={{ScriptBlock}} }

$PSDefaultParameterValues["Disabled"]=$True | $False
```

Les caractères génériques sont autorisés dans les valeurs **CmdletName** et **ParameterName** .

Pour définir, modifier, ajouter ou supprimer une paire **clé/valeur** spécifique de `$PSDefaultParameterValues` , utilisez les méthodes pour modifier une table de hachage standard. Par exemple, les méthodes **Add** et **Remove** . Ces méthodes ne remplacent pas les autres valeurs de la table de hachage.

Il existe une autre syntaxe qui ne remplace pas une `$PSDefaultParameterValues` table de hachage existante. Pour ajouter ou modifier une paire **clé/valeur** spécifique, utilisez la syntaxe suivante :

```
$PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

**CmdletName** doit être le nom d’une applet de commande ou le nom d’une fonction avancée qui utilise l’attribut **CmdletBinding** . Vous ne pouvez pas utiliser `$PSDefaultParameterValues` pour spécifier des valeurs par défaut pour les scripts ou les fonctions simples.

Le **DefaultValue** peut être un objet ou un bloc de script. Si la valeur est un bloc de script, PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre. Lorsque le paramètre spécifié accepte une valeur de bloc de script, mettez la valeur du bloc de script entre accolades, par exemple :

```powershell
$PSDefaultParameterValues=@{ "Invoke-Command:ScriptBlock"={{Get-Process}} }
```

Pour plus d’informations, consultez les documents suivants :

- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Script_Blocks](about_Script_Blocks.md)
- [about_Preference_Variables](about_Preference_Variables.md)

## <a name="examples"></a>Exemples

### <a name="how-to-set-psdefaultparametervalues"></a>Comment définir \$ PSDefaultParameterValues

`$PSDefaultParameterValues` est une variable de préférence, donc elle existe uniquement dans la session dans laquelle elle est définie. Il n'a aucune valeur par défaut.

Pour définir `$PSDefaultParameterValues` , tapez le nom de la variable et une ou plusieurs paires **clé/valeur** . Si vous exécutez une autre `$PSDefaultParameterValues` commande, elle remplace la table de hachage existante.

Pour obtenir des exemples sur la modification des paires **clé/valeur** sans remplacer les valeurs existantes de la table de hachage, consultez [How to Add values to \$ PSDefaultParameterValues](#how-to-add-values-to-psdefaultparametervalues) ou [How to change values in \$ PSDefaultParameterValues](#how-to-change-values-in-psdefaultparametervalues).

Pour enregistrer `$PSDefaultParameterValues` les sessions ultérieures, ajoutez une `$PSDefaultParameterValues` commande à votre profil PowerShell. Pour plus d’informations, consultez [about_Profiles](about_Profiles.md).

#### <a name="set-a-custom-default-value"></a>Définir une valeur par défaut personnalisée

La paire **clé/valeur** affecte `Send-MailMessage:SmtpServer` à la clé une valeur par défaut personnalisée de **SERVEUR123** .

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
}
```

#### <a name="set-default-values-for-multiple-parameters"></a>Définir des valeurs par défaut pour plusieurs paramètres

Pour définir des valeurs par défaut pour plusieurs paramètres, séparez chaque paire **clé/valeur** par un point-virgule ( `;` ). Les `Send-MailMessage:SmtpServer` `Get-WinEvent:LogName` clés et sont définies sur des valeurs par défaut personnalisées.

```powershell
$PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123";
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
}
```

#### <a name="use-wildcards-and-switch-parameters"></a>Utiliser des caractères génériques et des paramètres de commutateur

Les noms des applets de commande et des paramètres peuvent contenir des caractères génériques. Utilisez `$True` et `$False` pour définir des valeurs pour les paramètres de commutateur, tels que **Verbose** . Le paramètre **Verbose** du paramètre commun a la valeur `$True` pour toutes les commandes.

```powershell
$PSDefaultParameterValues = @{"*:Verbose"=$True}
```

#### <a name="use-an-array-for-the-default-value"></a>Utiliser un tableau pour la valeur par défaut

Si un paramètre peut accepter plusieurs valeurs, un tableau, vous pouvez définir plusieurs valeurs comme valeurs par défaut. La valeur par défaut de la `Invoke-Command:ComputerName` clé est définie sur une valeur de tableau **SERVEUR01** et **Server02** .

```powershell
$PSDefaultParameterValues = @{
  "Invoke-Command:ComputerName"="Server01","Server02"
}
```

#### <a name="use-a-script-block"></a>Utiliser un bloc de script

Vous pouvez utiliser un bloc de script pour spécifier différentes valeurs par défaut pour un paramètre dans des conditions différentes. PowerShell évalue le bloc de script et utilise le résultat comme valeur de paramètre par défaut.

La `Format-Table:AutoSize` clé affecte à ce paramètre la valeur par défaut **true** . L' `If` instruction contient une condition qui `$host.Name` doit être la console PowerShell, **ConsoleHost** .

```powershell
$PSDefaultParameterValues=@{
  "Format-Table:AutoSize"={if ($host.Name -eq "ConsoleHost"){$True}}
}
```

Si un paramètre accepte une valeur de bloc de script, placez le bloc de script entre accolades. Lorsque PowerShell évalue le bloc de script externe, le résultat est le bloc de script interne et défini comme valeur de paramètre par défaut.

La `Invoke-Command:ScriptBlock` clé est définie sur une valeur par défaut du **Journal des événements système** , car le bloc de script est entouré d’un deuxième ensemble d’accolades. Le résultat du bloc de script est passé à l' `Invoke-Command` applet de commande.

```powershell
$PSDefaultParameterValues=@{
  "Invoke-Command:ScriptBlock"={{Get-EventLog -Log System}}
}
```

### <a name="how-to-get-psdefaultparametervalues"></a>Obtention de \$ PSDefaultParameterValues

Les valeurs de la table de hachage sont affichées en entrant `$PSDefaultParameterValues` à l’invite de PowerShell.

Une `$PSDefaultParameterValues` table de hachage est définie avec trois paires **clé/valeur** .
Cette table de hachage est utilisée dans les exemples suivants qui décrivent comment ajouter, modifier et supprimer des valeurs dans `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues = @{
  "Send-MailMessage:SmtpServer"="Server123"
  "Get-WinEvent:LogName"="Microsoft-Windows-PrintService/Operational"
  "Get-*:Verbose"=$True
}

PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

Pour obtenir la valeur d’une `CmdletName:ParameterName` clé spécifique, utilisez la syntaxe suivante :

```
$PSDefaultParameterValues["CmdletName:ParameterName"]
```

Par exemple, pour obtenir la valeur de la `Send-MailMessage:SmtpServer` clé.

```
PS> $PSDefaultParameterValues["Send-MailMessage:SmtpServer"]
Server123
```

### <a name="how-to-add-values-to-psdefaultparametervalues"></a>Ajout de valeurs à \$ PSDefaultParameterValues

Pour ajouter une valeur à `$PSDefaultParameterValues` , utilisez la méthode **Add** . L’ajout d’une valeur n’affecte pas les valeurs existantes de la table de hachage.

Utilisez une virgule ( `,` ) pour séparer la **clé** de la **valeur** . La syntaxe suivante indique comment utiliser la méthode **Add** pour `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Add("CmdletName:ParameterName", "DefaultValue")
```

La table de hachage créée dans l’exemple précédent est mise à jour avec une nouvelle paire **clé/valeur** . La méthode **Add** affecte `Get-Process:Name` à la clé la valeur **PowerShell** .

```powershell
$PSDefaultParameterValues.Add("Get-Process:Name", "PowerShell")
```

La syntaxe suivante remplit le même résultat.

```powershell
$PSDefaultParameterValues["Get-Process:Name"]="PowerShell"
```

La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour. La `Get-Process:Name` clé a été ajoutée.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-Process:Name               PowerShell
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-remove-values-from-psdefaultparametervalues"></a>Comment supprimer des valeurs de \$ PSDefaultParameterValues

Pour supprimer une valeur de `$PSDefaultParameterValues` , utilisez la méthode **Remove** des tables de hachage. La suppression d’une valeur n’affecte pas les valeurs existantes de la table de hachage.

La syntaxe suivante montre comment utiliser la méthode **Remove** sur `$PSDefaultParameterValues` .

```
PS> $PSDefaultParameterValues.Remove("CmdletName:ParameterName")
```

Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour supprimer une paire **clé/valeur** . La méthode **Remove** supprime la `Get-Process:Name` clé.

```powershell
$PSDefaultParameterValues.Remove("Get-Process:Name")
```

La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour. La `Get-Process:Name` clé a été supprimée.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    Server123
```

### <a name="how-to-change-values-in-psdefaultparametervalues"></a>Comment modifier des valeurs dans \$ PSDefaultParameterValues

Les modifications apportées à une valeur spécifique n’affectent pas les valeurs existantes de la table de hachage. Pour modifier une paire **clé/valeur** spécifique dans `$PSDefaultParameterValues` , utilisez la syntaxe suivante :

```
PS> $PSDefaultParameterValues["CmdletName:ParameterName"]="DefaultValue"
```

Dans cet exemple, la table de hachage créée dans l’exemple précédent est mise à jour pour modifier une paire **clé/valeur** . La commande suivante remplace la `Send-MailMessage:SmtpServer` clé par une nouvelle valeur de **ServerXYZ** .

```powershell
$PSDefaultParameterValues["Send-MailMessage:SmtpServer"]="ServerXYZ"
```

La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour. La `Send-MailMessage:SmtpServer` clé a été remplacée par une nouvelle valeur.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

### <a name="how-to-disable-and-re-enable-psdefaultparametervalues"></a>Comment désactiver et réactiver \$ PSDefaultParameterValues

Vous pouvez désactiver et réactiver temporairement `$PSDefaultParameterValues` .
La désactivation `$PSDefaultParameterValues` de est utile si vous exécutez des scripts qui requièrent des valeurs de paramètre par défaut différentes.

Pour désactiver `$PSDefaultParameterValues` , ajoutez une clé `Disabled` avec la valeur **true** . Les valeurs de `$PSDefaultParameterValues` sont conservées, mais ne sont pas effectives.

```
PS> $PSDefaultParameterValues.Add("Disabled", $True)
```

La syntaxe suivante remplit le même résultat.

```
PS> $PSDefaultParameterValues["Disabled"]=$True
```

La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour avec la valeur de la `Disabled` clé.

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       True
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

Pour réactiver `$PSDefaultParameterValues` , supprimez la clé **désactivée** ou remplacez la valeur de la clé **désactivée** par `$False` . La valeur précédente de `$PSDefaultParameterValues` est à nouveau effective.

```
PS> $PSDefaultParameterValues.Remove("Disabled")
```

La syntaxe suivante remplit le même résultat.

```
PS> $PSDefaultParameterValues["Disabled"]=$False
```

La `$PSDefaultParameterValues` variable affiche la table de hachage mise à jour. Lorsque la méthode **Remove** est utilisée, la `Disabled` clé est supprimée de la sortie.
Si l’autre syntaxe a été utilisée pour réactiver `$PSDefaultParameterValues` , la `Disabled` clé est affichée avec la **valeur false** .

```
PS> $PSDefaultParameterValues

Name                           Value
----                           -----
Disabled                       False
Get-WinEvent:LogName           Microsoft-Windows-PrintService/Operational
Get-*:Verbose                  True
Send-MailMessage:SmtpServer    ServerXYZ
```

## <a name="see-also"></a>Voir aussi

[about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Profiles](about_Profiles.md)

[about_Script_Blocks](about_Script_Blocks.md)
