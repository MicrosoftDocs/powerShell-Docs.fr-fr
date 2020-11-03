---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: df5f335780ad04b2d833180c30cc46a06f85d850
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203590"
---
# <span data-ttu-id="77c84-103">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="77c84-103">New-PSDrive</span></span>

## <span data-ttu-id="77c84-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="77c84-104">SYNOPSIS</span></span>
<span data-ttu-id="77c84-105">Crée des lecteurs réseau mappés temporaires et persistants.</span><span class="sxs-lookup"><span data-stu-id="77c84-105">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="77c84-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="77c84-106">SYNTAX</span></span>

### <span data-ttu-id="77c84-107">Tous</span><span class="sxs-lookup"><span data-stu-id="77c84-107">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="77c84-108">Description</span><span class="sxs-lookup"><span data-stu-id="77c84-108">DESCRIPTION</span></span>

<span data-ttu-id="77c84-109">L' `New-PSDrive` applet de commande crée des lecteurs temporaires et persistants mappés à ou associés à un emplacement dans un magasin de données, tel qu’un lecteur réseau, un répertoire sur l’ordinateur local ou une clé de Registre, et des lecteurs réseau mappés Windows persistants associés à un emplacement de système de fichiers sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="77c84-109">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="77c84-110">Les lecteurs temporaires existent uniquement dans la session PowerShell active et dans les sessions que vous créez dans la session active.</span><span class="sxs-lookup"><span data-stu-id="77c84-110">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="77c84-111">Ils peuvent avoir n’importe quel nom valide dans PowerShell et peuvent être mappés à n’importe quelle ressource locale ou distante.</span><span class="sxs-lookup"><span data-stu-id="77c84-111">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="77c84-112">Vous pouvez utiliser des lecteurs PowerShell temporaires pour accéder aux données dans le magasin de données associé, comme vous le feriez avec n’importe quel lecteur réseau mappé.</span><span class="sxs-lookup"><span data-stu-id="77c84-112">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="77c84-113">Vous pouvez modifier les emplacements dans le lecteur, à l’aide de `Set-Location` , et accéder au contenu du lecteur à l’aide de `Get-Item` ou de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="77c84-113">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="77c84-114">Étant donné que les lecteurs temporaires sont connus uniquement de PowerShell, vous ne pouvez pas y accéder à l’aide de l’Explorateur de fichiers, Windows Management Instrumentation (WMI), COM (Component Object Model), Microsoft .NET Framework ou avec des outils tels que **net use** .</span><span class="sxs-lookup"><span data-stu-id="77c84-114">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use** .</span></span>

