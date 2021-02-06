---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 54b65a636fe05ed82d4f022b5bb8cbf8acaf7bab
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99597950"
---
# <span data-ttu-id="b20d3-102">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b20d3-102">New-PSDrive</span></span>

## <span data-ttu-id="b20d3-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b20d3-103">SYNOPSIS</span></span>
<span data-ttu-id="b20d3-104">Crée des lecteurs réseau mappés temporaires et persistants.</span><span class="sxs-lookup"><span data-stu-id="b20d3-104">Creates temporary and persistent mapped network drives.</span></span>

## <span data-ttu-id="b20d3-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b20d3-105">SYNTAX</span></span>

### <span data-ttu-id="b20d3-106">Tous</span><span class="sxs-lookup"><span data-stu-id="b20d3-106">All</span></span>

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b20d3-107">Description</span><span class="sxs-lookup"><span data-stu-id="b20d3-107">DESCRIPTION</span></span>

<span data-ttu-id="b20d3-108">L' `New-PSDrive` applet de commande crée des lecteurs temporaires et persistants mappés à ou associés à un emplacement dans un magasin de données, tel qu’un lecteur réseau, un répertoire sur l’ordinateur local ou une clé de Registre, et des lecteurs réseau mappés Windows persistants associés à un emplacement de système de fichiers sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b20d3-108">The `New-PSDrive` cmdlet creates temporary and persistent drives that are mapped to or associated with a location in a data store, such as a network drive, a directory on the local computer, or a registry key, and persistent Windows mapped network drives that are associated with a file system location on a remote computer.</span></span>

