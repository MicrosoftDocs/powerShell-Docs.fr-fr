---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99596732"
---
# <span data-ttu-id="50737-102">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="50737-102">Get-FileHash</span></span>

## <span data-ttu-id="50737-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="50737-103">SYNOPSIS</span></span>
<span data-ttu-id="50737-104">Calcule la valeur de hachage pour un fichier en utilisant un algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="50737-104">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="50737-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="50737-105">SYNTAX</span></span>

### <span data-ttu-id="50737-106">Chemin d’accès (par défaut)</span><span class="sxs-lookup"><span data-stu-id="50737-106">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="50737-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="50737-107">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="50737-108">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="50737-108">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="50737-109">Description</span><span class="sxs-lookup"><span data-stu-id="50737-109">DESCRIPTION</span></span>

<span data-ttu-id="50737-110">L' `Get-FileHash` applet de commande calcule la valeur de hachage d’un fichier à l’aide d’un algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="50737-110">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="50737-111">Une valeur de hachage est une valeur unique qui correspond au contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="50737-111">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="50737-112">Au lieu d'identifier le contenu d'un fichier par son nom, son extension ou toute autre désignation, un hachage assigne une valeur unique au contenu d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="50737-112">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="50737-113">Les extensions et les noms de fichiers peuvent être modifiés sans changer le contenu du fichier ni la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="50737-113">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="50737-114">De même, le contenu du fichier peut être modifié sans modification du nom ou de l’extension.</span><span class="sxs-lookup"><span data-stu-id="50737-114">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="50737-115">Toutefois, la modification d'un seul caractère dans le contenu d'un fichier change la valeur de hachage du fichier.</span><span class="sxs-lookup"><span data-stu-id="50737-115">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="50737-116">L'objectif des valeurs de hachage est de fournir un moyen sécurisé par chiffrement de vérifier que le contenu d'un fichier n'a pas été modifié.</span><span class="sxs-lookup"><span data-stu-id="50737-116">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="50737-117">Bien que certains algorithmes de hachage, y compris MD5 et SHA1, ne soient plus considérés comme sécurisés contre les attaques, l’objectif d’un algorithme de hachage sécurisé est de rendre impossible la modification du contenu d’un fichier, soit par accident, soit par tentative malveillante ou non autorisée et en conservant la même valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="50737-117">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="50737-118">Vous pouvez également utiliser des valeurs de hachage pour déterminer si deux fichiers différents ont exactement le même contenu.</span><span class="sxs-lookup"><span data-stu-id="50737-118">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="50737-119">Si les valeurs de hachage de deux fichiers sont identiques, le contenu des fichiers est aussi identique.</span><span class="sxs-lookup"><span data-stu-id="50737-119">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="50737-120">Par défaut, l' `Get-FileHash` applet de commande utilise l’algorithme SHA256, bien qu’un algorithme de hachage pris en charge par le système d’exploitation cible puisse être utilisé.</span><span class="sxs-lookup"><span data-stu-id="50737-120">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="50737-121">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="50737-121">EXAMPLES</span></span>

### <span data-ttu-id="50737-122">Exemple 1 : calculer la valeur de hachage pour un fichier</span><span class="sxs-lookup"><span data-stu-id="50737-122">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="50737-123">Cet exemple utilise l' `Get-FileHash` applet de commande pour calculer la valeur de hachage du `/etc/apt/sources.list` fichier.</span><span class="sxs-lookup"><span data-stu-id="50737-123">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="50737-124">L’algorithme de hachage utilisé est la valeur par défaut, **SHA256**.</span><span class="sxs-lookup"><span data-stu-id="50737-124">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="50737-125">La sortie est dirigée vers l' `Format-List` applet de commande pour mettre en forme la sortie sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="50737-125">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="50737-126">Exemple 2 : calculer la valeur de hachage pour un fichier ISO</span><span class="sxs-lookup"><span data-stu-id="50737-126">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="50737-127">Cet exemple utilise l' `Get-FileHash` applet de commande et l’algorithme **SHA384** pour calculer la valeur de hachage pour un fichier ISO qu’un administrateur a téléchargé à partir d’Internet.</span><span class="sxs-lookup"><span data-stu-id="50737-127">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="50737-128">La sortie est dirigée vers l' `Format-List` applet de commande pour mettre en forme la sortie sous forme de liste.</span><span class="sxs-lookup"><span data-stu-id="50737-128">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="50737-129">Exemple 3 : calculer la valeur de hachage d’un flux</span><span class="sxs-lookup"><span data-stu-id="50737-129">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="50737-130">Pour cet exemple, nous obtenons l’utilisation de **System .net. WebClient** pour télécharger un package à partir de la [page de version PowerShell](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span><span class="sxs-lookup"><span data-stu-id="50737-130">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="50737-131">La page de mise en version documente également le hachage SHA256 de chaque fichier de package.</span><span class="sxs-lookup"><span data-stu-id="50737-131">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="50737-132">Nous pouvons comparer la valeur de hachage publiée avec celle que nous calculons avec `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="50737-132">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="50737-133">Exemple 4 : calculer le hachage d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="50737-133">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="50737-134">PowerShell ne fournit pas de cmdlet pour calculer le hachage d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="50737-134">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="50737-135">Toutefois, vous pouvez écrire une chaîne dans un flux et utiliser le paramètre **InputStream** de `Get-FileHash` pour obtenir la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="50737-135">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="50737-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="50737-136">PARAMETERS</span></span>

