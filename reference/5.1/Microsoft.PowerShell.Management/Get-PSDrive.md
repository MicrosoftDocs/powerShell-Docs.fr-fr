---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: 7a37857d9a4fb9eb18869ef78dc0ac19dc26367f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203993"
---
# <span data-ttu-id="998a5-103">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="998a5-103">Get-PSDrive</span></span>

## <span data-ttu-id="998a5-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="998a5-104">SYNOPSIS</span></span>
<span data-ttu-id="998a5-105">Obtient les lecteurs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="998a5-105">Gets drives in the current session.</span></span>

## <span data-ttu-id="998a5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="998a5-106">SYNTAX</span></span>

### <span data-ttu-id="998a5-107">Nom (par défaut)</span><span class="sxs-lookup"><span data-stu-id="998a5-107">Name (Default)</span></span>

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="998a5-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="998a5-108">LiteralName</span></span>

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="998a5-109">Description</span><span class="sxs-lookup"><span data-stu-id="998a5-109">DESCRIPTION</span></span>

<span data-ttu-id="998a5-110">L' `Get-PSDrive` applet de commande obtient les lecteurs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="998a5-110">The `Get-PSDrive` cmdlet gets the drives in the current session.</span></span> <span data-ttu-id="998a5-111">Vous pouvez obtenir un lecteur particulier ou tous les lecteurs présents dans la session.</span><span class="sxs-lookup"><span data-stu-id="998a5-111">You can get a particular drive or all drives in the session.</span></span>

<span data-ttu-id="998a5-112">Cette applet de commande obtient les types de lecteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="998a5-112">This cmdlet gets the following types of drives:</span></span>

- <span data-ttu-id="998a5-113">Lecteurs logiques Windows sur l’ordinateur, y compris les lecteurs mappés à des partages réseau.</span><span class="sxs-lookup"><span data-stu-id="998a5-113">Windows logical drives on the computer, including drives mapped to network shares.</span></span>
- <span data-ttu-id="998a5-114">Lecteurs exposés par les fournisseurs PowerShell (tels que le certificat :, Function : et alias : Drives) et les lecteurs HKLM : et HKCU : qui sont exposés par le fournisseur de Registre Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-114">Drives exposed by PowerShell providers (such as the Certificate:, Function:, and Alias: drives) and the HKLM: and HKCU: drives that are exposed by the Windows PowerShell Registry provider.</span></span>
- <span data-ttu-id="998a5-115">Lecteurs temporaires spécifiés par session et lecteurs réseau mappés persistants que vous créez à l’aide de l’applet de commande New-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="998a5-115">Session-specified temporary drives and persistent mapped network drives that you create by using the New-PSDrive cmdlet.</span></span>

<span data-ttu-id="998a5-116">À compter de Windows PowerShell 3,0, le paramètre **Persist** de l’applet de commande `New-PSDrive` peut créer des lecteurs réseau mappés qui sont enregistrés sur l’ordinateur local et qui sont disponibles dans d’autres sessions.</span><span class="sxs-lookup"><span data-stu-id="998a5-116">Beginning in Windows PowerShell 3.0, the **Persist** parameter of the `New-PSDrive` cmdlet can create mapped network drives that are saved on the local computer and are available in other sessions.</span></span> <span data-ttu-id="998a5-117">Pour plus d’informations, consultez New-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="998a5-117">For more information, see New-PSDrive.</span></span>

<span data-ttu-id="998a5-118">De plus, depuis Windows PowerShell 3.0, lorsqu’un lecteur externe est connecté à l’ordinateur, Windows PowerShell ajoute automatiquement un lecteur PSDrive au système de fichiers qui représente le nouveau lecteur.</span><span class="sxs-lookup"><span data-stu-id="998a5-118">Also, beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, Windows PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="998a5-119">Il n'est pas nécessaire de redémarrer Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-119">You do not need to restart Windows PowerShell.</span></span> <span data-ttu-id="998a5-120">De même, lorsqu'un lecteur externe est déconnecté de l'ordinateur, Windows PowerShell supprime automatiquement le PSDrive qui représente le lecteur supprimé.</span><span class="sxs-lookup"><span data-stu-id="998a5-120">Similarly, when an external drive is disconnected from the computer, Windows PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="998a5-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="998a5-121">EXAMPLES</span></span>

### <span data-ttu-id="998a5-122">Exemple 1 : récupérer des lecteurs dans la session active</span><span class="sxs-lookup"><span data-stu-id="998a5-122">Example 1: Get drives in the current session</span></span>

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

<span data-ttu-id="998a5-123">Cette commande obtient les lecteurs dans la session active.</span><span class="sxs-lookup"><span data-stu-id="998a5-123">This command gets the drives in the current session.</span></span>

