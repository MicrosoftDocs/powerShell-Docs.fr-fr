---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-hotfix?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-HotFix
ms.openlocfilehash: 5b5b5939d4dcae8a99b1030b533fe6a85bcc601a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598553"
---
# <span data-ttu-id="988bf-102">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="988bf-102">Get-HotFix</span></span>

## <span data-ttu-id="988bf-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="988bf-103">SYNOPSIS</span></span>
<span data-ttu-id="988bf-104">Obtient les correctifs logiciels installés sur les ordinateurs locaux ou distants.</span><span class="sxs-lookup"><span data-stu-id="988bf-104">Gets the hotfixes that are installed on local or remote computers.</span></span>

## <span data-ttu-id="988bf-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="988bf-105">SYNTAX</span></span>

### <span data-ttu-id="988bf-106">Valeur par défaut (par défaut)</span><span class="sxs-lookup"><span data-stu-id="988bf-106">Default (Default)</span></span>

```
Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

### <span data-ttu-id="988bf-107">Description</span><span class="sxs-lookup"><span data-stu-id="988bf-107">Description</span></span>

```
Get-HotFix [-Description <String[]>] [-ComputerName <String[]>] [-Credential <PSCredential>]
[<CommonParameters>]
```

## <span data-ttu-id="988bf-108">Description</span><span class="sxs-lookup"><span data-stu-id="988bf-108">DESCRIPTION</span></span>

<span data-ttu-id="988bf-109">L' `Get-Hotfix` applet de commande obtient les correctifs logiciels, ou les mises à jour, qui sont installés sur l’ordinateur local ou les ordinateurs distants spécifiés.</span><span class="sxs-lookup"><span data-stu-id="988bf-109">The `Get-Hotfix` cmdlet gets hotfixes, or updates, that are installed on the local computer or specified remote computers.</span></span> <span data-ttu-id="988bf-110">Les mises à jour peuvent être installées par Windows Update, Microsoft Update, Windows Server Update Services ou installées manuellement.</span><span class="sxs-lookup"><span data-stu-id="988bf-110">The updates can be installed by Windows Update, Microsoft Update, Windows Server Update Services, or manually installed.</span></span>

## <span data-ttu-id="988bf-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="988bf-111">EXAMPLES</span></span>

### <span data-ttu-id="988bf-112">Exemple 1 : récupération de tous les correctifs logiciels sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="988bf-112">Example 1: Get all hotfixes on the local computer</span></span>

<span data-ttu-id="988bf-113">L' `Get-Hotfix` applet de commande obtient tous les correctifs logiciels installés sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="988bf-113">The `Get-Hotfix` cmdlet gets all hotfixes installed on the local computer.</span></span>

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

### <span data-ttu-id="988bf-114">Exemple 2 : obtenir des correctifs à partir de plusieurs ordinateurs filtrés par une chaîne</span><span class="sxs-lookup"><span data-stu-id="988bf-114">Example 2: Get hotfixes from multiple computers filtered by a string</span></span>

<span data-ttu-id="988bf-115">La `Get-Hotfix` commande utilise des paramètres pour installer les correctifs logiciels sur les ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="988bf-115">The `Get-Hotfix` command uses parameters to get hotfixes installed on remote computers.</span></span> <span data-ttu-id="988bf-116">Les résultats sont filtrés par une chaîne de description spécifiée.</span><span class="sxs-lookup"><span data-stu-id="988bf-116">The results are filtered by a specified description string.</span></span>

```
PS> Get-HotFix -Description Security* -ComputerName Server01, Server02 -Credential Domain01\admin01
```

<span data-ttu-id="988bf-117">`Get-Hotfix` filtre la sortie avec le paramètre **Description** et la **sécurité** de chaîne incluant le caractère générique astérisque ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="988bf-117">`Get-Hotfix` filters the output with the **Description** parameter and the string **Security** that includes the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="988bf-118">Le paramètre **ComputerName** contient une chaîne séparée par des virgules de noms d’ordinateurs distants.</span><span class="sxs-lookup"><span data-stu-id="988bf-118">The **ComputerName** parameter includes a comma-separated string of remote computer names.</span></span> <span data-ttu-id="988bf-119">Le paramètre **Credential** spécifie un compte d’utilisateur qui a l’autorisation d’accéder aux ordinateurs distants et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="988bf-119">The **Credential** parameter specifies a user account that has permission to access the remote computers and run commands.</span></span>

### <span data-ttu-id="988bf-120">Exemple 3 : vérifier si une mise à jour est installée et écrire des noms d’ordinateur dans un fichier</span><span class="sxs-lookup"><span data-stu-id="988bf-120">Example 3: Verify if an update is installed and write computer names to a file</span></span>

<span data-ttu-id="988bf-121">Les commandes de cet exemple vérifient si une mise à jour particulière est installée.</span><span class="sxs-lookup"><span data-stu-id="988bf-121">The commands in this example verify whether a particular update installed.</span></span> <span data-ttu-id="988bf-122">Si la mise à jour n’est pas installée, le nom de l’ordinateur est écrit dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="988bf-122">If the update isn't installed, the computer name is written to a text file.</span></span>

```
PS> $A = Get-Content -Path ./Servers.txt
PS> $A | ForEach-Object { if (!(Get-HotFix -Id KB957095 -ComputerName $_))
         { Add-Content $_ -Path ./Missing-KB957095.txt }}