### <span data-ttu-id="50737-137">-Algorithme</span><span class="sxs-lookup"><span data-stu-id="50737-137">-Algorithm</span></span>

<span data-ttu-id="50737-138">Spécifie la fonction de hachage de chiffrement à utiliser pour calculer la valeur de hachage du contenu du fichier ou du flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="50737-138">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="50737-139">Une fonction de hachage de chiffrement a la propriété qu’il est impossible de trouver deux fichiers différents avec la même valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="50737-139">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="50737-140">Les fonctions de hachage sont couramment utilisées avec des signatures numériques et pour l'intégrité des données.</span><span class="sxs-lookup"><span data-stu-id="50737-140">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="50737-141">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="50737-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="50737-142">SHA1</span><span class="sxs-lookup"><span data-stu-id="50737-142">SHA1</span></span>
- <span data-ttu-id="50737-143">SHA256</span><span class="sxs-lookup"><span data-stu-id="50737-143">SHA256</span></span>
- <span data-ttu-id="50737-144">SHA384</span><span class="sxs-lookup"><span data-stu-id="50737-144">SHA384</span></span>
- <span data-ttu-id="50737-145">SHA512</span><span class="sxs-lookup"><span data-stu-id="50737-145">SHA512</span></span>
- <span data-ttu-id="50737-146">MD5</span><span class="sxs-lookup"><span data-stu-id="50737-146">MD5</span></span>

<span data-ttu-id="50737-147">Si aucune valeur n'est spécifiée, ou que le paramètre est omis, la valeur par défaut est SHA256.</span><span class="sxs-lookup"><span data-stu-id="50737-147">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="50737-148">Pour des raisons de sécurité, MD5 et SHA1, qui ne sont plus considérées comme sécurisées, ne doivent être utilisées que pour la validation de modifications simples et non pour générer des valeurs de hachage pour des fichiers qui nécessitent une protection contre les attaques ou la falsification.</span><span class="sxs-lookup"><span data-stu-id="50737-148">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="50737-149">-InputStream</span><span class="sxs-lookup"><span data-stu-id="50737-149">-InputStream</span></span>

<span data-ttu-id="50737-150">Spécifie le flux d’entrée.</span><span class="sxs-lookup"><span data-stu-id="50737-150">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="50737-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="50737-151">-LiteralPath</span></span>

<span data-ttu-id="50737-152">Spécifie le chemin d'accès à un fichier.</span><span class="sxs-lookup"><span data-stu-id="50737-152">Specifies the path to a file.</span></span> <span data-ttu-id="50737-153">Contrairement au paramètre **Path**, la valeur du paramètre **LiteralPath** est utilisée exactement telle qu'elle est tapée.</span><span class="sxs-lookup"><span data-stu-id="50737-153">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="50737-154">Aucun caractère n'est interprété en tant que caractère générique.</span><span class="sxs-lookup"><span data-stu-id="50737-154">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="50737-155">Si le chemin d'accès inclut des caractères d'échappement, mettez-le entre des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="50737-155">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="50737-156">Les guillemets simples indiquent à PowerShell de ne pas interpréter les caractères comme des séquences d’échappement.</span><span class="sxs-lookup"><span data-stu-id="50737-156">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="50737-157">-Path</span><span class="sxs-lookup"><span data-stu-id="50737-157">-Path</span></span>

<span data-ttu-id="50737-158">Spécifie le chemin d’accès à un ou plusieurs fichiers sous la forme d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="50737-158">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="50737-159">Les caractères génériques sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="50737-159">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="50737-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="50737-160">CommonParameters</span></span>

<span data-ttu-id="50737-161">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="50737-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="50737-162">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="50737-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="50737-163">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="50737-163">INPUTS</span></span>

### <span data-ttu-id="50737-164">System.String</span><span class="sxs-lookup"><span data-stu-id="50737-164">System.String</span></span>

<span data-ttu-id="50737-165">Vous pouvez diriger une chaîne vers l' `Get-FileHash` applet de commande qui contient un chemin d’accès à un ou plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="50737-165">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="50737-166">SORTIES</span><span class="sxs-lookup"><span data-stu-id="50737-166">OUTPUTS</span></span>

### <span data-ttu-id="50737-167">Microsoft. PowerShell. Utility. FileHash</span><span class="sxs-lookup"><span data-stu-id="50737-167">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="50737-168">`Get-FileHash` retourne un objet qui représente le chemin d’accès au fichier spécifié, la valeur du hachage calculé et l’algorithme utilisé pour calculer le hachage.</span><span class="sxs-lookup"><span data-stu-id="50737-168">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="50737-169">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="50737-169">NOTES</span></span>

## <span data-ttu-id="50737-170">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="50737-170">RELATED LINKS</span></span>

[<span data-ttu-id="50737-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="50737-171">Format-List</span></span>](Format-List.md)

