---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 314734957eea971338ac886ad82e9ce9eeb6a242
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346562"
---
# Set-Acl

## SYNOPSIS
Change le descripteur de sécurité de l'élément spécifié, par exemple un fichier ou une clé de Registre.

## SYNTAXE

### ByPath (par défaut)

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Set-Acl` applet de commande modifie le descripteur de sécurité d’un élément spécifié, tel qu’un fichier ou une clé de Registre, pour qu’il corresponde aux valeurs d’un descripteur de sécurité que vous fournissez.

Pour utiliser `Set-Acl` , utilisez le paramètre **path** ou **InputObject** pour identifier l’élément dont vous souhaitez modifier le descripteur de sécurité. Utilisez ensuite les paramètres **AclObject** ou **SecurityDescriptor** pour fournir un descripteur de sécurité contenant les valeurs à appliquer. `Set-Acl` applique le descripteur de sécurité fourni. Cette applet de commande utilise la valeur du paramètre **AclObject** comme modèle, puis change les valeurs du descripteur de sécurité de l'élément pour qu'elles correspondent aux valeurs du paramètre **AclObject**.

## EXEMPLES

### Exemple 1 : copier un descripteur de sécurité d’un fichier à un autre

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

Ces commandes copient les valeurs du descripteur de sécurité du fichier Dog.txt vers le descripteur de sécurité du fichier Cat.txt. À la fin de l'exécution des commandes, les descripteurs de sécurité des fichiers Dog.txt et Cat.txt sont identiques.

La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.
L’opérateur d’assignation ( `=` ) stocke le descripteur de sécurité dans la valeur de la variable $DogACL.

La deuxième commande utilise `Set-Acl` pour modifier les valeurs de la liste de contrôle d’accès de Cat.txt en valeurs dans `$DogACL` .

La valeur du paramètre **Path** correspond au chemin d'accès du fichier Cat.txt. La valeur du paramètre **AclObject** est la liste de contrôle d’accès du modèle, dans ce cas, la liste de contrôle d’accès (ACL) de Dog.txt telle qu’elle est enregistrée dans la `$DogACL` variable.

### Exemple 2 : utiliser l’opérateur de pipeline pour passer un descripteur

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

Cette commande est presque identique à la commande dans l’exemple précédent, à ceci près qu’elle utilise un opérateur de pipeline ( `|` ) pour envoyer le descripteur de sécurité à partir d’une `Get-Acl` commande vers une `Set-Acl` commande.

La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt. L’opérateur de pipeline ( `|` ) passe un objet qui représente le descripteur de sécurité Dog.txt à l’applet de commande `Set-Acl` .

La deuxième commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de Dog.txt à Cat.txt.
À la fin de l'exécution de la commande, les listes ACL des fichiers Dog.txt et Cat.txt sont identiques.

### Exemple 3 : appliquer un descripteur de sécurité à plusieurs fichiers

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

Ces commandes appliquent les descripteurs de sécurité dans le fichier File0.txt à tous les fichiers texte du `C:\Temp` répertoire et à tous ses sous-répertoires.

La première commande obtient le descripteur de sécurité du fichier File0.txt dans le répertoire actif et utilise l’opérateur `=` d’assignation () pour le stocker dans la `$NewACL` variable.

La première commande du pipeline utilise l’applet de commande Get-ChildItem pour récupérer tous les fichiers texte dans le `C:\Temp` répertoire. Le paramètre **recurse** étend la commande à tous les sous-répertoires de `C:\temp` . Le paramètre **include** limite les fichiers récupérés à ceux avec l' `.txt` extension de nom de fichier. Le paramètre **Force** obtient les fichiers cachés, qui seraient sinon exclus. (Vous ne pouvez pas utiliser `c:\temp\*.txt` , car le paramètre **recurse** fonctionne sur les répertoires, et non sur les fichiers.)

L’opérateur de pipeline ( `|` ) envoie les objets représentant les fichiers récupérés à l’applet de commande `Set-Acl` , qui applique le descripteur de sécurité dans le paramètre **AclObject** à tous les fichiers dans le pipeline.

Dans la pratique, il est préférable d’utiliser le paramètre **WhatIf** avec toutes les `Set-Acl` commandes qui peuvent affecter plusieurs éléments. Dans ce cas, la deuxième commande dans le pipeline est `Set-Acl -AclObject $NewAcl -WhatIf` . Cette commande répertorie les fichiers affectés par la commande. Après avoir vérifié le résultat, vous pouvez réexécuter la commande sans le paramètre **WhatIf** .

### Exemple 4 : désactiver l’héritage et conserver les règles d’accès héritées

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Ces commandes désactivent l’héritage d’accès à partir des dossiers parents, tout en conservant les règles d’accès hérité existantes.

La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.

Ensuite, les variables sont créées pour convertir les règles d’accès héritées en règles d’accès explicites. Pour protéger les règles d’accès associées à cet héritage, affectez la valeur à la `$isProtected` variable `$true` . pour autoriser l’héritage, affectez à la valeur `$isProtected` `$false` . Pour plus d’informations, consultez [Set Access Rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).
La `$preserveInheritance` variable a la valeur `$true` pour conserver les règles d’accès héritées ; false pour supprimer les règles d’accès héritées. La protection de la règle d’accès est ensuite mise à jour à l’aide de la méthode **SetAccessRuleProtection ()** .

La dernière commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de à Dog.txt. Une fois la commande terminée, les listes de contrôle d’accès des Dog.txt qui ont été héritées du dossier animaux sont directement appliquées à Dog.txt, et les nouvelles stratégies d’accès ajoutées aux animaux ne modifient pas l’accès à Dog.txt.

### Exemple 5 : accorder aux administrateurs le contrôle total du fichier

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Cette commande accorde au groupe **BUILTIN\Administrators** le contrôle total du fichier Dog.txt.

La première commande utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité du fichier Dog.txt.

Les variables suivantes sont créées pour accorder au groupe **BUILTIN\Administrators** le contrôle total du fichier Dog.txt. La `$identity` variable définie sur le nom d’un [compte d’utilisateur](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor). La `$fileSystemRights` variable a la valeur FullControl et peut être l’une des valeurs [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) qui spécifie le type d’opération associé à la règle d’accès. La `$type` variable a la valeur « Allow » pour spécifier s’il faut autoriser ou refuser l’opération. La `$fileSystemAccessRuleArgumentList` variable est une liste d’arguments qui doit être passée lors de la création du nouvel objet **FileSystemAccessRule** . Un nouvel objet **FileSystemAccessRule** est créé, et l’objet **FileSystemAccessRule** est passé à la méthode **SetAccessRule ()** , ajoute la nouvelle règle d’accès.

La dernière commande utilise `Set-Acl` pour appliquer le descripteur de sécurité de à Dog.txt. Une fois la commande terminée, le groupe **BUILTIN\Administrateurs** disposera du contrôle total de la Dog.txt.

## PARAMÈTRES

### -AclObject

Spécifie une liste de contrôle d'accès (ACL, Access-Control List) avec les valeurs de propriété souhaitées. `Set-Acl` modifie la liste de contrôle d’accès de l’élément spécifié par le paramètre **path** ou **InputObject** afin qu’il corresponde aux valeurs de l’objet de sécurité spécifié.

Vous pouvez enregistrer la sortie d’une `Get-Acl` commande dans une variable, puis utiliser le paramètre **AclObject** pour passer la variable ou saisir une `Get-Acl` commande.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClearCentralAccessPolicy

Supprime la stratégie d'accès centralisée de l'élément spécifié.

À compter de Windows Server 2012, les administrateurs peuvent utiliser Active Directory et stratégie de groupe pour définir des stratégies d’accès centralisées pour les utilisateurs et les groupes. Pour plus d’informations, consultez [Access Control dynamique : vue d’ensemble du scénario](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

Omet les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path**. Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Spécifie un filtre dans le format ou le langage du fournisseur. La valeur de ce paramètre qualifie le paramètre **Path**. La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur. Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de la récupération des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Modifie uniquement les éléments spécifiés. La valeur de ce paramètre qualifie le paramètre **Path**.
Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` . Les caractères génériques sont autorisés.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

