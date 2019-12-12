---
title: Comment déclarer des jeux de paramètres | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365608"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="c2c3e-102">Guide pratique pour déclarer des jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="c2c3e-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="c2c3e-103">Cet exemple montre comment définir deux jeux de paramètres lorsque vous déclarez les paramètres d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="c2c3e-104">Chaque jeu de paramètres possède un paramètre unique et un paramètre partagé qui est utilisé par les deux jeux de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="c2c3e-105">Pour plus d’informations sur les jeux de paramètres, notamment sur la manière de spécifier le jeu de paramètres par défaut, consultez Jeux de paramètres d' [applet](./cmdlet-parameter-sets.md)de commande.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2c3e-106">Dans la mesure du possible, définissez le paramètre unique d’un jeu de paramètres comme paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="c2c3e-107">Toutefois, si vous souhaitez que votre applet de commande s’exécute sans spécifier de paramètres, le paramètre unique peut être un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="c2c3e-108">Par exemple, le paramètre unique de l’applet de commande `Get-Command` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="c2c3e-109">Comment définir deux jeux de paramètres</span><span class="sxs-lookup"><span data-stu-id="c2c3e-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="c2c3e-110">Ajoutez le mot clé `ParameterSet` à l’attribut de paramètre pour le paramètre unique du premier jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. <span data-ttu-id="c2c3e-111">Ajoutez le mot clé `ParameterSet` à l’attribut de paramètre pour le paramètre unique du deuxième jeu de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. <span data-ttu-id="c2c3e-112">Pour le paramètre qui appartient aux deux jeux de paramètres, ajoutez un attribut de paramètre pour chaque jeu de paramètres, puis ajoutez le mot clé `ParameterSet` à chaque ensemble.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="c2c3e-113">Dans chaque attribut de paramètre, vous pouvez spécifier la façon dont ce paramètre est défini.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="c2c3e-114">Un paramètre peut être facultatif dans un jeu et obligatoire dans un autre.</span><span class="sxs-lookup"><span data-stu-id="c2c3e-114">A parameter can be optional in one set and mandatory in another.</span></span>

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a><span data-ttu-id="c2c3e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2c3e-115">See Also</span></span>

[<span data-ttu-id="c2c3e-116">Ensembles de paramètres d’applet de commande</span><span class="sxs-lookup"><span data-stu-id="c2c3e-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="c2c3e-117">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2c3e-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
