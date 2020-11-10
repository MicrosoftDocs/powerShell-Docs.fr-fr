---
description: Décrit comment utiliser des noms de remplacement pour les applets de commande et les commandes dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_aliases?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Aliases
ms.openlocfilehash: 9094e34d4d3cbb8ee951593e15411e8e3234fa1a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387768"
---
# <a name="about-aliases"></a>À propos des alias

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit comment utiliser des noms de remplacement pour les applets de commande et les commandes dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Un alias est un autre nom ou surnom pour une applet de commande ou un élément de commande, comme une fonction, un script, un fichier ou un fichier exécutable. Vous pouvez utiliser l’alias à la place du nom de la commande dans toutes les commandes PowerShell.

Pour créer un alias, utilisez l’applet de commande New-Alias. Par exemple, la commande suivante crée l’alias « Gas » pour l' `Get-AuthenticodeSignature` applet de commande :

```powershell
New-Alias -Name gas -Value Get-AuthenticodeSignature
```

Après avoir créé l’alias pour le nom de l’applet de commande, vous pouvez utiliser l’alias à la place du nom de l’applet de commande. Par exemple, pour obtenir la signature Authenticode pour le fichier SqlScript.ps1, tapez :

```powershell
Get-AuthenticodeSignature SqlScript.ps1
```

Ou tapez :

```powershell
gas SqlScript.ps1
```

Si vous créez « Word » comme alias pour Microsoft Office Word, vous pouvez taper « Word » à la place de ce qui suit :

```powershell
"C:\Program Files\Microsoft Office\Office11\Winword.exe"
```

## <a name="built-in-aliases"></a>ALIAS INTÉGRÉS

PowerShell inclut un ensemble d’alias intégrés, y compris « CD » et « chdir » pour l’applet de commande Set-Location, et « LS » et « dir » pour l’applet de commande Get-ChildItem.

Pour récupérer tous les alias sur l’ordinateur, y compris les alias intégrés, tapez :

```powershell
Get-Alias
```

## <a name="alias-cmdlets"></a>APPLETS DE COMMANDE D’ALIAS

PowerShell comprend les applets de commande suivantes, qui sont conçues pour utiliser des alias :

- `Get-Alias` -Obtient tous les alias dans la session active.
- `New-Alias` -Crée un nouvel alias.
- `Set-Alias` -Crée ou modifie un alias.
- `Export-Alias` -Exporte un ou plusieurs alias dans un fichier.
- `Import-Alias` -Importe un fichier d’alias dans PowerShell.

Pour plus d’informations sur les applets de commande, tapez :

```powershell
Get-Help <cmdlet-Name> -Detailed
```

Par exemple, entrez :

```powershell
Get-Help Export-Alias -Detailed
```

## <a name="creating-an-alias"></a>CRÉATION D’UN ALIAS

Pour créer un alias, utilisez l’applet de commande New-Alias. Par exemple, pour créer l’alias « GH » pour obtenir-Help, tapez :

```powershell
New-Alias -Name gh -Value Get-Help
```

Vous pouvez utiliser l’alias dans les commandes, de la même façon que vous utilisez le nom complet de l’applet de commande, et vous pouvez utiliser l’alias avec des paramètres.

Par exemple, pour obtenir une aide détaillée sur l’applet de commande Get-WmiObject, tapez :

```powershell
Get-Help Get-WmiObject -Detailed
```

Ou tapez :

```powershell
gh Get-WmiObject -Detailed
```

## <a name="saving-aliases"></a>ENREGISTREMENT DES ALIAS

Les alias que vous créez sont enregistrés uniquement dans la session active. Pour utiliser les alias dans une autre session, ajoutez l’alias à votre profil PowerShell. Vous pouvez utiliser l’applet de commande Export-Alias pour enregistrer les alias dans un fichier.

Pour plus d’informations, tapez la commande suivante :

```powershell
Get-Help about_Profiles
```

## <a name="getting-aliases"></a>OBTENTION D’ALIAS

Pour obtenir tous les alias dans la session active, y compris les alias intégrés, les alias dans vos profils PowerShell et les alias que vous avez créés dans la session active, tapez :

```powershell
Get-Alias
```

Pour accéder à des alias particuliers, utilisez le paramètre Name de l’applet de commande Get-Alias. Par exemple, pour obtenir des alias qui commencent par « p », tapez :

```powershell
Get-Alias -Name p*
```

Pour obtenir les alias pour un élément particulier, utilisez le paramètre de définition. Par exemple, pour obtenir les alias pour le type d’applet de commande Get-ChildItem :

```powershell
Get-Alias -Definition Get-ChildItem
```