<span data-ttu-id="b20d3-109">Les lecteurs temporaires existent uniquement dans la session PowerShell active et dans les sessions que vous créez dans la session active.</span><span class="sxs-lookup"><span data-stu-id="b20d3-109">Temporary drives exist only in the current PowerShell session and in sessions that you create in the current session.</span></span> <span data-ttu-id="b20d3-110">Ils peuvent avoir n’importe quel nom valide dans PowerShell et peuvent être mappés à n’importe quelle ressource locale ou distante.</span><span class="sxs-lookup"><span data-stu-id="b20d3-110">They can have any name that is valid in PowerShell and can be mapped to any local or remote resource.</span></span> <span data-ttu-id="b20d3-111">Vous pouvez utiliser des lecteurs PowerShell temporaires pour accéder aux données dans le magasin de données associé, comme vous le feriez avec n’importe quel lecteur réseau mappé.</span><span class="sxs-lookup"><span data-stu-id="b20d3-111">You can use temporary PowerShell drives to access data in the associated data store, just as you would do with any mapped network drive.</span></span> <span data-ttu-id="b20d3-112">Vous pouvez modifier les emplacements dans le lecteur, à l’aide de `Set-Location` , et accéder au contenu du lecteur à l’aide de `Get-Item` ou de `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-112">You can change locations into the drive, by using `Set-Location`, and access the contents of the drive by using `Get-Item` or `Get-ChildItem`.</span></span>

<span data-ttu-id="b20d3-113">Étant donné que les lecteurs temporaires sont connus uniquement de PowerShell, vous ne pouvez pas y accéder à l’aide de l’Explorateur de fichiers, Windows Management Instrumentation (WMI), COM (Component Object Model), Microsoft .NET Framework ou avec des outils tels que **net use**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-113">Because temporary drives are known only to PowerShell, you can't access them by using File Explorer, Windows Management Instrumentation (WMI), Component Object Model (COM), Microsoft .NET Framework, or with tools such as **net use**.</span></span>

<span data-ttu-id="b20d3-114">Les fonctionnalités suivantes ont été ajoutées à `New-PSDrive` dans PowerShell 3,0 :</span><span class="sxs-lookup"><span data-stu-id="b20d3-114">The following features were added to `New-PSDrive` in PowerShell 3.0:</span></span>

- <span data-ttu-id="b20d3-115">Lecteurs réseau mappés.</span><span class="sxs-lookup"><span data-stu-id="b20d3-115">Mapped network drives.</span></span> <span data-ttu-id="b20d3-116">Vous pouvez utiliser le paramètre **Persist** de `New-PSDrive` pour créer des lecteurs réseau mappés Windows.</span><span class="sxs-lookup"><span data-stu-id="b20d3-116">You can use the **Persist** parameter of `New-PSDrive` to create Windows mapped network drives.</span></span> <span data-ttu-id="b20d3-117">Contrairement aux lecteurs PowerShell temporaires, les lecteurs réseau mappés Windows ne sont pas spécifiques à la session.</span><span class="sxs-lookup"><span data-stu-id="b20d3-117">Unlike temporary PowerShell drives, Windows mapped network drives aren't session-specific.</span></span> <span data-ttu-id="b20d3-118">Ils sont enregistrés dans Windows et peuvent être gérés à l’aide d’outils Windows standard, tels que l’Explorateur de fichiers et **net use**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-118">They're saved in Windows and they can be managed by using standard Windows tools, such as File Explorer and **net use**.</span></span> <span data-ttu-id="b20d3-119">Les lecteurs réseau mappés doivent avoir un nom de lettre de lecteur et être connectés à un emplacement du système de fichiers distant.</span><span class="sxs-lookup"><span data-stu-id="b20d3-119">Mapped network drives must have a drive-letter name and be connected to a remote file system location.</span></span> <span data-ttu-id="b20d3-120">Lorsque votre commande est limitée localement, sans point, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de l’étendue dans laquelle la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b20d3-120">When your command is scoped locally, no dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which the command is running.</span></span> <span data-ttu-id="b20d3-121">Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le lecteur persiste indéfiniment, vous devez effectuer un point-source du script.</span><span class="sxs-lookup"><span data-stu-id="b20d3-121">If you're running `New-PSDrive` inside a script, and you want the drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="b20d3-122">Pour de meilleurs résultats, pour forcer un nouveau lecteur à rester indéfiniment, ajoutez le paramètre **scope** à votre commande et définissez sa valeur sur **Global**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-122">For best results, to force a new drive to persist indefinitely, add the **Scope** parameter to your command, and set its value to **Global**.</span></span> <span data-ttu-id="b20d3-123">Pour plus d’informations sur la source de points, consultez [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="b20d3-123">For more information about dot-sourcing, see [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing).</span></span>
- <span data-ttu-id="b20d3-124">Lecteurs externes.</span><span class="sxs-lookup"><span data-stu-id="b20d3-124">External drives.</span></span> <span data-ttu-id="b20d3-125">Lorsqu’un lecteur externe est connecté à l’ordinateur, PowerShell ajoute automatiquement un **PSDrive** au système de fichiers qui représente le nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-125">When an external drive is connected to the computer, PowerShell automatically adds a **PSDrive** to the file system that represents the new drive.</span></span> <span data-ttu-id="b20d3-126">Vous n’avez pas besoin de redémarrer PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b20d3-126">You don't have to restart PowerShell.</span></span> <span data-ttu-id="b20d3-127">De même, lorsqu’un lecteur externe est déconnecté de l’ordinateur, PowerShell supprime automatiquement le **PSDrive** qui représente le lecteur supprimé.</span><span class="sxs-lookup"><span data-stu-id="b20d3-127">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the **PSDrive** that represents the removed drive.</span></span>
- <span data-ttu-id="b20d3-128">Informations d’identification pour les chemins d’accès UNC (Universal Naming Convention).</span><span class="sxs-lookup"><span data-stu-id="b20d3-128">Credentials for Universal Naming Convention (UNC) paths.</span></span>

<span data-ttu-id="b20d3-129">Lorsque la valeur du paramètre **root** est un chemin d’accès UNC, tel que `\\Server\Share` , les informations d’identification spécifiées dans la valeur du paramètre **Credential** sont utilisées pour créer le **PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-129">When the value of the **Root** parameter is a UNC path, such as `\\Server\Share`, the credential specified in the value of the **Credential** parameter is used to create the **PSDrive**.</span></span> <span data-ttu-id="b20d3-130">Dans le cas contraire, les **informations d’identification** ne sont pas effectives lorsque vous créez de nouveaux lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b20d3-130">Otherwise, **Credential** isn't effective when you're creating new file system drives.</span></span>

<span data-ttu-id="b20d3-131">Certains exemples de code utilisent la projection pour réduire la longueur de ligne et améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="b20d3-131">Some code samples use splatting to reduce the line length and improve readability.</span></span> <span data-ttu-id="b20d3-132">Pour plus d’informations, consultez [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="b20d3-132">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="b20d3-133">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b20d3-133">EXAMPLES</span></span>

### <span data-ttu-id="b20d3-134">Exemple 1 : créer un lecteur temporaire mappé à un partage réseau</span><span class="sxs-lookup"><span data-stu-id="b20d3-134">Example 1: Create a temporary drive mapped to a network share</span></span>

<span data-ttu-id="b20d3-135">Cet exemple crée un lecteur PowerShell temporaire qui est mappé à un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b20d3-135">This example creates a temporary PowerShell drive that's mapped to a network share.</span></span>

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

<span data-ttu-id="b20d3-136">`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `Public` et le paramètre **PSProvider** pour spécifier le `FileSystem` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b20d3-136">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `Public` and the **PSProvider** parameter to specify the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="b20d3-137">Le paramètre **root** spécifie le chemin d’accès UNC du partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b20d3-137">The **Root** parameter specifies the network share's UNC path.</span></span>

