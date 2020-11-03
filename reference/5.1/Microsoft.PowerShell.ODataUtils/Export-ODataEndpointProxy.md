---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 7550e2df319e5f195e65609ae29ebb00830ec8d2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203433"
---
# <span data-ttu-id="a9e79-103">Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="a9e79-103">Export-ODataEndpointProxy</span></span>

## <span data-ttu-id="a9e79-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a9e79-104">SYNOPSIS</span></span>
<span data-ttu-id="a9e79-105">Génère un module qui contient des applets de commande pour gérer un point de terminaison OData.</span><span class="sxs-lookup"><span data-stu-id="a9e79-105">Generates a module that contains cmdlets to manage an OData endpoint.</span></span>

## <span data-ttu-id="a9e79-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9e79-106">SYNTAX</span></span>

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a9e79-107">Description</span><span class="sxs-lookup"><span data-stu-id="a9e79-107">DESCRIPTION</span></span>

<span data-ttu-id="a9e79-108">L' `Export-ODataEndpointProxy` applet de commande utilise les métadonnées d’un point de terminaison OData pour générer un module qui contient des applets de commande que vous pouvez utiliser pour gérer ce point de terminaison OData.</span><span class="sxs-lookup"><span data-stu-id="a9e79-108">The `Export-ODataEndpointProxy` cmdlet uses the metadata of an OData endpoint to generate a module that contains cmdlets you can use to manage that OData endpoint.</span></span> <span data-ttu-id="a9e79-109">Le module est basé sur CDXML.</span><span class="sxs-lookup"><span data-stu-id="a9e79-109">The module is based on CDXML.</span></span> <span data-ttu-id="a9e79-110">Une fois que cette applet de commande a généré le module, elle enregistre ce module dans le chemin d’accès et le nom de fichier spécifiés par le paramètre **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="a9e79-110">After this cmdlet generates the module, it saves that module to the path and file name specified by the **OutputModule** parameter.</span></span>

<span data-ttu-id="a9e79-111">`Export-ODataEndpointProxy` génère des applets de commande pour les opérations CRUD (Create, Read, Update et Delete), les actions non CRUD et la manipulation d’association.</span><span class="sxs-lookup"><span data-stu-id="a9e79-111">`Export-ODataEndpointProxy` generates cmdlets for create, read, update, and delete (CRUD) operations, non-CRUD actions, and association manipulation.</span></span>

<span data-ttu-id="a9e79-112">`Export-ODataEndpointProxy` génère un fichier CDXML par ressource de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9e79-112">`Export-ODataEndpointProxy` generates one CDXML file per endpoint resource.</span></span> <span data-ttu-id="a9e79-113">Vous pouvez modifier ces fichiers CDXML après la génération du module.</span><span class="sxs-lookup"><span data-stu-id="a9e79-113">You can edit these CDXML files after the module is generated.</span></span> <span data-ttu-id="a9e79-114">Par exemple, si vous souhaitez modifier le nom ou les noms de verbe des applets de commande pour les aligner avec les instructions de dénomination des applets de commande Windows PowerShell, vous pouvez modifier le fichier.</span><span class="sxs-lookup"><span data-stu-id="a9e79-114">For example, if you want to change the noun or verb names of the cmdlets to align with Windows PowerShell cmdlet naming guidelines, you can modify the file.</span></span>

<span data-ttu-id="a9e79-115">Chaque applet de commande dans un module généré doit inclure un paramètre **ConnectionUri** afin de se connecter au point de terminaison géré par le module.</span><span class="sxs-lookup"><span data-stu-id="a9e79-115">Every cmdlet in a generated module must include a **ConnectionURI** parameter in order to connect to the endpoint that the module manages.</span></span>

## <span data-ttu-id="a9e79-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a9e79-116">EXAMPLES</span></span>

### <span data-ttu-id="a9e79-117">Exemple 1 : générer un module pour gérer un point de terminaison de service Web de vente au détail</span><span class="sxs-lookup"><span data-stu-id="a9e79-117">Example 1: Generate a module to manage a retail web service endpoint</span></span>

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

