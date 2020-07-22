---
title: Comment créer le fichier d’aide de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: b5a5f3e187634b38ba3ce3da18a7ad64ccc09ce2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893014"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="e99a8-102">Guide pratique pour créer le fichier d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="e99a8-103">Cette section décrit comment créer un fichier XML valide contenant du contenu pour les rubriques d’aide sur les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e99a8-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="e99a8-104">Cette section explique comment nommer le fichier d’aide, comment ajouter les en-têtes XML appropriés et comment ajouter des nœuds qui contiendront les différentes sections du contenu d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="e99a8-105">Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e99a8-105">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="e99a8-106">Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e99a8-106">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="e99a8-107">Comment créer un fichier d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="e99a8-108">Créez un fichier texte et enregistrez-le à l’aide de l’encodage UTF8.</span><span class="sxs-lookup"><span data-stu-id="e99a8-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="e99a8-109">Le nom de fichier doit avoir le format suivant afin que Windows PowerShell puisse le détecter en tant que fichier d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-109">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="e99a8-110">Ajoutez les en-têtes XML suivants au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e99a8-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="e99a8-111">Sachez que le fichier sera validé par rapport au schéma MAML (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="e99a8-111">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="e99a8-112">Actuellement, PowerShell ne fournit aucun outil pour valider le fichier.</span><span class="sxs-lookup"><span data-stu-id="e99a8-112">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="e99a8-113">Ajoutez un nœud de commande au fichier d’aide de l’applet de commande pour chaque applet de **commande** dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e99a8-113">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="e99a8-114">Chaque nœud du nœud de commande est associé aux différentes sections de la rubrique d’aide de l’applet de **commande** .</span><span class="sxs-lookup"><span data-stu-id="e99a8-114">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="e99a8-115">Le tableau suivant répertorie l’élément XML pour chaque nœud, suivi d’une description de chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="e99a8-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="e99a8-116">Nœud</span><span class="sxs-lookup"><span data-stu-id="e99a8-116">Node</span></span>           |                                                                                                     <span data-ttu-id="e99a8-117">Description</span><span class="sxs-lookup"><span data-stu-id="e99a8-117">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="e99a8-118">Ajoute du contenu pour les sections nom et SYNOPSIS de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-119">Pour plus d’informations, consultez [comment ajouter le nom de l’applet de commande et le synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="e99a8-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="e99a8-120">Ajoute du contenu pour la section DESCRIPTION de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-121">Pour plus d’informations, consultez [comment ajouter la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="e99a8-122">Ajoute du contenu pour la section syntaxe de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-123">Pour plus d’informations, consultez [comment ajouter une syntaxe à une rubrique d’aide sur une applet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="e99a8-124">Ajoute du contenu pour la section paramètres de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-125">Pour plus d’informations, consultez [comment ajouter des paramètres à une rubrique d’aide sur une applet](./how-to-add-parameter-information.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="e99a8-126">Ajoute du contenu pour la section des entrées de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-127">Pour plus d’informations, consultez [comment ajouter des types d’entrée à une rubrique d’aide sur une applet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="e99a8-128">Ajoute du contenu pour la section sorties de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-129">Pour plus d’informations, consultez [comment ajouter des valeurs de retour à une rubrique d’aide sur une applet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="e99a8-130">Ajoute du contenu pour la section Remarques de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-130">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-131">Pour plus d’informations, consultez [comment ajouter des notes à une rubrique d’aide sur une applet](./how-to-add-notes-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="e99a8-132">Ajoute du contenu pour la section Exemples de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-133">Pour plus d’informations, consultez [comment ajouter des exemples à une rubrique d’aide sur une applet](./how-to-add-examples-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="e99a8-134">Ajoute du contenu pour la section Liens connexes de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e99a8-135">Pour plus d’informations, consultez [comment ajouter des liens connexes à une rubrique d’aide sur une applet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="e99a8-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="e99a8-136">Example</span></span>

 <span data-ttu-id="e99a8-137">Voici un exemple de nœud de **commande** qui comprend les nœuds des différentes sections de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e99a8-137">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="e99a8-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e99a8-138">See Also</span></span>

 [<span data-ttu-id="e99a8-139">Comment ajouter le nom de l’applet de commande et le synopsis</span><span class="sxs-lookup"><span data-stu-id="e99a8-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-140">Comment ajouter la description détaillée à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e99a8-141">Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-142">Comment ajouter des paramètres à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e99a8-143">Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-144">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-145">Comment ajouter des notes à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-146">Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-147">Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e99a8-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e99a8-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e99a8-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