<span data-ttu-id="b20d3-138">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path Public:`</span><span class="sxs-lookup"><span data-stu-id="b20d3-138">To view the contents from a PowerShell session: `Get-ChildItem -Path Public:`</span></span>

### <span data-ttu-id="b20d3-139">Exemple 2 : créer un lecteur temporaire mappé à un répertoire local</span><span class="sxs-lookup"><span data-stu-id="b20d3-139">Example 2: Create a temporary drive mapped to a local directory</span></span>

<span data-ttu-id="b20d3-140">Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à un répertoire sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b20d3-140">This example creates a temporary PowerShell drive that provides access to a directory on the local computer.</span></span>

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

<span data-ttu-id="b20d3-141">La projection crée les clés et valeurs de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b20d3-141">Splatting creates the parameter keys and values.</span></span> <span data-ttu-id="b20d3-142">Le paramètre **Name** spécifie le nom du lecteur, **mydocs**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-142">The **Name** parameter specifies the drive name, **MyDocs**.</span></span> <span data-ttu-id="b20d3-143">Le paramètre **PSProvider** spécifie le `FileSystem` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b20d3-143">The **PSProvider** parameter specifies the PowerShell `FileSystem` provider.</span></span> <span data-ttu-id="b20d3-144">**Root** spécifie le répertoire de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b20d3-144">**Root** specifies the local computer's directory.</span></span> <span data-ttu-id="b20d3-145">Le paramètre **Description** décrit l’objectif du lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-145">The **Description** parameter describes the drive's purpose.</span></span> <span data-ttu-id="b20d3-146">`New-PSDrive` utilise les paramètres de projection pour créer le `MyDocs` lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-146">`New-PSDrive` uses the splatted parameters to create the `MyDocs` drive.</span></span>

<span data-ttu-id="b20d3-147">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyDocs:`</span><span class="sxs-lookup"><span data-stu-id="b20d3-147">To view the contents from a PowerShell session: `Get-ChildItem -Path MyDocs:`</span></span>

### <span data-ttu-id="b20d3-148">Exemple 3 : créer un lecteur temporaire pour une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="b20d3-148">Example 3: Create a temporary drive for a registry key</span></span>

<span data-ttu-id="b20d3-149">Cet exemple crée un lecteur PowerShell temporaire qui fournit l’accès à une clé de registre.</span><span class="sxs-lookup"><span data-stu-id="b20d3-149">This example creates a temporary PowerShell drive that provides access to a registry key.</span></span> <span data-ttu-id="b20d3-150">Il crée un lecteur nommé MyCompany qui est mappé à la `HKLM:\Software\MyCompany` clé de registre.</span><span class="sxs-lookup"><span data-stu-id="b20d3-150">It creates a drive named MyCompany that is mapped to the `HKLM:\Software\MyCompany` registry key.</span></span>

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