Change le descripteur de sécurité de l'objet spécifié. Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.

Vous ne pouvez pas diriger l’objet à modifier en `Set-Acl` . Utilisez plutôt le paramètre **InputObject** explicitement dans la commande.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Change le descripteur de sécurité de l'élément spécifié. Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée. Aucun caractère n’est interprété en tant que caractère générique. Si le chemin d’accès comprend des caractères d’échappement, mettez-le entre des guillemets simples ( `'` ).
Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.

Ce paramètre a été introduit dans Windows PowerShell 3.0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourne un objet qui représente le descripteur de sécurité modifié. Par défaut, cette applet de commande ne génère aucun résultat.

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

### -Path

Change le descripteur de sécurité de l'élément spécifié. Entrez le chemin d'accès d'un élément, par exemple le chemin d'accès d'un fichier ou d'une clé de Registre. Les caractères génériques sont autorisés.

Si vous passez un objet de sécurité à `Set-Acl` (en utilisant les paramètres **AclObject** ou **SecurityDescriptor** ou en passant un objet de sécurité de Get-Acl à `Set-Acl` ) et que vous omettez le paramètre **path** (Name et value), `Set-Acl` utilise le chemin d’accès qui est inclus dans l’objet de sécurité.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
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

### System. Security. AccessControl. objet ObjectSecurity, System. Security. AccessControl. CommonSecurityDescriptor

Vous pouvez diriger un objet ACL ou un descripteur de sécurité vers `Set-Acl` .

## SORTIES

### System. Security. AccessControl. FileSecurity

Par défaut, `Set-Acl` ne génère pas de sortie. Toutefois, si vous utilisez le paramètre **Passthru** , elle génère un objet de sécurité. Le type de l'objet de sécurité dépend du type de l'élément.

## REMARQUES

Cette applet de commande est disponible uniquement sur les plateformes Windows.

L' `Set-Acl` applet de commande est prise en charge par le système de fichiers PowerShell et les fournisseurs de registre. Ainsi, vous pouvez l'utiliser pour changer les descripteurs de sécurité des fichiers, des répertoires et des clés de Registre.

## LIENS CONNEXES

[Get-Acl](Get-Acl.md)

[FileSystemAccessRule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[Objet ObjectSecurity. SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)
