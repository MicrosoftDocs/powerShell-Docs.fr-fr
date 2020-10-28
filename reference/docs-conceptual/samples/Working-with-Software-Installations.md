---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Utilisation des installations de logiciels
description: Cet article explique comment utiliser WMI pour gérer les logiciels installés dans Windows.
ms.openlocfilehash: 3cf8e3c58e9f2814e2551b3602bd7b47b375aed8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500876"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="86df4-104">Utilisation des installations de logiciels</span><span class="sxs-lookup"><span data-stu-id="86df4-104">Working with Software Installations</span></span>

<span data-ttu-id="86df4-105">Les applications conçues pour utiliser Windows Installer sont accessibles via la classe WMI **Win32_Product** . Toutefois, toutes les applications ne font pas appel à Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="86df4-105">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="86df4-106">En général, les applications qui utilisent d'autres routines d'installation ne sont pas gérées par Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="86df4-106">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="86df4-107">Les techniques spécifiques à employer avec ces applications dépendent du programme d'installation et des décisions prises par le développeur de l'application.</span><span class="sxs-lookup"><span data-stu-id="86df4-107">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="86df4-108">Par exemple, les applications installées par copie des fichiers dans un dossier sur l'ordinateur ne peuvent généralement pas être gérées au moyen des techniques présentées ici.</span><span class="sxs-lookup"><span data-stu-id="86df4-108">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="86df4-109">Vous pouvez gérer ces applications en tant que fichiers et dossiers en utilisant les techniques présentées dans la section [Utilisation des fichiers et dossiers](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="86df4-109">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="86df4-110">La classe **Win32_Product** n’est pas optimisée pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="86df4-110">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="86df4-111">Les requêtes basées sur des filtres génériques forcent WMI à utiliser le fournisseur MSI pour énumérer tous les produits installés avant d’analyser de façon séquentielle la liste complète pour gérer le filtre.</span><span class="sxs-lookup"><span data-stu-id="86df4-111">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="86df4-112">Ce processus lance également une vérification de cohérence des packages installés, en vérifiant et en réparant l’installation.</span><span class="sxs-lookup"><span data-stu-id="86df4-112">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="86df4-113">La validation est un processus assez lent qui peut entraîner des erreurs dans les journaux des événements.</span><span class="sxs-lookup"><span data-stu-id="86df4-113">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="86df4-114">Pour plus d’informations, consultez l’[article 974524 de la Base de connaissances](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="86df4-114">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="86df4-115">Affichage de la liste des applications Windows Installer</span><span class="sxs-lookup"><span data-stu-id="86df4-115">Listing Windows Installer Applications</span></span>

<span data-ttu-id="86df4-116">Pour répertorier les applications installées avec Windows Installer sur un système local ou distant, utilisez la requête WMI simple suivante :</span><span class="sxs-lookup"><span data-stu-id="86df4-116">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="86df4-117">Pour afficher toutes les propriétés de l’objet **Win32_Product** , utilisez le paramètre **Property** des applets de commande de mise en forme, telle l’applet de commande `Format-List`, avec la valeur `*` (all).</span><span class="sxs-lookup"><span data-stu-id="86df4-117">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="86df4-118">Vous pouvez également utiliser le paramètre `Get-CimInstance` **Filtre** pour sélectionner uniquement le Runtime Microsoft .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="86df4-118">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="86df4-119">La valeur du paramètre **Filter** utilise la syntaxe du langage de requêtes WMI (WQL), et non la syntaxe Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86df4-119">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="86df4-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="86df4-120">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="86df4-121">Pour répertorier uniquement les propriétés qui vous intéressent, utilisez le paramètre **Property** des applets de commande de mise en forme pour répertorier les propriétés désirées.</span><span class="sxs-lookup"><span data-stu-id="86df4-121">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="86df4-122">Affichage de la liste de toutes les applications non installables</span><span class="sxs-lookup"><span data-stu-id="86df4-122">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="86df4-123">Étant donné que la plupart des applications standard inscrivent un programme de désinstallation auprès de Windows, nous pouvons les rechercher dans le Registre Windows pour les utiliser localement.</span><span class="sxs-lookup"><span data-stu-id="86df4-123">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="86df4-124">Aucune méthode ne garantit l'identification de toutes les applications présentes sur un système.</span><span class="sxs-lookup"><span data-stu-id="86df4-124">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="86df4-125">Il est toutefois possible de rechercher tous les programmes avec des listes affichées dans **Ajouter ou supprimer des programmes** dans la clé de registre suivante :</span><span class="sxs-lookup"><span data-stu-id="86df4-125">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="86df4-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="86df4-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="86df4-127">Nous pouvons examiner cette clé pour trouver des applications.</span><span class="sxs-lookup"><span data-stu-id="86df4-127">We can examine this key to find applications.</span></span> <span data-ttu-id="86df4-128">Pour faciliter l'affichage de la clé Uninstall, nous pouvons mapper un lecteur PowerShell à cet emplacement de Registre :</span><span class="sxs-lookup"><span data-stu-id="86df4-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="86df4-129">Nous disposons désormais d'un lecteur nommé « Uninstall » qui peut servir à rechercher rapidement et facilement des installations d'applications.</span><span class="sxs-lookup"><span data-stu-id="86df4-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="86df4-130">Nous pouvons trouver le nombre d’applications installées en comptant le nombre de clés de Registre dans le lecteur PowerShell Uninstall :</span><span class="sxs-lookup"><span data-stu-id="86df4-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="86df4-131">Nous pouvons affiner cette liste d’applications à l’aide de diverses techniques, la première d’entre elles étant `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="86df4-131">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="86df4-132">Pour obtenir la liste des applications et les enregistrer dans la variable `$UninstallableApplications`, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="86df4-132">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="86df4-133">Pour afficher les valeurs des entrées de Registre dans les clés de Registre sous Uninstall, utilisez la méthode GetValue des clés de Registre.</span><span class="sxs-lookup"><span data-stu-id="86df4-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="86df4-134">La valeur de la méthode est le nom de l'entrée de Registre.</span><span class="sxs-lookup"><span data-stu-id="86df4-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="86df4-135">Par exemple, pour rechercher les noms d'affichage des applications dans la clé Uninstall, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="86df4-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="86df4-136">Rien ne garantit que ces valeurs sont uniques.</span><span class="sxs-lookup"><span data-stu-id="86df4-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="86df4-137">Dans l'exemple suivant, deux éléments installés apparaissent sous le nom « Windows Media Encoder 9 Series » :</span><span class="sxs-lookup"><span data-stu-id="86df4-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a><span data-ttu-id="86df4-138">Installation d'applications</span><span class="sxs-lookup"><span data-stu-id="86df4-138">Installing Applications</span></span>