<span data-ttu-id="b20d3-151">`New-PSDrive` utilise le paramètre **Name** pour spécifier le lecteur PowerShell nommé `MyCompany` et le paramètre **PSProvider** pour spécifier le `Registry` fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b20d3-151">`New-PSDrive` uses the **Name** parameter to specify PowerShell drive named `MyCompany` and the **PSProvider** parameter to specify the PowerShell `Registry` provider.</span></span> <span data-ttu-id="b20d3-152">Le paramètre **root** spécifie l’emplacement du Registre.</span><span class="sxs-lookup"><span data-stu-id="b20d3-152">The **Root** parameter specifies the registry location.</span></span>

<span data-ttu-id="b20d3-153">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path MyCompany:`</span><span class="sxs-lookup"><span data-stu-id="b20d3-153">To view the contents from a PowerShell session: `Get-ChildItem -Path MyCompany:`</span></span>

### <span data-ttu-id="b20d3-154">Exemple 4 : créer un lecteur réseau mappé persistant à l’aide des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="b20d3-154">Example 4: Create a persistent mapped network drive using credentials</span></span>

<span data-ttu-id="b20d3-155">Cet exemple mappe un lecteur réseau authentifié avec les informations d’identification d’un compte de service de domaine.</span><span class="sxs-lookup"><span data-stu-id="b20d3-155">This example maps a network drive that's authenticated with a domain service account's credentials.</span></span>
<span data-ttu-id="b20d3-156">Pour plus d’informations sur l’objet **PSCredential** qui stocke les informations d’identification et sur la manière dont les mots de passe sont stockés sous forme de **SecureString**, consultez la description du paramètre **Credential** .</span><span class="sxs-lookup"><span data-stu-id="b20d3-156">For more information about the **PSCredential** object that stores credentials and how passwords are stored as a **SecureString**, see the **Credential** parameter's description.</span></span>

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
> <span data-ttu-id="b20d3-157">N’oubliez pas que si vous utilisez l’extrait de code ci-dessus dans un script, définissez la valeur du paramètre d' **étendue** sur « global » pour vous assurer que le lecteur persiste en dehors de l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b20d3-157">Remember, if you use the above snippet in a script, set the **Scope** parameter value to "Global" to ensure the drive persists outside the current scope.</span></span>

<span data-ttu-id="b20d3-158">La `$cred` variable stocke un objet **PSCredential** qui contient les informations d’identification du compte de service.</span><span class="sxs-lookup"><span data-stu-id="b20d3-158">The `$cred` variable stores a **PSCredential** object that contains the service account's credentials.</span></span> <span data-ttu-id="b20d3-159">`Get-Credential` vous invite à entrer le mot de passe qui est stocké dans une **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-159">`Get-Credential` prompts you to enter the password that's stored in a **SecureString**.</span></span>

<span data-ttu-id="b20d3-160">`New-PSDrive` crée le lecteur réseau mappé à l’aide de plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="b20d3-160">`New-PSDrive` creates the mapped network drive by using several parameters.</span></span> <span data-ttu-id="b20d3-161">**Nom** spécifie la `S` lettre de lecteur que Windows accepte.</span><span class="sxs-lookup"><span data-stu-id="b20d3-161">**Name** specifies the `S` drive letter that Windows accepts.</span></span> <span data-ttu-id="b20d3-162">et la **racine** définit `\\Server01\Scripts` comme emplacement sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b20d3-162">and **Root** defines `\\Server01\Scripts` as the location on a remote computer.</span></span> <span data-ttu-id="b20d3-163">**Persist** crée un lecteur réseau mappé Windows qui est enregistré sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b20d3-163">**Persist** creates a Windows mapped network drive that's saved on the local computer.</span></span> <span data-ttu-id="b20d3-164">**PSProvider** spécifie le `FileSystem` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-164">**PSProvider** specifies the `FileSystem` provider.</span></span> <span data-ttu-id="b20d3-165">**Credential** utilise la `$cred` variable pour obtenir les informations d’identification du compte de service pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="b20d3-165">**Credential** uses the `$cred` variable to get the service account credentials for authentication.</span></span>

<span data-ttu-id="b20d3-166">Le lecteur mappé peut être affiché sur l’ordinateur local dans les sessions PowerShell, l’Explorateur de fichiers et avec des outils tels que **net use**.</span><span class="sxs-lookup"><span data-stu-id="b20d3-166">The mapped drive can be viewed on the local computer in PowerShell sessions, File Explorer, and with tools such as **net use**.</span></span> <span data-ttu-id="b20d3-167">Pour afficher le contenu d’une session PowerShell : `Get-ChildItem -Path S:`</span><span class="sxs-lookup"><span data-stu-id="b20d3-167">To view the contents from a PowerShell session: `Get-ChildItem -Path S:`</span></span>

### <span data-ttu-id="b20d3-168">Exemple 5 : créer des lecteurs permanents et temporaires</span><span class="sxs-lookup"><span data-stu-id="b20d3-168">Example 5: Create persistent and temporary drives</span></span>

<span data-ttu-id="b20d3-169">Cet exemple montre la différence entre un lecteur réseau mappé persistant et un lecteur PowerShell temporaire qui est mappé au même partage réseau.</span><span class="sxs-lookup"><span data-stu-id="b20d3-169">This example shows the difference between a persistent mapped network drive and a temporary PowerShell drive that is mapped to the same network share.</span></span>

<span data-ttu-id="b20d3-170">Si vous fermez la session PowerShell et que vous ouvrez une nouvelle session, le temporaire `PSDrive:` n’est pas disponible, mais le `X:` lecteur persistant est disponible.</span><span class="sxs-lookup"><span data-stu-id="b20d3-170">If you close the PowerShell session and then open a new session, the temporary `PSDrive:` isn't available, but the persistent `X:` drive is available.</span></span> <span data-ttu-id="b20d3-171">Lorsque vous décidez de la méthode à utiliser pour mapper les lecteurs réseau, réfléchissez à la façon dont vous allez utiliser le lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-171">When deciding which method to use to map network drives, consider how you'll use the drive.</span></span> <span data-ttu-id="b20d3-172">Par exemple, s’il doit être persistant et si le lecteur doit être visible par d’autres fonctionnalités de Windows.</span><span class="sxs-lookup"><span data-stu-id="b20d3-172">For example, whether it has to be persistent, and whether the drive has to be visible to other Windows features.</span></span>

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

## <span data-ttu-id="b20d3-173">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b20d3-173">PARAMETERS</span></span>

### <span data-ttu-id="b20d3-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b20d3-174">-Confirm</span></span>

<span data-ttu-id="b20d3-175">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b20d3-175">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b20d3-176">-Credential</span><span class="sxs-lookup"><span data-stu-id="b20d3-176">-Credential</span></span>

<span data-ttu-id="b20d3-177">Spécifie un compte d’utilisateur qui a l’autorisation d’effectuer cette action.</span><span class="sxs-lookup"><span data-stu-id="b20d3-177">Specifies a user account that has permission to do this action.</span></span> <span data-ttu-id="b20d3-178">La valeur par défaut est l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="b20d3-178">The default is the current user.</span></span>

<span data-ttu-id="b20d3-179">Depuis PowerShell 3,0, lorsque la valeur du paramètre **root** est un chemin UNC, vous pouvez utiliser les informations d’identification pour créer des lecteurs de système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="b20d3-179">Since PowerShell 3.0, when the value of the **Root** parameter is a UNC path, you can use credentials to create file system drives.</span></span>

<span data-ttu-id="b20d3-180">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-180">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b20d3-181">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b20d3-181">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b20d3-182">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="b20d3-182">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b20d3-183">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="b20d3-183">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="b20d3-184">Description</span><span class="sxs-lookup"><span data-stu-id="b20d3-184">-Description</span></span>

<span data-ttu-id="b20d3-185">Spécifie une courte description du lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-185">Specifies a brief text description of the drive.</span></span> <span data-ttu-id="b20d3-186">Tapez une chaîne.</span><span class="sxs-lookup"><span data-stu-id="b20d3-186">Type any string.</span></span>

<span data-ttu-id="b20d3-187">Pour afficher les descriptions de tous les lecteurs de la session, `Get-PSDrive | Format-Table Name, Description` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-187">To see the descriptions of all the session's drives, `Get-PSDrive | Format-Table Name, Description`.</span></span>

<span data-ttu-id="b20d3-188">Pour afficher la description d’un lecteur particulier, tapez `(Get-PSDrive <DriveName>).Description` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-188">To see the description of a particular drive, type `(Get-PSDrive <DriveName>).Description`.</span></span>

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

### <span data-ttu-id="b20d3-189">-Name</span><span class="sxs-lookup"><span data-stu-id="b20d3-189">-Name</span></span>

<span data-ttu-id="b20d3-190">Spécifie le nom du nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-190">Specifies a name for the new drive.</span></span> <span data-ttu-id="b20d3-191">Pour les lecteurs réseau mappés persistants, utilisez une lettre de lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-191">For persistent mapped network drives, use a drive letter.</span></span> <span data-ttu-id="b20d3-192">Pour les lecteurs PowerShell temporaires, vous n’êtes pas limité aux lettres de lecteur, utilisez une chaîne valide.</span><span class="sxs-lookup"><span data-stu-id="b20d3-192">For temporary PowerShell drives, you aren't limited to drive letters, use any valid string.</span></span>

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

### <span data-ttu-id="b20d3-193">-Persist</span><span class="sxs-lookup"><span data-stu-id="b20d3-193">-Persist</span></span>

<span data-ttu-id="b20d3-194">Indique que cette applet de commande crée un lecteur réseau mappé Windows.</span><span class="sxs-lookup"><span data-stu-id="b20d3-194">Indicates that this cmdlet creates a Windows mapped network drive.</span></span> <span data-ttu-id="b20d3-195">Le paramètre **Persist** est uniquement disponible sur Windows.</span><span class="sxs-lookup"><span data-stu-id="b20d3-195">The **Persist** parameter is only available on Windows.</span></span>

<span data-ttu-id="b20d3-196">Les lecteurs réseau mappés sont enregistrés dans Windows sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="b20d3-196">Mapped network drives are saved in Windows on the local computer.</span></span> <span data-ttu-id="b20d3-197">Ils sont persistants, non spécifiques à la session et peuvent être affichés et gérés dans l’Explorateur de fichiers et d’autres outils.</span><span class="sxs-lookup"><span data-stu-id="b20d3-197">They're persistent, not session-specific, and can be viewed and managed in File Explorer and other tools.</span></span>

<span data-ttu-id="b20d3-198">Lorsque vous étendez la commande en local, sans la source de points, le paramètre **persiste** ne conserve pas la création d’un **PSDrive** au-delà de la portée dans laquelle vous exécutez la commande.</span><span class="sxs-lookup"><span data-stu-id="b20d3-198">When you scope the command locally, without dot-sourcing, the **Persist** parameter doesn't persist the creation of a **PSDrive** beyond the scope in which you run the command.</span></span> <span data-ttu-id="b20d3-199">Si vous exécutez `New-PSDrive` à l’intérieur d’un script et que vous souhaitez que le nouveau lecteur persiste indéfiniment, vous devez effectuer un point-source du script.</span><span class="sxs-lookup"><span data-stu-id="b20d3-199">If you run `New-PSDrive` inside a script, and you want the new drive to persist indefinitely, you must dot-source the script.</span></span> <span data-ttu-id="b20d3-200">Pour de meilleurs résultats, pour forcer la conservation d’un nouveau lecteur, spécifiez **Global** comme valeur du paramètre d' **étendue** et include **persiste** dans votre commande.</span><span class="sxs-lookup"><span data-stu-id="b20d3-200">For best results, to force a new drive to persist, specify **Global** as the value of the **Scope** parameter and include **Persist** in your command.</span></span>

<span data-ttu-id="b20d3-201">Le nom du lecteur doit être une lettre, telle que `D` ou `E` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-201">The name of the drive must be a letter, such as `D` or `E`.</span></span> <span data-ttu-id="b20d3-202">La valeur du paramètre **root** doit être un chemin d’accès UNC d’un autre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-202">The value of **Root** parameter must be a UNC path of a different computer.</span></span> <span data-ttu-id="b20d3-203">La valeur du paramètre **PSProvider** doit être `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-203">The **PSProvider** parameter's value must be `FileSystem`.</span></span>