### <a name="get-alias-output"></a>RÉSULTAT DE LA RÉCUPÉRATION DE L’ALIAS

Get-Alias retourne un seul type d’objet, un objet AliasInfo (System. Management. Automation. AliasInfo). Le nom des alias qui n’incluent pas de trait d’Union, tel que « CD », est affiché au format suivant :

```powershell
Get-Alias ac
```

```Output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Alias           ac -> Add-Content
```

Il est ainsi très rapide et facile d’accéder aux informations dont vous avez besoin.

Le format de nom d'alias basé sur les flèches n'est pas utilisé pour les alias qui comportent un trait d'union. Il s’agit probablement de noms de substitution préférés pour les applets de commande et les fonctions, plutôt que par des abréviations ou des surnoms typiques, et l’auteur peut ne pas souhaiter qu’ils soient aussi évidents.

## <a name="alternate-names-for-commands-with-parameters"></a>AUTRES NOMS POUR LES COMMANDES AVEC DES PARAMÈTRES

Vous pouvez assigner un alias à une applet de commande, un script, une fonction ou un fichier exécutable. Vous ne pouvez pas assigner un alias à une commande et à ses paramètres. Par exemple, vous pouvez assigner un alias à l' `Get-Eventlog` applet de commande, mais vous ne pouvez pas assigner un alias à la `Get-Eventlog -LogName System` commande.

Vous pouvez créer une fonction qui comprend la commande. Pour créer une fonction, tapez le mot « function » suivi d’un nom pour la fonction. Tapez la commande et mettez-la entre accolades ( {} ).

Par exemple, la commande suivante crée la fonction syslog. Cette fonction représente la `Get-Eventlog -LogName System` commande :

```powershell
function Get-SystemEventlog {Get-Eventlog -LogName System}
Set-Alias -Name syslog -Value Get-SystemEventlog
```

Vous pouvez maintenant taper « syslog » à la place de la commande. Vous pouvez créer des alias pour la nouvelle fonction.

Pour plus d’informations sur les fonctions, tapez :

```powershell
Get-Help about_Functions
```

## <a name="alias-objects"></a>OBJETS ALIAS

Les alias PowerShell sont représentés par des objets qui sont des instances de la classe System. Management. Automation. AliasInfo. Pour plus d’informations sur ce type d’objet, consultez [AliasInfo, classe][aliasinfo] dans le kit de développement logiciel (SDK) PowerShell.

Pour afficher les propriétés et les méthodes des objets alias, récupérez les alias.
Ensuite, dirigez-les vers l’applet de commande Get-Member. Par exemple :

```powershell
Get-Alias | Get-Member
```

Pour afficher les valeurs des propriétés d’un alias spécifique, telles que l' `dir` alias, récupérez l’alias. Ensuite, dirigez-le vers l’applet de commande Format-List. Par exemple, la commande suivante obtient l’alias « dir ». Ensuite, la commande dirige l’alias vers l’applet de commande Format-List. Ensuite, la commande utilise le paramètre Property de Format-List avec un caractère générique ( \* ) pour afficher toutes les propriétés de l' `dir` alias. La commande suivante effectue ces tâches :

```powershell
Get-Alias -Name dir | Format-List -Property *
```

## <a name="powershell-alias-provider"></a>FOURNISSEUR d’ALIAS PowerShell

PowerShell comprend le fournisseur d’alias. Le fournisseur alias vous permet d’afficher les alias dans PowerShell comme s’ils étaient sur un lecteur du système de fichiers.

Le fournisseur alias expose le lecteur Alias :. Pour accéder au lecteur Alias :, tapez :

```powershell
Set-Location Alias:
```

Pour afficher le contenu du lecteur, tapez :

```powershell
Get-ChildItem
```

Pour afficher le contenu du lecteur à partir d’un autre lecteur PowerShell, commencez le chemin d’accès par le nom du lecteur. Incluez le signe deux-points ( :). Par exemple :

```powershell
Get-ChildItem -Path Alias:
```

Pour obtenir des informations sur un alias particulier, tapez le nom du lecteur et le nom de l’alias. Ou tapez un modèle de nom. Par exemple, pour obtenir tous les alias qui commencent par « p », tapez :

```powershell
Get-ChildItem -Path Alias:p*
```

Pour plus d’informations sur le fournisseur d’alias PowerShell, tapez :

```powershell
Get-Help Alias
```

## <a name="see-also"></a>VOIR AUSSI

- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)
- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)
- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [about_functions](about_functions.md)
- [about_profiles](about_profiles.md)
- [about_providers](about_providers.md)

<!-- External links -->
[aliasinfo]: /dotnet/api/system.management.automation.aliasinfo
