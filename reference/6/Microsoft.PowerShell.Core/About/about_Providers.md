---
description: Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande. Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: cbafcab2b24e77a43d7b628ce9500f480ed9b5b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206954"
---
# <a name="about-providers"></a>À propos des fournisseurs

## <a name="short-description"></a>Description courte
Décrit comment les fournisseurs PowerShell fournissent un accès aux données et aux composants qui ne seraient pas facilement accessibles à partir de la ligne de commande.
Les données sont présentées dans un format cohérent qui ressemble à un lecteur du système de fichiers.

## <a name="long-description"></a>Description longue

Les fournisseurs PowerShell sont des programmes .NET qui fournissent un accès à des magasins de données spécialisés pour faciliter l’affichage et la gestion. Les données apparaissent dans un lecteur, et vous accédez aux données dans un chemin d’accès comme sur un lecteur de disque dur. Vous pouvez utiliser l’une des applets de commande intégrées que le fournisseur prend en charge pour gérer les données dans le lecteur du fournisseur. De plus, vous pouvez utiliser des applets de commande personnalisées conçues spécialement pour les données.

Les fournisseurs peuvent également ajouter des paramètres dynamiques aux applets de commande intégrées. Ces paramètres sont disponibles uniquement lorsque vous utilisez l’applet de commande avec les données du fournisseur.

## <a name="built-in-providers"></a>Fournisseurs intégrés

PowerShell comprend un ensemble de fournisseurs intégrés que vous pouvez utiliser pour accéder aux différents types de magasins de données.

| Fournisseur   |   Lecteur (s)  |OutputType                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |Alias:       |System. Management. Automation. AliasInfo                        |
|Certificat |Cert:        |Microsoft. PowerShell. Commands. X509StoreLocation               |
|            |             |System.Security.Cryptography.X509Certificates.X509Certificate2|
|Environnement |Env:         |System. Collections. DictionaryEntry                            |
|FileSystem  |C : (*)       |System. IO. FileInfo                                            |
|            |             |System. IO. DirectoryInfo                                       |
|Fonction    |Fonction :    |System. Management. Automation. FunctionInfo                     |
|Registre    |HKLM : HKCU :  |Microsoft. Win32. RegistryKey                                   |
|Variable    |Variable :    |System. Management. Automation. PSVariable                       |
|WSMan       |WSMan :       |Microsoft. WSMan. Management. WSManConfigContainerElement        |

(*) Les lecteurs de système de fichiers varient en fonction de chaque système.

Vous pouvez également créer vos propres fournisseurs PowerShell, et vous pouvez installer des fournisseurs développés par d’autres. Pour répertorier les fournisseurs disponibles dans votre session, tapez :

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>Installation et suppression de fournisseurs

Les fournisseurs sont généralement installés via des modules PowerShell. L’importation du module charge le fournisseur dans votre session. Vous ne pouvez pas désinstaller les fournisseurs intégrés. Vous pouvez désinstaller des fournisseurs chargés par d’autres modules.

Vous pouvez décharger un fournisseur de la session active à l’aide de l’applet de commande `Remove-Module` . Cette applet de commande ne désinstalle pas le fournisseur, mais le fournisseur n’est pas disponible dans la session.

Vous pouvez également utiliser l' `Remove-PSDrive` applet de commande pour supprimer un lecteur de la session active. Ces données sur le lecteur ne sont pas affectées, mais le lecteur n’est plus disponible dans cette session.

## <a name="viewing-providers"></a>Affichage des fournisseurs

Pour afficher les fournisseurs PowerShell sur votre ordinateur, tapez :

```powershell
Get-PSProvider
```

La sortie répertorie les fournisseurs intégrés et les fournisseurs que vous avez ajoutés à la session.

## <a name="the-provider-cmdlets"></a>Applets de commande du fournisseur

Les applets de commande suivantes sont conçues pour fonctionner avec les données exposées par n’importe quel fournisseur. Vous pouvez utiliser les mêmes cmdlets de la même façon pour gérer les différents types de données que les fournisseurs exposent. Une fois que vous avez appris à gérer les données d’un fournisseur, vous pouvez utiliser les mêmes procédures avec les données de n’importe quel fournisseur.

Par exemple, l' `New-Item` applet de commande crée un nouvel élément. Dans le `C:` lecteur pris en charge par le fournisseur **FileSystem** , vous pouvez utiliser `New-Item` pour créer un nouveau fichier ou dossier. Dans les lecteurs pris en charge par le fournisseur de **Registre** , vous pouvez utiliser `New-Item` pour créer une nouvelle clé de registre. Dans le `Alias:` lecteur, vous pouvez utiliser `New-Item` pour créer un nouvel alias.

