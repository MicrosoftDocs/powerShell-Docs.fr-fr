---
ms.date: 09/13/2016
ms.topic: reference
title: Déclaration de l’attribut Credential
description: Déclaration de l’attribut Credential
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648608"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="f4527-103">Déclaration de l’attribut Credential</span><span class="sxs-lookup"><span data-stu-id="f4527-103">Credential Attribute Declaration</span></span>

<span data-ttu-id="f4527-104">L’attribut Credential est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="f4527-104">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f4527-105">Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="f4527-105">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="f4527-106">Par exemple, l’applet de commande [« obtenir des informations d’identification »](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) utilise cet attribut pour que Windows PowerShell génère l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) qui est retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="f4527-106">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4527-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4527-107">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="f4527-108">Notes</span><span class="sxs-lookup"><span data-stu-id="f4527-108">Remarks</span></span>

- <span data-ttu-id="f4527-109">En général, cet attribut est utilisé par les paramètres de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="f4527-109">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="f4527-110">Quand un objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) est passé au paramètre, Windows PowerShell ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="f4527-110">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="f4527-111">Lors de la création de l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell utilise l’hôte actuel pour afficher les invites appropriées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f4527-111">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="f4527-112">Par exemple, l’hôte par défaut affiche une invite pour un nom d’utilisateur et un mot de passe lorsque cet attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f4527-112">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="f4527-113">Toutefois, si un hôte personnalisé est utilisé et définit une invite différente, l’invite s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f4527-113">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="f4527-114">Cet attribut est utilisé avec l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="f4527-114">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="f4527-115">Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="f4527-115">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="f4527-116">L’attribut Credential est défini par la classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f4527-116">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4527-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4527-117">See Also</span></span>

[<span data-ttu-id="f4527-118">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="f4527-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="f4527-119">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="f4527-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="f4527-120">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f4527-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
