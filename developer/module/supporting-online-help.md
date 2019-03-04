---
title: Prise en charge de l’aide en ligne | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857915"
---
# <a name="supporting-online-help"></a>Prise en charge de l’aide en ligne

À compter de Windows PowerShell 3.0, il existe deux façons pour prendre en charge la `Get-Help` fonctionnalité en ligne pour les commandes Windows PowerShell. Cette rubrique explique comment implémenter cette fonctionnalité pour différents types de commandes.

## <a name="about-online-help"></a>À propos de l’aide en ligne

Aide en ligne a toujours été un élément essentiel de Windows PowerShell. Bien que le `Get-Help` applet de commande affiche les rubriques d’aide à l’invite de commandes, de nombreux utilisateurs préfèrent l’expérience de lecture en ligne, y compris les codes de couleur des liens hypertexte et partage des idées dans le contenu de la Communauté et des documents basés sur le wiki. Plus important encore, avant l’arrivée de l’aide actualisable, aide en ligne fournie de la version la plus récente des fichiers d’aide.

Avec l’avènement de l’aide actualisable dans Windows PowerShell 3.0, aide en ligne joue un rôle essentiel. En plus de l’expérience utilisateur flexible, aide en ligne fournit une aide aux utilisateurs qui ne le faites pas ou ne peut pas utiliser l’aide actualisable pour télécharger les rubriques d’aide.

## <a name="how-get-help--online-works"></a>Comment Get-Help-Online-travaux

Pour aider les utilisateurs à trouver les rubriques d’aide en ligne pour les commandes, le `Get-Help` commande possède un paramètre en ligne qui ouvre la version en ligne de la rubrique d’aide pour une commande dans le navigateur Internet de l’utilisateur par défaut.

Par exemple, la commande suivante ouvre la rubrique d’aide en ligne pour le `Invoke-Command` applet de commande.

```powershell
Get-Help Invoke-Command -Online
```

Pour implémenter `Get-Help` -en ligne, le `Get-Help` applet de commande recherche pour un identificateur URI (Uniform Resource) pour la rubrique d’aide en ligne de version dans les emplacements suivants.

- Le premier lien dans la section liens connexes de la rubrique d’aide pour la commande. La rubrique d’aide doit être installée sur l’ordinateur. Cette fonctionnalité a été introduite dans Windows PowerShell 2.0.

- La propriété HelpUri de n’importe quelle commande. La propriété HelpUri est accessible, même lorsque la rubrique d’aide pour la commande n’est pas installée sur l’ordinateur. Cette fonctionnalité a été introduite dans Windows PowerShell 3.0.

  `Get-Help` recherche d’un URI dans la première entrée dans la section liens connexes avant d’obtenir la valeur de la propriété HelpUri. Si la valeur de propriété est incorrecte ou a changé, vous pouvez le remplacer en entrant une valeur différente dans le premier lien associé. Toutefois, le premier lien associé fonctionne uniquement lorsque les rubriques d’aide sont installés sur l’ordinateur de l’utilisateur.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Ajout d’un URI pour le premier lien associé d’une rubrique d’aide de commande

Vous pouvez prendre en charge `Get-Help` -Online pour n’importe quelle commande en ajoutant un URI valide à la première entrée dans la section liens connexes de la rubrique d’aide basé sur XML pour la commande. Cette option est valide uniquement dans les rubriques d’aide basé sur XML et ne fonctionne que si la rubrique d’aide est installée sur l’ordinateur de l’utilisateur. Lors de la rubrique d’aide est installée et l’URI est remplie, cette valeur est prioritaire sur la **HelpUri** propriété de la commande. Pour plus d’informations sur les rubriques d’aide basé sur XML pour les commandes, consultez [Writing XML-Based rubriques d’aide pour les commandes](../help/writing-xml-based-help-topics-for-commands.md).

Pour prendre en charge cette fonctionnalité, l’URI doit apparaître dans le `maml:uri` élément sous le premier `maml:relatedLinks/maml:navigationLink` élément dans le `maml:relatedLinks` élément.

Le code XML suivant indique le positionnement correct de l’URI. La « version en ligne : « texte dans la `maml:linkText` élément est une bonne pratique, mais il n’est pas obligatoire.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Ajout de la propriété HelpUri à une commande

Cette section montre comment ajouter la propriété HelpUri aux commandes de types différents.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Ajout d’une propriété HelpUri à une applet de commande

Pour les applets de commande écrite C#, ajoutez un **HelpUri** d’attribut à la classe d’applet de commande. La valeur de l’attribut doit être un URI qui commence par « http » ou « https ».

Le code suivant illustre l’attribut HelpUri de la `Get-History` classe de l’applet de commande.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Ajout d’une propriété HelpUri à une fonction avancée

Pour des fonctions avancées, ajoutez un **HelpUri** propriété le **CmdletBinding** attribut. La valeur de la propriété doit être un URI qui commence par « http » ou « https ».

Le code suivant illustre l’attribut HelpUri de la fonction New-calendrier

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Ajout d’un attribut HelpUri à une commande CIM

Pour les commandes CIM, ajoutez un **HelpUri** attribut le **CmdletMetadata** élément dans le fichier CDXML. La valeur de l’attribut doit être un URI qui commence par « http » ou « https ».

Le code suivant illustre l’attribut HelpUri de la commande Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Ajout d’un attribut HelpUri à un flux de travail

Pour les workflows qui sont écrits dans le langage Windows PowerShell, ajoutez un **. ExternalHelp** directive de commentaire pour le code de flux de travail. La valeur de la directive doit être un URI qui commence par « http » ou « https ».

> [!NOTE]
> La propriété HelpUri n’est pas pris en charge pour les flux de travail basé sur XAML dans Windows PowerShell.

Le code suivant montre le. Directive ExternalHelp dans un fichier de flux de travail.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```