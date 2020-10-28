---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d’objets .NET et COM New Object
description: En tant que langage de script orienté objet, PowerShell prend en charge les objets basés sur .NET et COM. Cet article vous explique comment créer ces objets et interagir avec eux.
ms.openlocfilehash: e6189ba465749dd045add7015fc82223c31c7e32
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500570"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="20abe-105">Création d’objets .NET et COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="20abe-105">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="20abe-106">Il existe des composants logiciels avec des interfaces COM et .NET Framework, qui vous permettent d’effectuer de nombreuses tâches d’administration système.</span><span class="sxs-lookup"><span data-stu-id="20abe-106">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="20abe-107">Windows PowerShell permet d’utiliser ces composants. Vous n’êtes donc pas limité aux tâches exécutables à l’aide d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="20abe-107">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="20abe-108">La plupart des applets de commande dans la version initiale de Windows PowerShell ne fonctionnent pas sur des ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="20abe-108">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="20abe-109">Nous allons expliquer comment contourner cette limitation lors de la gestion des journaux des événements à l’aide de la classe .NET Framework **System.Diagnostics.EventLog** directement à partir de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abe-109">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="20abe-110">Utilisation de l’applet de commande New-Object pour l’accès au journal des événements</span><span class="sxs-lookup"><span data-stu-id="20abe-110">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="20abe-111">La bibliothèque de classes .NET Framework inclut une classe nommée **System.Diagnostics.EventLog** qui permet de gérer les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="20abe-111">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="20abe-112">Vous pouvez créer une nouvelle instance d’une classe .NET Framework en utilisant l’applet de commande **New-Object** avec le paramètre **TypeName** .</span><span class="sxs-lookup"><span data-stu-id="20abe-112">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="20abe-113">Par exemple, la commande suivante crée une référence de journal des événements :</span><span class="sxs-lookup"><span data-stu-id="20abe-113">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="20abe-114">Même si la commande a créé une instance de la classe EventLog, l’instance n’inclut pas de données.</span><span class="sxs-lookup"><span data-stu-id="20abe-114">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="20abe-115">Cela est dû au fait que nous n’avons pas spécifié de journal des événements spécifique.</span><span class="sxs-lookup"><span data-stu-id="20abe-115">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="20abe-116">Comment obtenir un journal des événements réel ?</span><span class="sxs-lookup"><span data-stu-id="20abe-116">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="20abe-117">Utilisation de constructeurs avec l’applet de commande New-Object</span><span class="sxs-lookup"><span data-stu-id="20abe-117">Using Constructors with New-Object</span></span>

<span data-ttu-id="20abe-118">Pour faire référence à un journal des événements spécifique, vous devez spécifier son nom.</span><span class="sxs-lookup"><span data-stu-id="20abe-118">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="20abe-119">L’applet de commande **New-Object** a un paramètre **ArgumentList** .</span><span class="sxs-lookup"><span data-stu-id="20abe-119">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="20abe-120">Les arguments que vous passez en tant que valeurs pour ce paramètre sont utilisés par une méthode spéciale de démarrage de l’objet.</span><span class="sxs-lookup"><span data-stu-id="20abe-120">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="20abe-121">La méthode est appelée *constructeur* , car elles est utilisée pour construire l’objet.</span><span class="sxs-lookup"><span data-stu-id="20abe-121">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="20abe-122">Par exemple, pour obtenir une référence au journal des applications, vous spécifiez la chaîne « Application » en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="20abe-122">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="20abe-123">Étant donné que la plupart des classes de base de .NET Framework sont contenues dans l’espace de noms système, Windows PowerShell tente automatiquement de trouver les classes que vous spécifiez dans l’espace de noms système s’il ne trouve pas de correspondance pour le nom de type que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="20abe-123">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="20abe-124">Cela signifie que vous pouvez spécifier Diagnostics.EventLog au lieu de System.Diagnostics.EventLog.</span><span class="sxs-lookup"><span data-stu-id="20abe-124">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="20abe-125">Stockage d’objets dans des variables</span><span class="sxs-lookup"><span data-stu-id="20abe-125">Storing Objects in Variables</span></span>

