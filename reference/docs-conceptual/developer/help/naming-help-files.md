---
ms.date: 09/12/2016
ms.topic: reference
title: Nommage des fichiers d’aide
description: Nommage des fichiers d’aide
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667587"
---
# <a name="naming-help-files"></a>Nommage des fichiers d’aide

Cette rubrique explique comment nommer un fichier d’aide XML pour que l’applet [de commande d’obtention d’aide](/powershell/module/Microsoft.PowerShell.Core/Get-Help) puisse le trouver. Les spécifications de noms diffèrent pour chaque type de commande.

## <a name="cmdlet-help-files"></a>Fichiers d’aide sur les applets de commande

Le fichier d’aide d’une applet de commande C# doit être nommé pour l’assembly dans lequel l’applet de commande est définie. Utilisez le format de nom de fichier suivant :

```
<AssemblyName>.dll-help.xml
```

Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.

Par exemple, l’applet de commande [WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) est définie dans l’assembly Microsoft.PowerShell.Diagnostics.dll. L' `Get-Help` applet de commande recherche une rubrique d’aide pour l’applet de commande `Get-WinEvent` uniquement dans le `Microsoft.PowerShell.Diagnostics.dll-help.xml` fichier du répertoire du module.

## <a name="provider-help-files"></a>Fichiers d’aide du fournisseur

Le fichier d’aide d’un fournisseur PowerShell doit être nommé pour l’assembly dans lequel le fournisseur est défini. Utilisez le format de nom de fichier suivant :

`<AssemblyName>.dll-help.xml`

Le format du nom de l’assembly est requis même lorsque l’assembly est un module imbriqué.

Par exemple, le fournisseur de certificats est défini dans l' `Microsoft.PowerShell.Security.dll` assembly. L' `Get-Help` applet de commande recherche une rubrique d’aide pour le fournisseur de certificats uniquement dans le `Microsoft.PowerShell.Security.dll-help.xml` fichier du répertoire du module.

## <a name="function-help-files"></a>Fichiers d’aide de fonction

Les fonctions peuvent être documentées à l’aide d’une [aide basée sur des commentaires](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentées dans un fichier d’aide XML. Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` mot clé de commentaire qui associe la fonction au fichier XML. Dans le cas contraire, l’applet de commande `Get-Help` ne peut pas trouver le fichier d’aide.

Il n’existe aucune exigence technique pour le nom d’un fichier d’aide de fonction. Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel la fonction est définie. Par exemple, la fonction suivante est définie dans le `MyModule.psm1` fichier.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Fichiers d’aide de commande CIM

Le fichier d’aide pour une commande CIM doit être nommé pour le fichier CDXML dans lequel la commande CIM est définie. Utilisez le format de nom de fichier suivant :

`<FileName>.cdxml-help.xml`

Les commandes CIM sont définies dans les fichiers CDXML qui peuvent être inclus dans les modules en tant que modules imbriqués. Lorsque la commande CIM est importée dans la session en tant que fonction, PowerShell ajoute un `.ExternalHelp` mot clé de commentaire à la définition de fonction qui associe la fonction à un fichier d’aide XML nommé pour le fichier CDXML dans lequel la commande CIM est définie.

## <a name="script-workflow-help-files"></a>Script des fichiers d’aide du flux de travail

Les workflows de script inclus dans les modules peuvent être documentés dans les fichiers d’aide XML. Il n’existe aucune exigence technique pour le nom du fichier d’aide. Toutefois, il est recommandé de nommer le fichier d’aide pour le module de script dans lequel le flux de travail de script est défini. Par exemple :

`<ScriptModule>.psm1-help.xml`

Contrairement à d’autres commandes scriptées, les flux de travail de script ne nécessitent pas `.ExternalHelp` de mot clé de commentaire pour les associer à un fichier d’aide. Au lieu de cela, PowerShell recherche dans les sous-répertoires spécifiques à la culture de l’interface utilisateur du répertoire du module des fichiers d’aide basés sur XML et recherche de l’aide pour le workflow de script dans tous les fichiers. `.ExternalHelp` le mot clé de commentaire est ignoré.

Étant donné que le `.ExternalHelp` mot clé comment est ignoré, l' `Get-Help` applet de commande ne peut trouver de l’aide pour les workflows de script que lorsqu’ils sont inclus dans des modules.
