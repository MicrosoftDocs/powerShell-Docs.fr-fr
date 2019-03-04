---
title: Nommage des fichiers d’aide | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856665"
---
# <a name="naming-help-files"></a>Nommage des fichiers d’aide

Cette rubrique explique comment nommer un fichier d’aide basé sur XML afin que le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet peut le trouver. Les exigences relatives aux noms diffèrent pour chaque type de commande.
Cette rubrique explique comment nommer un fichier d’aide basé sur XML afin que le [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet peut le trouver. Les exigences relatives aux noms diffèrent pour chaque type de commande.

## <a name="cmdlet-help-files"></a>Fichiers d’aide de l’applet de commande

Le fichier d’aide pour un C# applet de commande doit être nommé pour l’assembly dans lequel l’applet de commande est défini. Utilisez le format de nom de fichier suivant :

```
<AssemblyName>.dll-help.xml
```

Le format de nom d’assembly est requis, même lorsque l’assembly est un module imbriqué.

Par exemple, le [Get-WinEvent ; PSITPro5_Diagnostic ; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) applet de commande est défini dans l’assembly Microsoft.PowerShell.Diagnostics.dll. Le `Get-Help` applet de commande recherche d’une rubrique d’aide pour le `Get-WinEvent` applet de commande uniquement dans le fichier Microsoft.PowerShell.Diagnostics.dll-help.xml dans le répertoire de module.
Par exemple, le [Get-WinEvent ; PSITPro5_Diagnostic ; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) applet de commande est défini dans l’assembly Microsoft.PowerShell.Diagnostics.dll. Le `Get-Help` applet de commande recherche d’une rubrique d’aide pour le `Get-WinEvent` applet de commande uniquement dans le fichier Microsoft.PowerShell.Diagnostics.dll-help.xml dans le répertoire de module.

## <a name="provider-help-files"></a>Fichiers d’aide du fournisseur

Le fichier d’aide pour un fournisseur Windows PowerShell doit être nommé pour l’assembly dans lequel le fournisseur est défini. Utilisez le format de nom de fichier suivant :

```
<AssemblyName>.dll-help.xml
```

Le format de nom d’assembly est requis, même lorsque l’assembly est un module imbriqué.

Par exemple, le fournisseur de certificats est défini dans l’assembly Microsoft.PowerShell.Security.dll. Le `Get-Help` applet de commande recherche une rubrique d’aide pour le fournisseur de certificats uniquement dans le fichier Microsoft.PowerShell.Security.dll-help.xml dans le répertoire de module.

## <a name="function-help-files"></a>Fichiers d’aide (fonction)

Fonctions peuvent être décrites à l’aide de [aide basée sur le commentaire](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentés dans un fichier d’aide XML. Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` commenter le mot clé qui associe la fonction avec le fichier XML. Sinon, le `Get-Help` applet de commande ne peut pas trouver le fichier d’aide.
Fonctions peuvent être décrites à l’aide de [aide basée sur le commentaire](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) ou documentés dans un fichier d’aide XML. Lorsque la fonction est documentée dans un fichier XML, la fonction doit avoir un `.ExternalHelp` commenter le mot clé qui associe la fonction avec le fichier XML. Sinon, le `Get-Help` applet de commande ne peut pas trouver le fichier d’aide.

Il n’existe aucune exigence technique pour le nom d’un fichier d’aide (fonction). Toutefois, une bonne pratique consiste à nommer le fichier d’aide pour le module de script dans lequel la fonction est définie. Par exemple, la fonction suivante est définie dans le fichier MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Fichiers d’aide commande CIM

Le fichier d’aide pour une commande CIM doit être nommé pour le fichier CDXML dans lequel la commande CIM est définie. Utilisez le format de nom de fichier suivant :

```
<FileName>.cdxml-help.xml
```

Commandes CIM sont définies dans les fichiers CDXML qui peuvent être inclus dans les modules en tant que modules imbriqués. Lorsque la commande CIM est importée dans la session en tant que fonction, Windows PowerShell ajoute un `.ExternalHelp` commentaire mot clé pour la définition de fonction qui associe la fonction avec un aide XML du fichier qui est nommé pour le fichier CDXML dans lequel la commande CIM est définie.

## <a name="script-workflow-help-files"></a>Fichiers d’aide de flux de travail de script

Workflows de script qui sont inclus dans les modules peuvent être documentées dans les fichiers d’aide basé sur XML. Il n’existe aucune exigence technique pour le nom du fichier d’aide. Toutefois, une bonne pratique consiste à nommer le fichier d’aide pour le module de script dans lequel le workflow de script est défini. Par exemple :

```
<ScriptModule>.psm1-help.xml
```

Contrairement à d’autres commandes de l’aide de scripts, les workflows de script ne nécessitent pas une `.ExternalHelp` commenter le mot clé pour les associer à un fichier d’aide. Au lieu de cela, Windows PowerShell recherche dans les sous-répertoires spécifiques de Culture de l’interface utilisateur du répertoire du module pour les fichiers d’aide basé sur XML et recherche de l’aide pour le workflow de script dans tous les fichiers. `.ExternalHelp` mot clé de commentaire sont ignorés.

Étant donné que le `.ExternalHelp` mot clé de commentaire est ignoré, le `Get-Help` applet de commande permettre trouver de l’aide pour les workflows de script uniquement lorsqu’ils sont inclus dans les modules.