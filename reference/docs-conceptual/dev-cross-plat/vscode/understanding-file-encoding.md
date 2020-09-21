---
title: Présentation de l’encodage de fichier dans VS Code et PowerShell
description: Configuration de l’encodage de fichier dans VS Code et PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: a4b13bcfbe5cffc4e015a37a5fd64fbb8b91f949
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87900012"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a><span data-ttu-id="30848-103">Présentation de l’encodage de fichier dans VS Code et PowerShell</span><span class="sxs-lookup"><span data-stu-id="30848-103">Understanding file encoding in VS Code and PowerShell</span></span>

<span data-ttu-id="30848-104">Quand vous utilisez Visual Studio Code pour créer et modifier des scripts PowerShell, il est important que vos fichiers soient enregistrés à l’aide du format d’encodage de caractères approprié.</span><span class="sxs-lookup"><span data-stu-id="30848-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="30848-105">Qu’est-ce que l’encodage de fichier et pourquoi est-il important ?</span><span class="sxs-lookup"><span data-stu-id="30848-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="30848-106">VS Code gère l’interface entre un utilisateur qui entre des chaînes de caractères dans une mémoire tampon et la lecture/écriture de blocs d’octets dans le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="30848-106">VS Code manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="30848-107">Quand VS Code enregistre un fichier, il utilise un encodage de texte pour décider des octets attribués à chaque caractère.</span><span class="sxs-lookup"><span data-stu-id="30848-107">When VS Code saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span>

<span data-ttu-id="30848-108">De même, quand PowerShell exécute un script, il doit convertir les octets d’un fichier en caractères afin de reconstruire le fichier dans un programme PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30848-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="30848-109">Comme VS Code écrit le fichier et que PowerShell le lit, ils doivent utiliser le même système d’encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-109">Since VS Code writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="30848-110">Ce processus d’analyse d’un script PowerShell est le suivant : _octets_ -> _caractères_ -> _jetons_ ->  _arborescence de syntaxe abstraite_ -> _exécution_.</span><span class="sxs-lookup"><span data-stu-id="30848-110">This process of parsing a PowerShell script goes: _bytes_ -> _characters_ -> _tokens_ -> _abstract syntax tree_ -> _execution_.</span></span>

<span data-ttu-id="30848-111">VS Code et PowerShell sont tous deux installés avec une configuration d’encodage par défaut adéquate.</span><span class="sxs-lookup"><span data-stu-id="30848-111">Both VS Code and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="30848-112">Toutefois, l’encodage par défaut utilisée par PowerShell a changé avec la publication de PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="30848-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="30848-113">Pour être sûr de n’avoir aucun problème lors de l’utilisation de PowerShell ou de l’extension PowerShell dans VS Code, vous devez configurer vos paramètres VS Code et PowerShell correctement.</span><span class="sxs-lookup"><span data-stu-id="30848-113">To ensure you have no problems using PowerShell or the PowerShell extension in VS Code, you need to configure your VS Code and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="30848-114">Causes courantes de problèmes d’encodage</span><span class="sxs-lookup"><span data-stu-id="30848-114">Common causes of encoding issues</span></span>

