---
title: Découverte des objets, propriétés et méthodes
description: Vous n’avez pas besoin d’être développeur pour comprendre et utiliser les objets, les propriétés et les méthodes.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: f226221da7dd3b663f54cf23439dd7f945ed3a2a
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99595704"
---
# <a name="chapter-3---discovering-objects-properties-and-methods"></a><span data-ttu-id="78766-103">Chapitre 3 - Découverte des objets, propriétés et méthodes</span><span class="sxs-lookup"><span data-stu-id="78766-103">Chapter 3 - Discovering objects, properties, and methods</span></span>

<span data-ttu-id="78766-104">Mon premier contact avec un ordinateur fut avec un Commodore 64. Toutefois, mon premier ordinateur moderne était un clone IBM 286 12 MHz équipé de 1 Mo de mémoire, d’un disque dur de 40 Mo, d’un lecteur de disquette 5,25 pouces, d’un moniteur CGA, et qui exécutait Microsoft DOS 3.3.</span><span class="sxs-lookup"><span data-stu-id="78766-104">My first introduction to computers was a Commodore 64, but my first modern computer was a 286 12-Mhz IBM clone with 1 megabyte of memory, a 40-megabyte hard drive, and one 5-1/4 inch floppy disk drive with a CGA monitor running Microsoft DOS 3.3.</span></span>

<span data-ttu-id="78766-105">De nombreux professionnels de l’informatique, comme moi-même, connaissent très bien la ligne de commande. Toutefois, lorsque l’on aborde le sujet des objets, des propriétés et des méthodes, ils se figent et vous répondent « je ne suis pas développeur ».</span><span class="sxs-lookup"><span data-stu-id="78766-105">Many IT Pros, like myself, are no stranger to the command line, but when the subject of objects, properties, and methods comes up, they get the deer in the headlights look and say, "I'm not a developer."</span></span> <span data-ttu-id="78766-106">Eh bien devinez quoi ?</span><span class="sxs-lookup"><span data-stu-id="78766-106">Guess what?</span></span> <span data-ttu-id="78766-107">Vous n’avez pas besoin d’être un développeur pour réussir avec PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78766-107">You don't have to be a developer to be successful with PowerShell.</span></span> <span data-ttu-id="78766-108">Ne soyez pas découragé par la terminologie.</span><span class="sxs-lookup"><span data-stu-id="78766-108">Don't get bogged down in the terminology.</span></span> <span data-ttu-id="78766-109">Vous n’allez peut-être pas tout comprendre tout de suite, mais après un peu de pratique, vous commencerez à avoir des révélations.</span><span class="sxs-lookup"><span data-stu-id="78766-109">Not everything may make sense initially, but after a little hands-on experience you'll start to have those "light bulb" moments.</span></span> <span data-ttu-id="78766-110">« Ah d’accord !</span><span class="sxs-lookup"><span data-stu-id="78766-110">"Aha!</span></span> <span data-ttu-id="78766-111">C’est donc de ça que parlait le livre ! ».</span><span class="sxs-lookup"><span data-stu-id="78766-111">So that's what the book was talking about."</span></span>

<span data-ttu-id="78766-112">Il est important de tester les exemples sur votre ordinateur pour bénéficier d’une expérience pratique.</span><span class="sxs-lookup"><span data-stu-id="78766-112">Be sure to try the examples on your computer to gain some of that hands-on experience.</span></span>

## <a name="requirements"></a><span data-ttu-id="78766-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78766-113">Requirements</span></span>

<span data-ttu-id="78766-114">Certains des exemples présentés dans ce chapitre nécessitent le module Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="78766-114">The Active Directory PowerShell module is required by some of the examples shown in this chapter.</span></span>
<span data-ttu-id="78766-115">Ce module fait partie des outils d’administration de serveur distant (RSAT) pour Windows.</span><span class="sxs-lookup"><span data-stu-id="78766-115">The module is part of the Remote Server Administration Tools (RSAT) for Windows.</span></span> <span data-ttu-id="78766-116">Pour la version 1809 (et versions ultérieures) de Windows, les outils RSAT sont installés comme des fonctionnalités Windows.</span><span class="sxs-lookup"><span data-stu-id="78766-116">For the 1809 (or higher) build of Windows, the RSAT tools are installed as a Windows feature.</span></span>

- <span data-ttu-id="78766-117">Pour plus d’informations sur l’installation des outils RSAT, consultez [Modules de gestion Windows][].</span><span class="sxs-lookup"><span data-stu-id="78766-117">For information about installing the RSAT tools, see [Windows Management modules][].</span></span>
- <span data-ttu-id="78766-118">Pour les versions antérieures de Windows, consultez [RSAT pour Windows][].</span><span class="sxs-lookup"><span data-stu-id="78766-118">For older versions of Windows, see [RSAT for Windows][].</span></span>

## <a name="get-member"></a><span data-ttu-id="78766-119">Get-Member</span><span class="sxs-lookup"><span data-stu-id="78766-119">Get-Member</span></span>

