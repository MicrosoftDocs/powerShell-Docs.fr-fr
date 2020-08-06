---
title: Déclaration d’attribut Credential | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a6deca52fa6c9e46138ae92401f58ac5dbd15852
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784365"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="15aa6-102">Déclaration de l’attribut Credential</span><span class="sxs-lookup"><span data-stu-id="15aa6-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="15aa6-103">L’attribut Credential est un attribut facultatif qui peut être utilisé avec les paramètres d’informations d’identification de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="15aa6-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="15aa6-104">Lorsque cet attribut est ajouté à une déclaration de paramètre, Windows PowerShell convertit l’entrée de chaîne en objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="15aa6-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="15aa6-105">Par exemple, l’applet de commande [« obtenir des informations d’identification »](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) utilise cet attribut pour que Windows PowerShell génère l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) qui est retourné par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="15aa6-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="15aa6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15aa6-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="15aa6-107">Notes</span><span class="sxs-lookup"><span data-stu-id="15aa6-107">Remarks</span></span>

- <span data-ttu-id="15aa6-108">En général, cet attribut est utilisé par les paramètres de type [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) afin qu’une chaîne puisse également être passée comme argument au paramètre.</span><span class="sxs-lookup"><span data-stu-id="15aa6-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="15aa6-109">Quand un objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) est passé au paramètre, Windows PowerShell ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="15aa6-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="15aa6-110">Lors de la création de l’objet [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell utilise l’hôte actuel pour afficher les invites appropriées à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="15aa6-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="15aa6-111">Par exemple, l’hôte par défaut affiche une invite pour un nom d’utilisateur et un mot de passe lorsque cet attribut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="15aa6-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="15aa6-112">Toutefois, si un hôte personnalisé est utilisé et définit une invite différente, l’invite s’affiche.</span><span class="sxs-lookup"><span data-stu-id="15aa6-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="15aa6-113">Cet attribut est utilisé avec l’attribut Parameter.</span><span class="sxs-lookup"><span data-stu-id="15aa6-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="15aa6-114">Pour plus d’informations sur cet attribut, consultez [déclaration d’attribut de paramètre](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="15aa6-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="15aa6-115">L’attribut Credential est défini par la classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="15aa6-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="15aa6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15aa6-116">See Also</span></span>

[<span data-ttu-id="15aa6-117">Alias de paramètres</span><span class="sxs-lookup"><span data-stu-id="15aa6-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="15aa6-118">Déclaration de l’attribut Parameter</span><span class="sxs-lookup"><span data-stu-id="15aa6-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="15aa6-119">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15aa6-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
