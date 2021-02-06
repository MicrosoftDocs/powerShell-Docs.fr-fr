---
description: Décrit les formats de nom de chemin d’accès complet et relatif dans PowerShell.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 9a95865d67dc15bf79762987622b702b14faf6c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601893"
---
# <a name="about-path-syntax"></a>À propos de la syntaxe de chemin

## <a name="short-description"></a>DESCRIPTION COURTE
Décrit les formats de nom de chemin d’accès complet et relatif dans PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Tous les éléments d’un magasin de données accessibles par le biais d’un fournisseur PowerShell peuvent être identifiés de manière unique par leurs noms de chemin d’accès. Un nom de chemin d’accès est une combinaison du nom de l’élément, du conteneur et des sous-conteneurs dans lesquels se trouve l’élément, et du lecteur PowerShell par le biais duquel les conteneurs sont accessibles.

Dans PowerShell, les noms de chemin d’accès sont répartis dans l’un des deux types suivants : complet et relatif. Un nom de chemin d’accès qualifié complet est constitué de tous les éléments qui composent un chemin d’accès. La syntaxe suivante montre les éléments dans un nom de chemin d’accès qualifié complet :

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

L' \<provider\> espace réservé fait référence au fournisseur PowerShell par le biais duquel vous accédez au magasin de données. Par exemple, le fournisseur FileSystem vous permet d’accéder aux fichiers et aux répertoires sur votre ordinateur. Cet élément de la syntaxe est facultatif et n’est jamais nécessaire, car les noms de lecteur sont uniques pour tous les fournisseurs.

L' \<drive\> espace réservé fait référence au lecteur PowerShell qui est pris en charge par un fournisseur PowerShell particulier. Dans le cas du fournisseur FileSystem, les lecteurs PowerShell sont mappés sur les lecteurs Windows qui sont configurés sur votre système. Par exemple, si votre système comprend un lecteur A : et un lecteur C :, le fournisseur FileSystem crée les mêmes lecteurs dans PowerShell.

Une fois que vous avez spécifié le lecteur, vous devez spécifier les conteneurs et les sous-conteneurs qui contiennent l’élément. Les conteneurs doivent être spécifiés dans l’ordre hiérarchique dans lequel ils se trouvent dans le magasin de données. En d’autres termes, vous devez commencer par le conteneur parent, puis le conteneur enfant dans ce conteneur parent, et ainsi de suite. En outre, chaque conteneur doit être précédé d’une barre oblique inverse. (Notez que PowerShell vous permet d’utiliser des barres obliques pour la compatibilité avec d’autres PowerShell.)

Une fois que le conteneur et les sous-conteneurs ont été spécifiés, vous devez fournir le nom de l’élément, précédé d’une barre oblique inverse. Par exemple, le nom de chemin d’accès complet pour le fichier Shell.dll dans le \\ répertoire system32 de C : Windows \\ est le suivant :

```powershell
C:\Windows\System32\Shell.dll
```

Dans ce cas, le lecteur sur lequel les conteneurs sont accessibles est le lecteur C :, le conteneur de niveau supérieur est Windows, le sous-conteneur est system32 (situé dans le conteneur Windows) et l’élément est Shell.dll.

Dans certains cas, vous n’avez pas besoin de spécifier un nom de chemin d’accès complet et pouvez utiliser à la place un nom de chemin d’accès relatif. Un nom de chemin d’accès relatif est basé sur l’emplacement de travail actuel. PowerShell vous permet d’identifier un élément en fonction de son emplacement par rapport à l’emplacement de travail actuel. Vous pouvez spécifier des noms de chemins d’accès relatifs en utilisant des caractères spéciaux. Le tableau suivant décrit chacun de ces caractères et fournit des exemples de noms de chemins d’accès relatifs et de noms de chemins d’accès qualifiés complets. Les exemples du tableau sont basés sur le répertoire de travail actuel défini sur C:\Windows.

|Symbole|Description               |Chemin relatif    |Le chemin d'accès complet          |
|------|--------------------------|-----------------|-------------------|
|.     |Emplacement actuel          |.\\ Requise        |c : \\ \\ système Windows|
|..    |Parent de l’emplacement actuel|..\\ Fichiers programme|c : \\ Program Files  |
|\     |Racine du lecteur actuel     |\\Fichiers programme  |c : \\ Program Files  |
|      |location                  |                 |                   |
|None|Aucun caractère spécial     |Système           |c : \\ \\ système Windows|

Lorsque vous utilisez un nom de chemin d’accès dans une commande, vous entrez ce nom de la même façon que vous utilisiez un nom de chemin d’accès qualifié complet ou un nom relatif. Par exemple, supposons que votre répertoire de travail actuel est C:\Windows. La commande Get-ChildItem suivante récupère tous les éléments dans le répertoire C:\Techdocs :

```powershell
Get-ChildItem \techdocs
```

La barre oblique inverse indique que la racine du lecteur de l’emplacement de travail actuel doit être utilisée. Étant donné que le répertoire de travail est C : \\ Windows, la racine du lecteur est le lecteur c :. Étant donné que le répertoire techdocs est situé en dehors de la racine, vous devez spécifier uniquement la barre oblique inverse.

Vous pouvez obtenir les mêmes résultats à l’aide de la commande suivante :

```powershell
Get-ChildItem c:\techdocs
```

Que vous utilisiez un nom de chemin d’accès qualifié complet ou un nom de chemin d’accès relatif, un nom de chemin d’accès est important non seulement parce qu’il localise un élément mais également qu’il identifie l’élément de manière unique, même si cet élément partage le même nom qu’un autre élément dans un conteneur différent.

Supposons, par exemple, que vous disposiez de deux fichiers nommés Results.txt.
Le premier fichier se trouve dans un répertoire nommé C : \\ techdocs \\ Jan et le deuxième fichier se trouve dans un répertoire nommé c : \\ techdocs \\ fév. Le nom du chemin d’accès pour le premier fichier (C : \\ techdocs \\ Jan \\Results.txt) et le nom du chemin d’accès pour le deuxième fichier (c : \\ techdocs \\ fév \\Results.txt) vous permettent de distinguer clairement les deux fichiers.

## <a name="see-also"></a>VOIR AUSSI

[about_Locations](about_Locations.md)

