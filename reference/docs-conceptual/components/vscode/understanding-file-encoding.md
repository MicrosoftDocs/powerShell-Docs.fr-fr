---
title: Présentation de l’encodage de fichier dans VSCode et PowerShell
description: Configuration de l’encodage de fichier dans VSCode et PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 6a00e45b3700f72f78e2fbcdf6e317f3a17b53c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058435"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="8c161-103">Présentation de l’encodage de fichier dans VSCode et PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c161-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="8c161-104">Quand vous utilisez Visual Studio Code pour créer et modifier des scripts PowerShell, il est important que vos fichiers soient enregistrés à l’aide du format d’encodage de caractères approprié.</span><span class="sxs-lookup"><span data-stu-id="8c161-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="8c161-105">Qu’est-ce que l’encodage de fichier et pourquoi est-il important ?</span><span class="sxs-lookup"><span data-stu-id="8c161-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="8c161-106">VSCode gère l’interface entre un utilisateur qui entre des chaînes de caractères dans une mémoire tampon et la lecture/écriture de blocs d’octets dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8c161-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="8c161-107">Quand VSCode enregistre un fichier, il utilise un encodage de texte.</span><span class="sxs-lookup"><span data-stu-id="8c161-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="8c161-108">De même, quand PowerShell exécute un script, il doit convertir les octets d’un fichier en caractères afin de reconstruire le fichier dans un programme PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c161-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="8c161-109">Comme VSCode écrit le fichier et que PowerShell le lit, ils doivent utiliser le même système d’encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="8c161-110">Ce processus d’analyse d’un script PowerShell est le suivant : *octets* -> *caractères* -> *jetons* ->  *arborescence de syntaxe abstraite* -> *exécution*.</span><span class="sxs-lookup"><span data-stu-id="8c161-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="8c161-111">VSCode et PowerShell sont tous deux installés avec une configuration d’encodage par défaut adéquate.</span><span class="sxs-lookup"><span data-stu-id="8c161-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="8c161-112">Toutefois, l’encodage par défaut utilisée par PowerShell a changé avec la publication de PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="8c161-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="8c161-113">Pour être sûr de n’avoir aucun problème lors de l’utilisation de PowerShell ou de l’extension PowerShell dans VSCode, vous devez configurer vos paramètres VSCode et PowerShell correctement.</span><span class="sxs-lookup"><span data-stu-id="8c161-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="8c161-114">Causes courantes de problèmes d’encodage</span><span class="sxs-lookup"><span data-stu-id="8c161-114">Common causes of encoding issues</span></span>

<span data-ttu-id="8c161-115">Des problèmes d’encodage se produisent quand l’encodage de VSCode ou de votre fichier de script ne correspond pas à l’encodage attendu par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c161-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="8c161-116">PowerShell ne dispose d’aucun moyen de déterminer automatiquement l’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="8c161-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="8c161-117">Vous risquez davantage de rencontrer des problèmes d’encodage quand vous utilisez des caractères qui ne figurent pas dans le [jeu de caractères ASCII sept bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="8c161-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="8c161-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8c161-118">For example:</span></span>

