---
ms.date: 09/13/2016
ms.topic: reference
title: Définition de méthodes par défaut pour les objets
description: Définition de méthodes par défaut pour les objets
ms.openlocfilehash: c65ca91a7038f32d8c3ef62cfe7881e5ad4dba5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355525"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="eb787-103">Définition de méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="eb787-103">Defining Default Methods for Objects</span></span>

<span data-ttu-id="eb787-104">Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des méthodes de code et des méthodes de script aux objets.</span><span class="sxs-lookup"><span data-stu-id="eb787-104">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="eb787-105">Le code XML utilisé pour définir ces méthodes est décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="eb787-105">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="eb787-106">Les exemples des sections suivantes proviennent du `Types.ps1xml` fichier types dans le répertoire d’installation de Windows PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="eb787-106">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="eb787-107">Pour plus d’informations, consultez [à propos de Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="eb787-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="eb787-108">Méthodes de code</span><span class="sxs-lookup"><span data-stu-id="eb787-108">Code methods</span></span>

<span data-ttu-id="eb787-109">Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb787-109">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="eb787-110">Dans l’exemple suivant, la méthode **ToString** est ajoutée au type de [ nœudSystem.Xml.Xml](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="eb787-110">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="eb787-111">L’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) définit la méthode étendue comme une méthode de code.</span><span class="sxs-lookup"><span data-stu-id="eb787-111">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="eb787-112">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="eb787-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="eb787-113">Et, l’élément [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) spécifie la méthode statique.</span><span class="sxs-lookup"><span data-stu-id="eb787-113">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="eb787-114">Vous pouvez également ajouter l’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="eb787-114">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="eb787-115">Méthodes de script</span><span class="sxs-lookup"><span data-stu-id="eb787-115">Script methods</span></span>

<span data-ttu-id="eb787-116">Une méthode de script définit une méthode dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="eb787-116">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="eb787-117">Dans l’exemple suivant, la méthode **ConvertToDateTime** est ajoutée au type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="eb787-117">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="eb787-118">L’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) définit la méthode étendue comme une méthode de script.</span><span class="sxs-lookup"><span data-stu-id="eb787-118">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) element defines the extended method as a script method.</span></span> <span data-ttu-id="eb787-119">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="eb787-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="eb787-120">Et l’élément [script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) spécifie le script qui génère la valeur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="eb787-120">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="eb787-121">Vous pouvez également ajouter l’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="eb787-121">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="eb787-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb787-122">See also</span></span>

[<span data-ttu-id="eb787-123">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eb787-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
