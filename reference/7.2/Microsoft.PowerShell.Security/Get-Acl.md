---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596736"
---
# <span data-ttu-id="e05d3-102">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="e05d3-102">Get-Acl</span></span>

## <span data-ttu-id="e05d3-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="e05d3-103">SYNOPSIS</span></span>
<span data-ttu-id="e05d3-104">Obtient le descripteur de sécurité d'une ressource, comme une clé de Registre ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="e05d3-104">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="e05d3-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="e05d3-105">SYNTAX</span></span>

### <span data-ttu-id="e05d3-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e05d3-106">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="e05d3-107">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="e05d3-107">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="e05d3-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="e05d3-108">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e05d3-109">Description</span><span class="sxs-lookup"><span data-stu-id="e05d3-109">DESCRIPTION</span></span>

<span data-ttu-id="e05d3-110">L' `Get-Acl` applet de commande obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-110">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="e05d3-111">Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-111">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="e05d3-112">La liste ACL spécifie les autorisations dont disposent les utilisateurs et les groupes d'utilisateurs pour accéder à la ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-112">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="e05d3-113">À compter de Windows PowerShell 3,0, vous pouvez utiliser le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité des objets qui n’ont pas de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="e05d3-113">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="e05d3-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="e05d3-114">EXAMPLES</span></span>

### <span data-ttu-id="e05d3-115">Exemple 1 : obtenir une liste de contrôle d’accès pour un dossier</span><span class="sxs-lookup"><span data-stu-id="e05d3-115">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="e05d3-116">Cet exemple obtient le descripteur de sécurité du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="e05d3-116">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="e05d3-117">Exemple 2 : obtenir une liste de contrôle d’accès pour un dossier à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="e05d3-117">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="e05d3-118">Cet exemple obtient le chemin d’accès PowerShell et le SDDL pour tous les `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-118">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="e05d3-119">La commande utilise l' `Get-Acl` applet de commande pour récupérer des objets représentant les descripteurs de sécurité de chaque fichier journal.</span><span class="sxs-lookup"><span data-stu-id="e05d3-119">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="e05d3-120">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-120">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="e05d3-121">La commande utilise le paramètre **Property** de `Format-List` pour afficher uniquement les propriétés **PSPath** et **SDDL** de chaque objet descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e05d3-121">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="e05d3-122">Les listes sont souvent utilisées dans PowerShell, car les valeurs longues apparaissent tronquées dans les tables.</span><span class="sxs-lookup"><span data-stu-id="e05d3-122">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="e05d3-123">Les valeurs **SDDL** sont précieuses pour les administrateurs système, car elles sont constituées de chaînes de texte simples qui contiennent toutes les informations du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e05d3-123">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="e05d3-124">Par conséquent, elles sont faciles à transmettre et à stocker, et peuvent être analysées si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e05d3-124">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="e05d3-125">Exemple 3 : obtenir le nombre d’entrées d’audit pour une liste de contrôle d’accès</span><span class="sxs-lookup"><span data-stu-id="e05d3-125">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="e05d3-126">Cet exemple obtient les descripteurs de sécurité des `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-126">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="e05d3-127">Elle utilise le paramètre **Audit** pour obtenir les enregistrements d'audit de la liste SACL dans le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e05d3-127">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="e05d3-128">Elle utilise ensuite l' `ForEach-Object` applet de commande pour compter le nombre d’enregistrements d’audit associés à chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="e05d3-128">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="e05d3-129">Le résultat est une liste de nombres représentant le nombre d'enregistrements d'audit de chaque fichier journal.</span><span class="sxs-lookup"><span data-stu-id="e05d3-129">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="e05d3-130">Exemple 4 : obtenir une liste de contrôle d’accès pour une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="e05d3-130">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="e05d3-131">Cet exemple utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité de la sous-clé de contrôle ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) du Registre.</span><span class="sxs-lookup"><span data-stu-id="e05d3-131">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="e05d3-132">Le paramètre **path** spécifie la sous-clé du contrôle.</span><span class="sxs-lookup"><span data-stu-id="e05d3-132">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="e05d3-133">L’opérateur de pipeline ( `|` ) passe le descripteur de sécurité qui `Get-Acl` est extrait à la `Format-List` commande, qui met en forme les propriétés du descripteur de sécurité sous la forme d’une liste afin qu’elles soient faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="e05d3-133">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="e05d3-134">Exemple 5 : récupération d’une liste de contrôle d’accès à l’aide d' **InputObject**</span><span class="sxs-lookup"><span data-stu-id="e05d3-134">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="e05d3-135">Cet exemple utilise le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité d’un objet de sous-système de stockage.</span><span class="sxs-lookup"><span data-stu-id="e05d3-135">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="e05d3-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e05d3-136">PARAMETERS</span></span>

### <span data-ttu-id="e05d3-137">-Audit</span><span class="sxs-lookup"><span data-stu-id="e05d3-137">-Audit</span></span>

<span data-ttu-id="e05d3-138">Obtient les données d'audit du descripteur de sécurité à partir de la liste de contrôle d'accès système (SACL).</span><span class="sxs-lookup"><span data-stu-id="e05d3-138">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e05d3-139">-Exclude</span><span class="sxs-lookup"><span data-stu-id="e05d3-139">-Exclude</span></span>

<span data-ttu-id="e05d3-140">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-140">Omits the specified items.</span></span> <span data-ttu-id="e05d3-141">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="e05d3-141">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e05d3-142">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-142">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e05d3-143">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-143">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e05d3-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="e05d3-144">-Filter</span></span>

