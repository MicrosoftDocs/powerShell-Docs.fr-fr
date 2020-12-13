---
ms.date: 09/13/2016
ms.topic: reference
title: Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande
description: Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande
ms.openlocfilehash: aeeb0cdd1d6d17b88067928ff952dc57a9441917
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659052"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="a9513-103">Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="a9513-103">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a9513-104">Cette section décrit comment ajouter du contenu qui s’affiche dans les sections **nom** et **Synopsis** de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9513-104">This section describes how to add content that is displayed in the **NAME** and **SYNOPSIS** sections of the cmdlet help.</span></span> <span data-ttu-id="a9513-105">Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9513-105">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="a9513-106">Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des `dll-Help.xml` fichiers situés dans le répertoire d’installation de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9513-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="a9513-107">Par exemple, le `Microsoft.PowerShell.Commands.Management.dll-Help.xml` fichier contient du contenu pour plusieurs des applets de commande PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9513-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="a9513-108">Pour ajouter le nom de l’applet de commande et un Synopsis</span><span class="sxs-lookup"><span data-stu-id="a9513-108">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="a9513-109">L’aide de l’applet de commande peut afficher deux descriptions pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9513-109">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="a9513-110">La première description est une brève description, appelée Synopsis.</span><span class="sxs-lookup"><span data-stu-id="a9513-110">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="a9513-111">La deuxième Description est une description plus détaillée qui est décrite dans [Ajout de la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="a9513-111">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>
  <span data-ttu-id="a9513-112">Ces deux descriptions doivent être écrites sous la forme d’un seul paragraphe.</span><span class="sxs-lookup"><span data-stu-id="a9513-112">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="a9513-113">Dans le synopsis, ne répétez pas le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9513-113">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="a9513-114">Informer l’utilisateur que l’applet de commande `Get-Server` obtient un serveur est bref, mais pas informatif.</span><span class="sxs-lookup"><span data-stu-id="a9513-114">Informing the user that the `Get-Server` cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="a9513-115">Utilisez plutôt des synonymes et ajoutez des détails à la description.</span><span class="sxs-lookup"><span data-stu-id="a9513-115">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="a9513-116">Exemple : « obtient un objet qui représente un ordinateur local ou distant ».</span><span class="sxs-lookup"><span data-stu-id="a9513-116">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="a9513-117">Utilisez des verbes simples tels que « obten », « Create » et « change » dans le synopsis.</span><span class="sxs-lookup"><span data-stu-id="a9513-117">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="a9513-118">Évitez d’utiliser « SET », car il est vague et des mots fantaisie tels que « modifier ».</span><span class="sxs-lookup"><span data-stu-id="a9513-118">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="a9513-119">Exemple : "obtient des informations sur la signature Authenticode dans un fichier."</span><span class="sxs-lookup"><span data-stu-id="a9513-119">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="a9513-120">Écrire dans la voix active.</span><span class="sxs-lookup"><span data-stu-id="a9513-120">Write in active voice.</span></span> <span data-ttu-id="a9513-121">Par exemple, « utiliser l’objet TimeSpan... » est plus clair que « l’objet TimeSpan peut être utilisé pour... »</span><span class="sxs-lookup"><span data-stu-id="a9513-121">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="a9513-122">Évitez le verbe « Display » lors de la description des applets de commande qui obtiennent des objets.</span><span class="sxs-lookup"><span data-stu-id="a9513-122">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="a9513-123">Bien que Windows PowerShell affiche les données des applets de commande, il est important d’introduire les utilisateurs au concept que l’applet de commande renvoie .NET Framework objets dont les données peuvent ne pas être affichées.</span><span class="sxs-lookup"><span data-stu-id="a9513-123">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="a9513-124">Si vous insistez sur l’affichage, l’utilisateur peut ne pas se rendre compte que l’applet de commande a peut-être retourné de nombreuses autres propriétés et méthodes utiles qui ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="a9513-124">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9513-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9513-125">See Also</span></span>

[<span data-ttu-id="a9513-126">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a9513-126">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