<span data-ttu-id="998a5-124">La sortie indique le disque dur (C :), le lecteur de CD-ROM (D :) et les lecteurs exposés par les fournisseurs Windows PowerShell (alias :, CERT :, env :, Function :, HKCU :, HKLM : et variable :).</span><span class="sxs-lookup"><span data-stu-id="998a5-124">The output shows the hard drive (C:), CD-ROM drive (D:), and the drives exposed by the Windows PowerShell providers (Alias:, Cert:, Env:, Function:, HKCU:, HKLM:, and Variable:).</span></span>

### <span data-ttu-id="998a5-125">Exemple 2 : obtenir un lecteur sur l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="998a5-125">Example 2: Get a drive on the computer</span></span>

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

<span data-ttu-id="998a5-126">Cette commande obtient le lecteur D: sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="998a5-126">This command gets the D: drive on the computer.</span></span> <span data-ttu-id="998a5-127">Notez que la lettre de lecteur dans la commande n’est pas suivie d’un signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="998a5-127">Note that the drive letter in the command is not followed by a colon.</span></span>

### <span data-ttu-id="998a5-128">Exemple 3 : récupération de tous les lecteurs pris en charge par le fournisseur de système de fichiers Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="998a5-128">Example 3: Get all the drives that are supported by the Windows PowerShell file system provider</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

<span data-ttu-id="998a5-129">Cette commande obtient tous les lecteurs qui sont pris en charge par le fournisseur de système de fichiers de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-129">This command gets all of the drives that are supported by the Windows PowerShell FileSystem provider.</span></span> <span data-ttu-id="998a5-130">Cela comprend les lecteurs fixes, les partitions logiques, les lecteurs réseau mappés et les lecteurs temporaires que vous créez à l’aide de l’applet de commande New-PSDrive.</span><span class="sxs-lookup"><span data-stu-id="998a5-130">This includes fixed drives, logical partitions, mapped network drives, and temporary drives that you create by using the New-PSDrive cmdlet.</span></span>

### <span data-ttu-id="998a5-131">Exemple 4 : vérifier si un lecteur est en cours d’utilisation en tant que nom de lecteur Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="998a5-131">Example 4: Check to see if a drive is in use as a Windows PowerShell drive name</span></span>

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

<span data-ttu-id="998a5-132">Cette commande vérifie si le lecteur X est déjà utilisé en tant que nom de lecteur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-132">This command checks to see whether the X drive is already in use as a Windows PowerShell drive name.</span></span>
<span data-ttu-id="998a5-133">Si ce n’est pas le cas, la commande utilise l' `New-PSDrive` applet de commande pour créer un lecteur temporaire mappé à la clé de Registre HKLM : \ Software.</span><span class="sxs-lookup"><span data-stu-id="998a5-133">If it is not, the command uses the `New-PSDrive` cmdlet to create a temporary drive that is mapped to the HKLM:\SOFTWARE registry key.</span></span>

### <span data-ttu-id="998a5-134">Exemple 5 : comparer les types de lecteurs système de fichiers</span><span class="sxs-lookup"><span data-stu-id="998a5-134">Example 5: Compare the types of files system drives</span></span>

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

<span data-ttu-id="998a5-135">Cet exemple compare les types de lecteurs de système de fichiers affichés par `Get-PSDrive` à ceux affichés à l’aide d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="998a5-135">This example compares the types of file system drives that are displayed by `Get-PSDrive` to those displayed by using other methods.</span></span> <span data-ttu-id="998a5-136">Cet exemple illustre différentes façons d’afficher des lecteurs dans Windows PowerShell et il montre que les lecteurs spécifiques à la session créés à l’aide de l’applet de commande New-PSDrive sont accessibles uniquement dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-136">This example demonstrates different ways to display drives in Windows PowerShell, and it shows that session-specific drives created by using the New-PSDrive cmdlet are accessible only in Windows PowerShell.</span></span>

<span data-ttu-id="998a5-137">La première commande utilise `Get-PSDrive` pour récupérer tous les lecteurs du système de fichiers dans la session.</span><span class="sxs-lookup"><span data-stu-id="998a5-137">The first command uses `Get-PSDrive` to get all of the file system drives in the session.</span></span> <span data-ttu-id="998a5-138">Cela comprend les lecteurs fixes (C : et D :), un lecteur réseau mappé (G :) qui a été créé à l’aide du paramètre **Persist** de `New-PSDrive` et d’un lecteur PowerShell (T :) qui a été créé à l’aide de `New-PSDrive` sans le paramètre **Persist** .</span><span class="sxs-lookup"><span data-stu-id="998a5-138">This includes the fixed drives (C: and D:), a mapped network drive (G:) that was created by using the **Persist** parameter of `New-PSDrive`, and a PowerShell drive (T:) that was created by using `New-PSDrive` without the **Persist** parameter.</span></span>