<span data-ttu-id="a9e79-118">Cette commande génère un module pour gérer un point de terminaison de service de vente au détail.</span><span class="sxs-lookup"><span data-stu-id="a9e79-118">This command generates a module to manage a retail service endpoint.</span></span> <span data-ttu-id="a9e79-119">La commande spécifie l’URI du point de terminaison et l’URI des métadonnées de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9e79-119">The command specifies the URI of the endpoint and the URI of the endpoint metadata.</span></span> <span data-ttu-id="a9e79-120">La commande fournit également un chemin de sortie et un nom de module de script comme valeur du paramètre **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="a9e79-120">The command also provides an output path and script module name as the value of the **OutputModule** parameter.</span></span> <span data-ttu-id="a9e79-121">Pour la valeur du paramètre **ResourceNameMapping** , la commande fournit une Hashtable qui mappe le nom de la collection de ressources au nom souhaité pour le jeu d’applets de commande.</span><span class="sxs-lookup"><span data-stu-id="a9e79-121">For the value of the **ResourceNameMapping** parameter, the command provides a hashtable that maps the resource collection name to the desired noun for the cmdlet set.</span></span> <span data-ttu-id="a9e79-122">Dans cet exemple, Products est le nom de la collection de ressources et la **marchandise** est le substantif.</span><span class="sxs-lookup"><span data-stu-id="a9e79-122">In this example, Products is the resource collection name and **Merchandise** is the noun.</span></span> <span data-ttu-id="a9e79-123">Pour autoriser les connexions à des sites non-SSL, HTTP, par opposition à HTTPs, ajoutez le paramètre **AllowUnsecureConnection** .</span><span class="sxs-lookup"><span data-stu-id="a9e79-123">To allow connections to non-SSL sites, HTTP, as opposed to HTTPS, add the **AllowUnsecureConnection** parameter.</span></span>

## <span data-ttu-id="a9e79-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9e79-124">PARAMETERS</span></span>

### <span data-ttu-id="a9e79-125">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="a9e79-125">-AllowClobber</span></span>

<span data-ttu-id="a9e79-126">Indique que cette applet de commande remplace un module existant.</span><span class="sxs-lookup"><span data-stu-id="a9e79-126">Indicates that this cmdlet replaces an existing module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-127">-AllowUnsecureConnection</span><span class="sxs-lookup"><span data-stu-id="a9e79-127">-AllowUnsecureConnection</span></span>

<span data-ttu-id="a9e79-128">Indique que ce module peut se connecter aux URI qui ne sont pas sécurisés par SSL.</span><span class="sxs-lookup"><span data-stu-id="a9e79-128">Indicates that this module can connect to URIs that are not SSL-secured.</span></span> <span data-ttu-id="a9e79-129">Le module peut gérer des sites HTTP en plus des sites HTTPs.</span><span class="sxs-lookup"><span data-stu-id="a9e79-129">The module can manage HTTP sites in addition to HTTPS sites.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-130">-CmdletAdapter</span><span class="sxs-lookup"><span data-stu-id="a9e79-130">-CmdletAdapter</span></span>

<span data-ttu-id="a9e79-131">Spécifie l’adaptateur d’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9e79-131">Specifies the cmdlet adapter.</span></span> <span data-ttu-id="a9e79-132">Les valeurs acceptables pour ce paramètre sont les suivantes : ODataAdapter et NetworkControllerAdapter.</span><span class="sxs-lookup"><span data-stu-id="a9e79-132">The acceptable values for this parameter are: ODataAdapter and NetworkControllerAdapter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-133">-CreateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="a9e79-133">-CreateRequestMethod</span></span>

<span data-ttu-id="a9e79-134">Spécifie la méthode de demande.</span><span class="sxs-lookup"><span data-stu-id="a9e79-134">Specifies the request method.</span></span> <span data-ttu-id="a9e79-135">Les valeurs acceptables pour ce paramètre sont les suivantes : PUT, poster et PATCH.</span><span class="sxs-lookup"><span data-stu-id="a9e79-135">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="a9e79-136">-Credential</span></span>

