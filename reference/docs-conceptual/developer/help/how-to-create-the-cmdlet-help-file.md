---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour créer le fichier d’aide d’une applet de commande
description: Guide pratique pour créer le fichier d’aide d’une applet de commande
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659093"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="0a938-103">Guide pratique pour créer le fichier d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-103">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="0a938-104">Cette section décrit comment créer un fichier XML valide contenant du contenu pour les rubriques d’aide sur les applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a938-104">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="0a938-105">Cette section explique comment nommer le fichier d’aide, comment ajouter les en-têtes XML appropriés et comment ajouter des nœuds qui contiendront les différentes sections du contenu d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-105">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="0a938-106">Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a938-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0a938-107">Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0a938-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="0a938-108">Comment créer un fichier d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-108">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="0a938-109">Créez un fichier texte et enregistrez-le à l’aide de l’encodage UTF8.</span><span class="sxs-lookup"><span data-stu-id="0a938-109">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="0a938-110">Le nom de fichier doit avoir le format suivant afin que Windows PowerShell puisse le détecter en tant que fichier d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-110">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="0a938-111">Ajoutez les en-têtes XML suivants au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="0a938-111">Add the following XML headers to the text file.</span></span> <span data-ttu-id="0a938-112">Sachez que le fichier sera validé par rapport au schéma MAML (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="0a938-112">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="0a938-113">Actuellement, PowerShell ne fournit aucun outil pour valider le fichier.</span><span class="sxs-lookup"><span data-stu-id="0a938-113">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="0a938-114">Ajoutez un nœud de commande au fichier d’aide de l’applet de commande pour chaque applet de **commande** dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0a938-114">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="0a938-115">Chaque nœud du nœud de commande est associé aux différentes sections de la rubrique d’aide de l’applet de **commande** .</span><span class="sxs-lookup"><span data-stu-id="0a938-115">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="0a938-116">Le tableau suivant répertorie l’élément XML pour chaque nœud, suivi d’une description de chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="0a938-116">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="0a938-117">Nœud</span><span class="sxs-lookup"><span data-stu-id="0a938-117">Node</span></span>           |                                                                                                     <span data-ttu-id="0a938-118">Description</span><span class="sxs-lookup"><span data-stu-id="0a938-118">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="0a938-119">Ajoute du contenu pour les sections nom et SYNOPSIS de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-119">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-120">Pour plus d’informations, consultez [comment ajouter le nom de l’applet de commande et le synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="0a938-120">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="0a938-121">Ajoute du contenu pour la section DESCRIPTION de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-121">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-122">Pour plus d’informations, consultez [comment ajouter la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-122">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="0a938-123">Ajoute du contenu pour la section syntaxe de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-123">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-124">Pour plus d’informations, consultez [comment ajouter une syntaxe à une rubrique d’aide sur une applet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-124">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="0a938-125">Ajoute du contenu pour la section paramètres de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-125">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-126">Pour plus d’informations, consultez [comment ajouter des paramètres à une rubrique d’aide sur une applet](./how-to-add-parameter-information.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-126">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="0a938-127">Ajoute du contenu pour la section des entrées de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-127">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-128">Pour plus d’informations, consultez [comment ajouter des types d’entrée à une rubrique d’aide sur une applet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-128">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="0a938-129">Ajoute du contenu pour la section sorties de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-129">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-130">Pour plus d’informations, consultez [comment ajouter des valeurs de retour à une rubrique d’aide sur une applet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-130">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="0a938-131">Ajoute du contenu pour la section Remarques de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-131">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-132">Pour plus d’informations, consultez [comment ajouter des notes à une rubrique d’aide sur une applet](./how-to-add-notes-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-132">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="0a938-133">Ajoute du contenu pour la section Exemples de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-133">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-134">Pour plus d’informations, consultez [comment ajouter des exemples à une rubrique d’aide sur une applet](./how-to-add-examples-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-134">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="0a938-135">Ajoute du contenu pour la section Liens connexes de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-135">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="0a938-136">Pour plus d’informations, consultez [comment ajouter des liens connexes à une rubrique d’aide sur une applet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-136">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="0a938-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a938-137">Example</span></span>

 <span data-ttu-id="0a938-138">Voici un exemple de nœud de **commande** qui comprend les nœuds des différentes sections de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="0a938-138">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
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

## <a name="see-also"></a><span data-ttu-id="0a938-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a938-139">See Also</span></span>

 [<span data-ttu-id="0a938-140">Comment ajouter le nom de l’applet de commande et le synopsis</span><span class="sxs-lookup"><span data-stu-id="0a938-140">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-141">Comment ajouter la description détaillée à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-141">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="0a938-142">Guide pratique pour ajouter la syntaxe à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-142">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-143">Comment ajouter des paramètres à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-143">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="0a938-144">Guide pratique pour ajouter des types d’entrée à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-144">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-145">Guide pratique pour ajouter des valeurs de retour à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-145">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-146">Comment ajouter des notes à une rubrique d’aide sur une applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-146">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-147">Guide pratique pour ajouter des exemples à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-147">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-148">Guide pratique pour ajouter des liens connexes à une rubrique d’aide d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="0a938-148">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="0a938-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0a938-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