<span data-ttu-id="b20d3-204">Pour déconnecter un lecteur réseau mappé Windows, utilisez l'applet de commande `Remove-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="b20d3-204">To disconnect a Windows mapped network drive, use the `Remove-PSDrive` cmdlet.</span></span> <span data-ttu-id="b20d3-205">Lorsque vous déconnectez un lecteur réseau Windows mappé, le mappage est définitivement supprimé de l'ordinateur (et pas simplement de la session active).</span><span class="sxs-lookup"><span data-stu-id="b20d3-205">When you disconnect a Windows mapped network drive, the mapping is permanently deleted from the computer, not just deleted from the current session.</span></span>

<span data-ttu-id="b20d3-206">les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-206">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="b20d3-207">Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b20d3-207">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

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

### <span data-ttu-id="b20d3-208">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="b20d3-208">-PSProvider</span></span>

<span data-ttu-id="b20d3-209">Spécifie le fournisseur PowerShell qui prend en charge les lecteurs de ce type.</span><span class="sxs-lookup"><span data-stu-id="b20d3-209">Specifies the PowerShell provider that supports drives of this kind.</span></span>

<span data-ttu-id="b20d3-210">Par exemple, si le lecteur est associé à un répertoire de partage réseau ou de système de fichiers, le fournisseur PowerShell est `FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-210">For example, if the drive is associated with a network share or file system directory, the PowerShell provider is `FileSystem`.</span></span> <span data-ttu-id="b20d3-211">Si le lecteur est associé à une clé de Registre, le fournisseur est `Registry` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-211">If the drive is associated with a registry key, the provider is `Registry`.</span></span>

<span data-ttu-id="b20d3-212">Les lecteurs PowerShell temporaires peuvent être associés à n’importe quel fournisseur PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b20d3-212">Temporary PowerShell drives can be associated with any PowerShell provider.</span></span> <span data-ttu-id="b20d3-213">Les lecteurs réseau mappés ne peuvent être associés qu’au `FileSystem` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-213">Mapped network drives can be associated only with the `FileSystem` provider.</span></span>

<span data-ttu-id="b20d3-214">Pour afficher la liste des fournisseurs dans votre session PowerShell, utilisez l’applet de commande `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-214">To see a list of the providers in your PowerShell session, use the `Get-PSProvider` cmdlet.</span></span>

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