<span data-ttu-id="a9e79-137">Spécifie un compte d’utilisateur qui a accès au point de terminaison OData.</span><span class="sxs-lookup"><span data-stu-id="a9e79-137">Specifies a user account that has access to the OData endpoint.</span></span> <span data-ttu-id="a9e79-138">La valeur par défaut est l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="a9e79-138">The default value is the current user.</span></span> <span data-ttu-id="a9e79-139">Si un ordinateur distant exécute Windows Vista ou une version ultérieure du système d’exploitation Windows, l’applet de commande vous invite à entrer des informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a9e79-139">If a remote computer runs Windows Vista or a later release of the Windows operating system, the cmdlet prompts you for credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-140">-CustomData</span><span class="sxs-lookup"><span data-stu-id="a9e79-140">-CustomData</span></span>

<span data-ttu-id="a9e79-141">Spécifie une table de hachage de données personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a9e79-141">Specifies a hash table of custom data.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-142">-Force</span><span class="sxs-lookup"><span data-stu-id="a9e79-142">-Force</span></span>

<span data-ttu-id="a9e79-143">Indique que cette applet de commande remplace un module généré existant du même nom dans un dossier existant `Modules` .</span><span class="sxs-lookup"><span data-stu-id="a9e79-143">Indicates that this cmdlet overwrites an existing generated module of the same name in an existing `Modules` folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-144">-En-têtes</span><span class="sxs-lookup"><span data-stu-id="a9e79-144">-Headers</span></span>

<span data-ttu-id="a9e79-145">Spécifie les en-têtes de la demande web.</span><span class="sxs-lookup"><span data-stu-id="a9e79-145">Specifies the headers of the web request.</span></span> <span data-ttu-id="a9e79-146">Entrez une table de hachage ou un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="a9e79-146">Enter a hash table or dictionary.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-147">-MetadataUri</span><span class="sxs-lookup"><span data-stu-id="a9e79-147">-MetadataUri</span></span>

<span data-ttu-id="a9e79-148">Spécifie l’URI des métadonnées du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9e79-148">Specifies the URI of the metadata of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-149">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="a9e79-149">-OutputModule</span></span>

<span data-ttu-id="a9e79-150">Spécifie le chemin d’accès et le nom du module dans lequel cette applet de commande enregistre le module de commandes proxy généré.</span><span class="sxs-lookup"><span data-stu-id="a9e79-150">Specifies the path and module name to which this cmdlet saves the generated module of proxy commands.</span></span>

<span data-ttu-id="a9e79-151">Cette applet de commande copie un module binaire, un manifeste de module et un fichier de mise en forme, le cas échéant, dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a9e79-151">This cmdlet copies a binary module, module manifest, and formatting file, if applicable, to the specified folder.</span></span> <span data-ttu-id="a9e79-152">Si vous spécifiez uniquement le nom du module, `Export-ODataEndpointProxy` enregistre le module dans le `$home\Documents\WindowsPowerShell\Modules` dossier.</span><span class="sxs-lookup"><span data-stu-id="a9e79-152">If you specify only the name of the module, `Export-ODataEndpointProxy` saves the module in the `$home\Documents\WindowsPowerShell\Modules` folder.</span></span> <span data-ttu-id="a9e79-153">Si vous spécifiez un chemin d’accès, l’applet de commande crée le dossier de module dans ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="a9e79-153">If you specify a path, the cmdlet creates the module folder in that path.</span></span>

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

### <span data-ttu-id="a9e79-154">-ResourceNameMapping</span><span class="sxs-lookup"><span data-stu-id="a9e79-154">-ResourceNameMapping</span></span>

