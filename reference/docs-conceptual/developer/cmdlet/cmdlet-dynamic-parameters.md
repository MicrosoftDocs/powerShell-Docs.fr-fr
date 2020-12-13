---
ms.date: 09/13/2016
ms.topic: reference
title: Paramètres dynamiques des applets de commande
description: Paramètres dynamiques des applets de commande
ms.openlocfilehash: b44dda2354e8b689e419c7bf4deefadfc4edcb07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653435"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="1b6bf-103">Paramètres dynamiques des applets de commande</span><span class="sxs-lookup"><span data-stu-id="1b6bf-103">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="1b6bf-104">Les applets de commande peuvent définir des paramètres qui sont disponibles pour l’utilisateur dans des conditions spéciales, par exemple lorsque l’argument d’un autre paramètre est une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-104">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="1b6bf-105">Ces paramètres sont ajoutés au moment de l’exécution et sont appelés paramètres dynamiques, car ils sont ajoutés uniquement lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-105">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="1b6bf-106">Par exemple, vous pouvez concevoir une applet de commande qui ajoute plusieurs paramètres uniquement lorsqu’un paramètre de commutateur spécifique est spécifié.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-106">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="1b6bf-107">Les fournisseurs et les fonctions PowerShell peuvent également définir des paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-107">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="1b6bf-108">Paramètres dynamiques dans les applets de commande PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b6bf-108">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="1b6bf-109">PowerShell utilise des paramètres dynamiques dans plusieurs de ses applets de commande de fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-109">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="1b6bf-110">Par exemple, les `Get-Item` applets de commande et `Get-ChildItem` ajoutent un paramètre **CodeSigningCert** au moment de l’exécution lorsque le paramètre **path** spécifie le chemin d’accès du fournisseur de **certificats** .</span><span class="sxs-lookup"><span data-stu-id="1b6bf-110">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="1b6bf-111">Si le paramètre **path** spécifie un chemin d’accès pour un autre fournisseur, le paramètre **CodeSigningCert** n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-111">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="1b6bf-112">Les exemples suivants montrent comment le paramètre **CodeSigningCert** est ajouté lors de l’exécution lors de l' `Get-Item` exécution de.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-112">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="1b6bf-113">Dans cet exemple, le runtime PowerShell a ajouté le paramètre et l’applet de commande est réussie.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-113">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="1b6bf-114">Dans cet exemple, un lecteur de **système de fichiers** est spécifié et une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-114">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="1b6bf-115">Le message d’erreur indique que le paramètre **CodeSigningCert** est introuvable.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-115">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="1b6bf-116">Prise en charge des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="1b6bf-116">Support for dynamic parameters</span></span>

<span data-ttu-id="1b6bf-117">Pour prendre en charge les paramètres dynamiques, les éléments suivants doivent être inclus dans le code de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-117">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="1b6bf-118">Interface</span><span class="sxs-lookup"><span data-stu-id="1b6bf-118">Interface</span></span>

<span data-ttu-id="1b6bf-119">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="1b6bf-119">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="1b6bf-120">Cette interface fournit la méthode qui récupère les paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-120">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="1b6bf-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1b6bf-121">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="1b6bf-122">Méthode</span><span class="sxs-lookup"><span data-stu-id="1b6bf-122">Method</span></span>

<span data-ttu-id="1b6bf-123">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="1b6bf-123">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="1b6bf-124">Cette méthode récupère l’objet qui contient les définitions de paramètres dynamiques.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-124">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="1b6bf-125">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1b6bf-125">For example:</span></span>

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

### <a name="class"></a><span data-ttu-id="1b6bf-126">Classe</span><span class="sxs-lookup"><span data-stu-id="1b6bf-126">Class</span></span>

<span data-ttu-id="1b6bf-127">Classe qui définit les paramètres dynamiques à ajouter.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-127">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="1b6bf-128">Cette classe doit inclure un attribut de **paramètre** pour chaque paramètre et tout **alias** facultatif et attributs de **validation** requis par l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="1b6bf-128">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="1b6bf-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1b6bf-129">For example:</span></span>

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

<span data-ttu-id="1b6bf-130">Pour obtenir un exemple complet d’une applet de commande qui prend en charge les paramètres dynamiques, consultez [comment déclarer des paramètres dynamiques](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1b6bf-130">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b6bf-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b6bf-131">See also</span></span>

[<span data-ttu-id="1b6bf-132">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="1b6bf-132">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="1b6bf-133">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="1b6bf-133">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="1b6bf-134">Guide pratique pour déclarer des paramètres dynamiques</span><span class="sxs-lookup"><span data-stu-id="1b6bf-134">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="1b6bf-135">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1b6bf-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