<span data-ttu-id="998a5-139">La commande **net use** affiche les lecteurs réseau mappés Windows. dans ce cas, elle affiche uniquement le lecteur G.</span><span class="sxs-lookup"><span data-stu-id="998a5-139">The **net use** command displays Windows mapped network drives, in this case it displays only the G drive.</span></span> <span data-ttu-id="998a5-140">Elle n’affiche pas le lecteur X : qui a été créé par `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="998a5-140">It does not display the X: drive that was created by `New-PSDrive`.</span></span> <span data-ttu-id="998a5-141">Elle indique que le lecteur G : est également mappé à \\ \\ Music \\ GratefulDead.</span><span class="sxs-lookup"><span data-stu-id="998a5-141">It shows that the G: drive is also mapped to \\\\Music\\GratefulDead.</span></span>

<span data-ttu-id="998a5-142">La troisième commande utilise la méthode **GetDrives** de la classe Microsoft .NET Framework **System.IO.DriveInfo** .</span><span class="sxs-lookup"><span data-stu-id="998a5-142">The third command uses the **GetDrives** method of the Microsoft .NET Framework **System.IO.DriveInfo** class.</span></span> <span data-ttu-id="998a5-143">Cette commande obtient les lecteurs du système de fichiers Windows, y compris le lecteur G :, mais il n’obtient pas les lecteurs créés par `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="998a5-143">This command gets the Windows file system drives, including drive G:, but it does not get the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="998a5-144">La quatrième commande utilise l’applet de commande `Get-CimInstance` pour obtenir les instances de la classe **Win32_LogicalDisk** .</span><span class="sxs-lookup"><span data-stu-id="998a5-144">The fourth command uses the `Get-CimInstance` cmdlet to get the instances of the **Win32_LogicalDisk** class.</span></span> <span data-ttu-id="998a5-145">Elle retourne les lecteurs A :, C :, D :, E : et G :, mais pas les lecteurs créés par `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="998a5-145">It returns the A:, C:, D:, E:, and G: drives, but not the drives created by `New-PSDrive`.</span></span>

<span data-ttu-id="998a5-146">La dernière commande utilise l’applet de commande `Get-CimInstance` pour afficher les instances de la classe **Win32_NetworkConnection** .</span><span class="sxs-lookup"><span data-stu-id="998a5-146">The last command uses the `Get-CimInstance` cmdlet to display the instances of the **Win32_NetworkConnection** class.</span></span> <span data-ttu-id="998a5-147">Tout comme **net use** , elle retourne uniquement le lecteur G : persistant créé par `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="998a5-147">Like **net use** , it returns only the persistent G: drive created by `New-PSDrive`.</span></span>

## <span data-ttu-id="998a5-148">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="998a5-148">PARAMETERS</span></span>

### <span data-ttu-id="998a5-149">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="998a5-149">-LiteralName</span></span>

<span data-ttu-id="998a5-150">Spécifie le nom du lecteur.</span><span class="sxs-lookup"><span data-stu-id="998a5-150">Specifies the name of the drive.</span></span>

<span data-ttu-id="998a5-151">La valeur de **LiteralName**  est utilisée exactement telle que vous la tapez.</span><span class="sxs-lookup"><span data-stu-id="998a5-151">The value of **LiteralName** is used exactly as it is typed.</span></span> <span data-ttu-id="998a5-152">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="998a5-152">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="998a5-153">Si le nom inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="998a5-153">If the name includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="998a5-154">Les guillemets simples indiquent à Windows PowerShell qu’aucun caractère ne doit être interprété en tant que séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="998a5-154">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="998a5-155">-Name</span><span class="sxs-lookup"><span data-stu-id="998a5-155">-Name</span></span>

<span data-ttu-id="998a5-156">Spécifie, sous forme de tableau de chaînes, le nom ou le nom des lecteurs que cette applet de commande obtient dans l’opération.</span><span class="sxs-lookup"><span data-stu-id="998a5-156">Specifies, as a string array, the name or name of drives that this cmdlet gets in the operation.</span></span>
<span data-ttu-id="998a5-157">Tapez la lettre ou le nom du lecteur sans le signe deux-points (:).</span><span class="sxs-lookup"><span data-stu-id="998a5-157">Type the drive name or letter without a colon (:).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="998a5-158">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="998a5-158">-PSProvider</span></span>

<span data-ttu-id="998a5-159">Spécifie, sous la forme d’un tableau de chaînes, le fournisseur Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="998a5-159">Specifies, as a string array, the Windows PowerShell provider.</span></span> <span data-ttu-id="998a5-160">Cette applet de commande obtient uniquement les lecteurs pris en charge par ce fournisseur.</span><span class="sxs-lookup"><span data-stu-id="998a5-160">This cmdlet gets only the drives supported by this provider.</span></span> <span data-ttu-id="998a5-161">Tapez le nom d’un fournisseur (FileSystem, Registry ou Certificate, par exemple).</span><span class="sxs-lookup"><span data-stu-id="998a5-161">Type the name of a provider, such as FileSystem, Registry, or Certificate.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="998a5-162">-Étendue</span><span class="sxs-lookup"><span data-stu-id="998a5-162">-Scope</span></span>

