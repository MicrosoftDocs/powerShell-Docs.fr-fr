---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: e42bc3d5e13f564a49e811d5a822912f72f5f1c0
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490735"
---
# Test-FileCatalog

## SYNOPSIS
`Test-FileCatalog` valide si les hachages contenus dans un fichier catalogue (. cat) correspondent aux hachages des fichiers réels afin de valider leur authenticité.

Cette applet de commande est uniquement prise en charge sur Windows.

## SYNTAXE

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Description

`Test-FileCatalog` valide l’authenticité des fichiers en comparant les hachages de fichier d’un fichier catalogue (. cat) avec les hachages des fichiers réels sur le disque. Si elle détecte des incompatibilités, elle retourne l’État ValidationFailed. Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre -Detailed. Il affiche également l’état de signature du catalogue dans la propriété signature, ce qui revient à appeler `Get-AuthenticodeSignature` l’applet de commande sur le fichier catalogue. Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre -FilesToSkip.

Cette applet de commande est uniquement prise en charge sur Windows.

## EXEMPLES

### Exemple 1 : créer et valider un catalogue de fichiers

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### Exemple 2 : valider un catalogue de fichiers avec une sortie détaillée

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## PARAMETERS

### -CatalogFilePath

Chemin d’accès à un fichier catalogue (. cat) qui contient les hachages à utiliser pour la validation.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### -Detailed

Retourne plus d’informations un objet plus détaillé `CatalogInformation` qui contient les fichiers testés, leurs hachages attendus/réels et une signature Authenticode du fichier catalogue s’il est signé.

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

### -FilesToSkip

Tableau de chemins d’accès qui ne doivent pas être testés dans le cadre de la validation.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Dossier ou tableau de fichiers qui doit être validé par rapport au fichier catalogue.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System. IO. DirectoryInfo [], System. String []

Le pipeline accepte un tableau de chaînes ou d' `DirectoryInfo` objets qui représentent les chemins d’accès aux fichiers qui doivent être validés.

## SORTIES

### System. Management. Automation. CatalogValidationStatus

Type de retour par défaut contenant la valeur `Valid` ou `ValidationFailed` .

### System. Management. Automation. CatalogInformation

Objet plus détaillé retourné lors de l’utilisation `-Detailed` de qui peut être utilisé pour analyser des fichiers spécifiques qui peuvent avoir été validés ou non, les hachages attendus ou trouvés, ainsi que l’algorithme utilisé dans le catalogue.

## REMARQUES

## LIENS CONNEXES

[New-FileCatalog](New-FileCatalog.md)

[PowerShellGet](/powershell/module/PowerShellGet)
