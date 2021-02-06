---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 0a990b1c0c46cda06c5239a4c8fde55b29296376
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "99597148"
---
# <span data-ttu-id="5ff88-102">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5ff88-102">Test-FileCatalog</span></span>

## <span data-ttu-id="5ff88-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="5ff88-103">SYNOPSIS</span></span>
<span data-ttu-id="5ff88-104">`Test-FileCatalog` valide si les hachages contenus dans un fichier catalogue (. cat) correspondent aux hachages des fichiers réels afin de valider leur authenticité.</span><span class="sxs-lookup"><span data-stu-id="5ff88-104">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="5ff88-105">Cette applet de commande est uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="5ff88-105">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="5ff88-106">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="5ff88-106">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5ff88-107">Description</span><span class="sxs-lookup"><span data-stu-id="5ff88-107">DESCRIPTION</span></span>

<span data-ttu-id="5ff88-108">`Test-FileCatalog` valide l’authenticité des fichiers en comparant les hachages de fichier d’un fichier catalogue (. cat) avec les hachages des fichiers réels sur le disque.</span><span class="sxs-lookup"><span data-stu-id="5ff88-108">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="5ff88-109">Si elle détecte des incompatibilités, elle retourne l’État ValidationFailed.</span><span class="sxs-lookup"><span data-stu-id="5ff88-109">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="5ff88-110">Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre -Detailed.</span><span class="sxs-lookup"><span data-stu-id="5ff88-110">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="5ff88-111">Il affiche également l’état de signature du catalogue dans la propriété signature, ce qui revient à appeler `Get-AuthenticodeSignature` l’applet de commande sur le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="5ff88-111">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="5ff88-112">Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre -FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="5ff88-112">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="5ff88-113">Cette applet de commande est uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="5ff88-113">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="5ff88-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="5ff88-114">EXAMPLES</span></span>

### <span data-ttu-id="5ff88-115">Exemple 1 : créer et valider un catalogue de fichiers</span><span class="sxs-lookup"><span data-stu-id="5ff88-115">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="5ff88-116">Exemple 2 : valider un catalogue de fichiers avec une sortie détaillée</span><span class="sxs-lookup"><span data-stu-id="5ff88-116">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -Detailed -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## <span data-ttu-id="5ff88-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5ff88-117">PARAMETERS</span></span>

### <span data-ttu-id="5ff88-118">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="5ff88-118">-CatalogFilePath</span></span>

<span data-ttu-id="5ff88-119">Chemin d’accès à un fichier catalogue (. cat) qui contient les hachages à utiliser pour la validation.</span><span class="sxs-lookup"><span data-stu-id="5ff88-119">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

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

### <span data-ttu-id="5ff88-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5ff88-120">-Confirm</span></span>

<span data-ttu-id="5ff88-121">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ff88-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5ff88-122">-Detailed</span><span class="sxs-lookup"><span data-stu-id="5ff88-122">-Detailed</span></span>

<span data-ttu-id="5ff88-123">Retourne plus d’informations un objet plus détaillé `CatalogInformation` qui contient les fichiers testés, leurs hachages attendus/réels et une signature Authenticode du fichier catalogue s’il est signé.</span><span class="sxs-lookup"><span data-stu-id="5ff88-123">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="5ff88-124">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="5ff88-124">-FilesToSkip</span></span>

<span data-ttu-id="5ff88-125">Tableau de chemins d’accès qui ne doivent pas être testés dans le cadre de la validation.</span><span class="sxs-lookup"><span data-stu-id="5ff88-125">An array of paths that should not be tested as part of the validation.</span></span>

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

### <span data-ttu-id="5ff88-126">-Path</span><span class="sxs-lookup"><span data-stu-id="5ff88-126">-Path</span></span>

<span data-ttu-id="5ff88-127">Dossier ou tableau de fichiers qui doit être validé par rapport au fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="5ff88-127">A folder or array of files that should be validated against the catalog file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5ff88-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5ff88-128">-WhatIf</span></span>

<span data-ttu-id="5ff88-129">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="5ff88-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5ff88-130">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="5ff88-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5ff88-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5ff88-131">CommonParameters</span></span>

<span data-ttu-id="5ff88-132">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5ff88-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5ff88-133">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5ff88-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5ff88-134">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="5ff88-134">INPUTS</span></span>

### <span data-ttu-id="5ff88-135">System. IO. DirectoryInfo [], System. String []</span><span class="sxs-lookup"><span data-stu-id="5ff88-135">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="5ff88-136">Le pipeline accepte un tableau de chaînes ou d' `DirectoryInfo` objets qui représentent les chemins d’accès aux fichiers qui doivent être validés.</span><span class="sxs-lookup"><span data-stu-id="5ff88-136">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="5ff88-137">SORTIES</span><span class="sxs-lookup"><span data-stu-id="5ff88-137">OUTPUTS</span></span>

### <span data-ttu-id="5ff88-138">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="5ff88-138">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="5ff88-139">Type de retour par défaut contenant la valeur `Valid` ou `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="5ff88-139">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="5ff88-140">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="5ff88-140">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="5ff88-141">Objet plus détaillé retourné lors de l’utilisation `-Detailed` de qui peut être utilisé pour analyser des fichiers spécifiques qui peuvent avoir été validés ou non, les hachages attendus ou trouvés, ainsi que l’algorithme utilisé dans le catalogue.</span><span class="sxs-lookup"><span data-stu-id="5ff88-141">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="5ff88-142">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="5ff88-142">NOTES</span></span>

<span data-ttu-id="5ff88-143">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="5ff88-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="5ff88-144">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="5ff88-144">RELATED LINKS</span></span>

[<span data-ttu-id="5ff88-145">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="5ff88-145">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="5ff88-146">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5ff88-146">PowerShellGet</span></span>](/powershell/module/PowerShellGet)