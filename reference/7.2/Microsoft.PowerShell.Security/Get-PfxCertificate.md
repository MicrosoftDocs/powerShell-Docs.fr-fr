---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603891"
---
# <span data-ttu-id="b7aa3-102">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="b7aa3-102">Get-PfxCertificate</span></span>

## <span data-ttu-id="b7aa3-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="b7aa3-103">SYNOPSIS</span></span>
<span data-ttu-id="b7aa3-104">Obtient des informations sur les fichiers de certificat PFX sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-104">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="b7aa3-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="b7aa3-105">SYNTAX</span></span>

### <span data-ttu-id="b7aa3-106">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="b7aa3-106">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="b7aa3-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7aa3-107">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="b7aa3-108">Description</span><span class="sxs-lookup"><span data-stu-id="b7aa3-108">DESCRIPTION</span></span>

<span data-ttu-id="b7aa3-109">L' `Get-PfxCertificate` applet de commande obtient un objet représentant chaque fichier de certificat pfx spécifié.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-109">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="b7aa3-110">Un fichier PFX contient à la fois le certificat et une clé privée.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-110">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="b7aa3-111">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="b7aa3-111">EXAMPLES</span></span>

### <span data-ttu-id="b7aa3-112">Exemple 1 : obtenir un certificat PFX</span><span class="sxs-lookup"><span data-stu-id="b7aa3-112">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="b7aa3-113">Cette commande obtient des informations sur le fichier de certificat test. pfx sur le système.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-113">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="b7aa3-114">Exemple 2 : obtenir un certificat PFX à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="b7aa3-114">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="b7aa3-115">Cette commande obtient un fichier de certificat PFX de l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-115">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="b7aa3-116">Il utilise `Invoke-Command` pour exécuter une `Get-PfxCertificate` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-116">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="b7aa3-117">Lorsque le fichier de certificat PFX n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-117">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="b7aa3-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7aa3-118">PARAMETERS</span></span>

### <span data-ttu-id="b7aa3-119">-FilePath</span><span class="sxs-lookup"><span data-stu-id="b7aa3-119">-FilePath</span></span>

<span data-ttu-id="b7aa3-120">Spécifie le chemin d’accès complet au fichier PFX du fichier sécurisé.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-120">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="b7aa3-121">Si vous spécifiez une valeur pour ce paramètre, il n’est pas nécessaire de taper `-FilePath` au niveau de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-121">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b7aa3-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7aa3-122">-LiteralPath</span></span>

<span data-ttu-id="b7aa3-123">Chemin d’accès complet au fichier PFX du fichier sécurisé.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-123">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="b7aa3-124">Contrairement à **FilePath**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-124">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b7aa3-125">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b7aa3-126">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="b7aa3-127">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-127">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b7aa3-128">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="b7aa3-128">-NoPromptForPassword</span></span>

<span data-ttu-id="b7aa3-129">Supprime la demande d’un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-129">Suppresses prompting for a password.</span></span>

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

### <span data-ttu-id="b7aa3-130">-Mot de passe</span><span class="sxs-lookup"><span data-stu-id="b7aa3-130">-Password</span></span>

<span data-ttu-id="b7aa3-131">Spécifie un mot de passe requis pour accéder à un `.pfx` fichier de certificat.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-131">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="b7aa3-132">Ce paramètre a été introduit dans PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-132">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="b7aa3-133">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="b7aa3-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7aa3-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7aa3-134">CommonParameters</span></span>

<span data-ttu-id="b7aa3-135">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7aa3-136">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b7aa3-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7aa3-137">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="b7aa3-137">INPUTS</span></span>

### <span data-ttu-id="b7aa3-138">System.String</span><span class="sxs-lookup"><span data-stu-id="b7aa3-138">System.String</span></span>

<span data-ttu-id="b7aa3-139">Vous pouvez diriger une chaîne qui contient un chemin d’accès de fichier vers `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="b7aa3-139">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="b7aa3-140">SORTIES</span><span class="sxs-lookup"><span data-stu-id="b7aa3-140">OUTPUTS</span></span>

### <span data-ttu-id="b7aa3-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="b7aa3-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="b7aa3-142">`Get-PfxCertificate` retourne un objet pour chaque certificat qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-142">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="b7aa3-143">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="b7aa3-143">NOTES</span></span>

<span data-ttu-id="b7aa3-144">Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Get-PfxCertificate` commande à distance et que le fichier de certificat pfx n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.</span><span class="sxs-lookup"><span data-stu-id="b7aa3-144">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="b7aa3-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="b7aa3-145">RELATED LINKS</span></span>

[<span data-ttu-id="b7aa3-146">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b7aa3-146">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="b7aa3-147">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b7aa3-147">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