### <span data-ttu-id="b20d3-215">-Racine</span><span class="sxs-lookup"><span data-stu-id="b20d3-215">-Root</span></span>

<span data-ttu-id="b20d3-216">Spécifie l’emplacement du magasin de données auquel un lecteur PowerShell est mappé.</span><span class="sxs-lookup"><span data-stu-id="b20d3-216">Specifies the data store location to which a PowerShell drive is mapped.</span></span>

<span data-ttu-id="b20d3-217">Par exemple, spécifiez un partage réseau, tel que `\\Server01\Public` , un répertoire local, tel que `C:\Program Files` , ou une clé de Registre, telle que `HKLM:\Software\Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-217">For example, specify a network share, such as `\\Server01\Public`, a local directory, such as `C:\Program Files`, or a registry key, such as `HKLM:\Software\Microsoft`.</span></span>

<span data-ttu-id="b20d3-218">Les lecteurs PowerShell temporaires peuvent être associés à un emplacement local ou distant sur n’importe quel lecteur de fournisseur pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b20d3-218">Temporary PowerShell drives can be associated with a local or remote location on any supported provider drive.</span></span> <span data-ttu-id="b20d3-219">Les lecteurs réseau mappés ne peuvent être associés qu'à un emplacement du système de fichiers sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="b20d3-219">Mapped network drives can be associated only with a file system location on a remote computer.</span></span>

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

### <span data-ttu-id="b20d3-220">-Étendue</span><span class="sxs-lookup"><span data-stu-id="b20d3-220">-Scope</span></span>

<span data-ttu-id="b20d3-221">Spécifie une portée pour le lecteur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-221">Specifies a scope for the drive.</span></span> <span data-ttu-id="b20d3-222">Les valeurs acceptables pour ce paramètre sont : **Global**, **local** et **script**, ou un nombre relatif à l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b20d3-222">The acceptable values for this parameter are: **Global**, **Local**, and **Script**, or a number relative to the current scope.</span></span> <span data-ttu-id="b20d3-223">Les étendues numéro 0 à travers le nombre d’étendues.</span><span class="sxs-lookup"><span data-stu-id="b20d3-223">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="b20d3-224">Le numéro d’étendue actuel est 0 et son parent est 1.</span><span class="sxs-lookup"><span data-stu-id="b20d3-224">The current scope number is 0 and its parent is 1.</span></span> <span data-ttu-id="b20d3-225">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="b20d3-225">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="b20d3-226">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b20d3-226">-WhatIf</span></span>

<span data-ttu-id="b20d3-227">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b20d3-227">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b20d3-228">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="b20d3-228">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b20d3-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b20d3-229">CommonParameters</span></span>

<span data-ttu-id="b20d3-230">Cette applet de commande prend en charge les paramètres communs : `-Debug` , `-ErrorAction` ,, `-ErrorVariable` `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` et `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-230">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b20d3-231">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b20d3-231">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b20d3-232">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b20d3-232">INPUTS</span></span>

