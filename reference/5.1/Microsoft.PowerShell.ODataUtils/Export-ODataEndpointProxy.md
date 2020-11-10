---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 846aca6974190863a073773fe5148f0c57d77dc3
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388193"
---
# Export-ODataEndpointProxy

## SYNOPSIS
Génère un module qui contient des applets de commande pour gérer un point de terminaison OData.

## SYNTAXE

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

L' `Export-ODataEndpointProxy` applet de commande utilise les métadonnées d’un point de terminaison OData pour générer un module qui contient des applets de commande que vous pouvez utiliser pour gérer ce point de terminaison OData. Le module est basé sur CDXML. Une fois que cette applet de commande a généré le module, elle enregistre ce module dans le chemin d’accès et le nom de fichier spécifiés par le paramètre **OutputModule** .

`Export-ODataEndpointProxy` génère des applets de commande pour les opérations CRUD (Create, Read, Update et Delete), les actions non CRUD et la manipulation d’association.

`Export-ODataEndpointProxy` génère un fichier CDXML par ressource de point de terminaison. Vous pouvez modifier ces fichiers CDXML après la génération du module. Par exemple, si vous souhaitez modifier le nom ou les noms de verbe des applets de commande pour les aligner avec les instructions de dénomination des applets de commande Windows PowerShell, vous pouvez modifier le fichier.

Chaque applet de commande dans un module généré doit inclure un paramètre **ConnectionUri** afin de se connecter au point de terminaison géré par le module.

## EXEMPLES

### Exemple 1 : générer un module pour gérer un point de terminaison de service Web de vente au détail

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

Cette commande génère un module pour gérer un point de terminaison de service de vente au détail. La commande spécifie l’URI du point de terminaison et l’URI des métadonnées de point de terminaison. La commande fournit également un chemin de sortie et un nom de module de script comme valeur du paramètre **OutputModule** . Pour la valeur du paramètre **ResourceNameMapping** , la commande fournit une Hashtable qui mappe le nom de la collection de ressources au nom souhaité pour le jeu d’applets de commande. Dans cet exemple, Products est le nom de la collection de ressources et la **marchandise** est le substantif. Pour autoriser les connexions à des sites non-SSL, HTTP, par opposition à HTTPs, ajoutez le paramètre **AllowUnsecureConnection** .

## PARAMÈTRES

### -AllowClobber

Indique que cette applet de commande remplace un module existant.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -AllowUnsecureConnection

Indique que ce module peut se connecter aux URI qui ne sont pas sécurisés par SSL. Le module peut gérer des sites HTTP en plus des sites HTTPs.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CmdletAdapter

Spécifie l’adaptateur d’applet de commande. Les valeurs acceptables pour ce paramètre sont les suivantes : ODataAdapter et NetworkControllerAdapter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CreateRequestMethod

Spécifie la méthode de demande. Les valeurs acceptables pour ce paramètre sont les suivantes : PUT, poster et PATCH.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Spécifie un compte d’utilisateur qui a accès au point de terminaison OData. La valeur par défaut est l'utilisateur actuel. Si un ordinateur distant exécute Windows Vista ou une version ultérieure du système d’exploitation Windows, l’applet de commande vous invite à entrer des informations d’identification.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CustomData

Spécifie une table de hachage de données personnalisées.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Indique que cette applet de commande remplace un module généré existant du même nom dans un dossier existant `Modules` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -En-têtes

Spécifie les en-têtes de la demande web. Entrez une table de hachage ou un dictionnaire.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MetadataUri

Spécifie l’URI des métadonnées du point de terminaison.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputModule

Spécifie le chemin d’accès et le nom du module dans lequel cette applet de commande enregistre le module de commandes proxy généré.

Cette applet de commande copie un module binaire, un manifeste de module et un fichier de mise en forme, le cas échéant, dans le dossier spécifié. Si vous spécifiez uniquement le nom du module, `Export-ODataEndpointProxy` enregistre le module dans le `$home\Documents\WindowsPowerShell\Modules` dossier. Si vous spécifiez un chemin d’accès, l’applet de commande crée le dossier de module dans ce chemin d’accès.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceNameMapping

Spécifie une Hashtable qui contient des mappages qui vous permettent de personnaliser les applets de commande générées. Dans cette Hashtable, le nom de la collection de ressources est la clé. Le nom de l’applet de commande souhaitée est la valeur.

Par exemple, dans la table de hachage `@{Products = 'Merchandise'}` , **Products** est le nom de la collection de ressources qui sert de clé. La **marchandise** est le nom de l’applet de commande qui en résulte. Les noms des applets de commande générées peuvent ne pas être alignés sur les instructions de dénomination des applets de commande Windows Vous pouvez modifier le fichier de ressources CDXML pour modifier les noms des applets de commande après que cette applet de commande a créé le module. Pour plus d’informations, consultez [instructions de développement fortement encouragées](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UpdateRequestMethod

Spécifie la méthode de demande de mise à jour. Les valeurs acceptables pour ce paramètre sont les suivantes : PUT, poster et PATCH.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -URI

Spécifie l’URI du point de terminaison.

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

### -WhatIf

Montre ce qui se passe en cas d’exécution de l’applet de commande.
L’applet de commande n’est pas exécutée.

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

## SORTIES

## REMARQUES

## LIENS CONNEXES

[Bibliothèque OData](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))

[Qu’est-ce que le protocole OData ?](https://www.odata.org/)

[Invoke-RestMethod](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