Pour obtenir des informations détaillées sur les applets de commande suivantes, tapez :

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>Applets de commande ChildItem

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>Applets de commande de contenu

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>Applets de commande Item

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rename-Item](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>Applets de commande ItemProperty

- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Rename-ItemProperty](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>Applets de commande Location

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-Location](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-Location](xref:Microsoft.PowerShell.Management.Push-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>Applets de commande Path

- [Join-Path](xref:Microsoft.PowerShell.Management.Join-Path)
- [Convert-Path](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)
- [Resolve-Path](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>PSDrive, applets de commande

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>Applets de commande PSProvider

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>Affichage des données du fournisseur

Le principal avantage d’un fournisseur est qu’il expose ses données de manière familière et cohérente. Le modèle de présentation des données est un lecteur du système de fichiers.

Le fournisseur vous permet d’afficher, de parcourir et de modifier des éléments dans le magasin de données comme s’il s’agissait de données dans un système de fichiers. Le magasin de données est accessible par le nom du lecteur qu’il prend en charge.

Le lecteur est indiqué dans l’affichage par défaut de l’applet de commande `Get-PSProvider` , mais vous pouvez obtenir des informations sur le lecteur du fournisseur à l’aide de l’applet de commande `Get-PSDrive` . Par exemple, pour obtenir toutes les propriétés du lecteur function :, tapez :

```powershell
Get-PSDrive Function | Format-List *
```

Vous pouvez afficher et parcourir les données d’un lecteur du fournisseur comme vous le feriez sur un lecteur du système de fichiers.

Pour afficher le contenu d’un lecteur de fournisseur, utilisez les applets de commande Get-Item ou Get-ChildItem. Tapez le nom du lecteur suivi d’un signe deux-points ( :). Par exemple, pour afficher le contenu du lecteur Alias :, tapez :

```powershell
Get-Item alias:
```

Vous pouvez afficher et gérer les données de n’importe quel lecteur à partir d’un autre lecteur en incluant le nom du lecteur dans le chemin d’accès. Par exemple, pour afficher la clé de Registre HKLM\Software dans le lecteur HKLM : à partir d’un autre lecteur, tapez :

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

Pour ouvrir le lecteur, utilisez l’applet de commande Set-Location. N’oubliez pas le signe deux-points lorsque vous spécifiez le chemin d’accès au lecteur. Par exemple, pour remplacer votre emplacement par le répertoire racine du lecteur Cert :, tapez :

```powershell
Set-Location cert:
```

Ensuite, pour afficher le contenu du lecteur Cert :, tapez :

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>Déplacement dans des données hiérarchiques

Vous pouvez vous déplacer dans un lecteur du fournisseur comme vous le feriez pour un lecteur de disque dur.
Si les données sont organisées dans une hiérarchie d’éléments dans les éléments, utilisez une barre oblique inverse ( `\` ) pour indiquer un élément enfant. Utilisez le format suivant :

```
drive:\location\child-location\...
```

Par exemple, pour modifier l’emplacement de la clé de Registre HKLM\Software, tapez une commande Set-Location, par exemple :

```powershell
Set-Location HKLM:\SOFTWARE\
```

Si un élément du nom complet comprend des espaces, vous devez placer le nom entre guillemets doubles ( `"` ). L’exemple suivant montre un chemin d’accès complet qui comprend des espaces.

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

Vous pouvez également utiliser des références relatives à des emplacements. Un point ( `.` ) représente l’emplacement actuel. Par exemple, si vous êtes dans la `HKLM:\Software\Microsoft` clé de Registre et que vous souhaitez répertorier les sous-clés de Registre dans la `HKLM:\Software\Microsoft\PowerShell` clé, tapez la commande suivante :

```powershell
Get-ChildItem .\PowerShell
```

En outre, les doubles points ( `..` ) font référence au répertoire ou au conteneur situé juste au-dessus de votre emplacement actuel. Vous pouvez utiliser des points doubles ( `..` ) pour naviguer dans une hiérarchie de fournisseur.

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>Page d’hébergement du fournisseur

Les fournisseurs disposent également d’un emplacement d' **hébergement** .  Cet emplacement est partagé par `PSDrives` le fournisseur. Il peut être récupéré en affichant la propriété de **démarrage** du fournisseur.

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

Le fournisseur **FileSystem** est le seul fournisseur qui a une valeur par défaut pour la **page d’hébergement** . Il s’agit de la même valeur que `$Home` . Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md).

Vous pouvez définir le répertoire de **départ** pour un fournisseur, pour la session active, à l’aide de sa propriété.

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

Le `~` caractère peut être utilisé pour représenter le répertoire de départ du fournisseur.
Si le fournisseur n’a pas d’emplacement de **départ** défini, une erreur s’affiche.

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>Recherche de paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés à une applet de commande par un fournisseur. Ces paramètres sont disponibles uniquement lorsque l’applet de commande est utilisée avec le fournisseur qui les a ajoutés.

Par exemple, le `Cert:` lecteur ajoute le paramètre **CodeSigningCert** aux `Get-Item` applets de commande et `Get-ChildItem` . Vous pouvez utiliser ce paramètre uniquement lorsque vous utilisez `Get-Item` ou `Get-ChildItem` dans le `Cert:` lecteur.

Pour obtenir la liste des paramètres dynamiques pris en charge par un fournisseur, consultez le fichier d’aide du fournisseur. Tapez :

```
Get-Help <provider-name>
```

Par exemple :

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>En savoir plus sur les fournisseurs

Bien que toutes les données du fournisseur apparaissent dans les lecteurs et que vous utilisiez les mêmes méthodes pour les parcourir, la similarité s’arrête là. Les magasins de données exposés par le fournisseur peuvent être aussi variés que les emplacements de Active Directory et les boîtes aux lettres de Microsoft Exchange Server.

Pour plus d’informations sur les différents fournisseurs PowerShell, tapez :

```
Get-Help <ProviderName>
```

Par exemple :

```powershell
Get-Help registry
```

Pour obtenir la liste des rubriques d’aide sur les fournisseurs, tapez :

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>Voir aussi

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)
