---
title: Comment ajouter une Description de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862595"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="e9410-102">Guide pratique pour ajouter une description de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="e9410-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="e9410-103">Cette section décrit comment ajouter du contenu qui s’affiche dans la section DESCRIPTION de l’aide de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e9410-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="e9410-104">Dans le fichier d’aide, ce contenu est ajouté au nœud de commande pour chaque applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e9410-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="e9410-105">Pour obtenir une vue complète d’un fichier d’aide, ouvrez un des fichiers dll-Help.xml situé dans le répertoire d’installation de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9410-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="e9410-106">Par exemple, le fichier Microsoft.PowerShell.Commands.Management.dll-Help.xml contient le contenu pour plusieurs des applets de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9410-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="e9410-107">Pour ajouter une Description</span><span class="sxs-lookup"><span data-stu-id="e9410-107">To Add a Description</span></span>

- <span data-ttu-id="e9410-108">Commencez par expliquer les fonctionnalités de base de l’applet de commande plus en détail.</span><span class="sxs-lookup"><span data-stu-id="e9410-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="e9410-109">Dans de nombreux cas, vous pouvez expliquer les termes utilisés dans le nom de l’applet de commande et illustrer les concepts êtes pas familiarisés avec un exemple.</span><span class="sxs-lookup"><span data-stu-id="e9410-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="e9410-110">Par exemple, si l’applet de commande ajoute des données à un fichier, expliquez qu’il ajoute des données à la fin d’un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="e9410-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="e9410-111">Pour rechercher toutes les fonctionnalités de l’applet de commande, passez en revue la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e9410-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="e9410-112">Décrire la fonction principale de l’applet de commande et ensuite inclure les autres fonctions et fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e9410-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="e9410-113">Par exemple, si la fonction principale de l’applet de commande consiste à modifier une propriété, mais l’applet de commande peut modifier toutes les propriétés, par exemple, dans la description détaillée.</span><span class="sxs-lookup"><span data-stu-id="e9410-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="e9410-114">Si les paramètres de l’applet de commande permettent aux utilisateurs de solliciter des informations de différentes façons, expliquer.</span><span class="sxs-lookup"><span data-stu-id="e9410-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="e9410-115">Inclure des informations sur les méthodes que les utilisateurs peuvent utiliser l’applet de commande, outre les utilisations évident.</span><span class="sxs-lookup"><span data-stu-id="e9410-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="e9410-116">Par exemple, vous pouvez utiliser l’objet qui le `Get-Host` récupère d’applet de commande pour modifier la couleur du texte dans la fenêtre de commande Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9410-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="e9410-117">Exemple :  « Le `Get-Acl` applet de commande Obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="e9410-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="e9410-118">Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e9410-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="e9410-119">La liste ACL spécifie les autorisations dont disposent les utilisateurs et groupes d’utilisateurs à accéder à la ressource. »</span><span class="sxs-lookup"><span data-stu-id="e9410-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="e9410-120">La description détaillée doit décrire l’applet de commande, mais elle ne doit pas décrire les concepts qui utilise l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e9410-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="e9410-121">Placez les définitions de concept dans les remarques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e9410-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9410-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9410-122">See Also</span></span>

[<span data-ttu-id="e9410-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e9410-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
