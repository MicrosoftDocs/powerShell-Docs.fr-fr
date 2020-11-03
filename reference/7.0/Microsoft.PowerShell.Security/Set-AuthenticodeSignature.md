---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: b246e316c209cd66602967d3ad41b03758057192
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201901"
---
# <span data-ttu-id="36280-103">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="36280-103">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="36280-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="36280-104">SYNOPSIS</span></span>
<span data-ttu-id="36280-105">Ajoute une signature [Authenticode](/windows-hardware/drivers/install/authenticode) à un script PowerShell ou à un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="36280-105">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="36280-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36280-106">SYNTAX</span></span>

### <span data-ttu-id="36280-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="36280-107">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36280-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="36280-108">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="36280-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="36280-109">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="36280-110">Description</span><span class="sxs-lookup"><span data-stu-id="36280-110">DESCRIPTION</span></span>

<span data-ttu-id="36280-111">L' `Set-AuthenticodeSignature` applet de commande ajoute une signature Authenticode à n’importe quel fichier qui prend en charge le package d’interface de sujet (SIP).</span><span class="sxs-lookup"><span data-stu-id="36280-111">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="36280-112">Dans un fichier de script PowerShell, la signature prend la forme d’un bloc de texte qui indique la fin des instructions qui sont exécutées dans le script.</span><span class="sxs-lookup"><span data-stu-id="36280-112">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="36280-113">S'il existe une signature dans le fichier lors de l'exécution de cette applet de commande, cette signature est supprimée.</span><span class="sxs-lookup"><span data-stu-id="36280-113">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="36280-114">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="36280-114">EXAMPLES</span></span>

### <span data-ttu-id="36280-115">Exemple 1 : signer un script à l’aide d’un certificat du magasin de certificats local</span><span class="sxs-lookup"><span data-stu-id="36280-115">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="36280-116">Ces commandes récupèrent un certificat de signature de code auprès du fournisseur de certificats PowerShell et l’utilisent pour signer un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36280-116">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="36280-117">La première commande utilise l' `Get-ChildItem` applet de commande et le fournisseur de certificats PowerShell pour récupérer les certificats dans le `Cert:\CurrentUser\My` sous-répertoire du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="36280-117">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="36280-118">Le `Cert:` lecteur est le lecteur exposé par le fournisseur de certificats.</span><span class="sxs-lookup"><span data-stu-id="36280-118">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="36280-119">Le paramètre **CodeSigningCert** , qui est pris en charge uniquement par le fournisseur de certificats, limite les certificats récupérés à ceux avec l’autorité de signature de code.</span><span class="sxs-lookup"><span data-stu-id="36280-119">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="36280-120">La commande stocke le résultat dans la `$cert` variable.</span><span class="sxs-lookup"><span data-stu-id="36280-120">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="36280-121">La deuxième commande utilise l' `Set-AuthenticodeSignature` applet de commande pour signer le `PSTestInternet2.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="36280-121">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="36280-122">Elle utilise le paramètre **filePath** pour spécifier le nom du script et le paramètre **Certificate** pour spécifier que le certificat est stocké dans la `$cert` variable.</span><span class="sxs-lookup"><span data-stu-id="36280-122">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="36280-123">L’utilisation du paramètre **CodeSigningCert** avec `Get-ChildItem` renvoie uniquement les certificats qui ont une autorité de signature de code et qui contiennent une clé privée.</span><span class="sxs-lookup"><span data-stu-id="36280-123">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="36280-124">S’il n’y a pas de clé privée, les certificats ne peuvent pas être utilisés pour la signature.</span><span class="sxs-lookup"><span data-stu-id="36280-124">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="36280-125">Exemple 2 : signer un script à l’aide d’un certificat à partir d’un fichier PFX</span><span class="sxs-lookup"><span data-stu-id="36280-125">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="36280-126">Ces commandes utilisent l' `Get-PfxCertificate` applet de commande pour charger un certificat de signature de code.</span><span class="sxs-lookup"><span data-stu-id="36280-126">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="36280-127">Ensuite, utilisez-le pour signer un script PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36280-127">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="36280-128">La première commande utilise l' `Get-PfxCertificate` applet de commande pour charger le certificat C:\Test\MySign.pfx dans la `$cert` variable.</span><span class="sxs-lookup"><span data-stu-id="36280-128">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="36280-129">La deuxième commande utilise `Set-AuthenticodeSignature` pour signer le script.</span><span class="sxs-lookup"><span data-stu-id="36280-129">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="36280-130">Le paramètre **filePath** de `Set-AuthenticodeSignature` spécifie le chemin d’accès au fichier de script en cours de signature et le paramètre **CERT** passe la `$cert` variable contenant le certificat à `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="36280-130">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="36280-131">Si le fichier de certificat est protégé par un mot de passe, PowerShell vous invite à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="36280-131">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="36280-132">Exemple 3 : ajouter une signature qui comprend l’autorité racine</span><span class="sxs-lookup"><span data-stu-id="36280-132">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="36280-133">Cette commande ajoute une signature numérique qui inclut l'autorité racine dans la chaîne d'approbation, et elle est signée par un serveur d'horodatage tiers.</span><span class="sxs-lookup"><span data-stu-id="36280-133">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="36280-134">La commande utilise le paramètre **filePath** pour spécifier le script en cours de signature et le paramètre **Certificate** pour spécifier le certificat qui est enregistré dans la `$cert` variable.</span><span class="sxs-lookup"><span data-stu-id="36280-134">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="36280-135">Elle utilise le paramètre **IncludeChain** pour inclure toutes les signatures dans la chaîne d’approbation, y compris l’autorité racine.</span><span class="sxs-lookup"><span data-stu-id="36280-135">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="36280-136">Elle utilise également le paramètre **TimeStampServer** pour ajouter un horodatage à la signature.</span><span class="sxs-lookup"><span data-stu-id="36280-136">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="36280-137">Cela empêche l'échec du script quand le certificat expire.</span><span class="sxs-lookup"><span data-stu-id="36280-137">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="36280-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36280-138">PARAMETERS</span></span>

