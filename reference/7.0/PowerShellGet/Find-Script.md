---
external help file: PSModule-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: 6eb617987b437337dc3c42c33f55033b64ec8a79
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201410"
---
# <span data-ttu-id="14288-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="14288-103">Find-Script</span></span>

## <span data-ttu-id="14288-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="14288-104">SYNOPSIS</span></span>
<span data-ttu-id="14288-105">Recherche un script.</span><span class="sxs-lookup"><span data-stu-id="14288-105">Finds a script.</span></span>

## <span data-ttu-id="14288-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="14288-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="14288-107">Description</span><span class="sxs-lookup"><span data-stu-id="14288-107">DESCRIPTION</span></span>

<span data-ttu-id="14288-108">L’applet de commande **Find-script** recherche un script spécifié dans les dépôts inscrits.</span><span class="sxs-lookup"><span data-stu-id="14288-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="14288-109">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="14288-109">EXAMPLES</span></span>

### <span data-ttu-id="14288-110">Exemple 1 : Rechercher tous les scripts disponibles</span><span class="sxs-lookup"><span data-stu-id="14288-110">Example 1: Find all available scripts</span></span>

```
PS C:\> Find-Script
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
2.5        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
2.5        Fabrikam-ServerScript               Script     LocalRepo1           Description for the Fabrikam-ServerScript script
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        Script-WithDependencies2            Script     LocalRepo1           Description for the Script-WithDependencies2 script
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
2.1        Test-Script1                        Script     LocalRepo1           Test-Script1 Script example
2.0        Test-Script2                        Script     LocalRepo1           Test-Script2 Script example
1.0        TestRunbook                         Script     LocalRepo1           Contoso Script example
```

