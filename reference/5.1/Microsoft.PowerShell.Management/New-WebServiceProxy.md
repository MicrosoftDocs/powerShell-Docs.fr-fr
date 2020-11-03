---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203586"
---
# <span data-ttu-id="e9477-103">New-WebServiceProxy</span><span class="sxs-lookup"><span data-stu-id="e9477-103">New-WebServiceProxy</span></span>

## <span data-ttu-id="e9477-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e9477-104">SYNOPSIS</span></span>
<span data-ttu-id="e9477-105">Crée un objet proxy de service Web qui vous permet d’utiliser et de gérer le service Web dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9477-105">Creates a Web service proxy object that lets you use and manage the Web service in PowerShell.</span></span>

## <span data-ttu-id="e9477-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e9477-106">SYNTAX</span></span>

### <span data-ttu-id="e9477-107">Informations d’identification (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e9477-107">NoCredentials (Default)</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### <span data-ttu-id="e9477-108">Informations d'identification</span><span class="sxs-lookup"><span data-stu-id="e9477-108">Credential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="e9477-109">UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="e9477-109">UseDefaultCredential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## <span data-ttu-id="e9477-110">Description</span><span class="sxs-lookup"><span data-stu-id="e9477-110">DESCRIPTION</span></span>

<span data-ttu-id="e9477-111">L' `New-WebServiceProxy` applet de commande vous permet d’utiliser un service Web dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9477-111">The `New-WebServiceProxy` cmdlet lets you use a Web service in PowerShell.</span></span> <span data-ttu-id="e9477-112">L’applet de commande se connecte à un service Web et crée un objet proxy de service Web dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9477-112">The cmdlet connects to a Web service and creates a Web service proxy object in PowerShell.</span></span> <span data-ttu-id="e9477-113">Vous pouvez utiliser l'objet proxy pour gérer le service Web.</span><span class="sxs-lookup"><span data-stu-id="e9477-113">You can use the proxy object to manage the Web service.</span></span>

<span data-ttu-id="e9477-114">Un service Web est un programme XML qui échange des données sur un réseau, en particulier sur Internet.</span><span class="sxs-lookup"><span data-stu-id="e9477-114">A Web service is an XML-based program that exchanges data over a network, especially over the Internet.</span></span> <span data-ttu-id="e9477-115">Microsoft .NET Framework fournit des objets proxy de service Web qui représentent le service Web sous la forme d'un objet .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9477-115">The Microsoft .NET Framework provides Web service proxy objects that represent the Web service as a .NET Framework object.</span></span>

## <span data-ttu-id="e9477-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e9477-116">EXAMPLES</span></span>

### <span data-ttu-id="e9477-117">Exemple 1 : créer un proxy pour un service Web</span><span class="sxs-lookup"><span data-stu-id="e9477-117">Example 1: Create a proxy for a Web service</span></span>

<span data-ttu-id="e9477-118">Cet exemple crée un proxy .NET Framework du service Web Calculator dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9477-118">This example creates a .NET Framework proxy of the calculator Web service in Windows PowerShell.</span></span>

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### <span data-ttu-id="e9477-119">Exemple 2 : créer un proxy pour un service Web et spécifier l’espace de noms et la classe</span><span class="sxs-lookup"><span data-stu-id="e9477-119">Example 2: Create a proxy for a Web service and specify namespace and class</span></span>

<span data-ttu-id="e9477-120">Cet exemple utilise l' `New-WebServiceProxy` applet de commande pour créer un proxy .NET Framework du service Web Calculator.</span><span class="sxs-lookup"><span data-stu-id="e9477-120">This example uses the `New-WebServiceProxy` cmdlet to create a .NET Framework proxy of the calculator Web service.</span></span>

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

<span data-ttu-id="e9477-121">La commande utilise le paramètre **URI** pour spécifier l’URI et les paramètres d' **espace de noms** et de **classe** pour spécifier l’espace de noms et la classe de l’objet.</span><span class="sxs-lookup"><span data-stu-id="e9477-121">The command uses the **Uri** parameter to specify the URI and the **Namespace** and **Class** parameters to specify the namespace and class of the object.</span></span>

### <span data-ttu-id="e9477-122">Exemple 3 : afficher les méthodes d’un proxy de service Web</span><span class="sxs-lookup"><span data-stu-id="e9477-122">Example 3: Display methods of a Web service proxy</span></span>

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