```

<span data-ttu-id="988bf-123">La `$A` variable contient les noms d’ordinateur obtenus par `Get-Content` à partir d’un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="988bf-123">The `$A` variable contains computer names that were obtained by `Get-Content` from a text file.</span></span> <span data-ttu-id="988bf-124">Les objets dans `$A` sont envoyés dans le pipeline à `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="988bf-124">The objects in `$A` are sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="988bf-125">Une `if` instruction utilise l' `Get-Hotfix` applet de commande avec le paramètre **ID** et un numéro d’ID spécifique pour chaque nom d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="988bf-125">An `if` statement uses the `Get-Hotfix` cmdlet with the **Id** parameter and a specific Id number for each computer name.</span></span> <span data-ttu-id="988bf-126">Si l’ID de correctif logiciel spécifié n’est pas installé sur l’ordinateur, l' `Add-Content` applet de commande écrit le nom de l’ordinateur dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="988bf-126">If a computer doesn't have the specified hotfix Id installed, the `Add-Content` cmdlet writes the computer name to a file.</span></span>

### <span data-ttu-id="988bf-127">Exemple 4 : récupérer le correctif logiciel le plus récent sur l’ordinateur local</span><span class="sxs-lookup"><span data-stu-id="988bf-127">Example 4: Get the most recent hotfix on the local computer</span></span>

<span data-ttu-id="988bf-128">Cet exemple obtient le correctif logiciel le plus récent installé sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="988bf-128">This example gets the most recent hotfix installed on a computer.</span></span>

```powershell
(Get-HotFix | Sort-Object -Property InstalledOn)[-1]
```

