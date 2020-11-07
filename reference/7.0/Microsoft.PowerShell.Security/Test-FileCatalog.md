---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 3219656c5c20372ac7fe999f4aafffa23b81be1a
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347021"
---
# <span data-ttu-id="20d8f-103">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="20d8f-103">Test-FileCatalog</span></span>

## <span data-ttu-id="20d8f-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="20d8f-104">SYNOPSIS</span></span>
<span data-ttu-id="20d8f-105">`Test-FileCatalog` valide si les hachages contenus dans un fichier catalogue (. cat) correspondent aux hachages des fichiers réels afin de valider leur authenticité.</span><span class="sxs-lookup"><span data-stu-id="20d8f-105">`Test-FileCatalog` validates whether the hashes contained in a catalog file (.cat) matches the hashes of the actual files in order to validate their authenticity.</span></span>

<span data-ttu-id="20d8f-106">Cette applet de commande est uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="20d8f-106">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="20d8f-107">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="20d8f-107">SYNTAX</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20d8f-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="20d8f-108">DESCRIPTION</span></span>

<span data-ttu-id="20d8f-109">`Test-FileCatalog` valide l’authenticité des fichiers en comparant les hachages de fichier d’un fichier catalogue (. cat) avec les hachages des fichiers réels sur le disque.</span><span class="sxs-lookup"><span data-stu-id="20d8f-109">`Test-FileCatalog` validates the authenticity of files by comparing the file hashes of a catalog file (.cat) with the hashes of actual files on disk.</span></span> <span data-ttu-id="20d8f-110">Si elle détecte des incompatibilités, elle retourne l’État ValidationFailed.</span><span class="sxs-lookup"><span data-stu-id="20d8f-110">If it detects any mismatches, it returns the status as ValidationFailed.</span></span> <span data-ttu-id="20d8f-111">Les utilisateurs peuvent récupérer toutes ces informations à l’aide du paramètre -Detailed.</span><span class="sxs-lookup"><span data-stu-id="20d8f-111">Users can retrieve all this information by using the -Detailed parameter.</span></span> <span data-ttu-id="20d8f-112">Il affiche également l’état de signature du catalogue dans la propriété signature, ce qui revient à appeler `Get-AuthenticodeSignature` l’applet de commande sur le fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="20d8f-112">It also displays signing status of catalog in Signature property which is equivalent to calling `Get-AuthenticodeSignature` cmdlet on the catalog file.</span></span> <span data-ttu-id="20d8f-113">Les utilisateurs peuvent également ignorer des fichiers lors de la validation à l’aide du paramètre -FilesToSkip.</span><span class="sxs-lookup"><span data-stu-id="20d8f-113">Users can also skip any file during validation by using the -FilesToSkip parameter.</span></span>

<span data-ttu-id="20d8f-114">Cette applet de commande est uniquement prise en charge sur Windows.</span><span class="sxs-lookup"><span data-stu-id="20d8f-114">This cmdlet is only supported on Windows.</span></span>

## <span data-ttu-id="20d8f-115">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="20d8f-115">EXAMPLES</span></span>

### <span data-ttu-id="20d8f-116">Exemple 1 : créer et valider un catalogue de fichiers</span><span class="sxs-lookup"><span data-stu-id="20d8f-116">Example 1: Create and validate a file catalog</span></span>

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### <span data-ttu-id="20d8f-117">Exemple 2 : valider un catalogue de fichiers avec une sortie détaillée</span><span class="sxs-lookup"><span data-stu-id="20d8f-117">Example 2: Validate a file catalog with detailed output</span></span>

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
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

## <span data-ttu-id="20d8f-118">PARAMÈTRES</span><span class="sxs-lookup"><span data-stu-id="20d8f-118">PARAMETERS</span></span>

### <span data-ttu-id="20d8f-119">-CatalogFilePath</span><span class="sxs-lookup"><span data-stu-id="20d8f-119">-CatalogFilePath</span></span>

<span data-ttu-id="20d8f-120">Chemin d’accès à un fichier catalogue (. cat) qui contient les hachages à utiliser pour la validation.</span><span class="sxs-lookup"><span data-stu-id="20d8f-120">A path to a catalog file (.cat) that contains the hashes to be used for validation.</span></span>

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

### <span data-ttu-id="20d8f-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20d8f-121">-Confirm</span></span>

<span data-ttu-id="20d8f-122">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20d8f-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="20d8f-123">-Detailed</span><span class="sxs-lookup"><span data-stu-id="20d8f-123">-Detailed</span></span>