### <span data-ttu-id="36280-139">-Certificat</span><span class="sxs-lookup"><span data-stu-id="36280-139">-Certificate</span></span>

<span data-ttu-id="36280-140">Spécifie le certificat qui sera utilisé pour signer le script ou le fichier.</span><span class="sxs-lookup"><span data-stu-id="36280-140">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="36280-141">Entrez une variable qui stocke un objet qui représente le certificat ou une expression qui obtient le certificat.</span><span class="sxs-lookup"><span data-stu-id="36280-141">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="36280-142">Pour rechercher un certificat, utilisez `Get-PfxCertificate` ou utilisez l' `Get-ChildItem` applet de commande dans le lecteur de certificat `Cert:` .</span><span class="sxs-lookup"><span data-stu-id="36280-142">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="36280-143">Si le certificat n’est pas valide ou n’a pas d' `code-signing` autorité, la commande échoue.</span><span class="sxs-lookup"><span data-stu-id="36280-143">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36280-144">-FilePath</span><span class="sxs-lookup"><span data-stu-id="36280-144">-FilePath</span></span>

<span data-ttu-id="36280-145">Spécifie le chemin d'accès à un fichier qui est en cours de signature.</span><span class="sxs-lookup"><span data-stu-id="36280-145">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36280-146">-Force</span><span class="sxs-lookup"><span data-stu-id="36280-146">-Force</span></span>

<span data-ttu-id="36280-147">Permet à l'applet de commande d'ajouter une signature à un fichier en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="36280-147">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="36280-148">Même en utilisant le paramètre **force** , l’applet de commande ne peut pas remplacer les restrictions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="36280-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36280-149">-HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="36280-149">-HashAlgorithm</span></span>

