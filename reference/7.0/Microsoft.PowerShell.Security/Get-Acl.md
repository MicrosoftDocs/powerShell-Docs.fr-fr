---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: cb38b327920fc56817c5c8ec73f548ffba8bdd7a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93202021"
---
# <span data-ttu-id="1a44f-103">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="1a44f-103">Get-Acl</span></span>

## <span data-ttu-id="1a44f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1a44f-104">SYNOPSIS</span></span>
<span data-ttu-id="1a44f-105">Obtient le descripteur de sécurité d'une ressource, comme une clé de Registre ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="1a44f-105">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="1a44f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a44f-106">SYNTAX</span></span>

### <span data-ttu-id="1a44f-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="1a44f-107">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="1a44f-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="1a44f-108">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1a44f-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="1a44f-109">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="1a44f-110">Description</span><span class="sxs-lookup"><span data-stu-id="1a44f-110">DESCRIPTION</span></span>

<span data-ttu-id="1a44f-111">L' `Get-Acl` applet de commande obtient les objets qui représentent le descripteur de sécurité d’un fichier ou d’une ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-111">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="1a44f-112">Le descripteur de sécurité contient les listes de contrôle d'accès (ACL) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-112">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="1a44f-113">La liste ACL spécifie les autorisations dont disposent les utilisateurs et les groupes d'utilisateurs pour accéder à la ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-113">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="1a44f-114">À compter de Windows PowerShell 3,0, vous pouvez utiliser le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité des objets qui n’ont pas de chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="1a44f-114">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="1a44f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="1a44f-115">EXAMPLES</span></span>

### <span data-ttu-id="1a44f-116">Exemple 1 : obtenir une liste de contrôle d’accès pour un dossier</span><span class="sxs-lookup"><span data-stu-id="1a44f-116">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="1a44f-117">Cet exemple obtient le descripteur de sécurité du `C:\Windows` répertoire.</span><span class="sxs-lookup"><span data-stu-id="1a44f-117">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="1a44f-118">Exemple 2 : obtenir une liste de contrôle d’accès pour un dossier à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="1a44f-118">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="1a44f-119">Cet exemple obtient le chemin d’accès PowerShell et le SDDL pour tous les `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-119">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="1a44f-120">La commande utilise l' `Get-Acl` applet de commande pour récupérer des objets représentant les descripteurs de sécurité de chaque fichier journal.</span><span class="sxs-lookup"><span data-stu-id="1a44f-120">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="1a44f-121">Elle utilise un opérateur de pipeline ( `|` ) pour envoyer les résultats à l’applet de commande `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-121">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1a44f-122">La commande utilise le paramètre **Property** de `Format-List` pour afficher uniquement les propriétés **PSPath** et **SDDL** de chaque objet descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1a44f-122">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="1a44f-123">Les listes sont souvent utilisées dans PowerShell, car les valeurs longues apparaissent tronquées dans les tables.</span><span class="sxs-lookup"><span data-stu-id="1a44f-123">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="1a44f-124">Les valeurs **SDDL** sont précieuses pour les administrateurs système, car elles sont constituées de chaînes de texte simples qui contiennent toutes les informations du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1a44f-124">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="1a44f-125">Par conséquent, elles sont faciles à transmettre et à stocker, et peuvent être analysées si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="1a44f-125">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="1a44f-126">Exemple 3 : obtenir le nombre d’entrées d’audit pour une liste de contrôle d’accès</span><span class="sxs-lookup"><span data-stu-id="1a44f-126">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="1a44f-127">Cet exemple obtient les descripteurs de sécurité des `.log` fichiers du `C:\Windows` répertoire dont les noms commencent par `s` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-127">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="1a44f-128">Elle utilise le paramètre **Audit** pour obtenir les enregistrements d'audit de la liste SACL dans le descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1a44f-128">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="1a44f-129">Elle utilise ensuite l' `ForEach-Object` applet de commande pour compter le nombre d’enregistrements d’audit associés à chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="1a44f-129">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="1a44f-130">Le résultat est une liste de nombres représentant le nombre d'enregistrements d'audit de chaque fichier journal.</span><span class="sxs-lookup"><span data-stu-id="1a44f-130">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="1a44f-131">Exemple 4 : obtenir une liste de contrôle d’accès pour une clé de Registre</span><span class="sxs-lookup"><span data-stu-id="1a44f-131">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="1a44f-132">Cet exemple utilise l' `Get-Acl` applet de commande pour récupérer le descripteur de sécurité de la sous-clé de contrôle ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) du Registre.</span><span class="sxs-lookup"><span data-stu-id="1a44f-132">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="1a44f-133">Le paramètre **path** spécifie la sous-clé du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1a44f-133">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="1a44f-134">L’opérateur de pipeline ( `|` ) passe le descripteur de sécurité qui `Get-Acl` est extrait à la `Format-List` commande, qui met en forme les propriétés du descripteur de sécurité sous la forme d’une liste afin qu’elles soient faciles à lire.</span><span class="sxs-lookup"><span data-stu-id="1a44f-134">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="1a44f-135">Exemple 5 : récupération d’une liste de contrôle d’accès à l’aide d' **InputObject**</span><span class="sxs-lookup"><span data-stu-id="1a44f-135">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="1a44f-136">Cet exemple utilise le paramètre **InputObject** de `Get-Acl` pour obtenir le descripteur de sécurité d’un objet de sous-système de stockage.</span><span class="sxs-lookup"><span data-stu-id="1a44f-136">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="1a44f-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a44f-137">PARAMETERS</span></span>

