---
title: Prise en charge de l’aide en ligne
ms.date: 09/13/2016
ms.openlocfilehash: b2d8eae2137e0e564a9baf271962b8669dd5eac5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892861"
---
# <a name="supporting-online-help"></a>Prise en charge de l’aide en ligne

À compter de PowerShell 3,0, il existe deux façons de prendre en charge la `Get-Help` fonctionnalité en ligne pour les commandes PowerShell. Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commande.

## <a name="about-online-help"></a>À propos de l’aide en ligne

L’aide en ligne a toujours été une partie essentielle de PowerShell. Bien que l' `Get-Help` applet de commande affiche les rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, notamment le codage de couleurs, les liens hypertexte et le partage d’idées dans le contenu de la communauté et les documents wiki. Plus important encore, avant l’avènement de l’aide actualisable, l’aide en ligne offrait la version la plus récente des fichiers d’aide.

Avec l’avènement de l’aide actualisable dans PowerShell 3,0, l’aide en ligne joue toujours un rôle vital. En plus de l’expérience utilisateur flexible, l’aide en ligne fournit de l’aide aux utilisateurs qui ne peuvent pas ou ne peuvent pas utiliser l’aide actualisable pour télécharger des rubriques d’aide.

## <a name="how-get-help--online-works"></a>Comment obtenir-Help-Online fonctionne

Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, la `Get-Help` commande dispose d’un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet par défaut de l’utilisateur.

Par exemple, la commande suivante ouvre la rubrique d’aide en ligne de l’applet de commande `Invoke-Command` .

```powershell
Get-Help Invoke-Command -Online
```

Pour implémenter `Get-Help -Online` , l' `Get-Help` applet de commande recherche une Uniform Resource Identifier (Uri) pour la rubrique d’aide de la version en ligne aux emplacements suivants.

- Premier lien de la section **liens connexes** de la rubrique d’aide de la commande. La rubrique d’aide doit être installée sur l’ordinateur de l’utilisateur. Cette fonctionnalité a été introduite dans PowerShell 2,0.

- Propriété **HelpUri** de toute commande. La propriété **HelpUri** est accessible même lorsque la rubrique d’aide de la commande n’est pas installée sur l’ordinateur de l’utilisateur. Cette fonctionnalité a été introduite dans PowerShell 3,0.

  `Get-Help`recherche un URI dans la première entrée de la section **liens connexes** avant d’obtenir la valeur de la propriété **HelpUri** . Si la valeur de la propriété est incorrecte ou a changé, vous pouvez la remplacer en entrant une valeur différente dans le premier lien associé. Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installées sur l’ordinateur de l’utilisateur.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Ajout d’un URI au premier lien associé d’une rubrique d’aide sur une commande

Vous pouvez prendre en charge `Get-Help -Online` n’importe quelle commande en ajoutant un URI valide à la première entrée de la section **liens connexes** de la rubrique d’aide XML de la commande. Cette option est valide uniquement dans les rubriques d’aide XML et fonctionne uniquement lorsque la rubrique d’aide est installée sur l’ordinateur de l’utilisateur. Lorsque la rubrique d’aide est installée et que l’URI est rempli, cette valeur est prioritaire par rapport à la propriété **HelpUri** de la commande.

Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans l' `maml:uri` élément sous le premier `maml:relatedLinks/maml:navigationLink` élément de l' `maml:relatedLinks` élément.

Le code XML suivant montre le positionnement correct de l’URI. Le `Online version:` texte de l' `maml:linkText` élément est une meilleure pratique, mais il n’est pas obligatoire.

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Ajout de la propriété HelpUri à une commande

Cette section montre comment ajouter la propriété HelpUri à des commandes de types différents.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Ajout d’une propriété HelpUri à une applet de commande

Pour les applets de commande écrites en C#, ajoutez un attribut **HelpUri** à la classe **cmdlet** . La valeur de l’attribut doit être un URI qui commence par `http` ou `https` .

Le code suivant illustre l’attribut **HelpUri** de la `Get-History` classe cmdlet.

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Ajout d’une propriété HelpUri à une fonction avancée

Pour fonctions avancées, ajoutez une propriété **HelpUri** à l’attribut **CmdletBinding** . La valeur de la propriété doit être un URI qui commence par « http » ou « HTTPS ».

Le code suivant illustre l’attribut **HelpUri** de la `New-Calendar` fonction.

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Ajout d’un attribut HelpUri à une commande CIM

Pour les commandes CIM, ajoutez un attribut **HelpUri** à l’élément **CmdletMetadata** dans le fichier CDXML.
La valeur de l’attribut doit être un URI qui commence par `http` ou `https` .

Le code suivant illustre l’attribut HelpUri de la `Start-Debug` commande CIM.

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Ajout d’un attribut HelpUri à un Workflow

Pour les flux de travail écrits dans le langage PowerShell, ajoutez un **. Commentaire ExternalHelp** directive de commentaire au code de Workflow. La valeur de la directive doit être un URI qui commence par `http` ou `https` .

> [!NOTE]
> La propriété HelpUri n’est pas prise en charge pour les flux de travail XAML dans PowerShell.

Le code suivant illustre. Directive commentaire ExternalHelp dans un fichier de flux de travail.

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
