---
title: Attributs de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055170"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="95fab-102">Attributs des applets de commande</span><span class="sxs-lookup"><span data-stu-id="95fab-102">Cmdlet Attributes</span></span>

<span data-ttu-id="95fab-103">Windows PowerShell définit plusieurs attributs que vous pouvez utiliser pour ajouter des fonctionnalités communes à vos applets de commande sans avoir à implémenter cette fonctionnalité dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="95fab-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="95fab-104">Cela inclut l’attribut de l’applet de commande qui identifie une classe Microsoft .NET Framework en tant qu’une classe d’applet de commande, l’attribut OutputType qui spécifie les types .NET Framework retournés par l’applet de commande, l’attribut de paramètre qui identifie les propriétés publiques en tant qu’applet de commande paramètres et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="95fab-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="95fab-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="95fab-105">In This Section</span></span>

<span data-ttu-id="95fab-106">[Attributs dans le Code de l’applet de commande](./attributes-in-cmdlet-code.md) décrit l’avantage d’utiliser des attributs dans le code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="95fab-107">[Types d’attributs](./attribute-types.md) décrit les différents attributs peuvent décorer une classe de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="95fab-108">[Déclaration d’attribut alias](./alias-attribute-declaration.md) explique comment définir des alias pour un nom de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="95fab-109">[Déclaration d’attribut cmdlet](./cmdlet-attribute-declaration.md) explique comment définir une classe .NET Framework en tant qu’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="95fab-110">[Informations d’identification de la déclaration d’attribut](./credential-attribute-declaration.md) décrit comment ajouter la prise en charge pour la conversion d’entrée de chaîne dans un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objet.</span><span class="sxs-lookup"><span data-stu-id="95fab-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="95fab-111">[L’attribut OutputType déclaration](./outputtype-attribute-declaration.md) explique comment spécifier les types .NET Framework retournés par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="95fab-112">[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md) explique comment définir les paramètres d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="95fab-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="95fab-113">[Déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md) décrit comment définir le nombre d’arguments est autorisé pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="95fab-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="95fab-114">[Déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md) explique comment définir la longueur (en caractères) d’un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="95fab-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="95fab-115">[Déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md) explique comment définir des modèles pour un argument de paramètre valides.</span><span class="sxs-lookup"><span data-stu-id="95fab-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="95fab-116">[Déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md) décrit comment définir la plage valide pour un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="95fab-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="95fab-117">[Déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md) décrit comment définir les valeurs possibles pour un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="95fab-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="95fab-118">Référence</span><span class="sxs-lookup"><span data-stu-id="95fab-118">Reference</span></span>

[<span data-ttu-id="95fab-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95fab-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
