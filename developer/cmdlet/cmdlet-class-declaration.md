---
title: Déclaration de classe de l’applet de commande | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068638"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="99995-102">Déclaration de classe d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="99995-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="99995-103">Une classe Microsoft .NET Framework est déclarée comme une applet de commande en spécifiant le **applet de commande** attribut en tant que métadonnées pour la classe.</span><span class="sxs-lookup"><span data-stu-id="99995-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="99995-104">(Le **applet de commande** attribut est le seul attribut requis pour toutes les applets de commande).</span><span class="sxs-lookup"><span data-stu-id="99995-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="99995-105">Lorsque vous spécifiez le **applet de commande** attribut, vous devez spécifier la paire verbe-substantif qui identifie l’applet de commande à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="99995-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="99995-106">Et bien, vous devez décrire les fonctionnalités de Windows PowerShell qui prend en charge de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="99995-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="99995-107">Pour plus d’informations sur la syntaxe de déclaration est utilisée pour spécifier le **applet de commande** d’attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="99995-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="99995-108">Le **applet de commande** attribut est défini par le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="99995-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="99995-109">Les propriétés de cette classe correspondent aux paramètres de déclaration qui sont utilisés lorsque vous déclarez l’attribut.</span><span class="sxs-lookup"><span data-stu-id="99995-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="99995-110">Noms</span><span class="sxs-lookup"><span data-stu-id="99995-110">Nouns</span></span>

<span data-ttu-id="99995-111">Le nom de l’applet de commande spécifie les ressources sur lesquelles l’applet de commande agit.</span><span class="sxs-lookup"><span data-stu-id="99995-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="99995-112">Le substantif différencie vos applets de commande à partir d’autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="99995-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="99995-113">Les noms dans les noms d’applet de commande doivent être spécifique et dans le cas des substantifs génériques, tel que *server*, il est préférable d’ajouter un préfixe court qui différencie votre ressource à partir d’autres ressources similaires.</span><span class="sxs-lookup"><span data-stu-id="99995-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="99995-114">Par exemple, un nom de l’applet de commande qui inclut un nom avec un préfixe est `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="99995-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="99995-115">La combinaison d’un nom spécifique avec un verbe plus général permet à l’utilisateur localiser rapidement l’applet de commande par son action et d’identifier puis de l’applet de commande par ses ressources tout en évitant de duplication de nom d’applet de commande inutiles.</span><span class="sxs-lookup"><span data-stu-id="99995-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="99995-116">Pour obtenir la liste des caractères spéciaux ne peuvent pas être utilisés dans les noms d’applet de commande, consultez [directives de développement requis](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="99995-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="99995-117">Verbes</span><span class="sxs-lookup"><span data-stu-id="99995-117">Verbs</span></span>

<span data-ttu-id="99995-118">Lorsque vous spécifiez un verbe, les instructions de développement vous obligent à utiliser un des verbes prédéfinis fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99995-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="99995-119">En utilisant l’une de ces verbes prédéfinis, vous allez vérifier la cohérence entre les applets de commande que vous écrivez et les applets de commande qui sont écrits par Microsoft et par d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="99995-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="99995-120">Par exemple, le verbe « Get » est utilisé pour les applets de commande qui extraient des données.</span><span class="sxs-lookup"><span data-stu-id="99995-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="99995-121">Pour plus d’informations sur les instructions de verbes, consultez [les noms de verbe applet de commande](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="99995-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="99995-122">Pour obtenir la liste des caractères spéciaux ne peuvent pas être utilisés dans les noms d’applet de commande, consultez [directives de développement requis](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="99995-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="99995-123">Prise en charge des fonctionnalités de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99995-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="99995-124">Le **applet de commande** attribut vous permet également de spécifier que votre applet de commande prend en charge certaines des fonctionnalités courantes qui sont fournie par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99995-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="99995-125">Cela inclut la prise en charge des fonctionnalités communes telles que confirmation de commentaires utilisateur (appelée prise en charge de la fonctionnalité de ShouldProcess) et la prise en charge des transactions.</span><span class="sxs-lookup"><span data-stu-id="99995-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="99995-126">(Prise en charge des transactions a été introduite dans Windows PowerShell 2.0).</span><span class="sxs-lookup"><span data-stu-id="99995-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="99995-127">Pour plus d’informations sur la syntaxe de déclaration est utilisée pour spécifier le **applet de commande** d’attribut, consultez [déclaration d’attribut applet de commande](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="99995-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="99995-128">Définition de classe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="99995-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="99995-129">Le code suivant est la définition d’une classe d’applet de commande GetProc.</span><span class="sxs-lookup"><span data-stu-id="99995-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="99995-130">Notez que Pascal de la casse appropriée et que le nom de la classe inclut le verbe et un nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="99995-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="99995-131">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="99995-131">Pascal Casing</span></span>

<span data-ttu-id="99995-132">Lorsque vous nommez des applets de commande, utilisez Pascal casse.</span><span class="sxs-lookup"><span data-stu-id="99995-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="99995-133">Par exemple, le `Get-Item` et `Get-ItemProperty` applets de commande indiquent la façon correcte d’utiliser des majuscules lorsque vous nommez des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="99995-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="99995-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99995-134">See Also</span></span>

[<span data-ttu-id="99995-135">System.Management.Automation.CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="99995-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="99995-136">Déclaration CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="99995-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="99995-137">Noms de verbe de l’applet de commande</span><span class="sxs-lookup"><span data-stu-id="99995-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="99995-138">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="99995-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="99995-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="99995-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
