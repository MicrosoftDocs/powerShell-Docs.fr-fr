---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation des installations de logiciels
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086270"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="8d631-103">Utilisation des installations de logiciels</span><span class="sxs-lookup"><span data-stu-id="8d631-103">Working with Software Installations</span></span>

<span data-ttu-id="8d631-104">Les applications conçues pour utiliser Windows Installer sont accessibles via la classe WMI **Win32_Product**. Toutefois, certaines applications ne font pas appel à Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="8d631-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="8d631-105">Étant donné que Windows Installer offre la plus vaste palette de techniques standard associées aux applications installables, nous allons examiner principalement ces applications.</span><span class="sxs-lookup"><span data-stu-id="8d631-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="8d631-106">En général, les applications qui utilisent d'autres routines d'installation ne sont pas gérées par Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="8d631-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="8d631-107">Les techniques spécifiques à employer avec ces applications dépendent du programme d'installation et des décisions prises par le développeur de l'application.</span><span class="sxs-lookup"><span data-stu-id="8d631-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="8d631-108">Dans la plupart des cas, les applications installées par copie des fichiers de l'application sur l'ordinateur ne peuvent pas être gérées au moyen des techniques présentées ici.</span><span class="sxs-lookup"><span data-stu-id="8d631-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="8d631-109">Vous pouvez gérer ces applications en tant que fichiers et dossiers en utilisant les techniques présentées dans la section « Utilisation des fichiers et dossiers ».</span><span class="sxs-lookup"><span data-stu-id="8d631-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="8d631-110">Affichage de la liste des applications Windows Installer</span><span class="sxs-lookup"><span data-stu-id="8d631-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="8d631-111">Pour répertorier les applications installées avec Windows Installer sur un système local ou distant, utilisez la requête WMI simple suivante :</span><span class="sxs-lookup"><span data-stu-id="8d631-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="8d631-112">Pour afficher toutes les propriétés de l’objet Win32_Product, utilisez le paramètre Property des applets de commande de mise en forme, telle l’applet de commande Format-List, avec la valeur \* (all).</span><span class="sxs-lookup"><span data-stu-id="8d631-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="8d631-113">Vous pouvez également utiliser le paramètre **Get-WmiObject Filter** pour sélectionner uniquement Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="8d631-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="8d631-114">Le filtre utilisé dans cette commande étant un filtre WMI, il utilise la syntaxe du langage de requêtes WMI (WQL), et non la syntaxe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d631-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="8d631-115">À la place :</span><span class="sxs-lookup"><span data-stu-id="8d631-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="8d631-116">Notez que les requêtes WQL utilisent fréquemment des caractères, tels que des espaces ou des signes d'égalité, qui ont une signification spéciale dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d631-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="8d631-117">Pour cette raison, il est préférable de toujours mettre la valeur du paramètre Filter entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="8d631-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="8d631-118">Vous pouvez également utiliser le caractère d’échappement de Windows PowerShell, à savoir l’accent grave (\`), bien que cela n’améliore pas nécessairement la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="8d631-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="8d631-119">La commande suivante est équivalente à la précédente et retourne les mêmes résultats. Toutefois, des accents graves sont utilisés pour échapper les caractères spéciaux, ce qui évite de mettre la chaîne de filtre entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="8d631-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="8d631-120">Pour répertorier uniquement les propriétés qui vous intéressent, utilisez le paramètre Property des applets de commande de mise en forme pour répertorier les propriétés désirées.</span><span class="sxs-lookup"><span data-stu-id="8d631-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="8d631-121">Enfin, pour obtenir uniquement les noms des applications installées, une instruction **Format-Wide** simplifie la sortie :</span><span class="sxs-lookup"><span data-stu-id="8d631-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="8d631-122">Si nous disposons de plusieurs méthodes pour examiner les applications faisant appel à Windows Installer pour l'installation, notre analyse ne tient pas compte des autres applications pour le moment.</span><span class="sxs-lookup"><span data-stu-id="8d631-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="8d631-123">Étant donné que la plupart des applications standard inscrivent leur programme de désinstallation auprès de Windows, nous pouvons les rechercher dans le Registre Windows pour les utiliser localement.</span><span class="sxs-lookup"><span data-stu-id="8d631-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="8d631-124">Affichage de la liste de toutes les applications non installables</span><span class="sxs-lookup"><span data-stu-id="8d631-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="8d631-125">Bien qu'aucune méthode ne garantisse l'identification de toutes les applications présentes sur un système, il est possible de trouver tous les programmes répertoriés dans la boîte de dialogue Ajout/Suppression de programmes.</span><span class="sxs-lookup"><span data-stu-id="8d631-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="8d631-126">Cette dernière recherche les applications dans la clé de Registre suivante :</span><span class="sxs-lookup"><span data-stu-id="8d631-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="8d631-127">**HKEY_LOCAL_MACHINE\\Logiciel\\Microsoft\\Windows\\CurrentVersion\\Désinstaller**.</span><span class="sxs-lookup"><span data-stu-id="8d631-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="8d631-128">Nous pouvons également examiner cette clé pour trouver des applications.</span><span class="sxs-lookup"><span data-stu-id="8d631-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="8d631-129">Pour faciliter l'affichage de la clé Uninstall, nous pouvons mapper un lecteur Windows PowerShell à cet emplacement de Registre :</span><span class="sxs-lookup"><span data-stu-id="8d631-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="8d631-130">Le lecteur **HKLM:** étant mappé à la racine de **HKEY_LOCAL_MACHINE**, nous utilisons ce lecteur dans le chemin d’accès à la clé Uninstall.</span><span class="sxs-lookup"><span data-stu-id="8d631-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="8d631-131">Au lieu d’utiliser **HKLM:**, nous pourrions recourir à **HKLM** ou à  **HKEY_LOCAL_MACHINE** pour spécifier le chemin d’accès au Registre.</span><span class="sxs-lookup"><span data-stu-id="8d631-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="8d631-132">L'avantage d'utiliser un lecteur de Registre existant, c'est que nous pouvons utiliser la saisie semi-automatique par tabulation pour remplir les noms des clés, ce qui nous évite de les taper.</span><span class="sxs-lookup"><span data-stu-id="8d631-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="8d631-133">Nous disposons désormais d'un lecteur nommé « Uninstall » qui peut servir à rechercher rapidement et facilement des installations d'applications.</span><span class="sxs-lookup"><span data-stu-id="8d631-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="8d631-134">Nous pouvons trouver le nombre d’applications installées en comptant le nombre de clés de Registre dans le lecteur Windows PowerShell Uninstall: :</span><span class="sxs-lookup"><span data-stu-id="8d631-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="8d631-135">Nous pouvons affiner cette liste d’applications à l’aide de diverses techniques, la première d’entre elles étant **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="8d631-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="8d631-136">Pour obtenir la liste des applications et les enregistrer dans la variable **$UninstallableApplications**, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8d631-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="8d631-137">Nous utilisons ici un nom de variable long par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="8d631-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="8d631-138">Dans la réalité, il est inutile d'utiliser des noms longs.</span><span class="sxs-lookup"><span data-stu-id="8d631-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="8d631-139">Bien que vous puissiez utiliser la saisie semi-automatique via la touche Tab pour les noms de variable, vous pouvez également utiliser des noms contenant 1 ou 2 caractères pour aller plus vite.</span><span class="sxs-lookup"><span data-stu-id="8d631-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="8d631-140">Des noms descriptifs plus longs sont particulièrement utiles quand vous développez du code destiné à être réutilisé.</span><span class="sxs-lookup"><span data-stu-id="8d631-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="8d631-141">Pour afficher les valeurs des entrées de Registre dans les clés de Registre sous Uninstall, utilisez la méthode GetValue des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="8d631-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="8d631-142">La valeur de la méthode est le nom de l'entrée de Registre.</span><span class="sxs-lookup"><span data-stu-id="8d631-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="8d631-143">Par exemple, pour rechercher les noms d'affichage des applications dans la clé Uninstall, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8d631-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="8d631-144">Rien ne garantit que ces valeurs sont uniques.</span><span class="sxs-lookup"><span data-stu-id="8d631-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="8d631-145">Dans l'exemple suivant, deux éléments installés apparaissent sous le nom « Windows Media Encoder 9 Series » :</span><span class="sxs-lookup"><span data-stu-id="8d631-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="8d631-146">Installation d'applications</span><span class="sxs-lookup"><span data-stu-id="8d631-146">Installing Applications</span></span>

<span data-ttu-id="8d631-147">Vous pouvez utiliser la classe **Win32_Product** pour installer, localement ou à distance, des packages Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="8d631-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="8d631-148">Dans Windows Vista, Windows Server 2008 et versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l'option « Exécuter en tant qu'administrateur » pour installer une application.</span><span class="sxs-lookup"><span data-stu-id="8d631-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="8d631-149">Pour effectuer une installation à distance, utilisez un chemin d'accès réseau UNC (Universal Naming Convention) pour spécifier le chemin d'accès au package .msi, car le sous-système WMI ne prend pas en charge les chemins d'accès Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8d631-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="8d631-150">Par exemple, pour installer le package NewPackage.msi situé dans le partage réseau \\\\AppServ\\dsp sur l’ordinateur distant PC01, tapez la commande suivante à l’invite Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8d631-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="8d631-151">Les applications qui n'utilisent pas la technologie Windows Installer peuvent faire appel à leurs propres méthodes de déploiement automatisé.</span><span class="sxs-lookup"><span data-stu-id="8d631-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="8d631-152">Pour déterminer s'il existe ou non une méthode d'automatisation du déploiement, examinez la documentation de l'application ou consultez le système d'aide du fournisseur de l'application.</span><span class="sxs-lookup"><span data-stu-id="8d631-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="8d631-153">Dans certains cas, même si le fournisseur d'une application n'a pas spécifiquement prévu d'automatiser l'installation, le fabricant du logiciel d'installation peut proposer certaines techniques d'automatisation.</span><span class="sxs-lookup"><span data-stu-id="8d631-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="8d631-154">Suppression d'applications</span><span class="sxs-lookup"><span data-stu-id="8d631-154">Removing Applications</span></span>

<span data-ttu-id="8d631-155">La procédure de suppression d'un package Windows Installer à l'aide de Windows PowerShell est semblable à la procédure d'installation.</span><span class="sxs-lookup"><span data-stu-id="8d631-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="8d631-156">Voici un exemple qui sélectionne le package à désinstaller d’après son nom. Dans certains cas, il peut être plus facile d’utiliser un filtre avec **IdentifyingNumber** :</span><span class="sxs-lookup"><span data-stu-id="8d631-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="8d631-157">La suppression d'autres applications n'est pas aussi simple, même si vous travaillez localement.</span><span class="sxs-lookup"><span data-stu-id="8d631-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="8d631-158">Pour obtenir les chaînes de désinstallation pour ces applications à partir de la ligne de commande, extrayez la propriété **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="8d631-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="8d631-159">Cette méthode fonctionne pour les applications Windows Installer et les programmes plus anciens qui apparaissent sous la clé de Uninstall :</span><span class="sxs-lookup"><span data-stu-id="8d631-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="8d631-160">Si vous le souhaitez, vous pouvez filtrer la sortie en fonction du nom d'affichage :</span><span class="sxs-lookup"><span data-stu-id="8d631-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="8d631-161">Toutefois, pour exploiter ces chaînes provenant directement de l'invite Windows PowerShell, vous devrez peut-être les modifier.</span><span class="sxs-lookup"><span data-stu-id="8d631-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="8d631-162">Mise à niveau d'applications Windows Installer</span><span class="sxs-lookup"><span data-stu-id="8d631-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="8d631-163">Pour mettre à niveau une application, vous devez connaître son nom et le chemin d'accès au package de mise à niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="8d631-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="8d631-164">Muni de ces informations, vous pouvez mettre à niveau une application avec une seule commande Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="8d631-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```