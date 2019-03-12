---
title: Présentation de l’encodage de fichier dans VSCode et PowerShell
description: Configurer l’encodage du fichier dans VSCode et PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429803"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="db0e3-103">Présentation de l’encodage de fichier dans VSCode et PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e3-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="db0e3-104">Lorsque vous utilisez Visual Studio Code pour créer et modifier des scripts PowerShell, il est important que vos fichiers sont enregistrés à l’aide du format d’encodage de caractères approprié.</span><span class="sxs-lookup"><span data-stu-id="db0e3-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="db0e3-105">Quel est l’encodage de fichier et pourquoi est-il important ?</span><span class="sxs-lookup"><span data-stu-id="db0e3-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="db0e3-106">VSCode gère l’interface entre un humain chaînes de saisie de caractères dans une mémoire tampon et les blocs de lecture/écriture d’octets pour le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="db0e3-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="db0e3-107">Quand VSCode enregistre un fichier, il utilise un codage de texte à le faire.</span><span class="sxs-lookup"><span data-stu-id="db0e3-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="db0e3-108">De même, lorsque PowerShell exécute un script il doit convertir les octets dans un fichier de caractères à reconstruire le fichier dans un programme de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db0e3-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="db0e3-109">VSCode écrit le fichier et PowerShell lit le fichier, ils doivent utiliser le même système d’encodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="db0e3-110">Ce processus de l’analyse d’un script PowerShell se déroule : *octets* -> *caractères* -> *jetons*  ->   *arborescence de syntaxe abstraite* -> *exécution*.</span><span class="sxs-lookup"><span data-stu-id="db0e3-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="db0e3-111">VSCode et PowerShell sont installés avec une configuration d’encodage par défaut.</span><span class="sxs-lookup"><span data-stu-id="db0e3-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="db0e3-112">Toutefois, l’encodage par défaut utilisée par PowerShell a changé avec la version de PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="db0e3-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="db0e3-113">Pour vous assurer de ne pose aucun problème à l’aide de PowerShell ou l’extension PowerShell dans VSCode, vous devez configurer vos paramètres VSCode et PowerShell correctement.</span><span class="sxs-lookup"><span data-stu-id="db0e3-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="db0e3-114">Causes courantes des problèmes de codage</span><span class="sxs-lookup"><span data-stu-id="db0e3-114">Common causes of encoding issues</span></span>

<span data-ttu-id="db0e3-115">Encodage problèmes lors de l’encodage de VSCode ou votre fichier de script ne correspond pas à l’encodage attendu de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db0e3-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="db0e3-116">Il n’existe aucun moyen de PowerShell pour déterminer automatiquement l’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="db0e3-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="db0e3-117">Vous êtes plus susceptible d’avoir des problèmes de codage lorsque vous utilisez des caractères pas dans le [jeu de caractères ASCII 7 bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="db0e3-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="db0e3-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="db0e3-118">For example:</span></span>

