---
title: Comment ajouter le nom de l’applet de commande et synopsis à une rubrique d’aide sur une applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361188"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="6fca5-102">Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="6fca5-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="6fca5-103">Cette section décrit comment ajouter du contenu qui s’affiche dans les sections nom et SYNOPSIS de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fca5-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="6fca5-104">Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fca5-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="6fca5-105">Pour obtenir une vue complète d’un fichier d’aide, ouvrez l’un des fichiers dll-Help. XML qui se trouvent dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fca5-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="6fca5-106">Par exemple, le fichier Microsoft. PowerShell. Commands. Management. dll-Help. xml contient du contenu pour plusieurs des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fca5-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="6fca5-107">Pour ajouter le nom de l’applet de commande et un Synopsis</span><span class="sxs-lookup"><span data-stu-id="6fca5-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="6fca5-108">L’aide de l’applet de commande peut afficher deux descriptions pour l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fca5-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="6fca5-109">La première description est une brève description, appelée Synopsis.</span><span class="sxs-lookup"><span data-stu-id="6fca5-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="6fca5-110">La deuxième Description est une description plus détaillée qui est décrite dans [Ajout de la description détaillée à une rubrique d’aide sur une applet](./how-to-add-a-cmdlet-description.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="6fca5-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="6fca5-111">Ces deux descriptions doivent être écrites sous la forme d’un seul paragraphe.</span><span class="sxs-lookup"><span data-stu-id="6fca5-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="6fca5-112">Dans le synopsis, ne répétez pas le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="6fca5-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="6fca5-113">Informant l’utilisateur que l’applet de commande obtenir-Server obtient un serveur est brève, mais pas informatif.</span><span class="sxs-lookup"><span data-stu-id="6fca5-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="6fca5-114">Utilisez plutôt des synonymes et ajoutez des détails à la description.</span><span class="sxs-lookup"><span data-stu-id="6fca5-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="6fca5-115">Exemple : « obtient un objet qui représente un ordinateur local ou distant ».</span><span class="sxs-lookup"><span data-stu-id="6fca5-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="6fca5-116">Utilisez des verbes simples tels que « obten », « Create » et « change » dans le synopsis.</span><span class="sxs-lookup"><span data-stu-id="6fca5-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="6fca5-117">Évitez d’utiliser « SET », car il est vague et des mots fantaisie tels que « modifier ».</span><span class="sxs-lookup"><span data-stu-id="6fca5-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="6fca5-118">Exemple : "obtient des informations sur la signature Authenticode dans un fichier."</span><span class="sxs-lookup"><span data-stu-id="6fca5-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="6fca5-119">Écrire dans la voix active.</span><span class="sxs-lookup"><span data-stu-id="6fca5-119">Write in active voice.</span></span> <span data-ttu-id="6fca5-120">Par exemple, « utiliser l’objet TimeSpan... » est plus clair que « l’objet TimeSpan peut être utilisé pour... »</span><span class="sxs-lookup"><span data-stu-id="6fca5-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="6fca5-121">Évitez le verbe « Display » lors de la description des applets de commande qui obtiennent des objets.</span><span class="sxs-lookup"><span data-stu-id="6fca5-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="6fca5-122">Bien que Windows PowerShell affiche les données des applets de commande, il est important d’introduire les utilisateurs au concept que l’applet de commande renvoie .NET Framework objets dont les données peuvent ne pas être affichées.</span><span class="sxs-lookup"><span data-stu-id="6fca5-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="6fca5-123">Si vous insistez sur l’affichage, l’utilisateur peut ne pas se rendre compte que l’applet de commande a peut-être retourné de nombreuses autres propriétés et méthodes utiles qui ne sont pas affichées.</span><span class="sxs-lookup"><span data-stu-id="6fca5-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="6fca5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fca5-124">See Also</span></span>

 [<span data-ttu-id="6fca5-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6fca5-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)