<span data-ttu-id="78766-120">`Get-Member` vous permet de découvrir les objets, les propriétés et les méthodes qui sont disponibles pour les commandes.</span><span class="sxs-lookup"><span data-stu-id="78766-120">`Get-Member` helps you discover what objects, properties, and methods are available for commands.</span></span>
<span data-ttu-id="78766-121">Toute commande qui produit une sortie basée sur un objet peut être redirigée vers `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-121">Any command that produces object-based output can be piped to `Get-Member`.</span></span> <span data-ttu-id="78766-122">Une propriété est une caractéristique d’un élément.</span><span class="sxs-lookup"><span data-stu-id="78766-122">A property is a characteristic about an item.</span></span> <span data-ttu-id="78766-123">Votre passeport a une propriété appelée « Couleur des yeux » et les valeurs les plus courantes pour cette propriété sont « bleu » et « marron ».</span><span class="sxs-lookup"><span data-stu-id="78766-123">Your drivers license has a property called eye color and the most common values for that property are blue and brown.</span></span> <span data-ttu-id="78766-124">Une méthode est une action qui peut être réalisée sur un élément.</span><span class="sxs-lookup"><span data-stu-id="78766-124">A method is an action that can be taken on an item.</span></span> <span data-ttu-id="78766-125">Pour rester sur l’exemple du passeport, une des méthodes pourraient être « Refuser », car les services des passeports peuvent refuser de vous le délivrer.</span><span class="sxs-lookup"><span data-stu-id="78766-125">In staying with the drivers license example, one of the methods is "Revoke" because the department of motor vehicles can revoke your drivers license.</span></span>

### <a name="properties"></a><span data-ttu-id="78766-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="78766-126">Properties</span></span>

<span data-ttu-id="78766-127">Dans l’exemple suivant, je vais récupérer des informations sur le service Temps Windows qui est exécuté sur mon ordinateur.</span><span class="sxs-lookup"><span data-stu-id="78766-127">In the following example, I'll retrieve information about the Windows Time service running on my computer.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="78766-128">**Status**, **Name** et **DisplayName** sont des exemples de propriétés, comme ceux du jeu de résultats précédent.</span><span class="sxs-lookup"><span data-stu-id="78766-128">**Status**, **Name**, and **DisplayName** are examples of properties as shown in the previous set of results.</span></span> <span data-ttu-id="78766-129">La valeur de la propriété **Status** est `Running`, la valeur de la propriété **Name** est `w32time`, et la valeur de **DisplayName** est `Windows Time`.</span><span class="sxs-lookup"><span data-stu-id="78766-129">The value for the **Status** property is `Running`, the value for the **Name** property is `w32time`, and the value for **DisplayName** is `Windows Time`.</span></span>

<span data-ttu-id="78766-130">Je vais maintenant rediriger la même commande vers `Get-Member` :</span><span class="sxs-lookup"><span data-stu-id="78766-130">Now I'll pipe that same command to `Get-Member`:</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="78766-131">La première ligne des résultats de l’exemple précédent contient une information très importante.</span><span class="sxs-lookup"><span data-stu-id="78766-131">The first line of the results in the previous example contains one piece of very important information.</span></span> <span data-ttu-id="78766-132">**TypeName** indique le type d’objet retourné.</span><span class="sxs-lookup"><span data-stu-id="78766-132">**TypeName** tells you what type of object was returned.</span></span> <span data-ttu-id="78766-133">Dans cet exemple, un objet **System.ServiceProcess.ServiceController** a été retourné.</span><span class="sxs-lookup"><span data-stu-id="78766-133">In this example, a **System.ServiceProcess.ServiceController** object was returned.</span></span> <span data-ttu-id="78766-134">Ceci est souvent abrégé dans la partie **TypeName** située juste après le dernier point (**ServiceController** dans cet exemple).</span><span class="sxs-lookup"><span data-stu-id="78766-134">This is often abbreviated as the portion of the **TypeName** just after the last period; **ServiceController** in this example.</span></span>

<span data-ttu-id="78766-135">Une fois que vous connaissez le type d’objet produit par une commande, vous pouvez utiliser ces informations pour rechercher les commandes qui acceptent ce type d’objet comme entrée.</span><span class="sxs-lookup"><span data-stu-id="78766-135">Once you know what type of object a command produces, you can use this information to find commands that accept that type of object as input.</span></span>

```powershell
Get-Command -ParameterType ServiceController
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
```

<span data-ttu-id="78766-136">Toutes ces commandes ont un paramètre qui accepte un type d’objet **ServiceController** par pipeline, par entrée de paramètre, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="78766-136">All of those commands have a parameter that accepts a **ServiceController** object type by pipeline, parameter input, or both.</span></span>

<span data-ttu-id="78766-137">Notez que les propriétés disponibles sont plus nombreuses que celles affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="78766-137">Notice that there are more properties than are displayed by default.</span></span> <span data-ttu-id="78766-138">Même si ces propriétés supplémentaires ne sont pas affichées par défaut, vous pouvez les sélectionner à partir du pipeline en redirigeant la commande vers l’applet de commande `Select-Object` et en utilisant le paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="78766-138">Although these additional properties aren't displayed by default, they can be selected from the pipeline by piping the command to the `Select-Object` cmdlet and using the **Property** parameter.</span></span> <span data-ttu-id="78766-139">L’exemple suivant sélectionne toutes les propriétés en redirigeant les résultats de `Get-Service` vers `Select-Object`, et en spécifiant le caractère générique `*` comme la valeur du paramètre **Property**.</span><span class="sxs-lookup"><span data-stu-id="78766-139">The following example selects all of the properties by piping the results of `Get-Service` to `Select-Object` and specifying the `*` wildcard character as the value for the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="78766-140">Pour la valeur du paramètre **Property**, vous pouvez également sélectionner certaines propriétés à l’aide d’une liste séparée par des virgules.</span><span class="sxs-lookup"><span data-stu-id="78766-140">Specific properties can also be selected using a comma-separated list for the value of the **Property** parameter.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, Name, DisplayName, ServiceType
```

```Output
 Status Name    DisplayName        ServiceType
 ------ ----    -----------        -----------
Running w32time Windows Time Win32ShareProcess
```

<span data-ttu-id="78766-141">Par défaut, quatre propriétés sont retournées dans un tableau et cinq ou plus sont retournées dans une liste.</span><span class="sxs-lookup"><span data-stu-id="78766-141">By default, four properties are returned in a table and five or more are returned in a list.</span></span> <span data-ttu-id="78766-142">Certaines commandes utilisent une mise en forme personnalisée pour remplacer le nombre de propriétés affichées par défaut dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="78766-142">Some commands use custom formatting to override how many properties are displayed by default in a table.</span></span>
<span data-ttu-id="78766-143">Plusieurs applets de commande `Format-*` peuvent être utilisées pour remplacer manuellement ces valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="78766-143">There are several `Format-*` cmdlets that can be used to manually override these defaults.</span></span> <span data-ttu-id="78766-144">Les plus courantes sont `Format-Table` et `Format-List`, qui seront toutes les deux abordées dans un prochain chapitre.</span><span class="sxs-lookup"><span data-stu-id="78766-144">The most common ones are `Format-Table` and `Format-List`, both of which will be covered in an upcoming chapter.</span></span>

<span data-ttu-id="78766-145">Les caractères génériques peuvent être utilisés lors de la spécification des noms de propriété avec `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="78766-145">Wildcard characters can be used when specifying the property names with `Select-Object`.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```powershell
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="78766-146">Dans l’exemple précédent, `Can*` a été utilisé comme l’une des valeurs du paramètre **Property** pour retourner toutes les propriétés qui commencent par `Can`.</span><span class="sxs-lookup"><span data-stu-id="78766-146">In the previous example, `Can*` was used as one of the values for the **Property** parameter to return all the properties that start with `Can`.</span></span> <span data-ttu-id="78766-147">Il s’agissait notamment de **CanPauseAndContinue**, **CanShutdown** et **CanStop**.</span><span class="sxs-lookup"><span data-stu-id="78766-147">These include **CanPauseAndContinue**, **CanShutdown**, and **CanStop**.</span></span>

### <a name="methods"></a><span data-ttu-id="78766-148">Méthodes</span><span class="sxs-lookup"><span data-stu-id="78766-148">Methods</span></span>