<span data-ttu-id="e9477-123">Cet exemple utilise l' `Get-Member` applet de commande pour afficher les méthodes de l’objet proxy de service Web dans la `$calc` variable.</span><span class="sxs-lookup"><span data-stu-id="e9477-123">This example uses the `Get-Member` cmdlet to display the methods of the Web service proxy object in the `$calc` variable.</span></span> <span data-ttu-id="e9477-124">Nous utilisons ces méthodes dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e9477-124">We uses these methods in the following example.</span></span>

<span data-ttu-id="e9477-125">Notez que le **TypeName** de l’objet proxy, WebServiceProxy, reflète les noms de l’espace de noms et de la classe qui ont été spécifiés dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="e9477-125">Notice that the **TypeName** of the proxy object, WebServiceProxy, reflects the namespace and class names that were specified in the previous example.</span></span>

### <span data-ttu-id="e9477-126">Exemple 4 : utiliser un proxy de service Web</span><span class="sxs-lookup"><span data-stu-id="e9477-126">Example 4: Use a Web service proxy</span></span>

```powershell
PS> $calc.Multiply(6,7)
42
```

<span data-ttu-id="e9477-127">Cet exemple utilise le proxy de service Web stocké dans la `$calc` variable.</span><span class="sxs-lookup"><span data-stu-id="e9477-127">This example uses the Web service proxy stored in the `$calc` variable.</span></span> <span data-ttu-id="e9477-128">La commande utilise la méthode **Multiply** du proxy.</span><span class="sxs-lookup"><span data-stu-id="e9477-128">The command uses the **Multiply** method of the proxy.</span></span>

## <span data-ttu-id="e9477-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e9477-129">PARAMETERS</span></span>

### <span data-ttu-id="e9477-130">-Classe</span><span class="sxs-lookup"><span data-stu-id="e9477-130">-Class</span></span>

<span data-ttu-id="e9477-131">Spécifie le nom de la classe proxy que l'applet de commande crée pour le service Web.</span><span class="sxs-lookup"><span data-stu-id="e9477-131">Specifies a name for the proxy class that the cmdlet creates for the Web service.</span></span> <span data-ttu-id="e9477-132">La valeur de ce paramètre est utilisée avec le paramètre **namespace** pour fournir un nom qualifié complet pour la classe.</span><span class="sxs-lookup"><span data-stu-id="e9477-132">The value of this parameter is used together with the **Namespace** parameter to provide a fully qualified name for the class.</span></span> <span data-ttu-id="e9477-133">La valeur par défaut est générée à partir de l’Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e9477-133">The default value is generated from the Uniform Resource Identifier (URI).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9477-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="e9477-134">-Credential</span></span>

<span data-ttu-id="e9477-135">Spécifie un compte d’utilisateur qui a l’autorisation d’exécuter cette action.</span><span class="sxs-lookup"><span data-stu-id="e9477-135">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="e9477-136">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e9477-136">The default is the current user.</span></span> <span data-ttu-id="e9477-137">Vous pouvez procéder de la sorte au lieu d'utiliser le paramètre **UseDefaultCredential** .</span><span class="sxs-lookup"><span data-stu-id="e9477-137">This is an alternative to using the **UseDefaultCredential** parameter.</span></span>

<span data-ttu-id="e9477-138">Tapez un nom d’utilisateur, tel que User01 ou Domaine01\utilisateur01, ou entrez un objet **PSCredential** , tel que celui généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="e9477-138">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="e9477-139">Si vous tapez un nom d’utilisateur, cette applet de commande vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e9477-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9477-140">-Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e9477-140">-Namespace</span></span>

<span data-ttu-id="e9477-141">Spécifie un espace de noms pour la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="e9477-141">Specifies a namespace for the new class.</span></span>

<span data-ttu-id="e9477-142">La valeur de ce paramètre est utilisée avec la valeur du paramètre **Class** pour générer un nom qualifié complet pour la classe.</span><span class="sxs-lookup"><span data-stu-id="e9477-142">The value of this parameter is used together with the value of the **Class** parameter to generate a fully qualified name for the class.</span></span> <span data-ttu-id="e9477-143">La valeur par défaut est **Microsoft. PowerShell. Commands. NewWebserviceProxy. AutogeneratedTypes** plus un type qui est généré à partir de l’URI.</span><span class="sxs-lookup"><span data-stu-id="e9477-143">The default value is **Microsoft.PowerShell.Commands.NewWebserviceProxy.AutogeneratedTypes** plus a type that is generated from the URI.</span></span>