### <span data-ttu-id="b20d3-233">None</span><span class="sxs-lookup"><span data-stu-id="b20d3-233">None</span></span>

<span data-ttu-id="b20d3-234">Vous ne pouvez pas effectuer de pipeline d’entrée pour cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="b20d3-234">You can't pipeline input to this cmdlet.</span></span>

## <span data-ttu-id="b20d3-235">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b20d3-235">OUTPUTS</span></span>

### <span data-ttu-id="b20d3-236">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="b20d3-236">System.Management.Automation.PSDriveInfo</span></span>

## <span data-ttu-id="b20d3-237">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b20d3-237">NOTES</span></span>

<span data-ttu-id="b20d3-238">`New-PSDrive` est conçu pour fonctionner avec les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-238">`New-PSDrive` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="b20d3-239">Pour répertorier les fournisseurs disponibles dans votre session, utilisez `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="b20d3-239">To list the providers available in your session, use `Get-PSProvider`.</span></span> <span data-ttu-id="b20d3-240">Pour plus d’informations sur les fournisseurs, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b20d3-240">For more information about providers, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="b20d3-241">les lecteurs réseau mappés sont spécifiques à un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b20d3-241">Mapped network drives are specific to a user account.</span></span> <span data-ttu-id="b20d3-242">Les lecteurs mappés créés dans les sessions ou sessions élevées à l’aide des informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées à l’aide d’autres informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b20d3-242">Mapped drives created in elevated sessions or sessions using the credential of another user aren't visible in sessions started using different credentials.</span></span>

## <span data-ttu-id="b20d3-243">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b20d3-243">RELATED LINKS</span></span>

[<span data-ttu-id="b20d3-244">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b20d3-244">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="b20d3-245">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="b20d3-245">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="b20d3-246">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b20d3-246">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="b20d3-247">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="b20d3-247">Remove-PSDrive</span></span>](Remove-PSDrive.md)