<span data-ttu-id="20d8f-124">Retourne plus d’informations un objet plus détaillé `CatalogInformation` qui contient les fichiers testés, leurs hachages attendus/réels et une signature Authenticode du fichier catalogue s’il est signé.</span><span class="sxs-lookup"><span data-stu-id="20d8f-124">Returns more information a more detailed `CatalogInformation` object that contains the files tested, their expected/actual hashes, and an Authenticode signature of the catalog file if it's signed.</span></span>

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

### <span data-ttu-id="20d8f-125">-FilesToSkip</span><span class="sxs-lookup"><span data-stu-id="20d8f-125">-FilesToSkip</span></span>

<span data-ttu-id="20d8f-126">Tableau de chemins d’accès qui ne doivent pas être testés dans le cadre de la validation.</span><span class="sxs-lookup"><span data-stu-id="20d8f-126">An array of paths that should not be tested as part of the validation.</span></span>

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

### <span data-ttu-id="20d8f-127">-Path</span><span class="sxs-lookup"><span data-stu-id="20d8f-127">-Path</span></span>

<span data-ttu-id="20d8f-128">Dossier ou tableau de fichiers qui doit être validé par rapport au fichier catalogue.</span><span class="sxs-lookup"><span data-stu-id="20d8f-128">A folder or array of files that should be validated against the catalog file.</span></span>

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

### <span data-ttu-id="20d8f-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20d8f-129">-WhatIf</span></span>

<span data-ttu-id="20d8f-130">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="20d8f-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="20d8f-131">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="20d8f-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="20d8f-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20d8f-132">CommonParameters</span></span>

<span data-ttu-id="20d8f-133">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20d8f-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20d8f-134">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20d8f-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20d8f-135">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="20d8f-135">INPUTS</span></span>

### <span data-ttu-id="20d8f-136">System. IO. DirectoryInfo [], System. String []</span><span class="sxs-lookup"><span data-stu-id="20d8f-136">System.IO.DirectoryInfo[], System.String[]</span></span>

<span data-ttu-id="20d8f-137">Le pipeline accepte un tableau de chaînes ou d' `DirectoryInfo` objets qui représentent les chemins d’accès aux fichiers qui doivent être validés.</span><span class="sxs-lookup"><span data-stu-id="20d8f-137">The pipeline accepts an array of strings or `DirectoryInfo` objects that represent paths to the files that need to be validated.</span></span>

## <span data-ttu-id="20d8f-138">SORTIES</span><span class="sxs-lookup"><span data-stu-id="20d8f-138">OUTPUTS</span></span>

### <span data-ttu-id="20d8f-139">System. Management. Automation. CatalogValidationStatus</span><span class="sxs-lookup"><span data-stu-id="20d8f-139">System.Management.Automation.CatalogValidationStatus</span></span>

<span data-ttu-id="20d8f-140">Type de retour par défaut contenant la valeur `Valid` ou `ValidationFailed` .</span><span class="sxs-lookup"><span data-stu-id="20d8f-140">The default return type containing a value of either `Valid` or `ValidationFailed`.</span></span>

### <span data-ttu-id="20d8f-141">System. Management. Automation. CatalogInformation</span><span class="sxs-lookup"><span data-stu-id="20d8f-141">System.Management.Automation.CatalogInformation</span></span>

<span data-ttu-id="20d8f-142">Objet plus détaillé retourné lors de l’utilisation `-Detailed` de qui peut être utilisé pour analyser des fichiers spécifiques qui peuvent avoir été validés ou non, les hachages attendus ou trouvés, ainsi que l’algorithme utilisé dans le catalogue.</span><span class="sxs-lookup"><span data-stu-id="20d8f-142">A more detailed object returned when using `-Detailed` which can be used to analyze specific files that may or may not have passed validation, which hashes were expected vs. found, and the algorithm used in the catalog.</span></span>

## <span data-ttu-id="20d8f-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="20d8f-143">NOTES</span></span>

<span data-ttu-id="20d8f-144">Cette applet de commande est disponible uniquement sur les plateformes Windows.</span><span class="sxs-lookup"><span data-stu-id="20d8f-144">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="20d8f-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="20d8f-145">RELATED LINKS</span></span>

[<span data-ttu-id="20d8f-146">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="20d8f-146">New-FileCatalog</span></span>](New-FileCatalog.md)

[<span data-ttu-id="20d8f-147">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="20d8f-147">PowerShellGet</span></span>](/powershell/module/PowerShellGet)