- <span data-ttu-id="8c161-119">Les caractères latins accentués (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="8c161-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="8c161-120">Les caractères non latins tels que les caractères cyrilliques (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="8c161-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="8c161-121">Les caractères chinois (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="8c161-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="8c161-122">Les causes courantes des problèmes d’encodage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8c161-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="8c161-123">Les encodages par défaut de VSCode et PowerShell n’ont pas été changés.</span><span class="sxs-lookup"><span data-stu-id="8c161-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="8c161-124">Pour PowerShell 5.1 et antérieur, l’encodage par défaut est différent de celui de VSCode.</span><span class="sxs-lookup"><span data-stu-id="8c161-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="8c161-125">Un autre éditeur a ouvert et remplacé le fichier dans un nouvel encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="8c161-126">Cela se produit souvent avec l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="8c161-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="8c161-127">Le fichier est archivé dans le contrôle de code source dans un encodage différent de celui attendu par VSCode ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c161-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="8c161-128">Cela peut se produire quand des collaborateurs utilisent des éditeurs avec différentes configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="8c161-129">Comment savoir quand vous avez des problèmes d’encodage ?</span><span class="sxs-lookup"><span data-stu-id="8c161-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="8c161-130">Souvent, les erreurs d’encodage se présentent sous forme d’erreurs d’analyse dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="8c161-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="8c161-131">Si vous remarquez des séquences de caractères étranges dans votre script, il peut s’agir de ce type de problème.</span><span class="sxs-lookup"><span data-stu-id="8c161-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="8c161-132">Dans l’exemple ci-dessous, les caractères `â€“` apparaissent à la place d’un tiret demi-cadratin (`–`) :</span><span class="sxs-lookup"><span data-stu-id="8c161-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="8c161-133">Ce problème se produit car VSCode encode le caractère `–` en UTF-8 en tant qu’octets `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="8c161-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="8c161-134">Quand ces octets sont décodés au format Windows-1252, ils sont interprétées en tant que caractères `â€“`.</span><span class="sxs-lookup"><span data-stu-id="8c161-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="8c161-135">Voici quelques séquences de caractères étranges susceptibles d’apparaître :</span><span class="sxs-lookup"><span data-stu-id="8c161-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="8c161-136">`â€“` au lieu de `–`</span><span class="sxs-lookup"><span data-stu-id="8c161-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="8c161-137">`â€”` au lieu de `—`</span><span class="sxs-lookup"><span data-stu-id="8c161-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="8c161-138">`Ã„2` au lieu de `Ä`</span><span class="sxs-lookup"><span data-stu-id="8c161-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="8c161-139">`Â` au lieu de ` ` (espace insécable)</span><span class="sxs-lookup"><span data-stu-id="8c161-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="8c161-140">`Ã©` au lieu de `é`</span><span class="sxs-lookup"><span data-stu-id="8c161-140">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="8c161-141">Cette [référence](https://www.i18nqa.com/debug/utf8-debug.html) très pratique liste les modèles courants qui indiquent un problème d’encodage UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="8c161-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="8c161-142">Interaction entre l’extension PowerShell dans VSCode et les encodages</span><span class="sxs-lookup"><span data-stu-id="8c161-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="8c161-143">L’extension PowerShell interagit avec les scripts de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="8c161-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="8c161-144">Quand les scripts sont modifiés dans VSCode, le contenu est envoyé par VSCode à l’extension.</span><span class="sxs-lookup"><span data-stu-id="8c161-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="8c161-145">Le [protocole de serveur de langage][] impose que ce contenu soit transféré en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c161-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="8c161-146">Par conséquent, il n’est pas possible pour l’extension d’obtenir l’encodage incorrect.</span><span class="sxs-lookup"><span data-stu-id="8c161-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="8c161-147">Quand les scripts sont exécutés directement dans la console intégrée, ils sont lus directement à partir du fichier par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c161-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="8c161-148">Si l’encodage de PowerShell est différent de celui de VSCode, les choses peuvent mal tourner.</span><span class="sxs-lookup"><span data-stu-id="8c161-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="8c161-149">Quand un script ouvert dans VSCode référence un autre script qui n’est pas ouvert dans VSCode, l’extension charge le contenu de ce script à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="8c161-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="8c161-150">L’extension PowerShell utilise par défaut l’encodage UTF-8, mais elle utilise la détection de [marque d’ordre d’octet][] pour sélectionner l’encodage correct.</span><span class="sxs-lookup"><span data-stu-id="8c161-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="8c161-151">Le problème se produit en cas d’encodage des formats sans marque d’ordre d’octet (comme [UTF-8][] sans marque d’ordre d’octet et [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="8c161-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="8c161-152">L’extension PowerShell utilise par défaut UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c161-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="8c161-153">L’extension ne peut pas modifier les paramètres d’encodage de VSCode.</span><span class="sxs-lookup"><span data-stu-id="8c161-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="8c161-154">Pour plus d’informations, consultez le [problème n°824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="8c161-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="8c161-155">Choix de l’encodage correct</span><span class="sxs-lookup"><span data-stu-id="8c161-155">Choosing the right encoding</span></span>

<span data-ttu-id="8c161-156">Différents systèmes et applications peuvent utiliser différents encodages :</span><span class="sxs-lookup"><span data-stu-id="8c161-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="8c161-157">Dans .NET Standard, sur le web et dans le monde de Linux, UTF-8 est désormais l’encodage dominant.</span><span class="sxs-lookup"><span data-stu-id="8c161-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="8c161-158">De nombreuses applications .NET Framework utilisent [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="8c161-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="8c161-159">Pour des raisons historiques, cet encodage est parfois appelé « Unicode », un terme qui fait aujourd’hui référence à une [norme](https://en.wikipedia.org/wiki/Unicode) étendue incluant UTF-8 et UTF-16.</span><span class="sxs-lookup"><span data-stu-id="8c161-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="8c161-160">Sur Windows, de nombreuses applications natives qui sont antérieures à Unicode continuent à utiliser Windows-1252 par défaut.</span><span class="sxs-lookup"><span data-stu-id="8c161-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="8c161-161">Avec les encodages Unicode, il existe également le concept de marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="8c161-162">Les marques d’ordre d’octet sont présentes au début, et elles indiquent au décodeur l’encodage utilisé par le texte.</span><span class="sxs-lookup"><span data-stu-id="8c161-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="8c161-163">Pour les encodages multioctets, la marque d’ordre d’octet indique également le [mode Endian](https://en.wikipedia.org/wiki/Endianness) de l’encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="8c161-164">Les marques d’ordre d’octet sont conçues pour être des octets qui se produisent rarement dans le texte non-Unicode, ce qui permet d’estimer avec une raisonnable certitude que le texte est au format Unicode quand une marque d’ordre d’octet est présente.</span><span class="sxs-lookup"><span data-stu-id="8c161-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="8c161-165">Les marques d’ordre d’octet sont facultatives, et leur adoption n’est pas aussi populaire dans le monde de Linux, car une convention fiable d’UTF-8 est utilisée partout.</span><span class="sxs-lookup"><span data-stu-id="8c161-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="8c161-166">La plupart des applications Linux partent du principe que l’entrée de texte est encodée en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c161-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="8c161-167">Bien que de nombreuses applications Linux reconnaissent et gèrent correctement les marques d’ordre d’octet, toutes ne le font pas, ce qui génère des artefacts dans le texte manipulé avec ces applications.</span><span class="sxs-lookup"><span data-stu-id="8c161-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="8c161-168">**Par conséquent** :</span><span class="sxs-lookup"><span data-stu-id="8c161-168">**Therefore**:</span></span>

- <span data-ttu-id="8c161-169">Si vous travaillez principalement avec des applications Windows et Windows PowerShell, vous devez privilégier un encodage comme UTF-8 avec marque d’ordre d’octet ou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="8c161-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="8c161-170">Si vous travaillez sur plusieurs plateformes, vous devez privilégier UTF-8 avec marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="8c161-171">Si vous travaillez principalement dans des contextes associés à Linux, vous devez privilégier UTF-8 sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="8c161-172">Windows-1252 et latin-1 sont essentiellement des encodages hérités que vous devez éviter dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="8c161-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="8c161-173">Toutefois, certaines applications Windows anciennes peuvent en dépendre.</span><span class="sxs-lookup"><span data-stu-id="8c161-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="8c161-174">Il convient également de noter que la signature de script est [dépendante du codage](https://github.com/PowerShell/PowerShell/issues/3466), ce qui signifie qu’un changement de l’encodage sur un script signé nécessitera une nouvelle signature.</span><span class="sxs-lookup"><span data-stu-id="8c161-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="8c161-175">Configuration de VSCode</span><span class="sxs-lookup"><span data-stu-id="8c161-175">Configuring VSCode</span></span>

<span data-ttu-id="8c161-176">L’encodage par défaut de VSCode est UTF-8 sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="8c161-177">Pour définir l’[encodage de VSCode][], accédez aux paramètres VSCode (<kbd>Ctrl</kbd>+<kbd>,</kbd>) et définissez le paramètre `"files.encoding"` :</span><span class="sxs-lookup"><span data-stu-id="8c161-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="8c161-178">Voici quelques valeurs possibles :</span><span class="sxs-lookup"><span data-stu-id="8c161-178">Some possible values are:</span></span>

- <span data-ttu-id="8c161-179">`utf8` : [UTF-8] sans marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="8c161-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="8c161-180">`utf8bom` : [UTF-8] avec marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="8c161-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="8c161-181">`utf16le` : Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="8c161-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="8c161-182">`utf16be` : Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="8c161-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="8c161-183">`windows1252` : [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="8c161-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="8c161-184">Vous devez obtenir une liste déroulante pour cette option dans la vue de l’interface graphique utilisateur, ou une complétion dans la vue JSON.</span><span class="sxs-lookup"><span data-stu-id="8c161-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="8c161-185">Vous pouvez aussi ajouter les éléments suivants pour détecter automatiquement l’encodage quand c’est possible :</span><span class="sxs-lookup"><span data-stu-id="8c161-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="8c161-186">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VSCode autorise également les configurations propres à un langage.</span><span class="sxs-lookup"><span data-stu-id="8c161-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="8c161-187">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="8c161-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="8c161-188">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="8c161-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="8c161-189">Configuration de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c161-189">Configuring PowerShell</span></span>

<span data-ttu-id="8c161-190">L’encodage par défaut de PowerShell varie en fonction de la version :</span><span class="sxs-lookup"><span data-stu-id="8c161-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="8c161-191">Dans PowerShell 6 et ultérieur, l’encodage par défaut est UTF-8 sans marque d’ordre d’octet sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="8c161-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="8c161-192">Dans Windows PowerShell, l’encodage par défaut est généralement Windows-1252, une extension de [latin-1][], également appelé ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="8c161-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="8c161-193">Dans PowerShell 5 et ultérieur, vous pouvez déterminer votre encodage comme suit :</span><span class="sxs-lookup"><span data-stu-id="8c161-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="8c161-194">Vous pouvez utiliser le [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) suivant pour déterminer quel encodage votre session PowerShell déduit pour un script sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="8c161-195">Il est possible de configurer PowerShell pour utiliser plus généralement un encodage donné à l’aide de paramètres de profil.</span><span class="sxs-lookup"><span data-stu-id="8c161-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="8c161-196">Voir les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="8c161-196">See the following articles:</span></span>

- <span data-ttu-id="8c161-197">La réponse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="8c161-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="8c161-198">Le billet de blog de [@rkeithhill] concernant le [traitement de l’entrée UTF-8 sans marque d’ordre d’octet dans PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="8c161-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="8c161-199">Il n’est pas possible de forcer PowerShell à utiliser un encodage d’entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="8c161-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="8c161-200">PowerShell 5.1 et antérieur utilisent par défaut l’encodage Windows-1252 quand il n’y a pas de marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="8c161-201">Pour des raisons d’interopérabilité, il est préférable d’enregistrer les scripts dans un format Unicode avec une marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="8c161-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c161-202">Tout autre outil qui traite des scripts PowerShell est susceptible d’être affecté par vos options d’encodage ou de ré-encoder vos scripts en un autre encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="8c161-203">Scripts existants</span><span class="sxs-lookup"><span data-stu-id="8c161-203">Existing scripts</span></span>

<span data-ttu-id="8c161-204">Vous devrez peut-être réencoder les scripts déjà présents sur le système de fichiers vers votre nouvel encodage choisi.</span><span class="sxs-lookup"><span data-stu-id="8c161-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="8c161-205">Dans la barre inférieure de VSCode, vous verrez l’étiquette UTF-8.</span><span class="sxs-lookup"><span data-stu-id="8c161-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="8c161-206">Cliquez dessus pour ouvrir la barre d’action et sélectionnez **Enregistrer avec encodage**.</span><span class="sxs-lookup"><span data-stu-id="8c161-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="8c161-207">Vous pouvez maintenant choisir un nouvel encodage pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="8c161-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="8c161-208">Pour des instructions complètes, consultez [Encodage de VSCode][].</span><span class="sxs-lookup"><span data-stu-id="8c161-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="8c161-209">Si vous avez besoin de ré-encoder plusieurs fichiers, vous pouvez utiliser le script suivant :</span><span class="sxs-lookup"><span data-stu-id="8c161-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="8c161-210">Environnement d'écriture de scripts intégré (ISE) de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c161-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="8c161-211">Si vous modifiez également des scripts à l’aide de PowerShell ISE, vous devez y synchroniser vos paramètres d’encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="8c161-212">L’environnement ISE doit respecter une marque d’ordre d’octet, mais il est également possible d’utiliser la réflexion pour [définir l’encodage](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="8c161-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="8c161-213">Notez que cela ne serait pas conservé d’un démarrage à un autre.</span><span class="sxs-lookup"><span data-stu-id="8c161-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="8c161-214">Logiciels de contrôle de code source</span><span class="sxs-lookup"><span data-stu-id="8c161-214">Source control software</span></span>

<span data-ttu-id="8c161-215">Certains outils de contrôle de code source, tels que GIT, ignorent les encodages. GIT ne fait que suivre les octets.</span><span class="sxs-lookup"><span data-stu-id="8c161-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="8c161-216">Ce n’est pas forcément le cas de tous, comme Azure DevOps ou Mercurial.</span><span class="sxs-lookup"><span data-stu-id="8c161-216">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="8c161-217">Même certains outils GIT s’appuient sur le décodage du texte.</span><span class="sxs-lookup"><span data-stu-id="8c161-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="8c161-218">Quand c’est le cas, veillez à :</span><span class="sxs-lookup"><span data-stu-id="8c161-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="8c161-219">Configurer l’encodage du texte dans votre contrôle de code source pour qu’il corresponde à votre configuration de VSCode.</span><span class="sxs-lookup"><span data-stu-id="8c161-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="8c161-220">Vérifier que tous vos fichiers sont archivés dans le contrôle de code source dans l’encodage approprié.</span><span class="sxs-lookup"><span data-stu-id="8c161-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="8c161-221">Méfiez-vous des modifications apportées à l’encodage reçues par le biais du contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="8c161-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="8c161-222">Un exemple courant est quand une comparaison indique des changements, mais que rien ne semble avoir été changé (car les octets ont changé, mais pas les caractères).</span><span class="sxs-lookup"><span data-stu-id="8c161-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="8c161-223">Environnements des collaborateurs</span><span class="sxs-lookup"><span data-stu-id="8c161-223">Collaborators' environments</span></span>

<span data-ttu-id="8c161-224">En plus de la configuration du contrôle de code source, veillez à ce que vos collaborateurs qui travaillent sur des fichiers que vous partagez n’aient pas de paramètres qui remplacent votre encodage en réencodant les fichiers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c161-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="8c161-225">Autres programmes</span><span class="sxs-lookup"><span data-stu-id="8c161-225">Other programs</span></span>

<span data-ttu-id="8c161-226">Tout autre programme qui lit ou écrit un script PowerShell est susceptible de le ré-encoder.</span><span class="sxs-lookup"><span data-stu-id="8c161-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="8c161-227">Quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="8c161-227">Some examples are:</span></span>

- <span data-ttu-id="8c161-228">Utilisation du Presse-papiers pour copier et coller un script.</span><span class="sxs-lookup"><span data-stu-id="8c161-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="8c161-229">C’est courant dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="8c161-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="8c161-230">Copie d’un script dans une machine virtuelle</span><span class="sxs-lookup"><span data-stu-id="8c161-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="8c161-231">Copie d’un script à partir d’un e-mail ou d’une page web</span><span class="sxs-lookup"><span data-stu-id="8c161-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="8c161-232">Copie d’un script dans ou à partir d’un document Microsoft Word ou PowerPoint</span><span class="sxs-lookup"><span data-stu-id="8c161-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="8c161-233">Autres éditeurs de texte, tels que :</span><span class="sxs-lookup"><span data-stu-id="8c161-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="8c161-234">Bloc-notes</span><span class="sxs-lookup"><span data-stu-id="8c161-234">Notepad</span></span>
  - <span data-ttu-id="8c161-235">Vim</span><span class="sxs-lookup"><span data-stu-id="8c161-235">vim</span></span>
  - <span data-ttu-id="8c161-236">Tout autre éditeur de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c161-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="8c161-237">Utilitaires d’édition de texte, tels que :</span><span class="sxs-lookup"><span data-stu-id="8c161-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="8c161-238">Opérateurs de redirection PowerShell comme `>` et `>>`</span><span class="sxs-lookup"><span data-stu-id="8c161-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="8c161-239">Programmes de transfert de fichiers, tels que :</span><span class="sxs-lookup"><span data-stu-id="8c161-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="8c161-240">Un navigateur web, lors du téléchargement de scripts</span><span class="sxs-lookup"><span data-stu-id="8c161-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="8c161-241">Un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="8c161-241">A file share</span></span>

<span data-ttu-id="8c161-242">Certains de ces outils traitent ses octets plutôt que du texte, mais d’autres offrent des configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="8c161-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="8c161-243">Dans les cas où vous devez configurer un encodage, vous devez faire en sorte qu’il soit identique à celui de votre éditeur afin d’éviter tout problème.</span><span class="sxs-lookup"><span data-stu-id="8c161-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="8c161-244">Autres ressources sur l’encodage dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c161-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="8c161-245">Il existe quelques autres billets intéressants sur l’encodage et sa configuration dans PowerShell qui méritent une lecture :</span><span class="sxs-lookup"><span data-stu-id="8c161-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="8c161-246">Synthèse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="8c161-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="8c161-247">Problèmes précédents ouverts sur vscode-PowerShell concernant l’encodage :</span><span class="sxs-lookup"><span data-stu-id="8c161-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="8c161-248">#1308</span><span class="sxs-lookup"><span data-stu-id="8c161-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="8c161-249">#1628</span><span class="sxs-lookup"><span data-stu-id="8c161-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="8c161-250">#1680</span><span class="sxs-lookup"><span data-stu-id="8c161-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="8c161-251">#1744</span><span class="sxs-lookup"><span data-stu-id="8c161-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="8c161-252">#1751</span><span class="sxs-lookup"><span data-stu-id="8c161-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="8c161-253">Article classique de *Joel on Software* concernant Unicode</span><span class="sxs-lookup"><span data-stu-id="8c161-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="8c161-254">Encodage dans .NET Standard</span><span class="sxs-lookup"><span data-stu-id="8c161-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


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
