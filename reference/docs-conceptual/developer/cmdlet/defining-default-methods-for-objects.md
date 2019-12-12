---
title: Définition des méthodes par défaut pour les objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365688"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="4029c-102">Définition de méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="4029c-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="4029c-103">Lorsque vous étendez .NET Framework objets, vous pouvez ajouter des méthodes de code et des méthodes de script aux objets.</span><span class="sxs-lookup"><span data-stu-id="4029c-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="4029c-104">Le code XML utilisé pour définir ces méthodes est décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="4029c-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4029c-105">Les exemples des sections suivantes proviennent du fichier de types `Types.ps1xml` dans le répertoire d’installation de Windows PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="4029c-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="4029c-106">Pour plus d’informations, consultez [à propos des types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="4029c-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="4029c-107">Méthodes de code</span><span class="sxs-lookup"><span data-stu-id="4029c-107">Code methods</span></span>

<span data-ttu-id="4029c-108">Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4029c-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="4029c-109">Dans l’exemple suivant, la méthode **ToString** est ajoutée au type [System. Xml. XMLNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="4029c-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="4029c-110">L’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) définit la méthode étendue comme une méthode de code.</span><span class="sxs-lookup"><span data-stu-id="4029c-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="4029c-111">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="4029c-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="4029c-112">Et, l’élément [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) spécifie la méthode statique.</span><span class="sxs-lookup"><span data-stu-id="4029c-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="4029c-113">Vous pouvez également ajouter l’élément [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="4029c-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="4029c-114">Méthodes de script</span><span class="sxs-lookup"><span data-stu-id="4029c-114">Script methods</span></span>

<span data-ttu-id="4029c-115">Une méthode de script définit une méthode dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="4029c-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="4029c-116">Dans l’exemple suivant, la méthode **ConvertToDateTime** est ajoutée au type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="4029c-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="4029c-117">L’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) définit la méthode étendue comme une méthode de script.</span><span class="sxs-lookup"><span data-stu-id="4029c-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="4029c-118">L’élément [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="4029c-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="4029c-119">Et l’élément [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) spécifie le script qui génère la valeur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4029c-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="4029c-120">Vous pouvez également ajouter l’élément [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) aux membres de l’élément [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="4029c-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4029c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4029c-121">See also</span></span>

[<span data-ttu-id="4029c-122">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4029c-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