<span data-ttu-id="20abe-126">Si vous souhaitez stocker une référence à un objet, vous pouvez l’utiliser dans l’interpréteur de commandes en cours.</span><span class="sxs-lookup"><span data-stu-id="20abe-126">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="20abe-127">Bien que Windows PowerShell permette d’effectuer de nombreuses tâches avec des pipelines, en réduisant le besoin de variables, parfois, des références de stockage à des objets dans des variables facilite la manipulation de ces objets.</span><span class="sxs-lookup"><span data-stu-id="20abe-127">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="20abe-128">Windows PowerShell permet de créer des variables qui sont essentiellement des objets nommés.</span><span class="sxs-lookup"><span data-stu-id="20abe-128">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="20abe-129">La sortie d’une commande Windows PowerShell valide peut être stockée dans une variable.</span><span class="sxs-lookup"><span data-stu-id="20abe-129">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="20abe-130">Les noms de variables commencent toujours par $.</span><span class="sxs-lookup"><span data-stu-id="20abe-130">Variable names always begin with $.</span></span> <span data-ttu-id="20abe-131">Si vous souhaitez stocker la référence de journal des applications dans une variable nommée $AppLog, tapez le nom de la variable, suivi d’un signe égal, puis tapez la commande utilisée pour créer l’objet journal des applications :</span><span class="sxs-lookup"><span data-stu-id="20abe-131">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="20abe-132">Si vous tapez $AppLog, vous pouvez voir qu’il contient le journal des applications :</span><span class="sxs-lookup"><span data-stu-id="20abe-132">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="20abe-133">Accès à un journal des événements à distance avec New-Object</span><span class="sxs-lookup"><span data-stu-id="20abe-133">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="20abe-134">Les commandes utilisées dans la section précédente ciblent l’ordinateur local. L’applet de commande **Get-EventLog** peut faire cela.</span><span class="sxs-lookup"><span data-stu-id="20abe-134">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="20abe-135">Pour accéder au journal des applications sur un ordinateur distant, vous devez fournir le nom du journal et un nom d’ordinateur (ou une adresse IP) en tant qu’arguments.</span><span class="sxs-lookup"><span data-stu-id="20abe-135">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="20abe-136">Maintenant que nous avons une référence à un journal des événements stocké dans la variable $RemoteAppLog, quelles tâches pouvons-nous effectuer sur celui-ci ?</span><span class="sxs-lookup"><span data-stu-id="20abe-136">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="20abe-137">Effacement d’un journal des événements avec des méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="20abe-137">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="20abe-138">Les objets ont souvent des méthodes associées qui peuvent être appelées pour effectuer des tâches.</span><span class="sxs-lookup"><span data-stu-id="20abe-138">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="20abe-139">L’applet de commande **Get-Member** permet d’afficher les méthodes associées à un objet.</span><span class="sxs-lookup"><span data-stu-id="20abe-139">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="20abe-140">La commande suivante et la sortie sélectionnée affichent certaines des méthodes de la classe EventLog :</span><span class="sxs-lookup"><span data-stu-id="20abe-140">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="20abe-141">La méthode **Clear()** permet d’effacer le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="20abe-141">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="20abe-142">Lors de l’appel d’une méthode, vous devez toujours faire suivre le nom de la méthode par des parenthèses, même si la méthode ne requiert pas d’argument.</span><span class="sxs-lookup"><span data-stu-id="20abe-142">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="20abe-143">Cela permet à Windows PowerShell de faire la distinction entre la méthode et une propriété éventuelle du même nom.</span><span class="sxs-lookup"><span data-stu-id="20abe-143">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="20abe-144">Tapez ce qui suit pour appeler la méthode **clair**  :</span><span class="sxs-lookup"><span data-stu-id="20abe-144">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="20abe-145">Tapez ce qui suit pour afficher le journal.</span><span class="sxs-lookup"><span data-stu-id="20abe-145">Type the following to display the log.</span></span> <span data-ttu-id="20abe-146">Vous voyez que le journal des événements a été effacé et contient désormais 0 entrée au lieu de 262 :</span><span class="sxs-lookup"><span data-stu-id="20abe-146">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="20abe-147">Création d’objets COM avec New-Object</span><span class="sxs-lookup"><span data-stu-id="20abe-147">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="20abe-148">L’applet de commande **New-Object** permet d’utiliser des composants COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="20abe-148">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="20abe-149">Les composants vont des différentes bibliothèques incluses dans l’environnement d’exécution de scripts WSH (Windows Script Host) aux applications ActiveX telles qu’Internet Explorer qui sont installées sur la plupart des systèmes.</span><span class="sxs-lookup"><span data-stu-id="20abe-149">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="20abe-150">L’applet de commande **New-Object** utilise des wrappers RCW (Runtime-Callable Wrappers) .NET Framework pour créer des objets COM. Elle est donc sujette aux mêmes limitations que .NET Framework lors de l’appel d’objets COM.</span><span class="sxs-lookup"><span data-stu-id="20abe-150">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="20abe-151">Pour créer un objet COM, vous devez spécifier le paramètre **ComObject** avec l’identificateur programmatique, ou *ProgId* , de la classe COM que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="20abe-151">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="20abe-152">Une description complète des limitations de l’utilisation de COM et de la détermination des ProgID disponibles sur un système dépasserait la portée de ce guide, mais la plupart des objets bien connus d’environnements tels que WSH peuvent être utilisés dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abe-152">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="20abe-153">Vous pouvez créer les objets WSH en spécifiant les ProgID suivants : **WScript.Shell** , **WScript.Network** , **Scripting.Dictionary** , et **Scripting.FileSystemObject** .</span><span class="sxs-lookup"><span data-stu-id="20abe-153">You can create the WSH objects by specifying these progids: **WScript.Shell** , **WScript.Network** , **Scripting.Dictionary** , and **Scripting.FileSystemObject** .</span></span> <span data-ttu-id="20abe-154">Les commandes suivantes créent ces objets :</span><span class="sxs-lookup"><span data-stu-id="20abe-154">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="20abe-155">Si l’essentiel de la fonctionnalité de ces classes est rendu disponible par d’autres moyens dans Windows PowerShell, quelques tâches telles que la création de raccourci sont encore plus faciles à effectuer à l’aide des classes WSH.</span><span class="sxs-lookup"><span data-stu-id="20abe-155">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="20abe-156">Création d’un raccourci sur le Bureau avec WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="20abe-156">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="20abe-157">Une tâche exécutable rapidement avec un objet COM est la création d’un raccourci.</span><span class="sxs-lookup"><span data-stu-id="20abe-157">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="20abe-158">Supposons que vous souhaitez créer un raccourci sur votre bureau, qui établit un lien vers le dossier de base de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abe-158">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="20abe-159">Vous devez commencer par créer une référence à **WScript.Shell** , que nous allons stocker dans une variable nommée **$WshShell**  :</span><span class="sxs-lookup"><span data-stu-id="20abe-159">You first need to create a reference to **WScript.Shell** , which we will store in a variable named **$WshShell** :</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="20abe-160">L’applet de commande Get-Member fonctionnant avec des objets COM, vous pouvez explorer les membres de l’objet en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20abe-160">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="20abe-161">L’applet de commande **Get-Member** dispose d’un paramètre facultatif, **InputObject** , que vous pouvez utiliser à la place d’un piping pour fournir l’entrée à **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="20abe-161">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member** .</span></span> <span data-ttu-id="20abe-162">Vous obtiendriez la même sortie que celle indiquée ci-dessus si vous utilisez à la place la commande **Get-Member -InputObject $WshShell** .</span><span class="sxs-lookup"><span data-stu-id="20abe-162">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell** .</span></span> <span data-ttu-id="20abe-163">Si vous utilisez **InputObject** , l’argument est traité comme un seul élément.</span><span class="sxs-lookup"><span data-stu-id="20abe-163">If you use **InputObject** , it treats its argument as a single item.</span></span> <span data-ttu-id="20abe-164">Cela signifie que, si vous disposez de plusieurs objets dans une variable, l’applet de commande **Get-Member** les traite comme un tableau d’objets.</span><span class="sxs-lookup"><span data-stu-id="20abe-164">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="20abe-165">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="20abe-165">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="20abe-166">La méthode **WScript.Shell CreateShortcut** accepte un seul argument, le chemin d’accès au fichier de raccourci à créer.</span><span class="sxs-lookup"><span data-stu-id="20abe-166">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="20abe-167">Nous pourrions taper le chemin d’accès complet au bureau, mais il existe un moyen plus simple.</span><span class="sxs-lookup"><span data-stu-id="20abe-167">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="20abe-168">Le bureau est généralement représenté par un dossier nommé Bureau à l’intérieur du dossier de base de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="20abe-168">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="20abe-169">Windows PowerShell dispose d’une variable **$Home** qui contient le chemin d’accès à ce dossier.</span><span class="sxs-lookup"><span data-stu-id="20abe-169">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="20abe-170">Nous pouvons spécifier le chemin d’accès au dossier de base à l’aide de cette variable, puis ajouter le nom du dossier Bureau et le nom du raccourci à créer en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20abe-170">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="20abe-171">Lorsque vous utilisez quelque chose ressemblant à un nom de variable entre guillemets doubles, Windows PowerShell tente de remplacer cet élément par une valeur correspondante.</span><span class="sxs-lookup"><span data-stu-id="20abe-171">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="20abe-172">Si vous utilisez des guillemets simples, Windows PowerShell n’essaie pas de remplacer la variable par une valeur.</span><span class="sxs-lookup"><span data-stu-id="20abe-172">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="20abe-173">Par exemple, essayez de taper les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="20abe-173">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="20abe-174">Nous avons désormais une variable nommée **$lnk** qui contient une nouvelle référence au raccourci.</span><span class="sxs-lookup"><span data-stu-id="20abe-174">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="20abe-175">Si vous souhaitez voir ses membres, vous pouvez la canaliser vers l’applet de commande **Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="20abe-175">If you want to see its members, you can pipe it to **Get-Member** .</span></span> <span data-ttu-id="20abe-176">La sortie ci-dessous montre les membres que nous devons utiliser pour achever la création de notre raccourci :</span><span class="sxs-lookup"><span data-stu-id="20abe-176">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="20abe-177">Nous devons spécifier **TargetPath** , qui est le dossier d’application pour Windows PowerShell, puis enregistrer le raccourci **$lnk** en appelant la méthode **Save** .</span><span class="sxs-lookup"><span data-stu-id="20abe-177">We need to specify the **TargetPath** , which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="20abe-178">Le chemin d’accès au dossier d’application de Windows PowerShell étant stocké dans la variable **$PSHome** , nous pouvons faire cela en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20abe-178">The Windows PowerShell application folder path is stored in the variable **$PSHome** , so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="20abe-179">Utilisation d’Internet Explorer à partir de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="20abe-179">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="20abe-180">De nombreuses applications (dont la famille d’applications Microsoft Office et Internet Explorer) peuvent être automatisées à l’aide de COM.</span><span class="sxs-lookup"><span data-stu-id="20abe-180">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="20abe-181">Internet Explorer illustre certains problèmes et techniques classiques impliqués dans l’utilisation d’applications basées sur COM.</span><span class="sxs-lookup"><span data-stu-id="20abe-181">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="20abe-182">Vous créez une instance Internet Explorer en spécifiant le ProgId d’Internet Explorer, **InternetExplorer.Application**  :</span><span class="sxs-lookup"><span data-stu-id="20abe-182">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application** :</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="20abe-183">Cette commande démarre Internet Explorer, mais ne le rend pas visible.</span><span class="sxs-lookup"><span data-stu-id="20abe-183">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="20abe-184">Si vous tapez Get-Process, vous pouvez voir qu’un processus nommé iexplore est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="20abe-184">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="20abe-185">En fait, si vous quittez Windows PowerShell, le processus continue à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="20abe-185">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="20abe-186">Pour arrêter le processus iexplore, vous devez redémarrer l’ordinateur ou utiliser un outil tel que le Gestionnaire des tâches.</span><span class="sxs-lookup"><span data-stu-id="20abe-186">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="20abe-187">Les objets COM qui démarrent en tant que processus séparés, généralement appelés *exécutables ActiveX* , peuvent ou non afficher une fenêtre d’interface utilisateur au démarrage.</span><span class="sxs-lookup"><span data-stu-id="20abe-187">COM objects that start as separate processes, commonly called *ActiveX executables* , may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="20abe-188">S’ils créent une fenêtre, comme Internet Explorer, mais ne la rendent pas visible, le focus se positionne généralement sur le Bureau Windows, et vous devez rendre la fenêtre visible pour pouvoir interagir avec elle.</span><span class="sxs-lookup"><span data-stu-id="20abe-188">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="20abe-189">Pour afficher les propriétés et méthodes pour Internet Explorer, tapez **$ie | Get-Member** .</span><span class="sxs-lookup"><span data-stu-id="20abe-189">By typing **$ie | Get-Member** , you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="20abe-190">Pour afficher la fenêtre Internet Explorer, définissez la propriété Visible sur $true en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20abe-190">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="20abe-191">Vous pouvez ensuite accéder à une adresse web spécifique à l’aide de la méthode Navigate :</span><span class="sxs-lookup"><span data-stu-id="20abe-191">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("https://devblogs.microsoft.com/scripting/")
```

<span data-ttu-id="20abe-192">En utilisant d’autres membres du modèle d’objet Internet Explorer, vous pouvez récupérer le contenu de texte de la page web.</span><span class="sxs-lookup"><span data-stu-id="20abe-192">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="20abe-193">La commande suivante affiche le texte HTML dans le corps de la page web active :</span><span class="sxs-lookup"><span data-stu-id="20abe-193">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="20abe-194">Pour fermer Internet Explorer à partir de PowerShell, appelez sa méthode Quit() :</span><span class="sxs-lookup"><span data-stu-id="20abe-194">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="20abe-195">Cette opération force la fermeture.</span><span class="sxs-lookup"><span data-stu-id="20abe-195">This will force it to close.</span></span> <span data-ttu-id="20abe-196">La variable $ie ne contient plus de référence valide, même si elle apparaît toujours comme un objet COM.</span><span class="sxs-lookup"><span data-stu-id="20abe-196">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="20abe-197">Si vous tentez de l’utiliser, vous obtenez une erreur Automation :</span><span class="sxs-lookup"><span data-stu-id="20abe-197">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="20abe-198">Vous pouvez soit supprimer la référence restante avec une commande telle que $ie = $null, ou supprimer complètement la variable en tapant ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="20abe-198">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="20abe-199">Il n’existe aucune norme commune déterminant si les exécutables ActiveX s’arrêtent ou continuent à s’exécuter lorsque vous supprimez une référence à ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="20abe-199">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="20abe-200">En fonction des circonstances, selon que l’application est visible, qu’un document modifié est en cours d’exécution dans celle-ci, et même que Windows PowerShell est toujours en cours d’exécution, l’application peut se fermer ou non.</span><span class="sxs-lookup"><span data-stu-id="20abe-200">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="20abe-201">C’est pourquoi, vous devez tester le comportement d’arrêt de chaque exécutable ActiveX à utiliser dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20abe-201">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="20abe-202">Obtention d’alertes sur les objets COM encapsulés .NET Framework</span><span class="sxs-lookup"><span data-stu-id="20abe-202">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="20abe-203">Dans certains cas, un objet COM peut avoir un *wrapper RCW* (Runtime-Callable Wrapper) .NET Framework associé, qui sera utilisé par l’applet de commande **New-Object** .</span><span class="sxs-lookup"><span data-stu-id="20abe-203">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object** .</span></span> <span data-ttu-id="20abe-204">Étant donné que le comportement du wrapper RCW peut différer du comportement de l’objet COM normal, l’applet de commande **New-Object** dispose d’un paramètre **Strict** pour vous avertir de l’accès au wrapper RCW.</span><span class="sxs-lookup"><span data-stu-id="20abe-204">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="20abe-205">Si vous spécifiez le paramètre **Strict** , puis créez un objet COM qui utilise un wrapper RCW, vous recevez un message d’avertissement :</span><span class="sxs-lookup"><span data-stu-id="20abe-205">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="20abe-206">Bien que l’objet soit toujours créé, vous êtes averti qu’il ne s’agit pas d’un objet COM standard.</span><span class="sxs-lookup"><span data-stu-id="20abe-206">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
