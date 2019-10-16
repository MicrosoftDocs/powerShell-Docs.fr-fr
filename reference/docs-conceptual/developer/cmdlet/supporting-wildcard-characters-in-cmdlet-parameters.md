---
title: Prise en charge des caractères génériques dans les paramètres des applets de commande
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365308"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="0def8-102">Prise en charge des caractères génériques dans les paramètres des applets de commande</span><span class="sxs-lookup"><span data-stu-id="0def8-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="0def8-103">Souvent, vous devez concevoir une applet de commande à exécuter sur un groupe de ressources plutôt que sur une seule ressource.</span><span class="sxs-lookup"><span data-stu-id="0def8-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="0def8-104">Par exemple, une applet de commande peut avoir besoin de localiser tous les fichiers d’une banque de données qui ont le même nom ou extension.</span><span class="sxs-lookup"><span data-stu-id="0def8-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="0def8-105">Vous devez fournir la prise en charge des caractères génériques lors de la conception d’une applet de commande qui sera exécutée sur un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="0def8-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="0def8-106">L’utilisation de caractères génériques est parfois appelée *globbing*.</span><span class="sxs-lookup"><span data-stu-id="0def8-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="0def8-107">Applets de commande Windows PowerShell utilisant des caractères génériques</span><span class="sxs-lookup"><span data-stu-id="0def8-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="0def8-108">De nombreuses applets de commande Windows PowerShell prennent en charge les caractères génériques pour leurs valeurs de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0def8-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="0def8-109">Par exemple, presque toutes les applets de commande ayant un paramètre `Name` ou `Path` prennent en charge les caractères génériques pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="0def8-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="0def8-110">(Bien que la plupart des cmdlets ayant un paramètre `Path` aient également un paramètre `LiteralPath` qui ne prend pas en charge les caractères génériques.) La commande suivante montre comment un caractère générique est utilisé pour retourner toutes les applets de commande de la session active dont le nom contient le verbe obtenir.</span><span class="sxs-lookup"><span data-stu-id="0def8-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="0def8-111">Caractères génériques pris en charge</span><span class="sxs-lookup"><span data-stu-id="0def8-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="0def8-112">Windows PowerShell prend en charge les caractères génériques suivants.</span><span class="sxs-lookup"><span data-stu-id="0def8-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="0def8-113">Caractère générique</span><span class="sxs-lookup"><span data-stu-id="0def8-113">Wildcard</span></span> |                             <span data-ttu-id="0def8-114">Description</span><span class="sxs-lookup"><span data-stu-id="0def8-114">Description</span></span>                             |  <span data-ttu-id="0def8-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="0def8-115">Example</span></span>   |     <span data-ttu-id="0def8-116">Correspond à</span><span class="sxs-lookup"><span data-stu-id="0def8-116">Matches</span></span>      | <span data-ttu-id="0def8-117">Ne correspond pas</span><span class="sxs-lookup"><span data-stu-id="0def8-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="0def8-118">Correspond à zéro ou plusieurs caractères, en commençant à la position spécifiée</span><span class="sxs-lookup"><span data-stu-id="0def8-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="0def8-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="0def8-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="0def8-120">?</span><span class="sxs-lookup"><span data-stu-id="0def8-120">?</span></span>        | <span data-ttu-id="0def8-121">Correspond à n’importe quel caractère à la position spécifiée</span><span class="sxs-lookup"><span data-stu-id="0def8-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="0def8-122">, Dans, sur</span><span class="sxs-lookup"><span data-stu-id="0def8-122">An, in, on</span></span>       | <span data-ttu-id="0def8-123">antécédent</span><span class="sxs-lookup"><span data-stu-id="0def8-123">ran</span></span>            |
| <span data-ttu-id="0def8-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="0def8-124">[ ]</span></span>      | <span data-ttu-id="0def8-125">Correspond à une plage de caractères</span><span class="sxs-lookup"><span data-stu-id="0def8-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="0def8-126">livre, Cook, look</span><span class="sxs-lookup"><span data-stu-id="0def8-126">book, cook, look</span></span> | <span data-ttu-id="0def8-127">Nook, pris</span><span class="sxs-lookup"><span data-stu-id="0def8-127">nook, took</span></span>     |
| <span data-ttu-id="0def8-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="0def8-128">[ ]</span></span>      | <span data-ttu-id="0def8-129">Correspond aux caractères spécifiés</span><span class="sxs-lookup"><span data-stu-id="0def8-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="0def8-130">livre, Nook</span><span class="sxs-lookup"><span data-stu-id="0def8-130">book, nook</span></span>       | <span data-ttu-id="0def8-131">Cook, regarder</span><span class="sxs-lookup"><span data-stu-id="0def8-131">cook, look</span></span>     |