### <span data-ttu-id="1a44f-138">-Audit</span><span class="sxs-lookup"><span data-stu-id="1a44f-138">-Audit</span></span>

<span data-ttu-id="1a44f-139">Obtient les données d'audit du descripteur de sécurité à partir de la liste de contrôle d'accès système (SACL).</span><span class="sxs-lookup"><span data-stu-id="1a44f-139">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="1a44f-140">-Exclude</span><span class="sxs-lookup"><span data-stu-id="1a44f-140">-Exclude</span></span>

<span data-ttu-id="1a44f-141">Omet les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-141">Omits the specified items.</span></span> <span data-ttu-id="1a44f-142">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="1a44f-142">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1a44f-143">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-143">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1a44f-144">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1a44f-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="1a44f-145">-Filter</span></span>

<span data-ttu-id="1a44f-146">Spécifie un filtre dans le format ou le langage du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1a44f-146">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="1a44f-147">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="1a44f-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1a44f-148">La syntaxe du filtre, notamment l'utilisation de caractères génériques, dépend du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="1a44f-148">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="1a44f-149">Les filtres sont plus efficaces que les autres paramètres, car le fournisseur les applique lors de l’obtention des objets, plutôt que de faire en sorte que PowerShell filtre les objets une fois qu’ils ont été récupérés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-149">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="1a44f-150">-Include</span><span class="sxs-lookup"><span data-stu-id="1a44f-150">-Include</span></span>

<span data-ttu-id="1a44f-151">Obtient uniquement les éléments spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-151">Gets only the specified items.</span></span> <span data-ttu-id="1a44f-152">La valeur de ce paramètre qualifie le paramètre **Path** .</span><span class="sxs-lookup"><span data-stu-id="1a44f-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1a44f-153">Entrez un élément ou un modèle de chemin d’accès, tel que `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-153">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1a44f-154">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1a44f-155">-Path</span><span class="sxs-lookup"><span data-stu-id="1a44f-155">-Path</span></span>

<span data-ttu-id="1a44f-156">Spécifie le chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-156">Specifies the path to a resource.</span></span> <span data-ttu-id="1a44f-157">`Get-Acl` Obtient le descripteur de sécurité de la ressource indiqué par le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="1a44f-157">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="1a44f-158">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="1a44f-158">Wildcards are permitted.</span></span> <span data-ttu-id="1a44f-159">Si vous omettez le paramètre **path** , `Get-Acl` obtient le descripteur de sécurité du répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="1a44f-159">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="1a44f-160">Le nom de paramètre (« Path ») est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1a44f-160">The parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="1a44f-161">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1a44f-161">-InputObject</span></span>