- <span data-ttu-id="db0e3-119">Les caractères de latin accentués (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="db0e3-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="db0e3-120">Caractères non latins comme cyrillique (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="db0e3-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="db0e3-121">Henri chinois (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="db0e3-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="db0e3-122">Causes courantes de problèmes de codage sont :</span><span class="sxs-lookup"><span data-stu-id="db0e3-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="db0e3-123">Les encodages de VSCode et PowerShell n’ont pas été modifiés à partir de leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="db0e3-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="db0e3-124">Pour PowerShell 5.1 et version antérieure, la valeur par défaut l’encodage est différent à partir de VSCode.</span><span class="sxs-lookup"><span data-stu-id="db0e3-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="db0e3-125">Un autre éditeur a ouvert et remplacé le fichier dans un nouvel encodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="db0e3-126">Cela se produit souvent avec l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="db0e3-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="db0e3-127">Le fichier est extrait dans le contrôle de source dans un encodage différent à partir de quel VSCode ou de PowerShell attend.</span><span class="sxs-lookup"><span data-stu-id="db0e3-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="db0e3-128">Cela peut se produire lorsque collaborateurs utilisent éditeurs avec différentes configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="db0e3-129">Comment savoir quand vous avez des problèmes de codage</span><span class="sxs-lookup"><span data-stu-id="db0e3-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="db0e3-130">Une erreur d’encodage souvent présente eux-mêmes comme des erreurs dans les scripts d’analyse.</span><span class="sxs-lookup"><span data-stu-id="db0e3-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="db0e3-131">Si vous trouvez des séquences de caractères étranges dans votre script, cela peut être le problème.</span><span class="sxs-lookup"><span data-stu-id="db0e3-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="db0e3-132">Dans l’exemple ci-dessous, un tiret demi-cadratin (`–`) s’affiche en tant que les caractères `â€“`:</span><span class="sxs-lookup"><span data-stu-id="db0e3-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="db0e3-133">Ce problème se produit parce que VSCode encode le caractère `–` en UTF-8 en tant que les octets `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="db0e3-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="db0e3-134">Lorsque ces octets sont décodées en tant que Windows-1252, elles sont interprétées comme les caractères `â€“`.</span><span class="sxs-lookup"><span data-stu-id="db0e3-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="db0e3-135">Certaines séquences de caractères étranges qui peuvent apparaître sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="db0e3-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="db0e3-136">`â€“` au lieu de `–`</span><span class="sxs-lookup"><span data-stu-id="db0e3-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="db0e3-137">`â€”` au lieu de `—`</span><span class="sxs-lookup"><span data-stu-id="db0e3-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="db0e3-138">`Ã„2` au lieu de `Ä`</span><span class="sxs-lookup"><span data-stu-id="db0e3-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="db0e3-139">`Â` au lieu de ` ` (espace insécable)</span><span class="sxs-lookup"><span data-stu-id="db0e3-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="db0e3-140">`Ã©` au lieu de `é`</span><span class="sxs-lookup"><span data-stu-id="db0e3-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="db0e3-141">Portée de main [référence](https://www.i18nqa.com/debug/utf8-debug.html) répertorie les modèles courants qui indiquent un problème de codage UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="db0e3-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="db0e3-142">Comment l’extension PowerShell dans VSCode interagit avec les encodages</span><span class="sxs-lookup"><span data-stu-id="db0e3-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="db0e3-143">L’extension PowerShell interagit avec des scripts dans une de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="db0e3-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="db0e3-144">Lorsque les scripts sont modifiés dans VSCode, le contenu est envoyé par VSCode à l’extension.</span><span class="sxs-lookup"><span data-stu-id="db0e3-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="db0e3-145">Le [protocole de serveur de langage][] impose que ce contenu est transféré en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="db0e3-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="db0e3-146">Par conséquent, il n’est pas possible pour l’extension obtenir l’encodage incorrect.</span><span class="sxs-lookup"><span data-stu-id="db0e3-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="db0e3-147">Lorsque les scripts sont exécutées directement dans la Console intégrée, ils sont lus à partir du fichier par PowerShell directement.</span><span class="sxs-lookup"><span data-stu-id="db0e3-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="db0e3-148">Si l’encodage de PowerShell est différent de VSCode, choses se passent mal ici.</span><span class="sxs-lookup"><span data-stu-id="db0e3-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="db0e3-149">Lorsqu’un script qui est ouvert dans VSCode fait référence à un autre script qui n’est pas ouvert dans VSCode, l’extension revient au chargement de contenu de ce script à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="db0e3-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="db0e3-150">L’extension PowerShell par défaut de l’encodage UTF-8, mais utilise [marque d’ordre d’octet][], ou BOM, détection permet de sélectionner l’encodage correct.</span><span class="sxs-lookup"><span data-stu-id="db0e3-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="db0e3-151">Le problème se produit lorsqu’en supposant que l’encodage des formats de sans BOM (comme [UTF-8][] sans BOM et [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="db0e3-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="db0e3-152">L’extension PowerShell par défaut est UTF-8.</span><span class="sxs-lookup"><span data-stu-id="db0e3-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="db0e3-153">L’extension ne peut pas modifier les paramètres d’encodage de VSCode.</span><span class="sxs-lookup"><span data-stu-id="db0e3-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="db0e3-154">Pour plus d’informations, consultez [émettre #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="db0e3-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="db0e3-155">Choix de l’encodage de droite</span><span class="sxs-lookup"><span data-stu-id="db0e3-155">Choosing the right encoding</span></span>

<span data-ttu-id="db0e3-156">Divers systèmes et applications peuvent utiliser différents codages :</span><span class="sxs-lookup"><span data-stu-id="db0e3-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="db0e3-157">Dans .NET Standard, sur le web et dans le monde de Linux, UTF-8 est désormais l’encodage dominant.</span><span class="sxs-lookup"><span data-stu-id="db0e3-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="db0e3-158">De nombreuses applications .NET Framework utilisent [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="db0e3-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="db0e3-159">Pour des raisons historiques, il est parfois appelé « Unicode », un terme qui fait référence à une large [standard](https://en.wikipedia.org/wiki/Unicode) incluant UTF-8 et UTF-16.</span><span class="sxs-lookup"><span data-stu-id="db0e3-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="db0e3-160">Sur Windows, de nombreuses applications natives qui sont antérieurs à Unicode continuent à utiliser Windows-1252 par défaut.</span><span class="sxs-lookup"><span data-stu-id="db0e3-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="db0e3-161">Les codages Unicode ont également le concept d’un ordre d’octet (BOM) de marquer.</span><span class="sxs-lookup"><span data-stu-id="db0e3-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="db0e3-162">Nomenclatures se produisent au début du texte pour indiquer un décodeur le codage à l’aide de texte.</span><span class="sxs-lookup"><span data-stu-id="db0e3-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="db0e3-163">Pour les encodages multi-octets, la nomenclature indique également [endianness](https://en.wikipedia.org/wiki/Endianness) du codage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="db0e3-164">Nomenclatures sont conçus pour être des octets qui se produisent rarement dans le texte non-Unicode, ce qui permet une estimation raisonnable que texte est au format Unicode lorsqu’un BOM est présent.</span><span class="sxs-lookup"><span data-stu-id="db0e3-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="db0e3-165">Nomenclatures sont facultatives et leur adoption n’est pas aussi populaire dans le monde de Linux, car une convention fiable d’UTF-8 est utilisée partout.</span><span class="sxs-lookup"><span data-stu-id="db0e3-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="db0e3-166">La plupart des applications Linux supposent que l’entrée de texte est encodée en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="db0e3-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="db0e3-167">Tandis que de nombreuses applications Linux reconnaît et gère correctement une nomenclature, un nombre ne le faites pas, ce qui conduit à des artefacts dans le texte manipulé avec ces applications.</span><span class="sxs-lookup"><span data-stu-id="db0e3-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="db0e3-168">**Par conséquent** :</span><span class="sxs-lookup"><span data-stu-id="db0e3-168">**Therefore**:</span></span>

- <span data-ttu-id="db0e3-169">Si vous travaillez principalement avec les applications Windows et Windows PowerShell, vous devez préférer un encodage comme UTF-8 avec BOM ou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="db0e3-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="db0e3-170">Si vous travaillez sur plusieurs plateformes, vous devez préférer UTF-8 avec BOM.</span><span class="sxs-lookup"><span data-stu-id="db0e3-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="db0e3-171">Si vous travaillez principalement dans les contextes associés à Linux, vous devez préférer UTF-8 sans BOM.</span><span class="sxs-lookup"><span data-stu-id="db0e3-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="db0e3-172">Windows-1252 et latin-1 sont essentiellement des encodages hérités que vous ne devez pas si possible.</span><span class="sxs-lookup"><span data-stu-id="db0e3-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="db0e3-173">Toutefois, certaines applications Windows plus anciens peuvent dépendre les.</span><span class="sxs-lookup"><span data-stu-id="db0e3-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="db0e3-174">Il est également important de noter que la signature de script est [dépendant du codage](https://github.com/PowerShell/PowerShell/issues/3466), ce qui signifie qu’une modification de codage sur un script signé nécessitera la nouvelle signature.</span><span class="sxs-lookup"><span data-stu-id="db0e3-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="db0e3-175">Configuration de VSCode</span><span class="sxs-lookup"><span data-stu-id="db0e3-175">Configuring VSCode</span></span>

<span data-ttu-id="db0e3-176">De VSCode encodage par défaut est UTF-8 sans BOM.</span><span class="sxs-lookup"><span data-stu-id="db0e3-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="db0e3-177">Pour définir [Encodage de VSCode][], accédez aux paramètres VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) et définissez le `"files.encoding"` paramètre :</span><span class="sxs-lookup"><span data-stu-id="db0e3-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="db0e3-178">Certaines valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="db0e3-178">Some possible values are:</span></span>

- <span data-ttu-id="db0e3-179">`utf8`: [UTF-8] sans BOM</span><span class="sxs-lookup"><span data-stu-id="db0e3-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="db0e3-180">`utf8bom`: [UTF-8] avec BOM</span><span class="sxs-lookup"><span data-stu-id="db0e3-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="db0e3-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="db0e3-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="db0e3-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="db0e3-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="db0e3-183">`windows1252` : [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="db0e3-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="db0e3-184">Vous devez obtenir une liste déroulante pour cela dans la vue de l’interface graphique utilisateur, ou d’afficher des saisies semi-automatiques pour celui-ci dans le JSON.</span><span class="sxs-lookup"><span data-stu-id="db0e3-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="db0e3-185">Vous pouvez également ajouter les éléments suivants pour détecter automatiquement lorsque cela est possible d’encodage :</span><span class="sxs-lookup"><span data-stu-id="db0e3-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="db0e3-186">Si vous ne souhaitez pas ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations de langage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="db0e3-187">Créer un paramètre spécifique à la langue en plaçant des paramètres dans un `[<language-name>]` champ.</span><span class="sxs-lookup"><span data-stu-id="db0e3-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="db0e3-188">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="db0e3-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="db0e3-189">Configuration de PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e3-189">Configuring PowerShell</span></span>

<span data-ttu-id="db0e3-190">De PowerShell encodage par défaut varie en fonction de la version :</span><span class="sxs-lookup"><span data-stu-id="db0e3-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="db0e3-191">Dans PowerShell 6 et versions ultérieures, l’encodage par défaut est UTF-8 sans BOM sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="db0e3-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="db0e3-192">Dans Windows PowerShell, l’encodage par défaut est généralement Windows-1252, une extension de [latin-1][], également appelée ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="db0e3-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="db0e3-193">Dans PowerShell 5 et versions ultérieures, vous pouvez trouver votre encodage par défaut avec ce :</span><span class="sxs-lookup"><span data-stu-id="db0e3-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="db0e3-194">Ce qui suit [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) peut être utilisée pour déterminer quel encodage votre session PowerShell déduit pour un script sans une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="db0e3-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

<span data-ttu-id="db0e3-195">Il est possible de configurer PowerShell pour utiliser un encodage donné plus généralement à l’aide de paramètres de profil.</span><span class="sxs-lookup"><span data-stu-id="db0e3-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="db0e3-196">Voir les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="db0e3-196">See the following articles:</span></span>

- <span data-ttu-id="db0e3-197">[@mklement0]de [réponses sur l’encodage de PowerShell sur StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="db0e3-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="db0e3-198">[@rkeithhill]de [billet de blog sur le traitement d’entrée sans BOM UTF-8 dans PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="db0e3-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="db0e3-199">Il n’est pas possible de forcer PowerShell à utiliser un codage d’entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="db0e3-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="db0e3-200">PowerShell 5.1 et en dessous de la valeur par défaut pour Windows-1252 encodage lorsqu’il n’existe aucune nomenclature.</span><span class="sxs-lookup"><span data-stu-id="db0e3-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="db0e3-201">Pour des raisons de l’interopérabilité, il est préférable enregistrer des scripts dans un format Unicode avec une nomenclature.</span><span class="sxs-lookup"><span data-stu-id="db0e3-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="db0e3-202">N’importe quel outil que vous avez ce tactile PowerShell scripts peuvent être affectées par vos options de codage ou ré-encoder vos scripts à un autre encodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="db0e3-203">Scripts existants</span><span class="sxs-lookup"><span data-stu-id="db0e3-203">Existing scripts</span></span>

<span data-ttu-id="db0e3-204">Scripts déjà sur le système de fichiers peut-être à ré-encoder à votre nouvel encodage choisi.</span><span class="sxs-lookup"><span data-stu-id="db0e3-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="db0e3-205">Dans la barre en bas de VSCode, vous verrez l’étiquette UTF-8.</span><span class="sxs-lookup"><span data-stu-id="db0e3-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="db0e3-206">Cliquez dessus pour ouvrir la barre d’action et sélectionnez **enregistrer avec encodage**.</span><span class="sxs-lookup"><span data-stu-id="db0e3-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="db0e3-207">Vous pouvez maintenant choisir un nouvel encodage pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="db0e3-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="db0e3-208">Consultez [Encodage de VSCode][] pour obtenir des instructions complètes.</span><span class="sxs-lookup"><span data-stu-id="db0e3-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="db0e3-209">Si vous avez besoin de ré-encoder plusieurs fichiers, vous pouvez utiliser le script suivant :</span><span class="sxs-lookup"><span data-stu-id="db0e3-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="db0e3-210">Environnement d'écriture de scripts intégré (ISE) de PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e3-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="db0e3-211">Si vous modifiez également les scripts à l’aide de PowerShell ISE, vous devez synchroniser vos paramètres d’encodage il.</span><span class="sxs-lookup"><span data-stu-id="db0e3-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="db0e3-212">L’environnement ISE doit respecter une nomenclature, mais il est également possible d’utiliser la réflexion pour [l’encodage de jeu](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="db0e3-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="db0e3-213">Notez que cela n’aurait pas rendues persistantes entre les startups.</span><span class="sxs-lookup"><span data-stu-id="db0e3-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="db0e3-214">Logiciel de contrôle de code source</span><span class="sxs-lookup"><span data-stu-id="db0e3-214">Source control software</span></span>

<span data-ttu-id="db0e3-215">Certains outils de contrôle source, tels que git, ignorent les encodages ; GIT suit uniquement les octets.</span><span class="sxs-lookup"><span data-stu-id="db0e3-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="db0e3-216">Autres, telles que TFS ou Mercurial, ne peuvent pas.</span><span class="sxs-lookup"><span data-stu-id="db0e3-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="db0e3-217">Même certains outils git s’appuient sur le texte de décodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="db0e3-218">C’est le cas, assurez-vous que vous :</span><span class="sxs-lookup"><span data-stu-id="db0e3-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="db0e3-219">Configurer l’encodage dans votre contrôle de code source pour correspondre à votre configuration de VSCode de texte.</span><span class="sxs-lookup"><span data-stu-id="db0e3-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="db0e3-220">Vérifiez que tous vos fichiers sont archivés dans le contrôle de code source dans l’encodage approprié.</span><span class="sxs-lookup"><span data-stu-id="db0e3-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="db0e3-221">Méfiez-vous des modifications apportées à l’encodage reçu via le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="db0e3-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="db0e3-222">Un signe de clé de ce est une comparaison qui indique des modifications, mais où rien ne semble avoir été modifié (car les octets ont mais caractères n’ont pas).</span><span class="sxs-lookup"><span data-stu-id="db0e3-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="db0e3-223">Environnements de collaborateurs</span><span class="sxs-lookup"><span data-stu-id="db0e3-223">Collaborators' environments</span></span>

<span data-ttu-id="db0e3-224">En haut de la configuration de contrôle de code source, assurez-vous que vous n’ont pas les paramètres qui remplacent votre encodage par ré-encodage fichiers PowerShell pour vos collaborateurs sur les fichiers que vous partagez.</span><span class="sxs-lookup"><span data-stu-id="db0e3-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="db0e3-225">Autres programmes</span><span class="sxs-lookup"><span data-stu-id="db0e3-225">Other programs</span></span>

<span data-ttu-id="db0e3-226">Tout autre programme qui lit ou écrit un script PowerShell peut ré-encoder.</span><span class="sxs-lookup"><span data-stu-id="db0e3-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="db0e3-227">Quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="db0e3-227">Some examples are:</span></span>

- <span data-ttu-id="db0e3-228">Utilisation du Presse-papiers pour copier et coller un script.</span><span class="sxs-lookup"><span data-stu-id="db0e3-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="db0e3-229">Cela est courant dans les scénarios tels que :</span><span class="sxs-lookup"><span data-stu-id="db0e3-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="db0e3-230">Copie d’un script dans une machine virtuelle</span><span class="sxs-lookup"><span data-stu-id="db0e3-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="db0e3-231">Copie d’un script en dehors d’un e-mail ou une page Web</span><span class="sxs-lookup"><span data-stu-id="db0e3-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="db0e3-232">Copie d’un script dans ou hors d’un document Microsoft Word ou PowerPoint</span><span class="sxs-lookup"><span data-stu-id="db0e3-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="db0e3-233">Autres éditeurs de texte, tel que :</span><span class="sxs-lookup"><span data-stu-id="db0e3-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="db0e3-234">Bloc-notes</span><span class="sxs-lookup"><span data-stu-id="db0e3-234">Notepad</span></span>
  - <span data-ttu-id="db0e3-235">Vim</span><span class="sxs-lookup"><span data-stu-id="db0e3-235">vim</span></span>
  - <span data-ttu-id="db0e3-236">N’importe quel autre éditeur de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e3-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="db0e3-237">Texte de l’édition des utilitaires, tels que :</span><span class="sxs-lookup"><span data-stu-id="db0e3-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="db0e3-238">Opérateurs de redirection de PowerShell comme `>` et `>>`</span><span class="sxs-lookup"><span data-stu-id="db0e3-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="db0e3-239">Fichiers programmes de transfert, telles que :</span><span class="sxs-lookup"><span data-stu-id="db0e3-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="db0e3-240">Un navigateur web, lors du téléchargement des scripts</span><span class="sxs-lookup"><span data-stu-id="db0e3-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="db0e3-241">Un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="db0e3-241">A file share</span></span>

<span data-ttu-id="db0e3-242">Certains de ces outils traitent en octets plutôt que texte, mais d’autres offrent des configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="db0e3-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="db0e3-243">Dans les cas où vous devez configurer un encodage, vous devez rendre identique à votre éditeur de codage pour éviter ces problèmes.</span><span class="sxs-lookup"><span data-stu-id="db0e3-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="db0e3-244">Autres ressources sur l’encodage dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="db0e3-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="db0e3-245">Il existe quelques autres billets intéressantes sur l’encodage et la configuration d’encodage dans PowerShell qui méritent d’être une lecture :</span><span class="sxs-lookup"><span data-stu-id="db0e3-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="db0e3-246">[@mklement0]de [résumé de l’encodage PowerShell sur StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="db0e3-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="db0e3-247">Numéros précédents ouvert sur vscode-PowerShell pour l’encodage des problèmes :</span><span class="sxs-lookup"><span data-stu-id="db0e3-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="db0e3-248">#1308</span><span class="sxs-lookup"><span data-stu-id="db0e3-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="db0e3-249">#1628</span><span class="sxs-lookup"><span data-stu-id="db0e3-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="db0e3-250">#1680</span><span class="sxs-lookup"><span data-stu-id="db0e3-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="db0e3-251">#1744</span><span class="sxs-lookup"><span data-stu-id="db0e3-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="db0e3-252">#1751</span><span class="sxs-lookup"><span data-stu-id="db0e3-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="db0e3-253">Classique *Joel sur les logiciels* le sujet Unicode</span><span class="sxs-lookup"><span data-stu-id="db0e3-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="db0e3-254">Encodage dans .NET Standard</span><span class="sxs-lookup"><span data-stu-id="db0e3-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marque d’ordre d’octet]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocole de serveur de langage]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Encodage de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