<span data-ttu-id="86df4-139">Vous pouvez utiliser la classe **Win32_Product** pour installer, localement ou à distance, des packages Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="86df4-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="86df4-140">Pour installer une application, vous devez démarrer PowerShell avec l'option « Exécuter en tant qu'administrateur ».</span><span class="sxs-lookup"><span data-stu-id="86df4-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="86df4-141">Pour effectuer une installation à distance, utilisez un chemin d'accès réseau UNC (Universal Naming Convention) pour spécifier le chemin d'accès au package .msi, car le sous-système WMI ne prend pas en charge les chemins d'accès PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86df4-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="86df4-142">Par exemple, pour installer le package NewPackage.msi situé dans le partage réseau `\\AppServ\dsp` sur l’ordinateur distant PC01, tapez la commande suivante à l’invite PowerShell :</span><span class="sxs-lookup"><span data-stu-id="86df4-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="86df4-143">Les applications qui n'utilisent pas la technologie Windows Installer peuvent faire appel à leurs propres méthodes de déploiement automatisé.</span><span class="sxs-lookup"><span data-stu-id="86df4-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="86df4-144">Examinez la documentation de l'application ou consultez le système d'aide du fournisseur de l'application.</span><span class="sxs-lookup"><span data-stu-id="86df4-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="86df4-145">Suppression d'applications</span><span class="sxs-lookup"><span data-stu-id="86df4-145">Removing Applications</span></span>

<span data-ttu-id="86df4-146">La procédure de suppression d'un package Installer à l'aide de Windows PowerShell est semblable à la procédure d'installation.</span><span class="sxs-lookup"><span data-stu-id="86df4-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="86df4-147">Voici un exemple qui sélectionne le package à désinstaller d'après son nom. Dans certains cas, il peut être plus facile d'utiliser un filtre avec **IdentifyingNumber**  :</span><span class="sxs-lookup"><span data-stu-id="86df4-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber** :</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="86df4-148">La suppression d'autres applications n'est pas aussi simple, même si vous travaillez localement.</span><span class="sxs-lookup"><span data-stu-id="86df4-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="86df4-149">Pour obtenir les chaînes de désinstallation à partir de la ligne de commande pour ces applications, extrayez la propriété **UninstallString** .</span><span class="sxs-lookup"><span data-stu-id="86df4-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="86df4-150">Cette méthode fonctionne pour les applications Windows Installer et les programmes plus anciens qui apparaissent sous la clé de Uninstall :</span><span class="sxs-lookup"><span data-stu-id="86df4-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="86df4-151">Si vous le souhaitez, vous pouvez filtrer la sortie en fonction du nom d'affichage :</span><span class="sxs-lookup"><span data-stu-id="86df4-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="86df4-152">Toutefois, pour exploiter ces chaînes provenant directement de l'invite PowerShell, vous devrez peut-être les modifier.</span><span class="sxs-lookup"><span data-stu-id="86df4-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="86df4-153">Mise à niveau d'applications Windows Installer</span><span class="sxs-lookup"><span data-stu-id="86df4-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="86df4-154">Pour mettre à niveau une application, vous devez connaître son nom et le chemin d'accès au package de mise à niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="86df4-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="86df4-155">Muni de ces informations, vous pouvez mettre à niveau une application avec une seule commande PowerShell :</span><span class="sxs-lookup"><span data-stu-id="86df4-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