<span data-ttu-id="e9477-144">Vous pouvez définir la valeur du paramètre d' **espace de noms** afin de pouvoir accéder à plusieurs services Web qui portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="e9477-144">You can set the value of the **Namespace** parameter so that you can access multiple Web services that have the same name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9477-145">-URI</span><span class="sxs-lookup"><span data-stu-id="e9477-145">-Uri</span></span>

<span data-ttu-id="e9477-146">Spécifie l'URI du service Web.</span><span class="sxs-lookup"><span data-stu-id="e9477-146">Specifies the URI of the Web service.</span></span> <span data-ttu-id="e9477-147">Entrez un URI ou le chemin d’accès et le nom de fichier d’un fichier qui contient une description de service.</span><span class="sxs-lookup"><span data-stu-id="e9477-147">Enter a URI or the path and filename of a file that contains a service description.</span></span>

<span data-ttu-id="e9477-148">L’URI doit retourner une `.asmx` page ou une page qui retourne une description de service.</span><span class="sxs-lookup"><span data-stu-id="e9477-148">The URI must return an `.asmx` page or to a page that returns a service description.</span></span> <span data-ttu-id="e9477-149">Pour retourner une description de service d’un service Web créé à l’aide de ASP.NET, ajoutez « ? WSDL "à l’URL du service Web (par exemple, `http://www.contoso.com/MyWebService.asmx?WSDL` ).</span><span class="sxs-lookup"><span data-stu-id="e9477-149">To return a service description of a Web service that was created using ASP.NET, append "?WSDL" to the URL of the Web service (for example, `http://www.contoso.com/MyWebService.asmx?WSDL`).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9477-150">-UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="e9477-150">-UseDefaultCredential</span></span>

<span data-ttu-id="e9477-151">Indique que cette applet de commande utilise les informations d’identification par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9477-151">Indicates that this cmdlet uses the default credential.</span></span> <span data-ttu-id="e9477-152">Cette applet de commande affecte la valeur true à la propriété **UseDefaultCredential** de l’objet proxy résultant.</span><span class="sxs-lookup"><span data-stu-id="e9477-152">This cmdlet sets the **UseDefaultCredential** property in the resulting proxy object to True.</span></span> <span data-ttu-id="e9477-153">Vous pouvez procéder de la sorte au lieu d'utiliser le paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="e9477-153">This is an alternative to using the **Credential** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9477-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e9477-154">CommonParameters</span></span>

<span data-ttu-id="e9477-155">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e9477-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e9477-156">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e9477-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e9477-157">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e9477-157">INPUTS</span></span>

### <span data-ttu-id="e9477-158">Aucun</span><span class="sxs-lookup"><span data-stu-id="e9477-158">None</span></span>

<span data-ttu-id="e9477-159">Vous ne pouvez pas diriger d'entrée vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="e9477-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e9477-160">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e9477-160">OUTPUTS</span></span>

### <span data-ttu-id="e9477-161">Objet proxy de service Web</span><span class="sxs-lookup"><span data-stu-id="e9477-161">A Web service proxy object</span></span>

<span data-ttu-id="e9477-162">Cette applet de commande retourne un objet proxy de service Web.</span><span class="sxs-lookup"><span data-stu-id="e9477-162">This cmdlet returns a Web service proxy object.</span></span> <span data-ttu-id="e9477-163">L'espace de noms et la classe des objets sont déterminés par les paramètres de la commande.</span><span class="sxs-lookup"><span data-stu-id="e9477-163">The namespace and class of the object are determined by the parameters of the command.</span></span> <span data-ttu-id="e9477-164">La valeur par défaut est générée à partir de l’URI d’entrée.</span><span class="sxs-lookup"><span data-stu-id="e9477-164">The default is generated from the input URI.</span></span>

## <span data-ttu-id="e9477-165">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e9477-165">NOTES</span></span>

<span data-ttu-id="e9477-166">`New-WebServiceProxy` utilise la classe **System .net. WebClient** pour charger le service Web spécifié.</span><span class="sxs-lookup"><span data-stu-id="e9477-166">`New-WebServiceProxy` uses the **System.Net.WebClient** class to load the specified Web service.</span></span>

## <span data-ttu-id="e9477-167">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e9477-167">RELATED LINKS</span></span>

[<span data-ttu-id="e9477-168">New-Service</span><span class="sxs-lookup"><span data-stu-id="e9477-168">New-Service</span></span>](New-Service.md)