<span data-ttu-id="988bf-129">`Get-Hotfix` envoie les objets dans le pipeline à l’applet de commande `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="988bf-129">`Get-Hotfix` sends the objects down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="988bf-130">`Sort-Object` trie les objets par ordre croissant et utilise le paramètre **Property** pour évaluer chaque date **InstalledOn** .</span><span class="sxs-lookup"><span data-stu-id="988bf-130">`Sort-Object` sorts objects by ascending order and uses the **Property** parameter to evaluate each **InstalledOn** date.</span></span> <span data-ttu-id="988bf-131">La notation de tableau `[-1]` sélectionne le correctif logiciel le plus récent installé.</span><span class="sxs-lookup"><span data-stu-id="988bf-131">The array notation `[-1]` selects the most recent installed hotfix.</span></span>

## <span data-ttu-id="988bf-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="988bf-132">PARAMETERS</span></span>

### <span data-ttu-id="988bf-133">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="988bf-133">-ComputerName</span></span>

<span data-ttu-id="988bf-134">Spécifie un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="988bf-134">Specifies a remote computer.</span></span> <span data-ttu-id="988bf-135">Tapez le nom NetBIOS, une adresse IP (Internet Protocol) ou un nom de domaine complet (FQDN) d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="988bf-135">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>

<span data-ttu-id="988bf-136">Lorsque le paramètre **ComputerName** n’est pas spécifié, `Get-Hotfix` s’exécute sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="988bf-136">When the **ComputerName** parameter isn't specified, `Get-Hotfix` runs on the local computer.</span></span>

<span data-ttu-id="988bf-137">Le paramètre **ComputerName** ne repose pas sur la communication à distance Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="988bf-137">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="988bf-138">Si votre ordinateur n’est pas configuré pour exécuter des commandes distantes, utilisez le paramètre **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="988bf-138">If your computer isn't configured to run remote commands, use the **ComputerName** parameter.</span></span>

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

### <span data-ttu-id="988bf-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="988bf-139">-Credential</span></span>

<span data-ttu-id="988bf-140">Spécifie un compte d’utilisateur qui a l’autorisation d’accéder à l’ordinateur et d’exécuter des commandes.</span><span class="sxs-lookup"><span data-stu-id="988bf-140">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="988bf-141">La valeur par défaut est l’utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="988bf-141">The default is the current user</span></span>

<span data-ttu-id="988bf-142">Tapez un nom d’utilisateur, tel que **User01** ou **Domaine01\Utilisateur01**, ou entrez un objet **PSCredential** généré par l’applet de commande `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="988bf-142">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="988bf-143">Si vous tapez un nom d’utilisateur, vous êtes invité à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="988bf-143">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="988bf-144">Les informations d’identification sont stockées dans un objet [PSCredential](/dotnet/api/system.management.automation.pscredential) et le mot de passe est stocké en tant que [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="988bf-144">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="988bf-145">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="988bf-145">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="988bf-146">Description</span><span class="sxs-lookup"><span data-stu-id="988bf-146">-Description</span></span>

<span data-ttu-id="988bf-147">`Get-HotFix` utilise le paramètre **Description** pour spécifier les types de correctifs logiciels.</span><span class="sxs-lookup"><span data-stu-id="988bf-147">`Get-HotFix` uses the **Description** parameter to specify hotfix types.</span></span> <span data-ttu-id="988bf-148">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="988bf-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="988bf-149">-Id</span><span class="sxs-lookup"><span data-stu-id="988bf-149">-Id</span></span>

<span data-ttu-id="988bf-150">Filtre les `Get-HotFix` résultats pour des ID de correctifs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="988bf-150">Filters the `Get-HotFix` results for specific hotfix Ids.</span></span> <span data-ttu-id="988bf-151">Les caractères génériques ne sont pas acceptés.</span><span class="sxs-lookup"><span data-stu-id="988bf-151">Wildcards aren't accepted.</span></span>

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

### <span data-ttu-id="988bf-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="988bf-152">CommonParameters</span></span>

<span data-ttu-id="988bf-153">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="988bf-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="988bf-154">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="988bf-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="988bf-155">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="988bf-155">INPUTS</span></span>

### <span data-ttu-id="988bf-156">String</span><span class="sxs-lookup"><span data-stu-id="988bf-156">String</span></span>

<span data-ttu-id="988bf-157">Vous pouvez diriger un ou plusieurs noms d’ordinateur vers le correctif logiciel.</span><span class="sxs-lookup"><span data-stu-id="988bf-157">You can pipe one or more computer names to Get-HotFix.</span></span>

## <span data-ttu-id="988bf-158">SORTIES</span><span class="sxs-lookup"><span data-stu-id="988bf-158">OUTPUTS</span></span>

### <span data-ttu-id="988bf-159">System. Management. ManagementObject # root\CIMV2\ Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="988bf-159">System.Management.ManagementObject#root\CIMV2\Win32_QuickFixEngineering</span></span>

<span data-ttu-id="988bf-160">`Get-HotFix` retourne des objets qui représentent les correctifs logiciels sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="988bf-160">`Get-HotFix` returns objects that represent the hotfixes on the computer.</span></span>

## <span data-ttu-id="988bf-161">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="988bf-161">NOTES</span></span>

<span data-ttu-id="988bf-162">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="988bf-162">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="988bf-163">La  [classe WMI](/windows/desktop/WmiSdk/retrieving-a-class) Win32_QuickFixEngineering représente une petite mise à jour à l’échelle du système, communément appelée mise à jour du correctif QFE (rapide), appliquée au système d’exploitation actuel.</span><span class="sxs-lookup"><span data-stu-id="988bf-163">The **Win32_QuickFixEngineering** [WMI class](/windows/desktop/WmiSdk/retrieving-a-class) represents a small system-wide update, commonly referred to as a quick-fix engineering (QFE) update, applied to the current operating system.</span></span> <span data-ttu-id="988bf-164">Cette classe retourne uniquement les mises à jour fournies par la fonction de maintenance basée sur les composants (CBS).</span><span class="sxs-lookup"><span data-stu-id="988bf-164">This class returns only the updates supplied by Component Based Servicing (CBS).</span></span> <span data-ttu-id="988bf-165">Ces mises à jour ne sont pas répertoriées dans le registre.</span><span class="sxs-lookup"><span data-stu-id="988bf-165">These updates are not listed in the registry.</span></span> <span data-ttu-id="988bf-166">Les mises à jour fournies par Microsoft Windows Installer (MSI) ou le site [Windows Update](https://update.microsoft.com) ne sont pas retournées par **Win32_QuickFixEngineering**.</span><span class="sxs-lookup"><span data-stu-id="988bf-166">Updates supplied by Microsoft Windows Installer (MSI) or the [Windows Update](https://update.microsoft.com) site are not returned by **Win32_QuickFixEngineering**.</span></span> <span data-ttu-id="988bf-167">Pour plus d’informations, consultez [Win32_QuickFixEngineering classe](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span><span class="sxs-lookup"><span data-stu-id="988bf-167">For more information, see [Win32_QuickFixEngineering class](/windows/desktop/CIMWin32Prov/win32-quickfixengineering).</span></span>

<span data-ttu-id="988bf-168">La `Get-HotFix` sortie peut varier selon les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="988bf-168">The `Get-HotFix` output might vary on different operating systems.</span></span>

## <span data-ttu-id="988bf-169">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="988bf-169">RELATED LINKS</span></span>

[<span data-ttu-id="988bf-170">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="988bf-170">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="988bf-171">Add-Content</span><span class="sxs-lookup"><span data-stu-id="988bf-171">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="988bf-172">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="988bf-172">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="988bf-173">Classe Win32_QuickFixEngineering</span><span class="sxs-lookup"><span data-stu-id="988bf-173">Win32_QuickFixEngineering class</span></span>](/windows/desktop/CIMWin32Prov/win32-quickfixengineering)