<span data-ttu-id="77c84-115">Les fonctionnalités suivantes ont été ajoutées à `New-PSDrive` dans PowerShell 3,0 :</span><span class="sxs-lookup"><span data-stu-id="77c84-115">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="77c84-116">Lecteurs réseau mappés.</span><span class="sxs-lookup"><span data-stu-id="77c84-116">Mapped network drives.</span></span> <span data-ttu-id="77c84-117">Vous pouvez utiliser le paramètre **Persist** de `New-PSDrive` pour créer des lecteurs réseau mappés Windows.</span><span class="sxs-lookup"><span data-stu-id="77c84-117">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="77c84-118">Contrairement aux lecteurs PowerShell temporaires, les lecteurs réseau mappés Windows ne sont pas spécifiques à la session.</span><span class="sxs-lookup"><span data-stu-id="77c84-118">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="77c84-119">Ils sont enregistrés dans Windows et peuvent être gérés à l’aide d’outils Windows standard, tels que l’Explorateur de fichiers et **net use** .</span><span class="sxs-lookup"><span data-stu-id="77c84-119">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use** .</span></span> <span data-ttu-id="77c84-120">Les lecteurs réseau mappés doivent avoir un nom de lettre de lecteur et être connectés à un emplacement du système de fichiers distant.</span><span class="sxs-lookup"><span data-stu-id="77c84-120">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="77c84-121">Lorsque votre commande est limitée localement, sans point, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de l’étendue dans laquelle la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="77c84-121">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="77c84-122">Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le lecteur persiste indéfiniment, vous devez effectuer un point-source du script.</span><span class="sxs-lookup"><span data-stu-id="77c84-122">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="77c84-123">Pour de meilleurs résultats, pour forcer un nouveau lecteur à rester indéfiniment, ajoutez le paramètre **scope** à votre commande et définissez sa valeur sur **Global** .</span><span class="sxs-lookup"><span data-stu-id="77c84-123">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global** .</span></span> <span data-ttu-id="77c84-124">Pour plus d’informations sur la source de points, consultez [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="77c84-124">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="77c84-125">Lecteurs externes.</span><span class="sxs-lookup"><span data-stu-id="77c84-125">External drives.</span></span> <span data-ttu-id="77c84-126">Lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un **PSDrive** au système de fichiers qui représente le nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-126">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="77c84-127">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c84-127">You don't have to restart PowerShell.</span></span> <span data-ttu-id="77c84-128">De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le **PSDrive** qui représente le lecteur supprimé.</span><span class="sxs-lookup"><span data-stu-id="77c84-128">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="77c84-129">Informations d’identification pour les chemins d’accès UNC (Universal Naming Convention).</span><span class="sxs-lookup"><span data-stu-id="77c84-129">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="77c84-130">Lorsque la valeur du paramètre **root** est un chemin d’accès UNC, tel que `\\Server\Share` , les informations d’identification spécifiées dans la valeur du paramètre **Credential** sont utilisées pour créer le **PSDrive** .</span><span class="sxs-lookup"><span data-stu-id="77c84-130">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive** .</span></span> <span data-ttu-id="77c84-131">Dans le cas contraire, les **informations d’identification** ne sont pas effectives lorsque vous créez de nouveaux lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="77c84-131">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="77c84-132">Certains exemples de code utilisent la projection pour réduire la longueur de ligne et améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="77c84-132">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="77c84-133">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="77c84-133">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="77c84-134">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="77c84-134">EXAMPLES</span></span>

### <span data-ttu-id="77c84-135">Exemple 1 : créer un lecteur temporaire mappé à un partage réseau</span><span class="sxs-lookup"><span data-stu-id="77c84-135">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="77c84-136">Cet exemple crée un lecteur PowerShell temporaire qui est mappé à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="77c84-136">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="77c84-137">`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `Public` et le paramètre **PSProvider** pour spécifier le `FileSystem` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c84-137">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="77c84-138">Le paramètre **root** spécifie le chemin d’accès UNC du partage réseau.</span><span class="sxs-lookup"><span data-stu-id="77c84-138">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="77c84-139">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="77c84-139">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="77c84-140">Exemple 2 : créer un lecteur temporaire mappé à un répertoire local</span><span class="sxs-lookup"><span data-stu-id="77c84-140">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="77c84-141">Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="77c84-141">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

<span data-ttu-id="77c84-142">La projection crée les clés et valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="77c84-142">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="77c84-143">Le paramètre **Name** spécifie le nom du lecteur, **mydocs** .</span><span class="sxs-lookup"><span data-stu-id="77c84-143">The **Name** parameter specifies the drive name, **MyDocs** .</span></span> <span data-ttu-id="77c84-144">Le paramètre **PSProvider** spécifie le `FileSystem` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c84-144">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="77c84-145">**Root** spécifie le répertoire de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="77c84-145">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="77c84-146">Le paramètre **Description** décrit l’objectif du lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-146">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="77c84-147">`New-PSDrive` utilise les paramètres de projection pour créer le `MyDocs` lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-147">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="77c84-148">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="77c84-148">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="77c84-149">Exemple 3 : créer un lecteur temporaire pour une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="77c84-149">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="77c84-150">Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à une clé de registre.</span><span class="sxs-lookup"><span data-stu-id="77c84-150">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="77c84-151">Il crée un lecteur nommé MyCompany qui est mappé à la `HKLM:\Software\MyCompany` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="77c84-151">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="77c84-152">`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `MyCompany` et le paramètre **PSProvider** pour spécifier le `Registry` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c84-152">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="77c84-153">Le paramètre **root** spécifie l’emplacement du Registre.</span><span class="sxs-lookup"><span data-stu-id="77c84-153">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="77c84-154">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="77c84-154">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="77c84-155">Exemple 4 : créer un lecteur réseau mappé persistant à l’aide des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="77c84-155">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="77c84-156">Cet exemple mappe un lecteur réseau authentifié avec les informations d’identification d’un compte de service de domaine.</span><span class="sxs-lookup"><span data-stu-id="77c84-156">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="77c84-157">Pour plus d’informations sur l’objet **PSCredential** qui stocke les informations d’identification et sur la manière dont les mots de passe sont stockés sous forme de **SecureString** , consultez la description du paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="77c84-157">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString** , see the **Credential** parameter's description.</span></span>

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> <span data-ttu-id="77c84-158">N’oubliez pas que si vous utilisez l’extrait de code ci-dessus dans un script, définissez la valeur du paramètre d' **étendue** sur « global » pour vous assurer que le lecteur persiste en dehors de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="77c84-158">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="77c84-159">La `$cred` variable stocke un objet **PSCredential** qui contient les informations d’identification du compte de service.</span><span class="sxs-lookup"><span data-stu-id="77c84-159">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="77c84-160">`Get-Credential` vous invite à entrer le mot de passe qui est stocké dans une **SecureString** .</span><span class="sxs-lookup"><span data-stu-id="77c84-160">`Get-Credential` prompts you to enter the password that's stored in a **SecureString** .</span></span>

<span data-ttu-id="77c84-161">`New-PSDrive` crée le lecteur réseau mappé à l’aide de plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="77c84-161">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="77c84-162">**Nom** spécifie la `S` lettre de lecteur que Windows accepte.</span><span class="sxs-lookup"><span data-stu-id="77c84-162">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="77c84-163">et la **racine** définit `\\Server01\Scripts` comme emplacement sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="77c84-163">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="77c84-164">**Persist** crée un lecteur réseau mappé Windows qui est enregistré sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="77c84-164">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="77c84-165">**PSProvider** spécifie le `FileSystem` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="77c84-165">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="77c84-166">**Credential** utilise la `$cred` variable pour obtenir les informations d’identification du compte de service pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="77c84-166">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="77c84-167">Le lecteur mappé peut être affiché sur l’ordinateur local dans les sessions PowerShell, l’Explorateur de fichiers et avec des outils tels que **net use** .</span><span class="sxs-lookup"><span data-stu-id="77c84-167">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use** .</span></span> <span data-ttu-id="77c84-168">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="77c84-168">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="77c84-169">Exemple 5 : créer des lecteurs permanents et temporaires</span><span class="sxs-lookup"><span data-stu-id="77c84-169">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="77c84-170">Cet exemple montre la différence entre un lecteur réseau mappé persistant et un lecteur PowerShell temporaire qui est mappé au même partage réseau.</span><span class="sxs-lookup"><span data-stu-id="77c84-170">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="77c84-171">Si vous fermez la session PowerShell et que vous ouvrez une nouvelle session, le temporaire `PSDrive:` n’est pas disponible, mais le `X:` lecteur persistant est disponible.</span><span class="sxs-lookup"><span data-stu-id="77c84-171">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="77c84-172">Lorsque vous décidez de la méthode à utiliser pour mapper les lecteurs réseau, réfléchissez à la façon dont vous allez utiliser le lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-172">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="77c84-173">Par exemple, s’il doit être persistant et si le lecteur doit être visible par d’autres fonctionnalités de Windows.</span><span class="sxs-lookup"><span data-stu-id="77c84-173">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

## <span data-ttu-id="77c84-174">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="77c84-174">PARAMETERS</span></span>

### <span data-ttu-id="77c84-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="77c84-175">-Confirm</span></span>

<span data-ttu-id="77c84-176">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="77c84-176">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-177">-Credential</span><span class="sxs-lookup"><span data-stu-id="77c84-177">-Credential</span></span>

<span data-ttu-id="77c84-178">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="77c84-178">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="77c84-179">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="77c84-179">The default is the current user.</span></span>

<span data-ttu-id="77c84-180">Depuis PowerShell 3,0, lorsque la valeur du paramètre **root** est un chemin UNC, vous pouvez utiliser les informations d’identification pour créer des lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="77c84-180">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="77c84-181">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="77c84-181">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="77c84-182">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="77c84-182">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="77c84-183">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="77c84-183">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="77c84-184">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="77c84-184">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-185">Description</span><span class="sxs-lookup"><span data-stu-id="77c84-185">-Description</span></span>

<span data-ttu-id="77c84-186">Spécifie une courte description du lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-186">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="77c84-187">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="77c84-187">Type any string.</span></span>

<span data-ttu-id="77c84-188">Pour afficher les descriptions de tous les lecteurs de la session, `Get-PSDrive | Format-Table Name, Description` .</span><span class="sxs-lookup"><span data-stu-id="77c84-188">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="77c84-189">Pour afficher la description d’un lecteur particulier, tapez `(Get-PSDrive <DriveName>).Description` .</span><span class="sxs-lookup"><span data-stu-id="77c84-189">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-190">-Name</span><span class="sxs-lookup"><span data-stu-id="77c84-190">-Name</span></span>

<span data-ttu-id="77c84-191">Spécifie le nom du nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-191">Specifies a name for the new drive.</span></span> <span data-ttu-id="77c84-192">Pour les lecteurs réseau mappés persistants, utilisez une lettre de lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-192">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="77c84-193">Pour les lecteurs PowerShell temporaires, vous n’êtes pas limité aux lettres de lecteur, utilisez une chaîne valide.</span><span class="sxs-lookup"><span data-stu-id="77c84-193">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-194">-Persist</span><span class="sxs-lookup"><span data-stu-id="77c84-194">-Persist</span></span>

<span data-ttu-id="77c84-195">Indique que cette applet de commande crée un lecteur réseau mappé Windows.</span><span class="sxs-lookup"><span data-stu-id="77c84-195">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="77c84-196">Le paramètre **Persist** est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="77c84-196">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="77c84-197">Les lecteurs réseau mappés sont enregistrés dans Windows sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="77c84-197">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="77c84-198">Ils sont persistants, non spécifiques à la session et peuvent être affichés et gérés dans l’Explorateur de fichiers et d’autres outils.</span><span class="sxs-lookup"><span data-stu-id="77c84-198">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="77c84-199">Lorsque vous étendez la commande en local, sans la source de points, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de la portée dans laquelle vous exécutez la commande.</span><span class="sxs-lookup"><span data-stu-id="77c84-199">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="77c84-200">Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le nouveau lecteur persiste indéfiniment, vous devez effectuer un point-source du script.</span><span class="sxs-lookup"><span data-stu-id="77c84-200">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="77c84-201">Pour de meilleurs résultats, pour forcer la conservation d’un nouveau lecteur, spécifiez **Global** comme valeur du paramètre d' **étendue** et include **persiste** dans votre commande.</span><span class="sxs-lookup"><span data-stu-id="77c84-201">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="77c84-202">Le nom du lecteur doit être une lettre, telle que `D` ou `E` .</span><span class="sxs-lookup"><span data-stu-id="77c84-202">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="77c84-203">La valeur du paramètre **root** doit être un chemin d’accès UNC d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="77c84-203">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="77c84-204">La valeur du paramètre **PSProvider** doit être `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="77c84-204">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="77c84-205">Pour déconnecter un lecteur réseau mappé Windows, utilisez l'applet de commande `Remove-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="77c84-205">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="77c84-206">Lorsque vous déconnectez un lecteur réseau Windows mappé, le mappage est définitivement supprimé de l'ordinateur (et pas simplement de la session active).</span><span class="sxs-lookup"><span data-stu-id="77c84-206">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="77c84-207">les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="77c84-207">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="77c84-208">Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="77c84-208">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-209">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="77c84-209">-PSProvider</span></span>

<span data-ttu-id="77c84-210">Spécifie le fournisseur PowerShell qui prend en charge les lecteurs de ce type.</span><span class="sxs-lookup"><span data-stu-id="77c84-210">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="77c84-211">Par exemple, si le lecteur est associé à un répertoire de partage réseau ou de système de fichiers, le fournisseur PowerShell est `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="77c84-211">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="77c84-212">Si le lecteur est associé à une clé de Registre, le fournisseur est `Registry` .</span><span class="sxs-lookup"><span data-stu-id="77c84-212">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="77c84-213">Les lecteurs PowerShell temporaires peuvent être associés à n’importe quel fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77c84-213">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="77c84-214">Les lecteurs réseau mappés ne peuvent être associés qu’au `FileSystem` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="77c84-214">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="77c84-215">Pour afficher la liste des fournisseurs dans votre session PowerShell, utilisez l’applet de commande `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="77c84-215">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-216">-Racine</span><span class="sxs-lookup"><span data-stu-id="77c84-216">-Root</span></span>

<span data-ttu-id="77c84-217">Spécifie l’emplacement du magasin de données auquel un lecteur PowerShell est mappé.</span><span class="sxs-lookup"><span data-stu-id="77c84-217">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="77c84-218">Par exemple, spécifiez un partage réseau, tel que `\\Server01\Public` , un répertoire local, tel que `C:\Program Files` , ou une clé de Registre, telle que `HKLM:\Software\Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="77c84-218">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="77c84-219">Les lecteurs PowerShell temporaires peuvent être associés à un emplacement local ou distant sur n’importe quel lecteur de fournisseur pris en charge.</span><span class="sxs-lookup"><span data-stu-id="77c84-219">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="77c84-220">Les lecteurs réseau mappés ne peuvent être associés qu'à un emplacement du système de fichiers sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="77c84-220">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-221">-Étendue</span><span class="sxs-lookup"><span data-stu-id="77c84-221">-Scope</span></span>

<span data-ttu-id="77c84-222">Spécifie une portée pour le lecteur.</span><span class="sxs-lookup"><span data-stu-id="77c84-222">Specifies a scope for the drive.</span></span> <span data-ttu-id="77c84-223">Les valeurs acceptables pour ce paramètre sont : **Global** , **local** et **script** , ou un nombre relatif à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="77c84-223">The acceptable values for this parameter are: **Global** , **Local** , and **Script** , or a number relative to the current scope.</span></span> <span data-ttu-id="77c84-224">Les étendues numéro 0 à travers le nombre d’étendues.</span><span class="sxs-lookup"><span data-stu-id="77c84-224">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="77c84-225">Le numéro d’étendue actuel est 0 et son parent est 1.</span><span class="sxs-lookup"><span data-stu-id="77c84-225">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="77c84-226">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="77c84-226">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-227">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="77c84-227">-UseTransaction</span></span>

<span data-ttu-id="77c84-228">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="77c84-228">Includes the command in the active transaction.</span></span> <span data-ttu-id="77c84-229">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="77c84-229">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="77c84-230">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="77c84-230">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-231">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="77c84-231">-WhatIf</span></span>

<span data-ttu-id="77c84-232">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="77c84-232">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="77c84-233">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="77c84-233">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77c84-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77c84-234">CommonParameters</span></span>

<span data-ttu-id="77c84-235">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="77c84-235">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="77c84-236">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="77c84-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77c84-237">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="77c84-237">INPUTS</span></span>

### <span data-ttu-id="77c84-238">Aucun</span><span class="sxs-lookup"><span data-stu-id="77c84-238">None</span></span>

<span data-ttu-id="77c84-239">Vous ne pouvez pas effectuer de pipeline d’entrée pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="77c84-239">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="77c84-240">SORTIES</span><span class="sxs-lookup"><span data-stu-id="77c84-240">OUTPUTS</span></span>

### <span data-ttu-id="77c84-241">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="77c84-241">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="77c84-242">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="77c84-242">NOTES</span></span>

<span data-ttu-id="77c84-243">`New-PSDrive` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="77c84-243">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="77c84-244">Pour répertorier les fournisseurs disponibles dans votre session, utilisez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="77c84-244">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="77c84-245">Pour plus d’informations sur les fournisseurs, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="77c84-245">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="77c84-246">les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="77c84-246">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="77c84-247">Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="77c84-247">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="77c84-248">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="77c84-248">RELATED LINKS</span></span>

[<span data-ttu-id="77c84-249">about_Providers</span><span class="sxs-lookup"><span data-stu-id="77c84-249">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="77c84-250">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="77c84-250">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="77c84-251">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="77c84-251">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="77c84-252">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="77c84-252">Remove-PSDrive</span></span>](Remove-PSDrive.md)
