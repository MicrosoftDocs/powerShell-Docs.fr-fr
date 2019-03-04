---
title: Comment ajouter le nom de l’applet de commande et le Synopsis à une rubrique d’aide applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861825"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="47d49-102">Guide pratique pour ajouter le nom de l’applet de commande et le synopsis à une rubrique d’aide d’une applet de commande</span><span class="sxs-lookup"><span data-stu-id="47d49-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="47d49-103">Cette section décrit comment ajouter du contenu qui s’affiche dans les sections nom et le résumé de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47d49-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="47d49-104">Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47d49-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="47d49-105">Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47d49-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="47d49-106">Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47d49-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="47d49-107">Pour ajouter le nom de l’applet de commande et un résumé</span><span class="sxs-lookup"><span data-stu-id="47d49-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="47d49-108">L’applet de commande aide peut afficher deux descriptions de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47d49-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="47d49-109">La première description est une brève description qui est appelée le synopsis.</span><span class="sxs-lookup"><span data-stu-id="47d49-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="47d49-110">La seconde description est une description plus détaillée est décrite dans [Ajout de la Description détaillée pour une rubrique d’aide applet de commande](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="47d49-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="47d49-111">Les deux de ces descriptions devraient être écrit comme un seul paragraphe.</span><span class="sxs-lookup"><span data-stu-id="47d49-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="47d49-112">Le résumé ne se répètent pas le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="47d49-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="47d49-113">Pour informer l’utilisateur que l’applet de commande Get-serveur obtient un serveur est courte, mais pas informatives.</span><span class="sxs-lookup"><span data-stu-id="47d49-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="47d49-114">À la place, utiliser des synonymes et ajouter des détails à la description.</span><span class="sxs-lookup"><span data-stu-id="47d49-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="47d49-115">Exemple : « Obtient un objet qui représente un ordinateur local ou distant. »</span><span class="sxs-lookup"><span data-stu-id="47d49-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="47d49-116">Utiliser des verbes simples comme « get », « créer » et « modifier » dans le résumé.</span><span class="sxs-lookup"><span data-stu-id="47d49-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="47d49-117">Évitez d’utiliser « set », car il est vague et fantaisistes mots tels que « modifier. »</span><span class="sxs-lookup"><span data-stu-id="47d49-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="47d49-118">Exemple : « Obtient des informations sur la signature Authenticode dans un fichier ».</span><span class="sxs-lookup"><span data-stu-id="47d49-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="47d49-119">Écrire dans la voix active.</span><span class="sxs-lookup"><span data-stu-id="47d49-119">Write in active voice.</span></span> <span data-ttu-id="47d49-120">Par exemple, « utiliser l’objet TimeSpan... » est beaucoup plus claire que « l’objet TimeSpan peut être utilisé pour... »</span><span class="sxs-lookup"><span data-stu-id="47d49-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="47d49-121">Évitez le verbe « affichage » lors de la description des applets de commande permettant d’obtenir des objets.</span><span class="sxs-lookup"><span data-stu-id="47d49-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="47d49-122">Bien que Windows PowerShell affiche des données de l’applet de commande, il est important présenter le concept de l’applet de commande retourne les objets .NET Framework dont les données ne peuvent pas s’afficher aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="47d49-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="47d49-123">Si vous mettre l’accent sur l’affichage, l’utilisateur peut-être ignorer que l’applet de commande a peut-être retourné nombreuses autres propriétés et méthodes utiles qui ne sont pas affichés.</span><span class="sxs-lookup"><span data-stu-id="47d49-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="47d49-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47d49-124">See Also</span></span>

 [<span data-ttu-id="47d49-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="47d49-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)