<span data-ttu-id="78766-149">Une méthode est une action qui peut être réalisée.</span><span class="sxs-lookup"><span data-stu-id="78766-149">Methods are an action that can be taken.</span></span> <span data-ttu-id="78766-150">Utilisez le paramètre **MemberType** pour affiner les résultats de `Get-Member` afin de n’afficher que les méthodes de `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="78766-150">Use the **MemberType** parameter to narrow down the results of `Get-Member` to only show the methods for `Get-Service`.</span></span>

```powershell
Get-Service -Name w32time | Get-Member -MemberType Method
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType Definition
----                      ---------- ----------
Close                     Method     void Close()
Continue                  Method     void Continue()
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type ...
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Equals                    Method     bool Equals(System.Object obj)
ExecuteCommand            Method     void ExecuteCommand(int command)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Pause                     Method     void Pause()
Refresh                   Method     void Refresh()
Start                     Method     void Start(), void Start(string[] args)
Stop                      Method     void Stop()
WaitForStatus             Method     void WaitForStatus(System.ServiceProcess.ServiceC...
```

<span data-ttu-id="78766-151">Comme vous pouvez le voir, il existe de nombreuses méthodes.</span><span class="sxs-lookup"><span data-stu-id="78766-151">As you can see, there are many methods.</span></span> <span data-ttu-id="78766-152">La méthode **Stop** peut être utilisée pour arrêter un service Windows.</span><span class="sxs-lookup"><span data-stu-id="78766-152">The **Stop** method can be used to stop a Windows service.</span></span>

```powershell
(Get-Service -Name w32time).Stop()
```

<span data-ttu-id="78766-153">Maintenant, vérifiez que le service Temps Windows a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="78766-153">Now to verify the Windows time service has indeed been stopped.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  w32time            Windows Time
```

<span data-ttu-id="78766-154">Je suis rarement amené à utiliser des méthodes. Toutefois, vous devez savoir vous en servir.</span><span class="sxs-lookup"><span data-stu-id="78766-154">I rarely find myself using methods, but they're something you need to be aware of.</span></span> <span data-ttu-id="78766-155">Il peut arriver que vous rencontriez une commande `Get-*` sans commande correspondante permettant de la modifier.</span><span class="sxs-lookup"><span data-stu-id="78766-155">There are times that you'll come across a `Get-*` command without a corresponding command to modify that item.</span></span>
<span data-ttu-id="78766-156">Souvent, une méthode peut être utilisée pour réaliser une action qui la modifie.</span><span class="sxs-lookup"><span data-stu-id="78766-156">Often, a method can be used to perform an action that modifies it.</span></span> <span data-ttu-id="78766-157">L’applet de commande `Get-SqlAgentJob` du module SqlServer PowerShell en est un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="78766-157">The `Get-SqlAgentJob` cmdlet in the SqlServer PowerShell module is a good example of this.</span></span> <span data-ttu-id="78766-158">Le module est installé dans le cadre de [SQL Server Management Studio (SMSS)][SMSS].</span><span class="sxs-lookup"><span data-stu-id="78766-158">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="78766-159">Il n’existe aucune applet de commande `Set-*` correspondante. Toutefois, vous pouvez utiliser une méthode pour effectuer cette même tâche.</span><span class="sxs-lookup"><span data-stu-id="78766-159">No corresponding `Set-*` cmdlet exists, but a method can be used to complete the same task.</span></span>

<span data-ttu-id="78766-160">Une autre raison pour laquelle il faut connaître les méthodes est que de nombreux débutants supposent qu’il n’est pas possible d’apporter des modifications destructrices avec les commandes `Get-*`.</span><span class="sxs-lookup"><span data-stu-id="78766-160">Another reason to be aware of methods is that many beginners assume destructive changes can't be made with `Get-*` commands.</span></span> <span data-ttu-id="78766-161">Pourtant, elles peuvent provoquer des problèmes graves si elles ne sont pas utilisées correctement.</span><span class="sxs-lookup"><span data-stu-id="78766-161">But they indeed can cause serious problems if used inappropriately.</span></span>

<span data-ttu-id="78766-162">Il est préférable d’utiliser une applet de commande pour exécuter l’action (s’il en existe une).</span><span class="sxs-lookup"><span data-stu-id="78766-162">A better option is to use a cmdlet to perform the action if one exists.</span></span> <span data-ttu-id="78766-163">Poursuivez en démarrant le service Temps Windows, mais cette fois-ci, utilisez l’applet de commande pour démarrer les services.</span><span class="sxs-lookup"><span data-stu-id="78766-163">Go ahead and start the Windows Time service, except this time use the cmdlet for starting services.</span></span>

```powershell
Get-Service -Name w32time | Start-Service -PassThru
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="78766-164">Par défaut, `Start-Service` ne retourne pas de résultats comme la méthode Start de `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="78766-164">By default, `Start-Service` doesn't return any results just like the start method of `Get-Service`.</span></span>
<span data-ttu-id="78766-165">Toutefois, l’un des avantages de l’utilisation d’une applet de commande est que souvent, une applet de commande offre des fonctionnalités qui ne sont pas disponibles avec une méthode.</span><span class="sxs-lookup"><span data-stu-id="78766-165">But one of the benefits of using a cmdlet is that many times the cmdlet offers additional functionality that isn't available with a method.</span></span> <span data-ttu-id="78766-166">Dans l’exemple précédent, le paramètre **PassThru** a été utilisé.</span><span class="sxs-lookup"><span data-stu-id="78766-166">In the previous example, the **PassThru** parameter was used.</span></span> <span data-ttu-id="78766-167">Avec ce paramètre, une applet de commande qui ne produit normalement pas de sortie est amenée à en produire une.</span><span class="sxs-lookup"><span data-stu-id="78766-167">This causes a cmdlet that doesn't normally produce output, to produce output.</span></span>

<span data-ttu-id="78766-168">Ne prenez pas de risques concernant la sortie d’une applet de commande.</span><span class="sxs-lookup"><span data-stu-id="78766-168">Be careful with assumptions about the output of a cmdlet.</span></span> <span data-ttu-id="78766-169">Nous savons tous ce qui se passe lorsque nous faisons des suppositions.</span><span class="sxs-lookup"><span data-stu-id="78766-169">We all know what happens when you assume things.</span></span> <span data-ttu-id="78766-170">Je vais récupérer des informations sur le processus PowerShell qui s’exécute sur mon ordinateur Windows 10 Lab Environment.</span><span class="sxs-lookup"><span data-stu-id="78766-170">I'll retrieve information about the PowerShell process running on my Windows 10 lab environment computer.</span></span>

```powershell
Get-Process -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    922      48   107984     140552       2.84   9020   1 powershell

```

<span data-ttu-id="78766-171">À présent, je vais maintenant rediriger la même commande vers la commande Get-Member :</span><span class="sxs-lookup"><span data-stu-id="78766-171">Now I'll pipe that same command to Get-Member:</span></span>

```powershell
Get-Process -Name PowerShell | Get-Member
```

```Output
   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
NPM                        AliasProperty  NPM = NonpagedSystemMemorySize64
PM                         AliasProperty  PM = PagedMemorySize64
SI                         AliasProperty  SI = SessionId
VM                         AliasProperty  VM = VirtualMemorySize64
WS                         AliasProperty  WS = WorkingSet64
Disposed                   Event          System.EventHandler Disposed(System.Object, ...
ErrorDataReceived          Event          System.Diagnostics.DataReceivedEventHandler ...
Exited                     Event          System.EventHandler Exited(System.Object, Sy...
OutputDataReceived         Event          System.Diagnostics.DataReceivedEventHandler ...
BeginErrorReadLine         Method         void BeginErrorReadLine()
BeginOutputReadLine        Method         void BeginOutputReadLine()
CancelErrorRead            Method         void CancelErrorRead()
CancelOutputRead           Method         void CancelOutputRead()
Close                      Method         void Close()
CloseMainWindow            Method         bool CloseMainWindow()
CreateObjRef               Method         System.Runtime.Remoting.ObjRef CreateObjRef(...
Dispose                    Method         void Dispose(), void IDisposable.Dispose()
Equals                     Method         bool Equals(System.Object obj)
GetHashCode                Method         int GetHashCode()
GetLifetimeService         Method         System.Object GetLifetimeService()
GetType                    Method         type GetType()
InitializeLifetimeService  Method         System.Object InitializeLifetimeService()
Kill                       Method         void Kill()
Refresh                    Method         void Refresh()
Start                      Method         bool Start()
ToString                   Method         string ToString()
WaitForExit                Method         bool WaitForExit(int milliseconds), void Wai...
WaitForInputIdle           Method         bool WaitForInputIdle(int milliseconds), boo...
__NounName                 NoteProperty   string __NounName=Process
BasePriority               Property       int BasePriority {get;}
Container                  Property       System.ComponentModel.IContainer Container {...
EnableRaisingEvents        Property       bool EnableRaisingEvents {get;set;}
ExitCode                   Property       int ExitCode {get;}
ExitTime                   Property       datetime ExitTime {get;}
Handle                     Property       System.IntPtr Handle {get;}
HandleCount                Property       int HandleCount {get;}
HasExited                  Property       bool HasExited {get;}
Id                         Property       int Id {get;}
MachineName                Property       string MachineName {get;}
MainModule                 Property       System.Diagnostics.ProcessModule MainModule ...
MainWindowHandle           Property       System.IntPtr MainWindowHandle {get;}
MainWindowTitle            Property       string MainWindowTitle {get;}
MaxWorkingSet              Property       System.IntPtr MaxWorkingSet {get;set;}
MinWorkingSet              Property       System.IntPtr MinWorkingSet {get;set;}
Modules                    Property       System.Diagnostics.ProcessModuleCollection M...
NonpagedSystemMemorySize   Property       int NonpagedSystemMemorySize {get;}
NonpagedSystemMemorySize64 Property       long NonpagedSystemMemorySize64 {get;}
PagedMemorySize            Property       int PagedMemorySize {get;}
PagedMemorySize64          Property       long PagedMemorySize64 {get;}
PagedSystemMemorySize      Property       int PagedSystemMemorySize {get;}
PagedSystemMemorySize64    Property       long PagedSystemMemorySize64 {get;}
PeakPagedMemorySize        Property       int PeakPagedMemorySize {get;}
PeakPagedMemorySize64      Property       long PeakPagedMemorySize64 {get;}
PeakVirtualMemorySize      Property       int PeakVirtualMemorySize {get;}
PeakVirtualMemorySize64    Property       long PeakVirtualMemorySize64 {get;}
PeakWorkingSet             Property       int PeakWorkingSet {get;}
PeakWorkingSet64           Property       long PeakWorkingSet64 {get;}
PriorityBoostEnabled       Property       bool PriorityBoostEnabled {get;set;}
PriorityClass              Property       System.Diagnostics.ProcessPriorityClass Prio...
PrivateMemorySize          Property       int PrivateMemorySize {get;}
PrivateMemorySize64        Property       long PrivateMemorySize64 {get;}
PrivilegedProcessorTime    Property       timespan PrivilegedProcessorTime {get;}
ProcessName                Property       string ProcessName {get;}
ProcessorAffinity          Property       System.IntPtr ProcessorAffinity {get;set;}
Responding                 Property       bool Responding {get;}
SafeHandle                 Property       Microsoft.Win32.SafeHandles.SafeProcessHandl...
SessionId                  Property       int SessionId {get;}
Site                       Property       System.ComponentModel.ISite Site {get;set;}
StandardError              Property       System.IO.StreamReader StandardError {get;}
StandardInput              Property       System.IO.StreamWriter StandardInput {get;}
StandardOutput             Property       System.IO.StreamReader StandardOutput {get;}
StartInfo                  Property       System.Diagnostics.ProcessStartInfo StartInf...
StartTime                  Property       datetime StartTime {get;}
SynchronizingObject        Property       System.ComponentModel.ISynchronizeInvoke Syn...
Threads                    Property       System.Diagnostics.ProcessThreadCollection T...
TotalProcessorTime         Property       timespan TotalProcessorTime {get;}
UserProcessorTime          Property       timespan UserProcessorTime {get;}
VirtualMemorySize          Property       int VirtualMemorySize {get;}
VirtualMemorySize64        Property       long VirtualMemorySize64 {get;}
WorkingSet                 Property       int WorkingSet {get;}
WorkingSet64               Property       long WorkingSet64 {get;}
PSConfiguration            PropertySet    PSConfiguration {Name, Id, PriorityClass, Fi...
PSResources                PropertySet    PSResources {Name, Id, Handlecount, WorkingS...
Company                    ScriptProperty System.Object Company {get=$this.Mainmodule....
CPU                        ScriptProperty System.Object CPU {get=$this.TotalProcessorT...
Description                ScriptProperty System.Object Description {get=$this.Mainmod...
FileVersion                ScriptProperty System.Object FileVersion {get=$this.Mainmod...
Path                       ScriptProperty System.Object Path {get=$this.Mainmodule.Fil...
Product                    ScriptProperty System.Object Product {get=$this.Mainmodule....
ProductVersion             ScriptProperty System.Object ProductVersion {get=$this.Main...
```

<span data-ttu-id="78766-172">Notez que les propriétés disponibles sont plus nombreuses que celles affichées par défaut.</span><span class="sxs-lookup"><span data-stu-id="78766-172">Notice that there are more properties listed than are displayed by default.</span></span> <span data-ttu-id="78766-173">Un certain nombre de propriétés par défaut ne s’affichent pas en tant que propriétés lors de l’affichage des résultats de `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-173">A number of the default properties displayed don't show up as properties when viewing the results of `Get-Member`.</span></span> <span data-ttu-id="78766-174">Cela est dû au fait que la plupart des valeurs affichées, telles que `NPM(K)`, `PM(K)`, `WS(K)` et `CPU(s)`, sont des propriétés calculées.</span><span class="sxs-lookup"><span data-stu-id="78766-174">This is because many of the displayed values, such as `NPM(K)`, `PM(K)`, `WS(K)`, and `CPU(s)`, are calculated properties.</span></span> <span data-ttu-id="78766-175">Pour déterminer le nom des propriétés, la commande doit être redirigée vers `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-175">To determine the actual property names, the command must be piped to `Get-Member`.</span></span>

<span data-ttu-id="78766-176">Si une commande ne produit pas de sortie, elle ne peut pas être redirigée vers `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-176">If a command does not produce output, it can't be piped to `Get-Member`.</span></span> <span data-ttu-id="78766-177">Étant donné que `Start-Service` ne produit pas de sortie par défaut, elle génère une erreur lorsque vous essayez de la rediriger vers `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-177">Since `Start-Service` doesn't produce any output by default, it generates an error when you try to pipe it to `Get-Member`.</span></span>

```powershell
Start-Service -Name w32time | Get-Member
```

```Output
Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:31
+ Start-Service -Name w32time | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMembe
   rCommand
```

<span data-ttu-id="78766-178">Le paramètre **PassThru** peut être spécifié à l’aide de l’applet de commande `Start-Service` pour lui faire produire une sortie, qui est ensuite redirigée vers `Get-Member` sans erreur.</span><span class="sxs-lookup"><span data-stu-id="78766-178">The **PassThru** parameter can be specified with the `Start-Service` cmdlet make it produce output, which is then piped to `Get-Member` without error.</span></span>

```powershell
Start-Service -Name w32time -PassThru | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController

Name                      MemberType    Definition
----                      ----------    ----------
Name                      AliasProperty Name = ServiceName
RequiredServices          AliasProperty RequiredServices = ServicesDependedOn
Disposed                  Event         System.EventHandler Disposed(System.Object, Sy...
Close                     Method        void Close()
Continue                  Method        void Continue()
CreateObjRef              Method        System.Runtime.Remoting.ObjRef CreateObjRef(ty...
Dispose                   Method        void Dispose(), void IDisposable.Dispose()
Equals                    Method        bool Equals(System.Object obj)
ExecuteCommand            Method        void ExecuteCommand(int command)
GetHashCode               Method        int GetHashCode()
GetLifetimeService        Method        System.Object GetLifetimeService()
GetType                   Method        type GetType()
InitializeLifetimeService Method        System.Object InitializeLifetimeService()
Pause                     Method        void Pause()
Refresh                   Method        void Refresh()
Start                     Method        void Start(), void Start(string[] args)
Stop                      Method        void Stop()
WaitForStatus             Method        void WaitForStatus(System.ServiceProcess.Servi...
CanPauseAndContinue       Property      bool CanPauseAndContinue {get;}
CanShutdown               Property      bool CanShutdown {get;}
CanStop                   Property      bool CanStop {get;}
Container                 Property      System.ComponentModel.IContainer Container {get;}
DependentServices         Property      System.ServiceProcess.ServiceController[] Depe...
DisplayName               Property      string DisplayName {get;set;}
MachineName               Property      string MachineName {get;set;}
ServiceHandle             Property      System.Runtime.InteropServices.SafeHandle Serv...
ServiceName               Property      string ServiceName {get;set;}
ServicesDependedOn        Property      System.ServiceProcess.ServiceController[] Serv...
ServiceType               Property      System.ServiceProcess.ServiceType ServiceType ...
Site                      Property      System.ComponentModel.ISite Site {get;set;}
StartType                 Property      System.ServiceProcess.ServiceStartMode StartTy...
Status                    Property      System.ServiceProcess.ServiceControllerStatus ...
ToString                  ScriptMethod  System.Object ToString();
```

<span data-ttu-id="78766-179">Pour être redirigée vers `Get-Member`, une commande doit produire une sortie basée sur un objet.</span><span class="sxs-lookup"><span data-stu-id="78766-179">To be piped to `Get-Member`, a command must produce object-based output.</span></span>

```powershell
Get-Service -Name w32time | Out-Host | Get-Member
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time

Get-Member : You must specify an object for the Get-Member cmdlet.
At line:1 char:40
+ Get-Service -Name w32time | Out-Host | Get-Member
+
    + CategoryInfo          : CloseError: (:) [Get-Member], InvalidOperationException
    + FullyQualifiedErrorId : NoObjectInGetMember,Microsoft.PowerShell.Commands.GetMemberCommand
```

<span data-ttu-id="78766-180">`Out-Host` écrit directement sur l’hôte PowerShell, mais ne produit pas de sortie basée sur les objets pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="78766-180">`Out-Host` writes directly to the PowerShell host, but it doesn't produce object-based output for the pipeline.</span></span> <span data-ttu-id="78766-181">Elle ne peut donc pas être redirigée vers `Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="78766-181">So it can't be piped to `Get-Member`.</span></span>

## <a name="active-directory"></a><span data-ttu-id="78766-182">Active Directory</span><span class="sxs-lookup"><span data-stu-id="78766-182">Active Directory</span></span>

> [!NOTE]
> <span data-ttu-id="78766-183">Les outils d’administration de serveur distant qui sont listés dans la section Configuration requise de ce chapitre sont nécessaires pour suivre cette section.</span><span class="sxs-lookup"><span data-stu-id="78766-183">The Remote Server Administration Tools listed in the requirements section of this chapter are required to complete this section.</span></span> <span data-ttu-id="78766-184">En outre, comme indiqué dans la présentation de ce livre, votre ordinateur Windows 10 Lab Environment doit faire partie du domaine de l’environnement lab.</span><span class="sxs-lookup"><span data-stu-id="78766-184">Also, as mentioned in the introduction to this book, your Windows 10 lab environment computer must be a member of the lab environment domain.</span></span>

<span data-ttu-id="78766-185">Utilisez `Get-Command` avec le paramètre **Module** pour déterminer quelles commandes ont été ajoutées dans le cadre du module PowerShell ActiveDirectory lors de l’installation des outils d’administration de serveur distant.</span><span class="sxs-lookup"><span data-stu-id="78766-185">Use `Get-Command` with the **Module** parameter to determine what commands were added as part of the ActiveDirectory PowerShell module when the remote server administration tools were installed.</span></span>

```powershell
Get-Command -Module ActiveDirectory
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Add-ADCentralAccessPolicyMember                    1.0.0.0    ActiveDi...
Cmdlet          Add-ADComputerServiceAccount                       1.0.0.0    ActiveDi...
Cmdlet          Add-ADDomainControllerPasswordReplicationPolicy    1.0.0.0    ActiveDi...
Cmdlet          Add-ADFineGrainedPasswordPolicySubject             1.0.0.0    ActiveDi...
Cmdlet          Add-ADGroupMember                                  1.0.0.0    ActiveDi...
Cmdlet          Add-ADPrincipalGroupMembership                     1.0.0.0    ActiveDi...
Cmdlet          Add-ADResourcePropertyListMember                   1.0.0.0    ActiveDi...
Cmdlet          Clear-ADAccountExpiration                          1.0.0.0    ActiveDi...
Cmdlet          Clear-ADClaimTransformLink                         1.0.0.0    ActiveDi...
Cmdlet          Disable-ADAccount                                  1.0.0.0    ActiveDi...
...
```

<span data-ttu-id="78766-186">Au total, 147 commandes ont été ajoutées dans le cadre du module PowerShell ActiveDirectory.</span><span class="sxs-lookup"><span data-stu-id="78766-186">A total of 147 commands were added as part of the ActiveDirectory PowerShell module.</span></span> <span data-ttu-id="78766-187">Certaines de ces commandes retournent uniquement une partie des propriétés disponibles par défaut.</span><span class="sxs-lookup"><span data-stu-id="78766-187">Some commands of these commands only return a portion of the available properties by default.</span></span>

<span data-ttu-id="78766-188">Avez-vous remarqué quelque chose de différent concernant le nom des commandes de ce module ?</span><span class="sxs-lookup"><span data-stu-id="78766-188">Did you notice anything different about the names of the commands in this module?</span></span> <span data-ttu-id="78766-189">La partie consacrée au nom comporte un préfixe AD.</span><span class="sxs-lookup"><span data-stu-id="78766-189">The noun portion of the commands has an AD prefix.</span></span> <span data-ttu-id="78766-190">Ceci est fréquent avec les commandes de la plupart des modules.</span><span class="sxs-lookup"><span data-stu-id="78766-190">This is common to see on the commands of most modules.</span></span> <span data-ttu-id="78766-191">Le préfixe est conçu pour éviter les conflits de noms.</span><span class="sxs-lookup"><span data-stu-id="78766-191">The prefix is designed to help prevent naming conflicts.</span></span>

```powershell
Get-ADUser -Identity mike | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name              MemberType            Definition
----              ----------            ----------
Contains          Method                bool Contains(string propertyName)
Equals            Method                bool Equals(System.Object obj)
GetEnumerator     Method                System.Collections.IDictionaryEnumerator GetEn...
GetHashCode       Method                int GetHashCode()
GetType           Method                type GetType()
ToString          Method                string ToString()
Item              ParameterizedProperty Microsoft.ActiveDirectory.Management.ADPropert...
DistinguishedName Property              System.String DistinguishedName {get;set;}
Enabled           Property              System.Boolean Enabled {get;set;}
GivenName         Property              System.String GivenName {get;set;}
Name              Property              System.String Name {get;}
ObjectClass       Property              System.String ObjectClass {get;set;}
ObjectGUID        Property              System.Nullable`1[[System.Guid, mscorlib, Vers...
SamAccountName    Property              System.String SamAccountName {get;set;}
SID               Property              System.Security.Principal.SecurityIdentifier S...
Surname           Property              System.String Surname {get;set;}
UserPrincipalName Property              System.String UserPrincipalName {get;set;}
```

<span data-ttu-id="78766-192">Même si votre connaissance d’Active Directory est limitée, vous savez probablement qu’un compte d’utilisateur a plus de propriétés que ce qui est indiqué dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="78766-192">Even if you're only vaguely familiar with Active Directory, you're probably aware that a user account has more properties than are shown in this example.</span></span>

<span data-ttu-id="78766-193">L’applet de commande `Get-ADUser` comporte un paramètre **Properties** qui est utilisé pour spécifier les propriétés supplémentaires (autres que par défaut) que vous souhaitez retourner.</span><span class="sxs-lookup"><span data-stu-id="78766-193">The `Get-ADUser` cmdlet has a **Properties** parameter that is used to specify the additional (non-default) properties you want to return.</span></span> <span data-ttu-id="78766-194">La spécification du caractère générique `*` permet de toutes les retourner.</span><span class="sxs-lookup"><span data-stu-id="78766-194">Specifying the `*` wildcard character returns all of them.</span></span>

```powershell
Get-ADUser -Identity mike -Properties * | Get-Member
```

```Output
   TypeName: Microsoft.ActiveDirectory.Management.ADUser

Name                                 MemberType            Definition
----                                 ----------            ----------
Contains                             Method                bool Contains(string proper...
Equals                               Method                bool Equals(System.Object obj)
GetEnumerator                        Method                System.Collections.IDiction...
GetHashCode                          Method                int GetHashCode()
GetType                              Method                type GetType()
ToString                             Method                string ToString()
Item                                 ParameterizedProperty Microsoft.ActiveDirectory.M...
AccountExpirationDate                Property              System.DateTime AccountExpi...
accountExpires                       Property              System.Int64 accountExpires...
AccountLockoutTime                   Property              System.DateTime AccountLock...
AccountNotDelegated                  Property              System.Boolean AccountNotDe...
AllowReversiblePasswordEncryption    Property              System.Boolean AllowReversi...
AuthenticationPolicy                 Property              Microsoft.ActiveDirectory.M...
AuthenticationPolicySilo             Property              Microsoft.ActiveDirectory.M...
BadLogonCount                        Property              System.Int32 BadLogonCount ...
badPasswordTime                      Property              System.Int64 badPasswordTim...
badPwdCount                          Property              System.Int32 badPwdCount {g...
CannotChangePassword                 Property              System.Boolean CannotChange...
CanonicalName                        Property              System.String CanonicalName...
Certificates                         Property              Microsoft.ActiveDirectory.M...
City                                 Property              System.String City {get;set;}
CN                                   Property              System.String CN {get;}
codePage                             Property              System.Int32 codePage {get;...
Company                              Property              System.String Company {get;...
CompoundIdentitySupported            Property              Microsoft.ActiveDirectory.M...
Country                              Property              System.String Country {get;...
countryCode                          Property              System.Int32 countryCode {g...
Created                              Property              System.DateTime Created {get;}
createTimeStamp                      Property              System.DateTime createTimeS...
Deleted                              Property              System.Boolean Deleted {get;}
Department                           Property              System.String Department {g...
Description                          Property              System.String Description {...
DisplayName                          Property              System.String DisplayName {...
DistinguishedName                    Property              System.String Distinguished...
Division                             Property              System.String Division {get...
DoesNotRequirePreAuth                Property              System.Boolean DoesNotRequi...
dSCorePropagationData                Property              Microsoft.ActiveDirectory.M...
EmailAddress                         Property              System.String EmailAddress ...
EmployeeID                           Property              System.String EmployeeID {g...
EmployeeNumber                       Property              System.String EmployeeNumbe...
Enabled                              Property              System.Boolean Enabled {get...
Fax                                  Property              System.String Fax {get;set;}
GivenName                            Property              System.String GivenName {ge...
HomeDirectory                        Property              System.String HomeDirectory...
HomedirRequired                      Property              System.Boolean HomedirRequi...
HomeDrive                            Property              System.String HomeDrive {ge...
HomePage                             Property              System.String HomePage {get...
HomePhone                            Property              System.String HomePhone {ge...
Initials                             Property              System.String Initials {get...
instanceType                         Property              System.Int32 instanceType {...
isDeleted                            Property              System.Boolean isDeleted {g...
KerberosEncryptionType               Property              Microsoft.ActiveDirectory.M...
LastBadPasswordAttempt               Property              System.DateTime LastBadPass...
LastKnownParent                      Property              System.String LastKnownPare...
lastLogoff                           Property              System.Int64 lastLogoff {ge...
lastLogon                            Property              System.Int64 lastLogon {get...
LastLogonDate                        Property              System.DateTime LastLogonDa...
lastLogonTimestamp                   Property              System.Int64 lastLogonTimes...
LockedOut                            Property              System.Boolean LockedOut {g...
logonCount                           Property              System.Int32 logonCount {ge...
LogonWorkstations                    Property              System.String LogonWorkstat...
Manager                              Property              System.String Manager {get;...
MemberOf                             Property              Microsoft.ActiveDirectory.M...
MNSLogonAccount                      Property              System.Boolean MNSLogonAcco...
MobilePhone                          Property              System.String MobilePhone {...
Modified                             Property              System.DateTime Modified {g...
modifyTimeStamp                      Property              System.DateTime modifyTimeS...
msDS-User-Account-Control-Computed   Property              System.Int32 msDS-User-Acco...
Name                                 Property              System.String Name {get;}
nTSecurityDescriptor                 Property              System.DirectoryServices.Ac...
ObjectCategory                       Property              System.String ObjectCategor...
ObjectClass                          Property              System.String ObjectClass {...
ObjectGUID                           Property              System.Nullable`1[[System.G...
objectSid                            Property              System.Security.Principal.S...
Office                               Property              System.String Office {get;s...
OfficePhone                          Property              System.String OfficePhone {...
Organization                         Property              System.String Organization ...
OtherName                            Property              System.String OtherName {ge...
PasswordExpired                      Property              System.Boolean PasswordExpi...
PasswordLastSet                      Property              System.DateTime PasswordLas...
PasswordNeverExpires                 Property              System.Boolean PasswordNeve...
PasswordNotRequired                  Property              System.Boolean PasswordNotR...
POBox                                Property              System.String POBox {get;set;}
PostalCode                           Property              System.String PostalCode {g...
PrimaryGroup                         Property              System.String PrimaryGroup ...
primaryGroupID                       Property              System.Int32 primaryGroupID...
PrincipalsAllowedToDelegateToAccount Property              Microsoft.ActiveDirectory.M...
ProfilePath                          Property              System.String ProfilePath {...
ProtectedFromAccidentalDeletion      Property              System.Boolean ProtectedFro...
pwdAnswer                            Property              System.String pwdAnswer {ge...
pwdLastSet                           Property              System.Int64 pwdLastSet {ge...
pwdQuestion                          Property              System.String pwdQuestion {...
SamAccountName                       Property              System.String SamAccountNam...
sAMAccountType                       Property              System.Int32 sAMAccountType...
ScriptPath                           Property              System.String ScriptPath {g...
sDRightsEffective                    Property              System.Int32 sDRightsEffect...
ServicePrincipalNames                Property              Microsoft.ActiveDirectory.M...
SID                                  Property              System.Security.Principal.S...
SIDHistory                           Property              Microsoft.ActiveDirectory.M...
SmartcardLogonRequired               Property              System.Boolean SmartcardLog...
sn                                   Property              System.String sn {get;set;}
State                                Property              System.String State {get;set;}
StreetAddress                        Property              System.String StreetAddress...
Surname                              Property              System.String Surname {get;...
Title                                Property              System.String Title {get;set;}
TrustedForDelegation                 Property              System.Boolean TrustedForDe...
TrustedToAuthForDelegation           Property              System.Boolean TrustedToAut...
UseDESKeyOnly                        Property              System.Boolean UseDESKeyOnl...
userAccountControl                   Property              System.Int32 userAccountCon...
userCertificate                      Property              Microsoft.ActiveDirectory.M...
UserPrincipalName                    Property              System.String UserPrincipal...
uSNChanged                           Property              System.Int64 uSNChanged {get;}
uSNCreated                           Property              System.Int64 uSNCreated {get;}
whenChanged                          Property              System.DateTime whenChanged...
whenCreated                          Property              System.DateTime whenCreated...
```

<span data-ttu-id="78766-195">Voilà, nous y sommes.</span><span class="sxs-lookup"><span data-stu-id="78766-195">Now that looks more like it.</span></span>

<span data-ttu-id="78766-196">Savez-vous pourquoi les propriétés d’un compte d’utilisateur Active Directory sont si limitées par défaut ?</span><span class="sxs-lookup"><span data-stu-id="78766-196">Can you think of a reason why the properties of an Active Directory user account would be so limited by default?</span></span> <span data-ttu-id="78766-197">Imaginez ce qui se passerait si vous retourniez chaque propriété de chaque compte d’utilisateur dans votre environnement Active Directory de production.</span><span class="sxs-lookup"><span data-stu-id="78766-197">Imagine if you returned every property for every user account in your production Active Directory environment.</span></span> <span data-ttu-id="78766-198">Pensez à la détérioration des performances que cela pourrait provoquer, non seulement pour les contrôleurs de domaine, mais également pour votre réseau.</span><span class="sxs-lookup"><span data-stu-id="78766-198">Think of the performance degradation that you could cause, not only to the domain controllers themselves, but also to your network.</span></span> <span data-ttu-id="78766-199">Il est peu probable que vous ayez besoin de toutes les propriétés de toutes façons.</span><span class="sxs-lookup"><span data-stu-id="78766-199">It's doubtful that you'll actually need every property anyway.</span></span> <span data-ttu-id="78766-200">Le fait de retourner toutes les propriétés d’un seul compte d’utilisateur est parfaitement acceptable si vous souhaitez connaître les propriétés qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="78766-200">Returning all of the properties for a single user account is perfectly acceptable when you're trying to determine what properties exist.</span></span>

<span data-ttu-id="78766-201">Il n’est pas rare d’exécuter une commande à de nombreuses reprises lors de son prototypage.</span><span class="sxs-lookup"><span data-stu-id="78766-201">It's not uncommon to run a command many times when prototyping it.</span></span> <span data-ttu-id="78766-202">Si vous envisagez d’exécuter une requête volumineuse, exécutez-la une fois et stockez les résultats dans une variable.</span><span class="sxs-lookup"><span data-stu-id="78766-202">If you're going to perform some huge query, query it once and store the results in a variable.</span></span> <span data-ttu-id="78766-203">Utilisez ensuite le contenu de la variable au lieu d’exécuter plusieurs fois une requête coûteuse.</span><span class="sxs-lookup"><span data-stu-id="78766-203">Then work with the contents of the variable instead of repeatedly using some expensive query.</span></span>

```powershell
$Users = Get-ADUser -Identity mike -Properties *
```

<span data-ttu-id="78766-204">Au lieu d’exécuter la commande précédente plusieurs fois, utilisez le contenu de la variable `$Users`.</span><span class="sxs-lookup"><span data-stu-id="78766-204">Use the contents of the `$Users` variable instead of running the previous command numerous times.</span></span>
<span data-ttu-id="78766-205">Notez que le contenu de la variable n’est pas mis à jour lorsque des modifications sont apportées à cet utilisateur dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="78766-205">Keep in mind that the contents of the variable aren't updated when changes are made to that user in Active Directory.</span></span>

<span data-ttu-id="78766-206">Vous pouvez rediriger la variable `$Users` vers `Get-Member` pour découvrir les propriétés disponibles.</span><span class="sxs-lookup"><span data-stu-id="78766-206">You could pipe the `$Users` variable to `Get-Member` to discover the available properties.</span></span>

```powershell
$Users | Get-Member
```

<span data-ttu-id="78766-207">Sélectionnez ensuite chaque propriété en redirigeant `$Users` vers `Select-Object`, sans jamais avoir à interroger Active Directory plus d’une fois.</span><span class="sxs-lookup"><span data-stu-id="78766-207">Then select the individual properties by piping `$Users` to `Select-Object`, all without ever having to query Active Directory more than one time.</span></span>

```powershell
$Users | Select-Object -Property Name, LastLogonDate, LastBadPasswordAttempt
```

<span data-ttu-id="78766-208">Si vous souhaitez interroger Active Directory plusieurs fois, utilisez le paramètre **Properties** pour spécifier les propriétés autres que par défaut de votre choix.</span><span class="sxs-lookup"><span data-stu-id="78766-208">If you are going to query Active Directory more than once, use the **Properties** parameter to specify any non-default properties you want.</span></span>

```powershell
Get-ADUser -Identity mike -Properties LastLogonDate, LastBadPasswordAttempt
```

```Output
DistinguishedName      : CN=Mike F. Robbins,OU=Sales,DC=mikefrobbins,DC=com
Enabled                : True
GivenName              : Mike
LastBadPasswordAttempt : 2/4/2017 10:46:15 AM
LastLogonDate          : 2/18/2017 12:45:14 AM
Name                   : Mike F. Robbins
ObjectClass            : user
ObjectGUID             : a82a8c58-1332-4a57-a6e2-68e0c750ea56
SamAccountName         : mike
SID                    : S-1-5-21-2989741381-570885089-3319121794-1108
Surname                : Robbins
UserPrincipalName      : miker@mikefrobbins.com
```

## <a name="summary"></a><span data-ttu-id="78766-209">Résumé</span><span class="sxs-lookup"><span data-stu-id="78766-209">Summary</span></span>

<span data-ttu-id="78766-210">Dans ce chapitre, vous avez vu comment déterminer le type d’objet produit par une commande, comment déterminer quelles propriétés et méthodes sont disponibles pour une commande, et comment utiliser des commandes qui limitent les propriétés retournées par défaut.</span><span class="sxs-lookup"><span data-stu-id="78766-210">In this chapter, you've learned how to determine what type of object a command produces, how to determine what properties and methods are available for a command, and how to work with commands that limit the properties that are returned by default.</span></span>

## <a name="review"></a><span data-ttu-id="78766-211">Révision</span><span class="sxs-lookup"><span data-stu-id="78766-211">Review</span></span>

1. <span data-ttu-id="78766-212">Quel type d’objet est généré par l’applet de commande `Get-Process` ?</span><span class="sxs-lookup"><span data-stu-id="78766-212">What type of object does the `Get-Process` cmdlet produce?</span></span>
1. <span data-ttu-id="78766-213">Comment connaître les propriétés qui sont disponibles pour une commande ?</span><span class="sxs-lookup"><span data-stu-id="78766-213">How do you determine what the available properties are for a command?</span></span>
1. <span data-ttu-id="78766-214">Si une commande existe pour obtenir quelque chose, mais pas pour définir cette même chose, que devez-vous vérifier ?</span><span class="sxs-lookup"><span data-stu-id="78766-214">If a command exists for getting something but not for setting the same thing, what should you check for?</span></span>
1. <span data-ttu-id="78766-215">Comment faire produire une sortie à certaines commandes qui ne produisent pas de sortie par défaut ?</span><span class="sxs-lookup"><span data-stu-id="78766-215">How can certain commands that don't produce output by default be made to produce output?</span></span>
1. <span data-ttu-id="78766-216">Si vous prévoyez d’utiliser les résultats d’une commande qui produit une sortie très volumineuse, que devez-vous faire ?</span><span class="sxs-lookup"><span data-stu-id="78766-216">If you're going to be working with the results of a command that produces an enormous amount of output, what should you consider doing?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="78766-217">Lecture recommandée</span><span class="sxs-lookup"><span data-stu-id="78766-217">Recommended Reading</span></span>

- <span data-ttu-id="78766-218">[Get-Member][]</span><span class="sxs-lookup"><span data-stu-id="78766-218">[Get-Member][]</span></span>
- <span data-ttu-id="78766-219">[Affichage de la structure des objets (Get-Member)][]</span><span class="sxs-lookup"><span data-stu-id="78766-219">[Viewing Object Structure (Get-Member)][]</span></span>
- <span data-ttu-id="78766-220">[about_Objects][]</span><span class="sxs-lookup"><span data-stu-id="78766-220">[about_Objects][]</span></span>
- <span data-ttu-id="78766-221">[about_Properties][]</span><span class="sxs-lookup"><span data-stu-id="78766-221">[about_Properties][]</span></span>
- <span data-ttu-id="78766-222">[about_Methods][]</span><span class="sxs-lookup"><span data-stu-id="78766-222">[about_Methods][]</span></span>
- <span data-ttu-id="78766-223">[Aucune applet de commande PowerShell pour démarrer ou arrêter un événement ? N’oubliez pas de vérifier les méthodes sur les applets de commande obtenir][use-methods]</span><span class="sxs-lookup"><span data-stu-id="78766-223">[No PowerShell Cmdlet to Start or Stop Something? Don't Forget to Check for Methods on the Get Cmdlets][use-methods]</span></span>

<!-- link references -->
[RSAT pour Windows]: https://support.microsoft.com/help/2693643
[RSAT for Windows]: https://support.microsoft.com/help/2693643
[Modules de gestion Windows]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Windows Management modules]: /powershell/scripting/whats-new/module-compatibility#windows-management-modules
[Get-Member]: /powershell/module/microsoft.powershell.utility/get-member
[Affichage de la structure des objets (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[Viewing Object Structure (Get-Member)]: /powershell/scripting/samples/viewing-object-structure--get-member-
[about_Objects]: /powershell/module/microsoft.powershell.core/about/about_objects
[about_Properties]: /powershell/module/microsoft.powershell.core/about/about_properties
[about_Methods]: /powershell/module/microsoft.powershell.core/about/about_methods
[use-methods]: https://mikefrobbins.com/2016/12/15/no-powershell-cmdlet-to-start-or-stop-something-dont-forget-to-check-for-methods-on-the-get-cmdlets/
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
