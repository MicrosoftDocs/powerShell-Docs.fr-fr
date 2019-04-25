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
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083244"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="35187-102">Guide pratique pour créer le fichier d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="35187-103">Cette section décrit comment créer un fichier XML valide qui contient le contenu des rubriques d’aide applet de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35187-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="35187-104">Cette section explique comment nommer le fichier d’aide, comment ajouter les en-têtes XML appropriés et comment ajouter des nœuds qui contiendront les différentes sections de contenu de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="35187-105">Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35187-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="35187-106">Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35187-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="35187-107">Comment créer un fichier d’aide de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="35187-108">Créez un fichier texte et enregistrez-le à l’aide de l’encodage UTF8.</span><span class="sxs-lookup"><span data-stu-id="35187-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="35187-109">Le nom de fichier doit avoir le format suivant pour que Windows PowerShell puisse le détecter en tant qu’un fichier d’aide applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="35187-110">Ajoutez les en-têtes XML suivants au fichier texte.</span><span class="sxs-lookup"><span data-stu-id="35187-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="35187-111">N’oubliez pas que le fichier sera être validé par rapport au schéma de langage de modélisation multi-agent (MAML).</span><span class="sxs-lookup"><span data-stu-id="35187-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="35187-112">Actuellement, Windows PowerShell ne fournit pas d’outils pour valider le fichier.</span><span class="sxs-lookup"><span data-stu-id="35187-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="35187-113">Ajouter un nœud de commande pour chaque applet de commande dans l’assembly dans le fichier d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="35187-114">Chaque nœud dans le nœud commande concerne les différentes sections de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="35187-115">Le tableau suivant répertorie l’élément XML pour chaque nœud, suivie d’une description de chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="35187-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="35187-116">Nœud</span><span class="sxs-lookup"><span data-stu-id="35187-116">Node</span></span>|<span data-ttu-id="35187-117">Description</span><span class="sxs-lookup"><span data-stu-id="35187-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="35187-118">Ajoute du contenu pour les sections nom et le résumé de la rubrique d’aide applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-119">Pour plus d’informations, consultez [comment ajouter le nom de l’applet de commande et le Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="35187-120">Ajoute du contenu de la section DESCRIPTION de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-121">Pour plus d’informations, consultez [comment ajouter la Description détaillée pour une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="35187-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="35187-122">Ajoute le contenu de la section syntaxe de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-123">Pour plus d’informations, consultez [comment la syntaxe de l’ajouter à une rubrique d’aide applet de commande](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="35187-124">Ajoute du contenu de la section Paramètres de rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-125">Pour plus d’informations, consultez [comment ajouter des paramètres à une rubrique d’aide applet de commande](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="35187-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="35187-126">Ajoute du contenu de la section d’entrées de la rubrique d’aide applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-127">Pour plus d’informations, consultez [comment ajouter des Types d’entrée à une rubrique d’aide applet de commande](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="35187-128">Ajoute le contenu de la section des sorties de rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-129">Pour plus d’informations, consultez [comment ajouter la valeurs de retour pour une rubrique d’aide applet de commande](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="35187-130">Ajoute du contenu à la section Remarques de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-131">Pour plus d’informations, consultez [comment ajouter des Notes à une rubrique d’aide applet de commande](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="35187-132">Ajoute le contenu de la section Exemples de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-133">Pour plus d’informations, consultez [comment ajouter des exemples pour une rubrique d’aide applet de commande](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="35187-134">Ajoute du contenu de la section liens connexes de rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="35187-135">Pour plus d’informations, consultez [comment ajouter des liens connexes à une rubrique d’aide applet de commande](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="35187-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="35187-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="35187-136">Example</span></span>

 <span data-ttu-id="35187-137">Voici un exemple d’un nœud de commande qui inclut les nœuds pour les différentes sections de la rubrique d’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="35187-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="35187-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35187-138">See Also</span></span>

 [<span data-ttu-id="35187-139">Comment ajouter le nom de l’applet de commande et le résumé</span><span class="sxs-lookup"><span data-stu-id="35187-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-140">Comment ajouter la Description détaillée à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="35187-141">Comment ajouter la syntaxe pour une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-142">Comment ajouter des paramètres à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="35187-143">Comment ajouter des Types d’entrée à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-144">Comment ajouter des valeurs de retour à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-145">Comment ajouter des Notes à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-146">Comment ajouter des exemples à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-147">Comment ajouter des liens connexes à une rubrique d’aide applet de commande</span><span class="sxs-lookup"><span data-stu-id="35187-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="35187-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="35187-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)