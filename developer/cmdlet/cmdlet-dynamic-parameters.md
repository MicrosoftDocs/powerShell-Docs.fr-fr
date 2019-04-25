---
title: Paramètres de l’applet de commande dynamique | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068536"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="5be70-102">Paramètres dynamiques des applets de commande</span><span class="sxs-lookup"><span data-stu-id="5be70-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="5be70-103">Applets de commande peut définir des paramètres qui sont disponibles à l’utilisateur sous certaines conditions, par exemple lorsque l’argument d’un autre paramètre est une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="5be70-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="5be70-104">Ces paramètres sont ajoutés lors de l’exécution et sont appelés *paramètres dynamiques* , car ils sont ajoutés uniquement lorsqu’elles sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5be70-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="5be70-105">Par exemple, vous pouvez concevoir une applet de commande qui ajoute plusieurs paramètres uniquement lorsqu’un paramètre de commutateur spécifique est spécifié.</span><span class="sxs-lookup"><span data-stu-id="5be70-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="5be70-106">Fournisseurs et des fonctions Windows PowerShell peuvent également définir des paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="5be70-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="5be70-107">Paramètres dynamiques dans les applets de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5be70-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="5be70-108">Windows PowerShell utilise des paramètres dynamiques dans plusieurs de ses applets de commande fournisseur.</span><span class="sxs-lookup"><span data-stu-id="5be70-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="5be70-109">Par exemple, le `Get-Item` et `Get-ChildItem` ajouter des applets de commande un `CodeSigningCert` paramètre lors de l’exécution lorsque le `Path` paramètre de l’applet de commande spécifie le chemin d’accès du fournisseur de certificat.</span><span class="sxs-lookup"><span data-stu-id="5be70-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="5be70-110">Si le `Path` paramètre de l’applet de commande spécifie un chemin d’accès pour un autre fournisseur, le `CodeSigningCert` paramètre n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="5be70-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="5be70-111">Les exemples suivants montrent comment la `CodeSigningCert` paramètre est ajouté lors de l’exécution lorsque le `Get-Item` applet de commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="5be70-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="5be70-112">Dans le premier exemple, le runtime Windows PowerShell a ajouté le paramètre, et l’applet de commande a réussi.</span><span class="sxs-lookup"><span data-stu-id="5be70-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="5be70-113">Dans le deuxième exemple, un lecteur de système de fichiers est spécifié, et une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="5be70-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="5be70-114">Le message d’erreur indique que le `CodeSigningCert` paramètre ne peut pas être trouvé.</span><span class="sxs-lookup"><span data-stu-id="5be70-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="5be70-115">Prise en charge pour les paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="5be70-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="5be70-116">Pour prendre en charge des paramètres dynamiques, le code de l’applet de commande doit inclure les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="5be70-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="5be70-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) cette interface fournit la méthode qui Récupère les paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="5be70-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="5be70-118">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5be70-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="5be70-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) cette méthode récupère l’objet qui contient les définitions de paramètre dynamique.</span><span class="sxs-lookup"><span data-stu-id="5be70-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="5be70-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5be70-120">Example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

<span data-ttu-id="5be70-121">Classe de paramètre dynamique cette classe définit les paramètres à ajouter.</span><span class="sxs-lookup"><span data-stu-id="5be70-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="5be70-122">Cette classe doit inclure un attribut de paramètre pour chaque paramètre et les attributs facultatifs Alias et la Validation qui sont requises par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5be70-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="5be70-123">Exemple :</span><span class="sxs-lookup"><span data-stu-id="5be70-123">Example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="5be70-124">Pour obtenir un exemple complet d’une applet de commande qui prend en charge des paramètres dynamiques, consultez [comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5be70-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5be70-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be70-125">See Also</span></span>

[<span data-ttu-id="5be70-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="5be70-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="5be70-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="5be70-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="5be70-128">Comment déclarer des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="5be70-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="5be70-129">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5be70-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