<span data-ttu-id="30848-115">Des problèmes d’encodage se produisent quand l’encodage de VS Code ou de votre fichier de script ne correspond pas à l’encodage attendu par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30848-115">Encoding problems occur when the encoding of VS Code or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="30848-116">PowerShell ne dispose d’aucun moyen de déterminer automatiquement l’encodage du fichier.</span><span class="sxs-lookup"><span data-stu-id="30848-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="30848-117">Vous risquez davantage de rencontrer des problèmes d’encodage quand vous utilisez des caractères qui ne figurent pas dans le [jeu de caractères ASCII sept bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="30848-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="30848-118">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30848-118">For example:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="30848-119">les caractères non alphabétiques étendus comme le tiret cadratin (`—`), l’espace insécable (` `) ou le guillemet double gauche (`"`)</span><span class="sxs-lookup"><span data-stu-id="30848-119">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`"`)</span></span>
- <span data-ttu-id="30848-120">Les caractères latins accentués (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="30848-120">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="30848-121">Les caractères non latins tels que les caractères cyrilliques (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="30848-121">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="30848-122">Caractères CJC (`本`, `화`, `が`)</span><span class="sxs-lookup"><span data-stu-id="30848-122">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="30848-123">Les causes courantes des problèmes d’encodage sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="30848-123">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="30848-124">Les encodages par défaut de VS Code et PowerShell n’ont pas été changés.</span><span class="sxs-lookup"><span data-stu-id="30848-124">The encodings of VS Code and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="30848-125">Pour PowerShell 5.1 et antérieur, l’encodage par défaut est différent de celui de VS Code.</span><span class="sxs-lookup"><span data-stu-id="30848-125">For PowerShell 5.1 and below, the default encoding is different from VS Code's.</span></span>
- <span data-ttu-id="30848-126">Un autre éditeur a ouvert et remplacé le fichier dans un nouvel encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-126">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="30848-127">Cela se produit souvent avec l’environnement ISE.</span><span class="sxs-lookup"><span data-stu-id="30848-127">This often happens with the ISE.</span></span>
- <span data-ttu-id="30848-128">Le fichier est archivé dans le contrôle de code source dans un encodage différent de celui attendu par VS Code ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30848-128">The file is checked into source control in an encoding that is different from what VS Code or PowerShell expects.</span></span> <span data-ttu-id="30848-129">Cela peut se produire quand des collaborateurs utilisent des éditeurs avec différentes configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-129">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="30848-130">Comment savoir quand vous avez des problèmes d’encodage ?</span><span class="sxs-lookup"><span data-stu-id="30848-130">How to tell when you have encoding issues</span></span>

<span data-ttu-id="30848-131">Souvent, les erreurs d’encodage se présentent sous forme d’erreurs d’analyse dans les scripts.</span><span class="sxs-lookup"><span data-stu-id="30848-131">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="30848-132">Si vous remarquez des séquences de caractères étranges dans votre script, il peut s’agir de ce type de problème.</span><span class="sxs-lookup"><span data-stu-id="30848-132">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="30848-133">Dans l’exemple ci-dessous, les caractères `â€"` apparaissent à la place d’un tiret demi-cadratin (`–`) :</span><span class="sxs-lookup"><span data-stu-id="30848-133">In the example below, an en-dash (`–`) appears as the characters `â€"`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€"From $from â€"To $recipient1 â€"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="30848-134">Ce problème se produit car VS Code encode le caractère `–` en UTF-8 en tant qu’octets `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="30848-134">This problem occurs because VS Code encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span> <span data-ttu-id="30848-135">Quand ces octets sont décodés au format Windows-1252, ils sont interprétées en tant que caractères `â€"`.</span><span class="sxs-lookup"><span data-stu-id="30848-135">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€"`.</span></span>

<span data-ttu-id="30848-136">Voici quelques séquences de caractères étranges susceptibles d’apparaître :</span><span class="sxs-lookup"><span data-stu-id="30848-136">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="30848-137">`â€"` au lieu de `–`</span><span class="sxs-lookup"><span data-stu-id="30848-137">`â€"` instead of `–`</span></span>
- <span data-ttu-id="30848-138">`â€"` au lieu de `—`</span><span class="sxs-lookup"><span data-stu-id="30848-138">`â€"` instead of `—`</span></span>
- <span data-ttu-id="30848-139">`Ã„2` au lieu de `Ä`</span><span class="sxs-lookup"><span data-stu-id="30848-139">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="30848-140">`Â` au lieu de ` ` (espace insécable)</span><span class="sxs-lookup"><span data-stu-id="30848-140">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="30848-141">`Ã©` au lieu de `é`</span><span class="sxs-lookup"><span data-stu-id="30848-141">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="30848-142">Cette [référence](https://www.i18nqa.com/debug/utf8-debug.html) très pratique liste les modèles courants qui indiquent un problème d’encodage UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="30848-142">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a><span data-ttu-id="30848-143">Interaction entre l’extension PowerShell dans VS Code et les encodages</span><span class="sxs-lookup"><span data-stu-id="30848-143">How the PowerShell extension in VS Code interacts with encodings</span></span>

<span data-ttu-id="30848-144">L’extension PowerShell interagit avec les scripts de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="30848-144">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="30848-145">Quand les scripts sont modifiés dans VS Code, le contenu est envoyé par VS Code à l’extension.</span><span class="sxs-lookup"><span data-stu-id="30848-145">When scripts are edited in VS Code, the contents are sent by VS Code to the extension.</span></span> <span data-ttu-id="30848-146">Le [protocole de serveur de langage][] impose que ce contenu soit transféré en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30848-146">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="30848-147">Par conséquent, il n’est pas possible pour l’extension d’obtenir l’encodage incorrect.</span><span class="sxs-lookup"><span data-stu-id="30848-147">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
1. <span data-ttu-id="30848-148">Quand les scripts sont exécutés directement dans la console intégrée, ils sont lus directement à partir du fichier par PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30848-148">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="30848-149">Si l’encodage de PowerShell est différent de celui de VS Code, les choses peuvent mal tourner.</span><span class="sxs-lookup"><span data-stu-id="30848-149">If PowerShell's encoding differs from VS Code's, something can go wrong here.</span></span>
1. <span data-ttu-id="30848-150">Quand un script ouvert dans VS Code référence un autre script qui n’est pas ouvert dans VS Code, l’extension charge le contenu de ce script à partir du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="30848-150">When a script that is open in VS Code references another script that is not open in VS Code, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="30848-151">L’extension PowerShell utilise par défaut l’encodage UTF-8, mais elle utilise la détection de [marque d’ordre d’octet][] pour sélectionner l’encodage correct.</span><span class="sxs-lookup"><span data-stu-id="30848-151">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="30848-152">Le problème se produit en cas d’encodage des formats sans marque d’ordre d’octet (comme [UTF-8][] sans marque d’ordre d’octet et [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="30848-152">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span> <span data-ttu-id="30848-153">L’extension PowerShell utilise par défaut UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30848-153">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="30848-154">L’extension ne peut pas modifier les paramètres d’encodage de VS Code.</span><span class="sxs-lookup"><span data-stu-id="30848-154">The extension cannot change VS Code's encoding settings.</span></span> <span data-ttu-id="30848-155">Pour plus d’informations, consultez le [problème n°824](https://github.com/Microsoft/VSCode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="30848-155">For more information, see [issue #824](https://github.com/Microsoft/VSCode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="30848-156">Choix de l’encodage correct</span><span class="sxs-lookup"><span data-stu-id="30848-156">Choosing the right encoding</span></span>

<span data-ttu-id="30848-157">Différents systèmes et applications peuvent utiliser différents encodages :</span><span class="sxs-lookup"><span data-stu-id="30848-157">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="30848-158">Dans .NET Standard, sur le web et dans le monde de Linux, UTF-8 est désormais l’encodage dominant.</span><span class="sxs-lookup"><span data-stu-id="30848-158">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="30848-159">De nombreuses applications .NET Framework utilisent [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="30848-159">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="30848-160">Pour des raisons historiques, cet encodage est parfois appelé « Unicode », un terme qui fait aujourd’hui référence à une [norme](https://en.wikipedia.org/wiki/Unicode) étendue incluant UTF-8 et UTF-16.</span><span class="sxs-lookup"><span data-stu-id="30848-160">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="30848-161">Sur Windows, de nombreuses applications natives qui sont antérieures à Unicode continuent à utiliser Windows-1252 par défaut.</span><span class="sxs-lookup"><span data-stu-id="30848-161">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="30848-162">Avec les encodages Unicode, il existe également le concept de marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-162">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="30848-163">Les marques d’ordre d’octet sont présentes au début, et elles indiquent au décodeur l’encodage utilisé par le texte.</span><span class="sxs-lookup"><span data-stu-id="30848-163">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="30848-164">Pour les encodages multioctets, la marque d’ordre d’octet indique également le [mode Endian](https://en.wikipedia.org/wiki/Endianness) de l’encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-164">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="30848-165">Les marques d’ordre d’octet sont conçues pour être des octets qui se produisent rarement dans le texte non-Unicode, ce qui permet d’estimer avec une raisonnable certitude que le texte est au format Unicode quand une marque d’ordre d’octet est présente.</span><span class="sxs-lookup"><span data-stu-id="30848-165">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="30848-166">Les marques d’ordre d’octet sont facultatives, et leur adoption n’est pas aussi populaire dans le monde de Linux, car une convention fiable d’UTF-8 est utilisée partout.</span><span class="sxs-lookup"><span data-stu-id="30848-166">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="30848-167">La plupart des applications Linux partent du principe que l’entrée de texte est encodée en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30848-167">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="30848-168">Bien que de nombreuses applications Linux reconnaissent et gèrent correctement les marques d’ordre d’octet, toutes ne le font pas, ce qui génère des artefacts dans le texte manipulé avec ces applications.</span><span class="sxs-lookup"><span data-stu-id="30848-168">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="30848-169">**Par conséquent** :</span><span class="sxs-lookup"><span data-stu-id="30848-169">**Therefore**:</span></span>

- <span data-ttu-id="30848-170">Si vous travaillez principalement avec des applications Windows et Windows PowerShell, vous devez privilégier un encodage comme UTF-8 avec marque d’ordre d’octet ou UTF-16.</span><span class="sxs-lookup"><span data-stu-id="30848-170">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="30848-171">Si vous travaillez sur plusieurs plateformes, vous devez privilégier UTF-8 avec marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-171">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="30848-172">Si vous travaillez principalement dans des contextes associés à Linux, vous devez privilégier UTF-8 sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-172">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="30848-173">Windows-1252 et latin-1 sont essentiellement des encodages hérités que vous devez éviter dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="30848-173">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="30848-174">Toutefois, certaines applications Windows anciennes peuvent en dépendre.</span><span class="sxs-lookup"><span data-stu-id="30848-174">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="30848-175">Il convient également de noter que la signature de script est [dépendante du codage](https://github.com/PowerShell/PowerShell/issues/3466), ce qui signifie qu’un changement de l’encodage sur un script signé nécessitera une nouvelle signature.</span><span class="sxs-lookup"><span data-stu-id="30848-175">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vs-code"></a><span data-ttu-id="30848-176">Configuration de VS Code</span><span class="sxs-lookup"><span data-stu-id="30848-176">Configuring VS Code</span></span>

<span data-ttu-id="30848-177">L’encodage par défaut de VS Code est UTF-8 sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-177">VS Code's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="30848-178">Pour définir [Encodage de VS Code][], accédez aux paramètres VS Code (<kbd>Ctrl</kbd>+<kbd>,</kbd>) et définissez le paramètre `"files.encoding"` :</span><span class="sxs-lookup"><span data-stu-id="30848-178">To set [VS Code's encoding][], go to the VS Code settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="30848-179">Voici quelques valeurs possibles :</span><span class="sxs-lookup"><span data-stu-id="30848-179">Some possible values are:</span></span>

- <span data-ttu-id="30848-180">`utf8`: [UTF-8] sans marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="30848-180">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="30848-181">`utf8bom`: [UTF-8] avec marque d’ordre d’octet</span><span class="sxs-lookup"><span data-stu-id="30848-181">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="30848-182">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="30848-182">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="30848-183">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="30848-183">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="30848-184">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="30848-184">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="30848-185">Vous devez obtenir une liste déroulante pour cette option dans la vue de l’interface graphique utilisateur, ou une complétion dans la vue JSON.</span><span class="sxs-lookup"><span data-stu-id="30848-185">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="30848-186">Vous pouvez aussi ajouter les éléments suivants pour détecter automatiquement l’encodage quand c’est possible :</span><span class="sxs-lookup"><span data-stu-id="30848-186">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="30848-187">Si vous ne souhaitez pas que ces paramètres affectent tous les types de fichiers, VS Code autorise également les configurations propres à un langage.</span><span class="sxs-lookup"><span data-stu-id="30848-187">If you don't want these settings to affect all files types, VS Code also allows per-language configurations.</span></span> <span data-ttu-id="30848-188">Vous pouvez créer un paramètre propre au langage en plaçant des paramètres dans un champ `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="30848-188">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="30848-189">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="30848-189">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="30848-190">Configuration de PowerShell</span><span class="sxs-lookup"><span data-stu-id="30848-190">Configuring PowerShell</span></span>

<span data-ttu-id="30848-191">L’encodage par défaut de PowerShell varie en fonction de la version :</span><span class="sxs-lookup"><span data-stu-id="30848-191">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="30848-192">Dans PowerShell 6 et ultérieur, l’encodage par défaut est UTF-8 sans marque d’ordre d’octet sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="30848-192">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="30848-193">Dans Windows PowerShell, l’encodage par défaut est généralement Windows-1252, une extension de [latin-1][], également appelé ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="30848-193">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="30848-194">Dans PowerShell 5 et ultérieur, vous pouvez déterminer votre encodage comme suit :</span><span class="sxs-lookup"><span data-stu-id="30848-194">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="30848-195">Vous pouvez utiliser le [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) suivant pour déterminer quel encodage votre session PowerShell déduit pour un script sans marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-195">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="30848-196">Il est possible de configurer PowerShell pour utiliser plus généralement un encodage donné à l’aide de paramètres de profil.</span><span class="sxs-lookup"><span data-stu-id="30848-196">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span>
<span data-ttu-id="30848-197">Voir les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="30848-197">See the following articles:</span></span>

- <span data-ttu-id="30848-198">La réponse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="30848-198">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="30848-199">Le billet de blog de [@rkeithhill] concernant le [traitement de l’entrée UTF-8 sans marque d’ordre d’octet dans PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="30848-199">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="30848-200">Il n’est pas possible de forcer PowerShell à utiliser un encodage d’entrée spécifique.</span><span class="sxs-lookup"><span data-stu-id="30848-200">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="30848-201">PowerShell 5.1 et versions antérieures, s’exécutant sur Windows avec les paramètres régionaux définis sur en-US, utilise par défaut le codage Windows-1252 en l’absence de marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-201">PowerShell 5.1 and below, running on Windows with the locale set to en-US, defaults to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="30848-202">D’autres paramètres régionaux peuvent utiliser un codage différent.</span><span class="sxs-lookup"><span data-stu-id="30848-202">Other locale settings may use a different encoding.</span></span> <span data-ttu-id="30848-203">Pour garantir leur interopérabilité, il est préférable d’enregistrer les scripts dans un format Unicode avec une marque d’ordre d’octet.</span><span class="sxs-lookup"><span data-stu-id="30848-203">To ensure interoperability, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30848-204">Tout autre outil qui traite des scripts PowerShell est susceptible d’être affecté par vos options d’encodage ou de ré-encoder vos scripts en un autre encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-204">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="30848-205">Scripts existants</span><span class="sxs-lookup"><span data-stu-id="30848-205">Existing scripts</span></span>

<span data-ttu-id="30848-206">Vous devrez peut-être réencoder les scripts déjà présents sur le système de fichiers vers votre nouvel encodage choisi.</span><span class="sxs-lookup"><span data-stu-id="30848-206">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="30848-207">Dans la barre inférieure de VS Code, vous verrez l’étiquette UTF-8.</span><span class="sxs-lookup"><span data-stu-id="30848-207">In the bottom bar of VS Code, you'll see the label UTF-8.</span></span> <span data-ttu-id="30848-208">Cliquez dessus pour ouvrir la barre d’action et sélectionnez **Enregistrer avec encodage**.</span><span class="sxs-lookup"><span data-stu-id="30848-208">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="30848-209">Vous pouvez maintenant choisir un nouvel encodage pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="30848-209">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="30848-210">Pour des instructions complètes, consultez [Encodage de VS Code][].</span><span class="sxs-lookup"><span data-stu-id="30848-210">See [VS Code's encoding][] for full instructions.</span></span>

<span data-ttu-id="30848-211">Si vous avez besoin de ré-encoder plusieurs fichiers, vous pouvez utiliser le script suivant :</span><span class="sxs-lookup"><span data-stu-id="30848-211">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="30848-212">Environnement d'écriture de scripts intégré (ISE) de PowerShell</span><span class="sxs-lookup"><span data-stu-id="30848-212">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="30848-213">Si vous modifiez également des scripts à l’aide de PowerShell ISE, vous devez y synchroniser vos paramètres d’encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-213">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="30848-214">L’environnement ISE doit respecter une marque d’ordre d’octet, mais il est également possible d’utiliser la réflexion pour [définir l’encodage](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="30848-214">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="30848-215">Notez que cela ne serait pas conservé d’un démarrage à un autre.</span><span class="sxs-lookup"><span data-stu-id="30848-215">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="30848-216">Logiciels de contrôle de code source</span><span class="sxs-lookup"><span data-stu-id="30848-216">Source control software</span></span>

<span data-ttu-id="30848-217">Certains outils de contrôle de code source, tels que GIT, ignorent les encodages. GIT ne fait que suivre les octets.</span><span class="sxs-lookup"><span data-stu-id="30848-217">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span> <span data-ttu-id="30848-218">Ce n’est pas forcément le cas de tous, comme Azure DevOps ou Mercurial.</span><span class="sxs-lookup"><span data-stu-id="30848-218">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="30848-219">Même certains outils GIT s’appuient sur le décodage du texte.</span><span class="sxs-lookup"><span data-stu-id="30848-219">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="30848-220">Quand c’est le cas, veillez à :</span><span class="sxs-lookup"><span data-stu-id="30848-220">When this is the case, make sure you:</span></span>

- <span data-ttu-id="30848-221">Configurer l’encodage du texte dans votre contrôle de code source pour qu’il corresponde à votre configuration de VS Code.</span><span class="sxs-lookup"><span data-stu-id="30848-221">Configure the text encoding in your source control to match your VS Code configuration.</span></span>
- <span data-ttu-id="30848-222">Vérifier que tous vos fichiers sont archivés dans le contrôle de code source dans l’encodage approprié.</span><span class="sxs-lookup"><span data-stu-id="30848-222">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="30848-223">Méfiez-vous des modifications apportées à l’encodage reçues par le biais du contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="30848-223">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="30848-224">Un exemple courant est quand une comparaison indique des changements, mais que rien ne semble avoir été changé (car les octets ont changé, mais pas les caractères).</span><span class="sxs-lookup"><span data-stu-id="30848-224">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="30848-225">Environnements des collaborateurs</span><span class="sxs-lookup"><span data-stu-id="30848-225">Collaborators' environments</span></span>

<span data-ttu-id="30848-226">En plus de la configuration du contrôle de code source, veillez à ce que vos collaborateurs qui travaillent sur des fichiers que vous partagez n’aient pas de paramètres qui remplacent votre encodage en réencodant les fichiers PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30848-226">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="30848-227">Autres programmes</span><span class="sxs-lookup"><span data-stu-id="30848-227">Other programs</span></span>

<span data-ttu-id="30848-228">Tout autre programme qui lit ou écrit un script PowerShell est susceptible de le ré-encoder.</span><span class="sxs-lookup"><span data-stu-id="30848-228">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="30848-229">Quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="30848-229">Some examples are:</span></span>

- <span data-ttu-id="30848-230">Utilisation du Presse-papiers pour copier et coller un script.</span><span class="sxs-lookup"><span data-stu-id="30848-230">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="30848-231">C’est courant dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="30848-231">This is common in scenarios like:</span></span>
  - <span data-ttu-id="30848-232">Copie d’un script dans une machine virtuelle</span><span class="sxs-lookup"><span data-stu-id="30848-232">Copying a script into a VM</span></span>
  - <span data-ttu-id="30848-233">Copie d’un script à partir d’un e-mail ou d’une page web</span><span class="sxs-lookup"><span data-stu-id="30848-233">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="30848-234">Copie d’un script dans ou à partir d’un document Microsoft Word ou PowerPoint</span><span class="sxs-lookup"><span data-stu-id="30848-234">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="30848-235">Autres éditeurs de texte, tels que :</span><span class="sxs-lookup"><span data-stu-id="30848-235">Other text editors, such as:</span></span>
  - <span data-ttu-id="30848-236">Bloc-notes</span><span class="sxs-lookup"><span data-stu-id="30848-236">Notepad</span></span>
  - <span data-ttu-id="30848-237">Vim</span><span class="sxs-lookup"><span data-stu-id="30848-237">vim</span></span>
  - <span data-ttu-id="30848-238">Tout autre éditeur de script PowerShell</span><span class="sxs-lookup"><span data-stu-id="30848-238">Any other PowerShell script editor</span></span>
- <span data-ttu-id="30848-239">Utilitaires d’édition de texte, tels que :</span><span class="sxs-lookup"><span data-stu-id="30848-239">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="30848-240">Opérateurs de redirection PowerShell comme `>` et `>>`</span><span class="sxs-lookup"><span data-stu-id="30848-240">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="30848-241">Programmes de transfert de fichiers, tels que :</span><span class="sxs-lookup"><span data-stu-id="30848-241">File transfer programs, like:</span></span>
  - <span data-ttu-id="30848-242">Un navigateur web, lors du téléchargement de scripts</span><span class="sxs-lookup"><span data-stu-id="30848-242">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="30848-243">Un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="30848-243">A file share</span></span>

<span data-ttu-id="30848-244">Certains de ces outils traitent ses octets plutôt que du texte, mais d’autres offrent des configurations d’encodage.</span><span class="sxs-lookup"><span data-stu-id="30848-244">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="30848-245">Dans les cas où vous devez configurer un encodage, vous devez faire en sorte qu’il soit identique à celui de votre éditeur afin d’éviter tout problème.</span><span class="sxs-lookup"><span data-stu-id="30848-245">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="30848-246">Autres ressources sur l’encodage dans PowerShell</span><span class="sxs-lookup"><span data-stu-id="30848-246">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="30848-247">Il existe quelques autres billets intéressants sur l’encodage et sa configuration dans PowerShell qui méritent une lecture :</span><span class="sxs-lookup"><span data-stu-id="30848-247">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="30848-248">Synthèse de [@mklement0] concernant l’[encodage PowerShell sur StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="30848-248">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="30848-249">Problèmes précédents ouverts sur VS Code-PowerShell concernant l’encodage :</span><span class="sxs-lookup"><span data-stu-id="30848-249">Previous issues opened on VS Code-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="30848-250">#1308</span><span class="sxs-lookup"><span data-stu-id="30848-250">#1308</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [<span data-ttu-id="30848-251">#1628</span><span class="sxs-lookup"><span data-stu-id="30848-251">#1628</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [<span data-ttu-id="30848-252">#1680</span><span class="sxs-lookup"><span data-stu-id="30848-252">#1680</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [<span data-ttu-id="30848-253">#1744</span><span class="sxs-lookup"><span data-stu-id="30848-253">#1744</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [<span data-ttu-id="30848-254">#1751</span><span class="sxs-lookup"><span data-stu-id="30848-254">#1751</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [<span data-ttu-id="30848-255">Article classique de _Joel on Software_ concernant Unicode</span><span class="sxs-lookup"><span data-stu-id="30848-255">The classic _Joel on Software_ write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="30848-256">Encodage dans .NET Standard</span><span class="sxs-lookup"><span data-stu-id="30848-256">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

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
[Encodage de VS Code]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VS Code's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
