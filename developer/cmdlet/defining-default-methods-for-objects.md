---
title: Définition de méthodes par défaut des objets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733979"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="65275-102">Définition de méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="65275-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="65275-103">Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter des méthodes de code et les méthodes de script pour les objets.</span><span class="sxs-lookup"><span data-stu-id="65275-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="65275-104">Le code XML qui est utilisé pour définir ces méthodes est décrite dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="65275-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="65275-105">Les exemples dans les sections suivantes sont à partir du fichier de types Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="65275-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="65275-106">Méthodes de code</span><span class="sxs-lookup"><span data-stu-id="65275-106">Code Methods</span></span>

<span data-ttu-id="65275-107">Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65275-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="65275-108">Dans l’exemple suivant, le **ConvertLargeIntegerToInt64** méthode est ajoutée à la [System.Xml.Xmlnode ? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type.</span><span class="sxs-lookup"><span data-stu-id="65275-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="65275-109">Le [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) élément définit la méthode étendue en tant qu’une méthode de code.</span><span class="sxs-lookup"><span data-stu-id="65275-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="65275-110">Le [nom](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) élément spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="65275-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="65275-111">Et, le [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) élément spécifie la méthode statique.</span><span class="sxs-lookup"><span data-stu-id="65275-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="65275-112">(Vous pouvez également ajouter le [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) élément aux membres de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) élément.)</span><span class="sxs-lookup"><span data-stu-id="65275-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="65275-113">Méthodes de script</span><span class="sxs-lookup"><span data-stu-id="65275-113">Script Methods</span></span>

<span data-ttu-id="65275-114">Une méthode de script définit une méthode dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="65275-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="65275-115">Dans l’exemple suivant, le **ConvertToDateTime** méthode est ajoutée à la [System.Management.Managementobject ? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type.</span><span class="sxs-lookup"><span data-stu-id="65275-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="65275-116">Le [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) élément définit la méthode étendue en tant qu’une méthode de script.</span><span class="sxs-lookup"><span data-stu-id="65275-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="65275-117">Le [nom](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) élément spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="65275-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="65275-118">Et, le [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) élément spécifie le script qui génère la valeur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="65275-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="65275-119">(Vous pouvez également ajouter le [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) élément aux membres de la [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) élément.)</span><span class="sxs-lookup"><span data-stu-id="65275-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="65275-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65275-120">See Also</span></span>

[<span data-ttu-id="65275-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="65275-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