<span data-ttu-id="0def8-132">Lorsque vous concevez des applets de commande qui prennent en charge les caractères génériques, autorisez les combinaisons de caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="0def8-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="0def8-133">Par exemple, la commande suivante utilise l’applet de commande `Get-ChildItem` pour récupérer tous les fichiers. txt qui se trouvent dans le dossier c:\Techdocs et qui commencent par les lettres « a » à « l ».</span><span class="sxs-lookup"><span data-stu-id="0def8-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="0def8-134">La commande précédente utilise le caractère générique de plage `[a-l]` pour spécifier que le nom de fichier doit commencer par les caractères « a » à « l » et utilise le caractère générique `*` comme espace réservé pour tous les caractères entre la première lettre du nom de fichier et le fichier **. txt** extension.</span><span class="sxs-lookup"><span data-stu-id="0def8-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="0def8-135">L’exemple suivant utilise un modèle de caractère générique de plage qui exclut la lettre « d », mais inclut toutes les autres lettres de « a » à « f ».</span><span class="sxs-lookup"><span data-stu-id="0def8-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="0def8-136">Gestion des caractères littéraux dans les modèles de caractères génériques</span><span class="sxs-lookup"><span data-stu-id="0def8-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="0def8-137">Si le modèle de caractère générique que vous spécifiez contient des caractères littéraux qui ne doivent pas être interprétés comme des caractères génériques, utilisez le caractère de soulignement (`` ` ``) comme caractère d’échappement.</span><span class="sxs-lookup"><span data-stu-id="0def8-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="0def8-138">Lorsque vous spécifiez des caractères littéraux int l’API PowerShell, utilisez un seul cycle.</span><span class="sxs-lookup"><span data-stu-id="0def8-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="0def8-139">Lorsque vous spécifiez des caractères littéraux à l’invite de commandes PowerShell, utilisez deux cycles.</span><span class="sxs-lookup"><span data-stu-id="0def8-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="0def8-140">Par exemple, le modèle suivant contient deux crochets qui doivent être pris littéralement.</span><span class="sxs-lookup"><span data-stu-id="0def8-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="0def8-141">En cas d’utilisation dans l’API PowerShell, utilisez :</span><span class="sxs-lookup"><span data-stu-id="0def8-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="0def8-142">« John Smith \` [\* '] »</span><span class="sxs-lookup"><span data-stu-id="0def8-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="0def8-143">En cas d’utilisation à partir de l’invite de commandes PowerShell :</span><span class="sxs-lookup"><span data-stu-id="0def8-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="0def8-144">« John Smith \` @ no__t-1 [\* \` '] »</span><span class="sxs-lookup"><span data-stu-id="0def8-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="0def8-145">Ce modèle correspond à « John Smith [marketing] » ou « John Smith [Development] ».</span><span class="sxs-lookup"><span data-stu-id="0def8-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="0def8-146">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="0def8-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="0def8-147">Sortie de l’applet de commande et caractères génériques</span><span class="sxs-lookup"><span data-stu-id="0def8-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="0def8-148">Lorsque les paramètres d’applet de commande prennent en charge les caractères génériques, l’opération génère généralement une sortie de tableau.</span><span class="sxs-lookup"><span data-stu-id="0def8-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="0def8-149">Parfois, il n’est pas judicieux de prendre en charge une sortie de tableau, car l’utilisateur ne peut utiliser qu’un seul élément.</span><span class="sxs-lookup"><span data-stu-id="0def8-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="0def8-150">Par exemple, l’applet de commande `Set-Location` ne prend pas en charge la sortie de tableau, car l’utilisateur ne définit qu’un seul emplacement.</span><span class="sxs-lookup"><span data-stu-id="0def8-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="0def8-151">Dans ce cas, l’applet de commande prend toujours en charge les caractères génériques, mais elle force la résolution sur un emplacement unique.</span><span class="sxs-lookup"><span data-stu-id="0def8-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="0def8-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0def8-152">See Also</span></span>

[<span data-ttu-id="0def8-153">Écriture d’une applet de commande Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0def8-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="0def8-154">WildcardPattern, classe</span><span class="sxs-lookup"><span data-stu-id="0def8-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
