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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861405"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="25813-102">Définition de méthodes par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="25813-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="25813-103">Lorsque vous étendez des objets .NET Framework, vous pouvez ajouter des méthodes de code et les méthodes de script pour les objets.</span><span class="sxs-lookup"><span data-stu-id="25813-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="25813-104">Le code XML qui est utilisé pour définir ces méthodes est décrite dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="25813-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="25813-105">Les exemples dans les sections suivantes sont à partir du fichier de types Types.ps1xml dans le répertoire d’installation de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="25813-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="25813-106">Méthodes de code</span><span class="sxs-lookup"><span data-stu-id="25813-106">Code Methods</span></span>

<span data-ttu-id="25813-107">Une méthode de code fait référence à une méthode statique d’un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25813-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="25813-108">Dans l’exemple suivant, le **ConvertLargeIntegerToInt64** méthode est ajoutée à la [System.Xml.Xmlnode ? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type.</span><span class="sxs-lookup"><span data-stu-id="25813-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="25813-109">Le [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) élément définit la méthode étendue en tant qu’une méthode de code.</span><span class="sxs-lookup"><span data-stu-id="25813-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="25813-110">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="25813-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="25813-111">Et, le [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) élément spécifie la méthode statique.</span><span class="sxs-lookup"><span data-stu-id="25813-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="25813-112">(Vous pouvez également ajouter le [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="25813-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="25813-113">Méthodes de script</span><span class="sxs-lookup"><span data-stu-id="25813-113">Script Methods</span></span>

<span data-ttu-id="25813-114">Une méthode de script définit une méthode dont la valeur est la sortie d’un script.</span><span class="sxs-lookup"><span data-stu-id="25813-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="25813-115">Dans l’exemple suivant, le **ConvertToDateTime** méthode est ajoutée à la [System.Management.Managementobject ? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type.</span><span class="sxs-lookup"><span data-stu-id="25813-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="25813-116">Le [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) élément définit la méthode étendue en tant qu’une méthode de script.</span><span class="sxs-lookup"><span data-stu-id="25813-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="25813-117">Le [nom](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) élément spécifie le nom de la méthode étendue.</span><span class="sxs-lookup"><span data-stu-id="25813-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="25813-118">Et, le [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) élément spécifie le script qui génère la valeur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="25813-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="25813-119">(Vous pouvez également ajouter le [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) élément aux membres de la [jeux de membres](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) élément.)</span><span class="sxs-lookup"><span data-stu-id="25813-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25813-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25813-120">See Also</span></span>

[<span data-ttu-id="25813-121">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="25813-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)