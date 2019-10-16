---
title: Déclaration de classe d’applet de commande | Microsoft Docs
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
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363518"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="4ea0a-102">Déclaration de classe d’applets de commande</span><span class="sxs-lookup"><span data-stu-id="4ea0a-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="4ea0a-103">Une classe Microsoft .NET Framework est déclarée en tant qu’applet de commande en spécifiant l’attribut d' **applet** de commande en tant que métadonnées pour la classe.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="4ea0a-104">(L’attribut d' **applet** de commande est le seul attribut requis pour toutes les applets de commande).</span><span class="sxs-lookup"><span data-stu-id="4ea0a-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="4ea0a-105">Lorsque vous spécifiez l’attribut d' **applet** de commande, vous devez spécifier la paire verbe-and-substantif qui identifie l’applet de commande auprès de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="4ea0a-106">Et, vous devez décrire les fonctionnalités de Windows PowerShell prises en charge par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="4ea0a-107">Pour plus d’informations sur la syntaxe de déclaration utilisée pour spécifier l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4ea0a-108">L’attribut d' **applet** de commande est défini par la classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="4ea0a-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="4ea0a-109">Les propriétés de cette classe correspondent aux paramètres de déclaration utilisés lorsque vous déclarez l’attribut.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="4ea0a-110">Noms</span><span class="sxs-lookup"><span data-stu-id="4ea0a-110">Nouns</span></span>

<span data-ttu-id="4ea0a-111">Le nom de l’applet de commande spécifie les ressources sur lesquelles agit l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="4ea0a-112">Le substantif fait la différence entre vos applets de commande et d’autres applets de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="4ea0a-113">Les noms des applets de commande doivent être spécifiques, et dans le cas de noms génériques, tels que *serveur*, il est préférable d’ajouter un préfixe abrégé qui différencie votre ressource des autres ressources similaires.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="4ea0a-114">Par exemple, un nom d’applet de commande incluant un nom avec un préfixe est `Get-SQLServer`.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="4ea0a-115">La combinaison d’un nom spécifique avec un verbe plus général permet à l’utilisateur de localiser rapidement l’applet de commande en fonction de son action, puis d’identifier l’applet de commande par sa ressource tout en évitant les doublons de noms d’applets de commande inutiles.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="4ea0a-116">Pour obtenir la liste des caractères spéciaux qui ne peuvent pas être utilisés dans les noms d’applets de commande, consultez [instructions de développement requises](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="4ea0a-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="4ea0a-117">Verbes</span><span class="sxs-lookup"><span data-stu-id="4ea0a-117">Verbs</span></span>

<span data-ttu-id="4ea0a-118">Lorsque vous spécifiez un verbe, les instructions de développement vous obligent à utiliser l’un des verbes prédéfinis fournis par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="4ea0a-119">En utilisant l’un de ces verbes prédéfinis, vous assurez la cohérence entre les applets de commande que vous écrivez et les applets de commande écrites par Microsoft et par d’autres.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="4ea0a-120">Par exemple, le verbe « obtenir » est utilisé pour les applets de commande qui récupèrent des données.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="4ea0a-121">Pour plus d’informations sur les instructions pour les verbes, consultez [noms des verbes d’applet](./approved-verbs-for-windows-powershell-commands.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="4ea0a-122">Pour obtenir la liste des caractères spéciaux qui ne peuvent pas être utilisés dans les noms d’applets de commande, consultez [instructions de développement requises](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="4ea0a-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="4ea0a-123">Prise en charge des fonctionnalités de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ea0a-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="4ea0a-124">L’attribut **cmdlet** vous permet également de spécifier que votre applet de commande prend en charge certaines des fonctionnalités communes fournies par Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="4ea0a-125">Cela comprend la prise en charge de fonctionnalités communes telles que la confirmation de commentaires des utilisateurs (appelée prise en charge de la fonctionnalité ShouldProcess) et la prise en charge des transactions.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="4ea0a-126">(La prise en charge des transactions a été introduite dans Windows PowerShell 2,0).</span><span class="sxs-lookup"><span data-stu-id="4ea0a-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="4ea0a-127">Pour plus d’informations sur la syntaxe de déclaration utilisée pour spécifier l’attribut d' **applet** de commande, consultez [déclaration d’attribut d’applet](./cmdlet-attribute-declaration.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="4ea0a-128">Définition de la classe cmdlet</span><span class="sxs-lookup"><span data-stu-id="4ea0a-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="4ea0a-129">Le code suivant est la définition d’une classe d’applet de commande GetProc.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="4ea0a-130">Notez que la casse Pascal est utilisée et que le nom de la classe comprend le verbe et le nom de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="4ea0a-131">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="4ea0a-131">Pascal Casing</span></span>

<span data-ttu-id="4ea0a-132">Lorsque vous nommez des applets de commande, utilisez la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="4ea0a-133">Par exemple, les applets de commande `Get-Item` et `Get-ItemProperty` montrent la méthode correcte pour utiliser la mise en majuscules lorsque vous nommez des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="4ea0a-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ea0a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ea0a-134">See Also</span></span>

[<span data-ttu-id="4ea0a-135">System. Management. Automation. CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="4ea0a-135">System.Management.Automation.CmdletAttribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="4ea0a-136">Déclaration CmdletAttribute</span><span class="sxs-lookup"><span data-stu-id="4ea0a-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="4ea0a-137">Noms des verbes d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="4ea0a-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="4ea0a-138">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4ea0a-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="4ea0a-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="4ea0a-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
