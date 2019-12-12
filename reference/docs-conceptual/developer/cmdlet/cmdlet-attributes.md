---
title: Attributs d’applet de commande | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369958"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="4e945-102">Attributs des applets de commande</span><span class="sxs-lookup"><span data-stu-id="4e945-102">Cmdlet Attributes</span></span>

<span data-ttu-id="4e945-103">Windows PowerShell définit plusieurs attributs que vous pouvez utiliser pour ajouter des fonctionnalités communes à vos applets de commande sans implémenter cette fonctionnalité dans votre propre code.</span><span class="sxs-lookup"><span data-stu-id="4e945-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="4e945-104">Cela comprend l’attribut d’applet de commande qui identifie une classe d’infrastructure Microsoft .NET en tant que classe d’applet de commande, l’attribut OutputType qui spécifie les types de .NET Framework retournés par l’applet de commande, l’attribut de paramètre qui identifie les propriétés publiques comme cmdlet paramètres, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="4e945-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4e945-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4e945-105">In This Section</span></span>

<span data-ttu-id="4e945-106">[Attributs dans le code d’applet de](./attributes-in-cmdlet-code.md) commande Décrit l’avantage de l’utilisation d’attributs dans le code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="4e945-107">[Types d’attributs](./attribute-types.md) Décrit les différents attributs qui peuvent décorer une classe d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="4e945-108">[Déclaration d’attribut d’alias](./alias-attribute-declaration.md) Décrit comment définir des alias pour un nom de paramètre d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="4e945-109">[Déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md) de commande Décrit comment définir une classe .NET Framework en tant qu’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="4e945-110">[Déclaration d’attribut Credential](./credential-attribute-declaration.md) Décrit comment ajouter la prise en charge de la conversion de l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="4e945-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="4e945-111">[OutputType (déclaration d’attribut](./outputtype-attribute-declaration.md) ) Décrit comment spécifier les types de .NET Framework retournés par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="4e945-112">[Déclaration d’attribut de paramètre](./parameter-attribute-declaration.md) Décrit comment définir les paramètres d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4e945-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="4e945-113">[Déclaration d’attribut ValidateCount](./validatecount-attribute-declaration.md) Décrit comment définir le nombre d’arguments autorisés pour un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e945-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="4e945-114">[Déclaration d’attribut ValidateLength](./validatelength-attribute-declaration.md) Décrit comment définir la longueur (en caractères) d’un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e945-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="4e945-115">[Déclaration d’attribut ValidatePattern](./validatepattern-attribute-declaration.md) Décrit comment définir les modèles valides pour un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e945-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="4e945-116">[Déclaration d’attribut ValidateRange](./validaterange-attribute-declaration.md) Décrit comment définir la plage valide pour un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e945-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="4e945-117">[Déclaration d’attribut ValidateSet](./validateset-attribute-declaration.md) Décrit comment définir les valeurs possibles pour un argument de paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e945-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="4e945-118">Référence</span><span class="sxs-lookup"><span data-stu-id="4e945-118">Reference</span></span>

[<span data-ttu-id="4e945-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e945-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