<span data-ttu-id="36280-150">Spécifie l'algorithme de hachage que Windows utilise pour calculer la signature numérique du fichier.</span><span class="sxs-lookup"><span data-stu-id="36280-150">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="36280-151">Pour PowerShell 3,0, la valeur par défaut est SHA256, qui est l’algorithme de hachage par défaut de Windows.</span><span class="sxs-lookup"><span data-stu-id="36280-151">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="36280-152">Pour PowerShell 2,0, la valeur par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="36280-152">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="36280-153">Les fichiers qui sont signés avec un algorithme de hachage différent peuvent ne pas être reconnus sur d'autres systèmes.</span><span class="sxs-lookup"><span data-stu-id="36280-153">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="36280-154">Les algorithmes pris en charge dépendent de la version du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="36280-154">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="36280-155">Pour obtenir la liste des valeurs possibles, consultez [struct HashAlgorithmName](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span><span class="sxs-lookup"><span data-stu-id="36280-155">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36280-156">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="36280-156">-IncludeChain</span></span>

<span data-ttu-id="36280-157">Détermine les certificats de la chaîne d'approbation des certificats qui sont inclus dans la signature numérique.</span><span class="sxs-lookup"><span data-stu-id="36280-157">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="36280-158">**NotRoot** est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="36280-158">**NotRoot** is the default.</span></span>

<span data-ttu-id="36280-159">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="36280-159">Valid values are:</span></span>

- <span data-ttu-id="36280-160">Signataire : comprend uniquement le certificat du signataire.</span><span class="sxs-lookup"><span data-stu-id="36280-160">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="36280-161">NotRoot : comprend tous les certificats dans la chaîne de certificats, à l’exception de l’autorité racine.</span><span class="sxs-lookup"><span data-stu-id="36280-161">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="36280-162">All : comprend tous les certificats dans la chaîne de certificats.</span><span class="sxs-lookup"><span data-stu-id="36280-162">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36280-163">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="36280-163">-TimestampServer</span></span>

<span data-ttu-id="36280-164">Utilise le serveur d'horodatage spécifié pour ajouter un horodatage à la signature.</span><span class="sxs-lookup"><span data-stu-id="36280-164">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="36280-165">Tapez l'URL du serveur d'horodatage sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="36280-165">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="36280-166">L'horodatage représente l'heure exacte à laquelle le certificat a été ajouté au fichier.</span><span class="sxs-lookup"><span data-stu-id="36280-166">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="36280-167">Un horodatage empêche le script d'échouer si le certificat expire, car les utilisateurs et programmes peuvent vérifier que le certificat était valide au moment de la signature.</span><span class="sxs-lookup"><span data-stu-id="36280-167">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

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

### <span data-ttu-id="36280-168">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="36280-168">-LiteralPath</span></span>

<span data-ttu-id="36280-169">Spécifie le chemin d'accès à un fichier qui est en cours de signature.</span><span class="sxs-lookup"><span data-stu-id="36280-169">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="36280-170">Contrairement à **FilePath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="36280-170">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="36280-171">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="36280-171">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="36280-172">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="36280-172">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="36280-173">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="36280-173">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36280-174">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="36280-174">-SourcePathOrExtension</span></span>

<span data-ttu-id="36280-175">Chemin du fichier ou type de fichier du contenu pour lequel la signature numérique est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="36280-175">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="36280-176">Ce paramètre est utilisé avec le **contenu** où le contenu du fichier est passé en tant que tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="36280-176">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36280-177">-Contenu</span><span class="sxs-lookup"><span data-stu-id="36280-177">-Content</span></span>

<span data-ttu-id="36280-178">Contenu d’un fichier sous la forme d’un tableau d’octets pour lequel la signature numérique est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="36280-178">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="36280-179">Ce paramètre doit être utilisé avec le paramètre **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="36280-179">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="36280-180">Le contenu du fichier doit être au format Unicode (UTF-16LE).</span><span class="sxs-lookup"><span data-stu-id="36280-180">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36280-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="36280-181">-Confirm</span></span>

<span data-ttu-id="36280-182">Vous demande une confirmation avant d’exécuter l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36280-182">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="36280-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="36280-183">-WhatIf</span></span>

<span data-ttu-id="36280-184">Montre ce qui se passe en cas d’exécution de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="36280-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="36280-185">L’applet de commande n’est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="36280-185">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="36280-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36280-186">CommonParameters</span></span>

<span data-ttu-id="36280-187">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36280-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36280-188">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="36280-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36280-189">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="36280-189">INPUTS</span></span>

### <span data-ttu-id="36280-190">System.String</span><span class="sxs-lookup"><span data-stu-id="36280-190">System.String</span></span>

<span data-ttu-id="36280-191">Vous pouvez diriger une chaîne qui contient le chemin d’accès du fichier vers `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="36280-191">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="36280-192">SORTIES</span><span class="sxs-lookup"><span data-stu-id="36280-192">OUTPUTS</span></span>

### <span data-ttu-id="36280-193">System. Management. Automation. signature</span><span class="sxs-lookup"><span data-stu-id="36280-193">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="36280-194">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="36280-194">NOTES</span></span>

## <span data-ttu-id="36280-195">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="36280-195">RELATED LINKS</span></span>

[<span data-ttu-id="36280-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="36280-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="36280-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="36280-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="36280-198">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="36280-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="36280-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="36280-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="36280-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="36280-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="36280-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="36280-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
