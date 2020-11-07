---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 277dd2678b54c9e708d09f6ca27d82ab9afd4c1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347616"
---
# <span data-ttu-id="9f50a-103">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="9f50a-103">Get-HotFix</span></span>

## <span data-ttu-id="9f50a-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9f50a-104">SYNOPSIS</span></span>
<span data-ttu-id="9f50a-105">Obtient les correctifs logiciels installés sur les ordinateurs locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="9f50a-105">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="9f50a-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="9f50a-106">SYNTAX</span></span>

### <span data-ttu-id="9f50a-107">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="9f50a-107">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="9f50a-108">Description</span><span class="sxs-lookup"><span data-stu-id="9f50a-108">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="9f50a-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9f50a-109">DESCRIPTION</span></span>

<span data-ttu-id="9f50a-110">L' `Get-Hotfix` applet de commande obtient les correctifs logiciels, ou les mises à jour, qui sont installés sur l’ordinateur local ou les ordinateurs distants spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9f50a-110">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="9f50a-111">Les mises à jour peuvent être installées par Windows Update, Microsoft Update, Windows Server Update Services ou installées manuellement.</span><span class="sxs-lookup"><span data-stu-id="9f50a-111">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="9f50a-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="9f50a-112">EXAMPLES</span></span>

### <span data-ttu-id="9f50a-113">Exemple 1 : récupération de tous les correctifs logiciels sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="9f50a-113">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="9f50a-114">L' `Get-Hotfix` applet de commande obtient tous les correctifs logiciels installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9f50a-114">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

```powershell
Get-HotFix
```

```output
Source         Description      HotFixID      InstalledBy          InstalledOn
------         -----------      --------      -----------          -----------
Server01       Update           KB4495590     NT AUTHORITY\SYSTEM  5/16/2019 00:00:00
Server01       Security Update  KB4470788     NT AUTHORITY\SYSTEM  1/22/2019 00:00:00
Server01       Update           KB4480056     NT AUTHORITY\SYSTEM  1/24/2019 00:00:00
```

### <span data-ttu-id="9f50a-115">Exemple 2 : obtenir des correctifs à partir de plusieurs ordinateurs filtrés par une chaîne</span><span class="sxs-lookup"><span data-stu-id="9f50a-115">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="9f50a-116">La `Get-Hotfix` commande utilise des paramètres pour installer les correctifs logiciels sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9f50a-116">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="9f50a-117">Les résultats sont filtrés par une chaîne de description spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f50a-117">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="9f50a-118">`Get-Hotfix` filtre la sortie avec le paramètre **Description** et la **sécurité** de chaîne incluant le caractère générique astérisque ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="9f50a-118">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="9f50a-119">Le paramètre **ComputerName** contient une chaîne séparée par des virgules de noms d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="9f50a-119">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="9f50a-120">Le paramètre **Credential** spécifie un compte d’utilisateur qui a l’autorisation d’accéder aux ordinateurs distants et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="9f50a-120">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="9f50a-121">Exemple 3 : vérifier si une mise à jour est installée et écrire des noms d’ordinateur dans un fichier</span><span class="sxs-lookup"><span data-stu-id="9f50a-121">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="9f50a-122">Les commandes de cet exemple vérifient si une mise à jour particulière est installée.</span><span class="sxs-lookup"><span data-stu-id="9f50a-122">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="9f50a-123">Si la mise à jour n’est pas installée, le nom de l’ordinateur est écrit dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="9f50a-123">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="9f50a-124">La `$A` variable contient les noms d’ordinateur obtenus par `Get-Content` à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="9f50a-124">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="9f50a-125">Les objets dans `$A` sont envoyés dans le pipeline à `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="9f50a-125">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="9f50a-126">Une `if` instruction utilise l' `Get-Hotfix` applet de commande avec le paramètre **ID** et un numéro d’ID spécifique pour chaque nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9f50a-126">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="9f50a-127">Si l’ID de correctif logiciel spécifié n’est pas installé sur l’ordinateur, l' `Add-Content` applet de commande écrit le nom de l’ordinateur dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="9f50a-127">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="9f50a-128">Exemple 4 : récupérer le correctif logiciel le plus récent sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="9f50a-128">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="9f50a-129">Cet exemple obtient le correctif logiciel le plus récent installé sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9f50a-129">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="9f50a-130">`Get-Hotfix` envoie les objets dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="9f50a-130">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="9f50a-131">`Sort-Object` trie les objets par ordre croissant et utilise le paramètre **Property** pour évaluer chaque date **InstalledOn** .</span><span class="sxs-lookup"><span data-stu-id="9f50a-131">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="9f50a-132">La notation de tableau `[-1]` sélectionne le correctif logiciel le plus récent installé.</span><span class="sxs-lookup"><span data-stu-id="9f50a-132">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="9f50a-133">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="9f50a-133">PARAMETERS</span></span>

