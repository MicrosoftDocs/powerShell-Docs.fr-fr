---
title: Déclaration d’attribut Credential | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369888"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="bc91a-102">Déclaration de l’attribut Credential</span><span class="sxs-lookup"><span data-stu-id="bc91a-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="bc91a-103">L’attribut Credential est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc91a-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bc91a-104">Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="bc91a-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="bc91a-105">Par exemple, l’applet de commande [« obtenir des informations d’identification »](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) utilise cet attribut pour que Windows PowerShell génère l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) qui est retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="bc91a-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc91a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc91a-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="bc91a-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="bc91a-107">Remarks</span></span>

- <span data-ttu-id="bc91a-108">En général, cet attribut est utilisé par les paramètres de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc91a-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="bc91a-109">Quand un objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) est passé au paramètre, Windows PowerShell ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="bc91a-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="bc91a-110">Lors de la création de l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell utilise l’hôte actuel pour afficher les invites appropriées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc91a-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="bc91a-111">Par exemple, l’hôte par défaut affiche une invite pour un nom d’utilisateur et un mot de passe lorsque cet attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="bc91a-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="bc91a-112">Toutefois, si un hôte personnalisé est utilisé et définit une invite différente, l’invite s’affiche.</span><span class="sxs-lookup"><span data-stu-id="bc91a-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="bc91a-113">Cet attribut est utilisé avec l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="bc91a-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="bc91a-114">Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="bc91a-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="bc91a-115">L’attribut Credential est défini par la classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="bc91a-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc91a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc91a-116">See Also</span></span>

[<span data-ttu-id="bc91a-117">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="bc91a-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="bc91a-118">Déclaration d’attribut de paramètre</span><span class="sxs-lookup"><span data-stu-id="bc91a-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="bc91a-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc91a-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
