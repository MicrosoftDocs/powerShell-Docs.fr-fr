---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 67bb56a50f452475ba12abb2fccaeeaf5785c8b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204737"
---
# <span data-ttu-id="a0cac-103">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="a0cac-103">Get-PfxCertificate</span></span>

## <span data-ttu-id="a0cac-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="a0cac-104">SYNOPSIS</span></span>
<span data-ttu-id="a0cac-105">Obtient des informations sur les fichiers de certificat PFX sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a0cac-105">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="a0cac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0cac-106">SYNTAX</span></span>

### <span data-ttu-id="a0cac-107">ByPath (par défaut)</span><span class="sxs-lookup"><span data-stu-id="a0cac-107">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="a0cac-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0cac-108">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="a0cac-109">Description</span><span class="sxs-lookup"><span data-stu-id="a0cac-109">DESCRIPTION</span></span>

<span data-ttu-id="a0cac-110">L' `Get-PfxCertificate` applet de commande obtient un objet représentant chaque fichier de certificat pfx spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0cac-110">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="a0cac-111">Un fichier PFX contient à la fois le certificat et une clé privée.</span><span class="sxs-lookup"><span data-stu-id="a0cac-111">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="a0cac-112">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="a0cac-112">EXAMPLES</span></span>

### <span data-ttu-id="a0cac-113">Exemple 1 : obtenir un certificat PFX</span><span class="sxs-lookup"><span data-stu-id="a0cac-113">Example 1: Get a PFX certificate</span></span>

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

<span data-ttu-id="a0cac-114">Cette commande obtient des informations sur le fichier de certificat test. pfx sur le système.</span><span class="sxs-lookup"><span data-stu-id="a0cac-114">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="a0cac-115">Exemple 2 : obtenir un certificat PFX à partir d’un ordinateur distant</span><span class="sxs-lookup"><span data-stu-id="a0cac-115">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="a0cac-116">Cette commande obtient un fichier de certificat PFX de l’ordinateur distant SERVEUR01.</span><span class="sxs-lookup"><span data-stu-id="a0cac-116">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="a0cac-117">Il utilise `Invoke-Command` pour exécuter une `Get-PfxCertificate` commande à distance.</span><span class="sxs-lookup"><span data-stu-id="a0cac-117">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="a0cac-118">Lorsque le fichier de certificat PFX n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.</span><span class="sxs-lookup"><span data-stu-id="a0cac-118">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="a0cac-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0cac-119">PARAMETERS</span></span>

### <span data-ttu-id="a0cac-120">-FilePath</span><span class="sxs-lookup"><span data-stu-id="a0cac-120">-FilePath</span></span>

<span data-ttu-id="a0cac-121">Spécifie le chemin d’accès complet au fichier PFX du fichier sécurisé.</span><span class="sxs-lookup"><span data-stu-id="a0cac-121">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="a0cac-122">Si vous spécifiez une valeur pour ce paramètre, il n’est pas nécessaire de taper `-FilePath` au niveau de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a0cac-122">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

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

### <span data-ttu-id="a0cac-123">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a0cac-123">-LiteralPath</span></span>

<span data-ttu-id="a0cac-124">Chemin d’accès complet au fichier PFX du fichier sécurisé.</span><span class="sxs-lookup"><span data-stu-id="a0cac-124">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="a0cac-125">Contrairement à **FilePath** , la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="a0cac-125">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="a0cac-126">Aucun caractère n’est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="a0cac-126">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a0cac-127">Si le chemin d’accès inclut des caractères d’échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="a0cac-127">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a0cac-128">Les guillemets simples indiquent à PowerShell qu’il n’est pas possible d’interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="a0cac-128">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a0cac-129">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="a0cac-129">-NoPromptForPassword</span></span>

<span data-ttu-id="a0cac-130">Supprime la demande d’un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a0cac-130">Suppresses prompting for a password.</span></span>

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

### <span data-ttu-id="a0cac-131">-Mot de passe</span><span class="sxs-lookup"><span data-stu-id="a0cac-131">-Password</span></span>

<span data-ttu-id="a0cac-132">Spécifie un mot de passe requis pour accéder à un `.pfx` fichier de certificat.</span><span class="sxs-lookup"><span data-stu-id="a0cac-132">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="a0cac-133">Ce paramètre a été introduit dans PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="a0cac-133">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="a0cac-134">Pour plus d’informations sur la protection des données **SecureString** , consultez la section relative à [la sécurité de SecureString](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="a0cac-134">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="a0cac-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0cac-135">CommonParameters</span></span>

<span data-ttu-id="a0cac-136">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0cac-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0cac-137">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0cac-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0cac-138">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="a0cac-138">INPUTS</span></span>

### <span data-ttu-id="a0cac-139">System.String</span><span class="sxs-lookup"><span data-stu-id="a0cac-139">System.String</span></span>

<span data-ttu-id="a0cac-140">Vous pouvez diriger une chaîne qui contient un chemin d’accès de fichier vers `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="a0cac-140">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="a0cac-141">SORTIES</span><span class="sxs-lookup"><span data-stu-id="a0cac-141">OUTPUTS</span></span>

### <span data-ttu-id="a0cac-142">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="a0cac-142">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="a0cac-143">`Get-PfxCertificate` retourne un objet pour chaque certificat qu’il obtient.</span><span class="sxs-lookup"><span data-stu-id="a0cac-143">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="a0cac-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="a0cac-144">NOTES</span></span>

<span data-ttu-id="a0cac-145">Lorsque vous utilisez la `Invoke-Command` cmdlet pour exécuter une `Get-PfxCertificate` commande à distance et que le fichier de certificat pfx n’est pas protégé par un mot de passe, la valeur du paramètre d' **authentification** de `Invoke-Command` doit être CredSSP.</span><span class="sxs-lookup"><span data-stu-id="a0cac-145">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="a0cac-146">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="a0cac-146">RELATED LINKS</span></span>

[<span data-ttu-id="a0cac-147">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a0cac-147">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="a0cac-148">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="a0cac-148">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