<span data-ttu-id="14288-111">Cette commande recherche tous les scripts disponibles.</span><span class="sxs-lookup"><span data-stu-id="14288-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="14288-112">Exemple 2 : Rechercher un script par nom</span><span class="sxs-lookup"><span data-stu-id="14288-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="14288-113">Cette commande recherche le script nommé start-WFContosoServer.</span><span class="sxs-lookup"><span data-stu-id="14288-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="14288-114">Exemple 3 : Rechercher un script par nom, version requise et à partir d’un référentiel spécifié</span><span class="sxs-lookup"><span data-stu-id="14288-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="14288-115">Cette commande recherche un script par nom et la version requise dans le référentiel LocalRepo01.</span><span class="sxs-lookup"><span data-stu-id="14288-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="14288-116">Exemple 4 : Rechercher un script et mettre en forme la sortie sous forme de liste</span><span class="sxs-lookup"><span data-stu-id="14288-116">Example 4: Find a script and format the output as a list</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo1" | Format-List * -Force
Name                       : Required-Script2
Version                    : 2.0
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/14/2015 2:37:01 PM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {, Tag1, Tag2, Tag-Required-Script2-2.0...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : C:\MyLocalRepo
Repository                 : LocalRepo01
PackageManagementProvider  : NuGet
```

<span data-ttu-id="14288-117">Cette commande recherche Required-Script2 dans le référentiel LocalRepo1, puis passe l’objet **PSRepositoryItemInfo** résultant à l’applet de commande Format-List.</span><span class="sxs-lookup"><span data-stu-id="14288-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="14288-118">Exemple 5 : Rechercher un script dans la plage de versions spécifiée</span><span class="sxs-lookup"><span data-stu-id="14288-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="14288-119">Cette commande recherche toutes les versions de RequiredScript2 entre les versions 2,1 et 2,5 dans le référentiel LocalRepo1.</span><span class="sxs-lookup"><span data-stu-id="14288-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="14288-120">Exemple 6 : Rechercher toutes les versions d’un script</span><span class="sxs-lookup"><span data-stu-id="14288-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="14288-121">Cette commande recherche toutes les versions de required-Script02.</span><span class="sxs-lookup"><span data-stu-id="14288-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="14288-122">Exemple 7 : Rechercher un script et ses dépendances</span><span class="sxs-lookup"><span data-stu-id="14288-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="14288-123">Cette commande recherche un script et ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="14288-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="14288-124">Exemple 8 : Rechercher des scripts avec la balise spécifiée</span><span class="sxs-lookup"><span data-stu-id="14288-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="14288-125">Cette commande recherche les scripts qui ont la balise : Étiquette1 dans le référentiel LocalRepo1</span><span class="sxs-lookup"><span data-stu-id="14288-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="14288-126">Exemple 9 : Rechercher les scripts avec le nom de commande spécifié</span><span class="sxs-lookup"><span data-stu-id="14288-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="14288-127">Cette commande recherche un script qui contient le nom de commande spécifié.</span><span class="sxs-lookup"><span data-stu-id="14288-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="14288-128">Exemple 10 : Rechercher des scripts avec des flux de travail</span><span class="sxs-lookup"><span data-stu-id="14288-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="14288-129">Cette commande recherche les scripts de workflow dans le référentiel LocalRepo1.</span><span class="sxs-lookup"><span data-stu-id="14288-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="14288-130">Exemple 11 : Rechercher des scripts à l’aide de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="14288-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="14288-131">Cette commande utilise le caractère générique (\*) pour rechercher les scripts qui commencent par le script requis.</span><span class="sxs-lookup"><span data-stu-id="14288-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="14288-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14288-132">PARAMETERS</span></span>

### <span data-ttu-id="14288-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="14288-133">-AllowPrerelease</span></span>

<span data-ttu-id="14288-134">Comprend dans les scripts de résultats marqués comme version préliminaire.</span><span class="sxs-lookup"><span data-stu-id="14288-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="14288-135">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="14288-135">-AllVersions</span></span>

<span data-ttu-id="14288-136">Indique que cette opération recherche toutes les versions de script.</span><span class="sxs-lookup"><span data-stu-id="14288-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="14288-137">-Command</span><span class="sxs-lookup"><span data-stu-id="14288-137">-Command</span></span>

<span data-ttu-id="14288-138">Spécifie un tableau de commandes à rechercher dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="14288-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="14288-139">Une commande peut être une fonction ou un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="14288-139">A command can be a function or workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14288-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="14288-140">-Credential</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14288-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="14288-141">-Filter</span></span>

<span data-ttu-id="14288-142">Recherche des scripts en fonction de la syntaxe de recherche spécifique au fournisseur PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="14288-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14288-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="14288-143">-IncludeDependencies</span></span>

<span data-ttu-id="14288-144">Indique que cette opération obtient tous les scripts qui dépendent du script spécifié dans le paramètre *Name* .</span><span class="sxs-lookup"><span data-stu-id="14288-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="14288-145">-Comprend</span><span class="sxs-lookup"><span data-stu-id="14288-145">-Includes</span></span>

<span data-ttu-id="14288-146">Spécifie le type de script à récupérer.</span><span class="sxs-lookup"><span data-stu-id="14288-146">Specifies type of script to get.</span></span>
<span data-ttu-id="14288-147">Les valeurs acceptables pour ce paramètre sont : function, Workflow.</span><span class="sxs-lookup"><span data-stu-id="14288-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Function, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14288-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="14288-148">-MaximumVersion</span></span>

<span data-ttu-id="14288-149">Spécifie la version maximale ou la plus récente du script à rechercher.</span><span class="sxs-lookup"><span data-stu-id="14288-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="14288-150">Les paramètres *MaximumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="14288-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="14288-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="14288-151">-MinimumVersion</span></span>

<span data-ttu-id="14288-152">Spécifie la version minimale du script à rechercher.</span><span class="sxs-lookup"><span data-stu-id="14288-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="14288-153">Les paramètres *MinimumVersion* et *RequiredVersion* s’excluent mutuellement ; vous ne pouvez pas utiliser les deux paramètres dans la même commande.</span><span class="sxs-lookup"><span data-stu-id="14288-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="14288-154">-Name</span><span class="sxs-lookup"><span data-stu-id="14288-154">-Name</span></span>

<span data-ttu-id="14288-155">Spécifie un tableau de noms de scripts à rechercher.</span><span class="sxs-lookup"><span data-stu-id="14288-155">Specifies an array of names of scripts to find.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="14288-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="14288-156">-Proxy</span></span>

<span data-ttu-id="14288-157">Spécifie un serveur proxy pour la demande, au lieu de se connecter directement à la ressource Internet.</span><span class="sxs-lookup"><span data-stu-id="14288-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14288-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="14288-158">-ProxyCredential</span></span>

<span data-ttu-id="14288-159">Spécifie un compte d'utilisateur qui a l'autorisation d'utiliser le serveur proxy spécifié par le paramètre **Proxy** .</span><span class="sxs-lookup"><span data-stu-id="14288-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14288-160">-Référentiel</span><span class="sxs-lookup"><span data-stu-id="14288-160">-Repository</span></span>

<span data-ttu-id="14288-161">Spécifie le nom convivial d’un référentiel inscrit en exécutant Register-PSRepository.</span><span class="sxs-lookup"><span data-stu-id="14288-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14288-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="14288-162">-RequiredVersion</span></span>

<span data-ttu-id="14288-163">Spécifie le numéro de version exact du script à rechercher.</span><span class="sxs-lookup"><span data-stu-id="14288-163">Specifies the exact version number of the script to find.</span></span>

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

### <span data-ttu-id="14288-164">-Tag</span><span class="sxs-lookup"><span data-stu-id="14288-164">-Tag</span></span>

<span data-ttu-id="14288-165">Spécifie un tableau de balises.</span><span class="sxs-lookup"><span data-stu-id="14288-165">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14288-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14288-166">CommonParameters</span></span>

<span data-ttu-id="14288-167">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14288-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14288-168">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="14288-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14288-169">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="14288-169">INPUTS</span></span>

### <span data-ttu-id="14288-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="14288-170">System.String[]</span></span>

### <span data-ttu-id="14288-171">System.String</span><span class="sxs-lookup"><span data-stu-id="14288-171">System.String</span></span>

### <span data-ttu-id="14288-172">System.Uri</span><span class="sxs-lookup"><span data-stu-id="14288-172">System.Uri</span></span>

### <span data-ttu-id="14288-173">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="14288-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="14288-174">SORTIES</span><span class="sxs-lookup"><span data-stu-id="14288-174">OUTPUTS</span></span>

### <span data-ttu-id="14288-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="14288-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="14288-176">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="14288-176">NOTES</span></span>

## <span data-ttu-id="14288-177">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="14288-177">RELATED LINKS</span></span>

[<span data-ttu-id="14288-178">Install-Script</span><span class="sxs-lookup"><span data-stu-id="14288-178">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="14288-179">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="14288-179">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="14288-180">Save-Script</span><span class="sxs-lookup"><span data-stu-id="14288-180">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="14288-181">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="14288-181">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="14288-182">Update-Script</span><span class="sxs-lookup"><span data-stu-id="14288-182">Update-Script</span></span>](Update-Script.md)