### <span data-ttu-id="9f50a-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="9f50a-134">-ComputerName</span></span>

<span data-ttu-id="9f50a-135">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9f50a-135">Specifies a remote computer.</span></span> <span data-ttu-id="9f50a-136">Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN) d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="9f50a-136">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="9f50a-137">Lorsque le paramètre **ComputerName** n’est pas spécifié, `Get-Hotfix` s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="9f50a-137">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="9f50a-138">Le paramètre **ComputerName** ne repose pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f50a-138">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="9f50a-139">Si votre ordinateur n’est pas configuré pour exécuter des commandes distantes, utilisez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="9f50a-139">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __Server, IPAddress

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9f50a-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="9f50a-140">-Credential</span></span>

<span data-ttu-id="9f50a-141">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="9f50a-141">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="9f50a-142">La valeur par défaut est l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="9f50a-142">The default is the current user</span></span>

<span data-ttu-id="9f50a-143">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01** , ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="9f50a-143">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="9f50a-144">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9f50a-144">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="9f50a-145">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="9f50a-145">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="9f50a-146">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="9f50a-146">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f50a-147">Description</span><span class="sxs-lookup"><span data-stu-id="9f50a-147">-Description</span></span>

<span data-ttu-id="9f50a-148">`Get-HotFix` utilise le paramètre **Description** pour spécifier les types de correctifs logiciels.</span><span class="sxs-lookup"><span data-stu-id="9f50a-148">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="9f50a-149">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="9f50a-149">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Description
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="9f50a-150">-Id</span><span class="sxs-lookup"><span data-stu-id="9f50a-150">-Id</span></span>

<span data-ttu-id="9f50a-151">Filtre les `Get-HotFix` résultats pour des ID de correctifs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9f50a-151">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="9f50a-152">Les caractères génériques ne sont pas acceptés.</span><span class="sxs-lookup"><span data-stu-id="9f50a-152">Wildcards aren't accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: HFID

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f50a-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f50a-153">CommonParameters</span></span>

<span data-ttu-id="9f50a-154">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9f50a-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f50a-155">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9f50a-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f50a-156">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="9f50a-156">INPUTS</span></span>

### <span data-ttu-id="9f50a-157">String</span><span class="sxs-lookup"><span data-stu-id="9f50a-157">String</span></span>

<span data-ttu-id="9f50a-158">Vous pouvez diriger un ou plusieurs noms d’ordinateur vers le correctif logiciel.</span><span class="sxs-lookup"><span data-stu-id="9f50a-158">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="9f50a-159">SORTIES</span><span class="sxs-lookup"><span data-stu-id="9f50a-159">OUTPUTS</span></span>

### <span data-ttu-id="9f50a-160">System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="9f50a-160">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="9f50a-161">`Get-HotFix` retourne des objets qui représentent les correctifs logiciels sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9f50a-161">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="9f50a-162">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="9f50a-162">NOTES</span></span>

<span data-ttu-id="9f50a-163">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="9f50a-163">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="9f50a-164">La **Win32_QuickFixEngineering** [classe WMI](/windows/desktop/WmiSdk/retrieving-a-class) Win32_QuickFixEngineering représente une petite mise à jour à l’échelle du système, communément appelée mise à jour du correctif QFE (rapide), appliquée au système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="9f50a-164">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="9f50a-165">Cette classe retourne uniquement les mises à jour fournies par la fonction de maintenance basée sur les composants (CBS).</span><span class="sxs-lookup"><span data-stu-id="9f50a-165">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="9f50a-166">Ces mises à jour ne sont pas répertoriées dans le registre.</span><span class="sxs-lookup"><span data-stu-id="9f50a-166">These updates are not listed in the registry.</span></span> <span data-ttu-id="9f50a-167">Les mises à jour fournies par Microsoft Windows Installer (MSI) ou le site [Windows Update](https://update.microsoft.com) ne sont pas retournées par **Win32_QuickFixEngineering**.</span><span class="sxs-lookup"><span data-stu-id="9f50a-167">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="9f50a-168">Pour plus d’informations, consultez [Win32_QuickFixEngineering classe](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span><span class="sxs-lookup"><span data-stu-id="9f50a-168">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="9f50a-169">La `Get-HotFix` sortie peut varier selon les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9f50a-169">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="9f50a-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="9f50a-170">RELATED LINKS</span></span>

[<span data-ttu-id="9f50a-171">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="9f50a-171">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="9f50a-172">Add-Content</span><span class="sxs-lookup"><span data-stu-id="9f50a-172">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="9f50a-173">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9f50a-173">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="9f50a-174">Classe Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="9f50a-174">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