<span data-ttu-id="1a44f-162">Obtient le descripteur de sécurité de l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a44f-162">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="1a44f-163">Entrez une variable qui contient l'objet ou tapez une commande permettant d'obtenir cet objet.</span><span class="sxs-lookup"><span data-stu-id="1a44f-163">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="1a44f-164">Vous ne pouvez pas diriger un objet, autre qu’un chemin d’accès, vers `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-164">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="1a44f-165">Utilisez plutôt le paramètre **InputObject** explicitement dans la commande.</span><span class="sxs-lookup"><span data-stu-id="1a44f-165">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="1a44f-166">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1a44f-166">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1a44f-167">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1a44f-167">-LiteralPath</span></span>

<span data-ttu-id="1a44f-168">Spécifie le chemin d'accès à une ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-168">Specifies the path to a resource.</span></span> <span data-ttu-id="1a44f-169">Contrairement au paramètre **Path** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="1a44f-169">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="1a44f-170">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="1a44f-170">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1a44f-171">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="1a44f-171">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1a44f-172">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="1a44f-172">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="1a44f-173">Ce paramètre est introduit dans Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="1a44f-173">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1a44f-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a44f-174">CommonParameters</span></span>

<span data-ttu-id="1a44f-175">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a44f-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a44f-176">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1a44f-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a44f-177">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="1a44f-177">INPUTS</span></span>

### <span data-ttu-id="1a44f-178">System.String</span><span class="sxs-lookup"><span data-stu-id="1a44f-178">System.String</span></span>

<span data-ttu-id="1a44f-179">Vous pouvez diriger une chaîne qui contient un chemin d’accès vers `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="1a44f-179">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="1a44f-180">SORTIES</span><span class="sxs-lookup"><span data-stu-id="1a44f-180">OUTPUTS</span></span>

### <span data-ttu-id="1a44f-181">System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="1a44f-181">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="1a44f-182">`Get-Acl` retourne un objet qui représente les listes de contrôle d’accès qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="1a44f-182">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="1a44f-183">Le type d'objet varie selon le type d'ACL.</span><span class="sxs-lookup"><span data-stu-id="1a44f-183">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="1a44f-184">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="1a44f-184">NOTES</span></span>

<span data-ttu-id="1a44f-185">Par défaut, `Get-Acl` affiche le chemin d’accès PowerShell à la ressource ( `<provider>::<resource-path>` ), le propriétaire de la ressource et « Access », une liste (tableau) des entrées de contrôle d’accès dans la liste de contrôle d’accès discrétionnaire (DACL) de la ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="1a44f-186">La liste DACL est contrôlée par le propriétaire de la ressource.</span><span class="sxs-lookup"><span data-stu-id="1a44f-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="1a44f-187">Lorsque vous mettez en forme le résultat sous la forme d’une liste, ( `Get-Acl | Format-List` ), en plus du chemin d’accès, du propriétaire et de la liste d’accès, PowerShell affiche les propriétés et les valeurs de propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a44f-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="1a44f-188">**Groupe** : groupe de sécurité du propriétaire.</span><span class="sxs-lookup"><span data-stu-id="1a44f-188">**Group** : The security group of the owner.</span></span>
- <span data-ttu-id="1a44f-189">**Audit** : liste (tableau) d’entrées dans la liste de contrôle d’accès système (SACL).</span><span class="sxs-lookup"><span data-stu-id="1a44f-189">**Audit** :  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="1a44f-190">La liste SACL spécifie les types de tentatives d'accès pour lesquels Windows génère des enregistrements d'audit.</span><span class="sxs-lookup"><span data-stu-id="1a44f-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="1a44f-191">**SDDL** : descripteur de sécurité de la ressource affiché dans une chaîne de texte unique au format de langage de définition du descripteur de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1a44f-191">**Sddl** : The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="1a44f-192">PowerShell utilise la méthode **GetSddlForm** des descripteurs de sécurité pour récupérer ces données.</span><span class="sxs-lookup"><span data-stu-id="1a44f-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="1a44f-193">Étant donné que `Get-Acl` est pris en charge par le système de fichiers et les fournisseurs de Registre, vous pouvez utiliser `Get-Acl` pour afficher la liste de contrôle d’accès des objets de système de fichiers, tels que les fichiers et les répertoires, et les objets de Registre, tels que les clés de Registre et les entrées.</span><span class="sxs-lookup"><span data-stu-id="1a44f-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="1a44f-194">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="1a44f-194">RELATED LINKS</span></span>

[<span data-ttu-id="1a44f-195">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="1a44f-195">Set-Acl</span></span>](Set-Acl.md)