<span data-ttu-id="e05d3-145">Spécifie un filtre dans le format ou le langage du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e05d3-145">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="e05d3-146">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="e05d3-146">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e05d3-147">La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="e05d3-147">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="e05d3-148">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de l’obtention des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-148">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e05d3-149">-Include</span><span class="sxs-lookup"><span data-stu-id="e05d3-149">-Include</span></span>

<span data-ttu-id="e05d3-150">Obtient uniquement les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-150">Gets only the specified items.</span></span> <span data-ttu-id="e05d3-151">La valeur de ce paramètre qualifie le paramètre **Path**.</span><span class="sxs-lookup"><span data-stu-id="e05d3-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e05d3-152">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e05d3-153">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-153">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e05d3-154">-Path</span><span class="sxs-lookup"><span data-stu-id="e05d3-154">-Path</span></span>

<span data-ttu-id="e05d3-155">Spécifie le chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-155">Specifies the path to a resource.</span></span> <span data-ttu-id="e05d3-156">`Get-Acl` Obtient le descripteur de sécurité de la ressource indiqué par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="e05d3-156">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="e05d3-157">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="e05d3-157">Wildcards are permitted.</span></span> <span data-ttu-id="e05d3-158">Si vous omettez le paramètre **path** , `Get-Acl` obtient le descripteur de sécurité du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e05d3-158">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="e05d3-159">Le nom de paramètre (« Path ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e05d3-159">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="e05d3-160">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e05d3-160">-InputObject</span></span>

<span data-ttu-id="e05d3-161">Obtient le descripteur de sécurité de l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="e05d3-161">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="e05d3-162">Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.</span><span class="sxs-lookup"><span data-stu-id="e05d3-162">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="e05d3-163">Vous ne pouvez pas diriger un objet, autre qu’un chemin d’accès, vers `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-163">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="e05d3-164">Utilisez plutôt le paramètre **InputObject** explicitement dans la commande.</span><span class="sxs-lookup"><span data-stu-id="e05d3-164">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="e05d3-165">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e05d3-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e05d3-166">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e05d3-166">-LiteralPath</span></span>

<span data-ttu-id="e05d3-167">Spécifie le chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-167">Specifies the path to a resource.</span></span> <span data-ttu-id="e05d3-168">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="e05d3-168">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="e05d3-169">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="e05d3-169">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e05d3-170">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="e05d3-170">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e05d3-171">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="e05d3-171">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="e05d3-172">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e05d3-172">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e05d3-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e05d3-173">CommonParameters</span></span>

<span data-ttu-id="e05d3-174">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e05d3-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e05d3-175">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e05d3-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e05d3-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="e05d3-176">INPUTS</span></span>

### <span data-ttu-id="e05d3-177">System.String</span><span class="sxs-lookup"><span data-stu-id="e05d3-177">System.String</span></span>

<span data-ttu-id="e05d3-178">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="e05d3-178">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="e05d3-179">SORTIES</span><span class="sxs-lookup"><span data-stu-id="e05d3-179">OUTPUTS</span></span>

### <span data-ttu-id="e05d3-180">System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="e05d3-180">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="e05d3-181">`Get-Acl` retourne un objet qui représente les listes de contrôle d’accès qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="e05d3-181">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="e05d3-182">Le type d'objet varie selon le type d'ACL.</span><span class="sxs-lookup"><span data-stu-id="e05d3-182">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="e05d3-183">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="e05d3-183">NOTES</span></span>

<span data-ttu-id="e05d3-184">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="e05d3-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="e05d3-185">Par défaut, `Get-Acl` affiche le chemin d’accès PowerShell à la ressource ( `<provider>::<resource-path>` ), le propriétaire de la ressource et « Access », une liste (tableau) des entrées de contrôle d’accès dans la liste de contrôle d’accès discrétionnaire (DACL) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="e05d3-186">La liste DACL est contrôlée par le propriétaire de la ressource.</span><span class="sxs-lookup"><span data-stu-id="e05d3-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="e05d3-187">Lorsque vous mettez en forme le résultat sous la forme d’une liste, ( `Get-Acl | Format-List` ), en plus du chemin d’accès, du propriétaire et de la liste d’accès, PowerShell affiche les propriétés et les valeurs de propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e05d3-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="e05d3-188">**Groupe**: groupe de sécurité du propriétaire.</span><span class="sxs-lookup"><span data-stu-id="e05d3-188">**Group**: The security group of the owner.</span></span>
- <span data-ttu-id="e05d3-189">**Audit**: liste (tableau) d’entrées dans la liste de contrôle d’accès système (SACL).</span><span class="sxs-lookup"><span data-stu-id="e05d3-189">**Audit**:  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="e05d3-190">La liste SACL spécifie les types de tentatives d'accès pour lesquels Windows génère des enregistrements d'audit.</span><span class="sxs-lookup"><span data-stu-id="e05d3-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="e05d3-191">**SDDL**: descripteur de sécurité de la ressource affiché dans une chaîne de texte unique au format de langage de définition du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e05d3-191">**Sddl**: The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="e05d3-192">PowerShell utilise la méthode **GetSddlForm** des descripteurs de sécurité pour récupérer ces données.</span><span class="sxs-lookup"><span data-stu-id="e05d3-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="e05d3-193">Étant donné que `Get-Acl` est pris en charge par le système de fichiers et les fournisseurs de Registre, vous pouvez utiliser `Get-Acl` pour afficher la liste de contrôle d’accès des objets de système de fichiers, tels que les fichiers et les répertoires, et les objets de Registre, tels que les clés de Registre et les entrées.</span><span class="sxs-lookup"><span data-stu-id="e05d3-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="e05d3-194">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="e05d3-194">RELATED LINKS</span></span>

[<span data-ttu-id="e05d3-195">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="e05d3-195">Set-Acl</span></span>](Set-Acl.md)