<span data-ttu-id="a9e79-155">Spécifie une Hashtable qui contient des mappages qui vous permettent de personnaliser les applets de commande générées.</span><span class="sxs-lookup"><span data-stu-id="a9e79-155">Specifies a hashtable that contains mappings that let you customize the generated cmdlets.</span></span> <span data-ttu-id="a9e79-156">Dans cette Hashtable, le nom de la collection de ressources est la clé.</span><span class="sxs-lookup"><span data-stu-id="a9e79-156">In this hashtable, the resource collection name is the key.</span></span> <span data-ttu-id="a9e79-157">Le nom de l’applet de commande souhaitée est la valeur.</span><span class="sxs-lookup"><span data-stu-id="a9e79-157">The desired cmdlet noun is the value.</span></span>

<span data-ttu-id="a9e79-158">Par exemple, dans la table de hachage `@{Products = 'Merchandise'}` , **Products** est le nom de la collection de ressources qui sert de clé.</span><span class="sxs-lookup"><span data-stu-id="a9e79-158">For example, in the hash table `@{Products = 'Merchandise'}`, **Products** is the resource collection name that serves as the key.</span></span> <span data-ttu-id="a9e79-159">La **marchandise** est le nom de l’applet de commande qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="a9e79-159">**Merchandise** is the resulting cmdlet noun.</span></span> <span data-ttu-id="a9e79-160">Les noms des applets de commande générées peuvent ne pas être alignés sur les instructions de dénomination des applets de commande Windows</span><span class="sxs-lookup"><span data-stu-id="a9e79-160">The generated cmdlet names might not align to Windows PowerShell cmdlet naming guidelines.</span></span> <span data-ttu-id="a9e79-161">Vous pouvez modifier le fichier de ressources CDXML pour modifier les noms des applets de commande après que cette applet de commande a créé le module.</span><span class="sxs-lookup"><span data-stu-id="a9e79-161">You can modify the resource CDXML file to change the cmdlet names after this cmdlet creates the module.</span></span> <span data-ttu-id="a9e79-162">Pour plus d’informations, consultez [instructions de développement fortement encouragées](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span><span class="sxs-lookup"><span data-stu-id="a9e79-162">For more information, see [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-163">-UpdateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="a9e79-163">-UpdateRequestMethod</span></span>

<span data-ttu-id="a9e79-164">Spécifie la méthode de demande de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="a9e79-164">Specifies the update request method.</span></span> <span data-ttu-id="a9e79-165">Les valeurs acceptables pour ce paramètre sont les suivantes : PUT, poster et PATCH.</span><span class="sxs-lookup"><span data-stu-id="a9e79-165">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-166">-URI</span><span class="sxs-lookup"><span data-stu-id="a9e79-166">-Uri</span></span>

<span data-ttu-id="a9e79-167">Spécifie l’URI du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a9e79-167">Specifies the URI of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a9e79-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a9e79-168">-Confirm</span></span>

<span data-ttu-id="a9e79-169">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9e79-169">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a9e79-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a9e79-170">-WhatIf</span></span>

<span data-ttu-id="a9e79-171">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="a9e79-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a9e79-172">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="a9e79-172">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a9e79-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9e79-173">CommonParameters</span></span>

<span data-ttu-id="a9e79-174">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9e79-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9e79-175">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a9e79-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9e79-176">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a9e79-176">INPUTS</span></span>

## <span data-ttu-id="a9e79-177">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a9e79-177">OUTPUTS</span></span>

## <span data-ttu-id="a9e79-178">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a9e79-178">NOTES</span></span>

## <span data-ttu-id="a9e79-179">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a9e79-179">RELATED LINKS</span></span>

<span data-ttu-id="a9e79-180">[Bibliothèque OData](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)</span><span class="sxs-lookup"><span data-stu-id="a9e79-180">[OData Library](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)</span></span>

[<span data-ttu-id="a9e79-181">Qu’est-ce que le protocole OData ?</span><span class="sxs-lookup"><span data-stu-id="a9e79-181">What is the OData Protocol?</span></span>](https://www.odata.org/)

[<span data-ttu-id="a9e79-182">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="a9e79-182">Invoke-RestMethod</span></span>](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