<span data-ttu-id="998a5-163">Spécifie l’étendue dans laquelle cette applet de commande obtient les lecteurs.</span><span class="sxs-lookup"><span data-stu-id="998a5-163">Specifies the scope in which this cmdlet gets the drives.</span></span>

<span data-ttu-id="998a5-164">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="998a5-164">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="998a5-165">Global</span><span class="sxs-lookup"><span data-stu-id="998a5-165">Global</span></span>
- <span data-ttu-id="998a5-166">Local</span><span class="sxs-lookup"><span data-stu-id="998a5-166">Local</span></span>
- <span data-ttu-id="998a5-167">Script</span><span class="sxs-lookup"><span data-stu-id="998a5-167">Script</span></span>
- <span data-ttu-id="998a5-168">nombre relatif à la portée actuelle (0 jusqu’au nombre d’étendues, où 0 est la portée actuelle et 1 est son parent).</span><span class="sxs-lookup"><span data-stu-id="998a5-168">a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span> <span data-ttu-id="998a5-169">« Local » est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="998a5-169">"Local" is the default.</span></span>

<span data-ttu-id="998a5-170">Pour plus d’informations, consultez [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="998a5-170">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="998a5-171">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="998a5-171">-UseTransaction</span></span>

<span data-ttu-id="998a5-172">Inclut la commande dans la transaction active.</span><span class="sxs-lookup"><span data-stu-id="998a5-172">Includes the command in the active transaction.</span></span> <span data-ttu-id="998a5-173">Ce paramètre est uniquement valide au cours d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="998a5-173">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="998a5-174">Pour plus d'informations, consultez [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="998a5-174">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

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

### <span data-ttu-id="998a5-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="998a5-175">CommonParameters</span></span>

<span data-ttu-id="998a5-176">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="998a5-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="998a5-177">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="998a5-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="998a5-178">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="998a5-178">INPUTS</span></span>

### <span data-ttu-id="998a5-179">Aucun</span><span class="sxs-lookup"><span data-stu-id="998a5-179">None</span></span>

<span data-ttu-id="998a5-180">Vous ne pouvez pas rediriger des objets vers cette applet de commande.</span><span class="sxs-lookup"><span data-stu-id="998a5-180">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="998a5-181">SORTIES</span><span class="sxs-lookup"><span data-stu-id="998a5-181">OUTPUTS</span></span>

### <span data-ttu-id="998a5-182">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="998a5-182">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="998a5-183">Cette applet de commande retourne des objets qui représentent les lecteurs dans la session.</span><span class="sxs-lookup"><span data-stu-id="998a5-183">This cmdlet returns objects that represent the drives in the session.</span></span>

## <span data-ttu-id="998a5-184">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="998a5-184">NOTES</span></span>

* <span data-ttu-id="998a5-185">Cette applet de commande est conçue pour utiliser les données exposées par n’importe quel fournisseur.</span><span class="sxs-lookup"><span data-stu-id="998a5-185">This cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="998a5-186">Pour répertorier les fournisseurs disponibles dans votre session, utilisez l'applet de commande `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="998a5-186">To list the providers available in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="998a5-187">Pour plus d'informations, consultez [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="998a5-187">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
* <span data-ttu-id="998a5-188">Les lecteurs réseau mappés qui sont créés à l’aide du paramètre **Persist** de l’applet de commande New-PSDrive sont spécifiques à un compte d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="998a5-188">Mapped network drives that are created by using the **Persist** parameter of the New-PSDrive cmdlet are specific to a user account.</span></span> <span data-ttu-id="998a5-189">Les lecteurs réseau mappés que vous créez dans les sessions démarrées avec l’option Exécuter en tant qu’administrateur ou avec les informations d’identification d’un autre utilisateur ne sont pas visibles dans les sessions démarrées sans informations d’identification explicites ou avec les informations d’identification de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="998a5-189">Mapped network drives that you create in sessions that are started with the Run as administrator option or with the credentials of another user are not visible in sessions that are started without explicit credentials or with the credentials of the current user.</span></span>

## <span data-ttu-id="998a5-190">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="998a5-190">RELATED LINKS</span></span>

[<span data-ttu-id="998a5-191">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="998a5-191">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="998a5-192">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="998a5-192">Remove-PSDrive</span></span>](Remove-PSDrive.md)

[<span data-ttu-id="998a5-193">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="998a5-193">Get-PSProvider</span></span>](Get-PSProvider.md)
