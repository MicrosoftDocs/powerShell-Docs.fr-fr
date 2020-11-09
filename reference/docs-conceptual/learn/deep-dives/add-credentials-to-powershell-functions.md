---
title: Ajout de la prise en charge des informations d’identification aux fonctions PowerShell
description: Ajout des paramètres d’informations d’identification à vos scripts, fonctions et applets de commande PowerShell.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354624"
---
# <a name="add-credential-support-to-powershell-functions"></a><span data-ttu-id="ca935-103">Ajout de la prise en charge des informations d’identification aux fonctions PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca935-103">Add Credential support to PowerShell functions</span></span>

> [!NOTE]
> <span data-ttu-id="ca935-104">La [Version d’origine][] de cet article est parue sur le blog écrit par [@joshduffney][].</span><span class="sxs-lookup"><span data-stu-id="ca935-104">The [original version][] of this article appeared on the blog written by [@joshduffney][].</span></span> <span data-ttu-id="ca935-105">Cet article a été modifié pour être inclus sur ce site.</span><span class="sxs-lookup"><span data-stu-id="ca935-105">This article has been edited for inclusion on this site.</span></span> <span data-ttu-id="ca935-106">L’équipe PowerShell remercie Josh d’avoir partagé ce contenu.</span><span class="sxs-lookup"><span data-stu-id="ca935-106">The PowerShell team thanks Josh for sharing this content with us.</span></span> <span data-ttu-id="ca935-107">Consultez son blog à l’adresse [duffney.io][].</span><span class="sxs-lookup"><span data-stu-id="ca935-107">Please check out his blog at [duffney.io][].</span></span>

<span data-ttu-id="ca935-108">Cet article explique comment (et pourquoi) ajouter des paramètres d’informations d’identification aux fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca935-108">This article shows you how to add credential parameters to PowerShell functions and why you'd want to.</span></span> <span data-ttu-id="ca935-109">Un paramètre d’informations d'identification vous permet d’exécuter la fonction ou l’applet de commande en tant qu’autre utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ca935-109">A credential parameter is to allow you to run the function or cmdlet as a different user.</span></span> <span data-ttu-id="ca935-110">L’utilisation la plus courante consiste à exécuter la fonction ou l’applet de commande en tant que compte d’utilisateur avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="ca935-110">The most common use is to run the function or cmdlet as an elevated user account.</span></span>

<span data-ttu-id="ca935-111">Par exemple, l’applet de commande `New-ADUser` inclut un paramètre d’ **informations d’identification** , qui fournit des informations d’identification d’administrateur de domaine pour créer un compte dans un domaine.</span><span class="sxs-lookup"><span data-stu-id="ca935-111">For example, the cmdlet `New-ADUser` has a **Credential** parameter, which you could provide domain admin credentials to create an account in a domain.</span></span> <span data-ttu-id="ca935-112">On suppose que votre compte normal exécutant la session PowerShell ne dispose pas déjà de cet accès.</span><span class="sxs-lookup"><span data-stu-id="ca935-112">Assuming your normal account running the PowerShell session doesn't have that access already.</span></span>

## <a name="creating-credential-object"></a><span data-ttu-id="ca935-113">Création d’un objet d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="ca935-113">Creating credential object</span></span>

<span data-ttu-id="ca935-114">L’objet [PSCredential][] représente un ensemble d’informations d’identification de sécurité comme un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-114">The [PSCredential][] object represents a set of security credentials such as a user name and password.</span></span> <span data-ttu-id="ca935-115">L’objet peut être passé en tant que paramètre à une fonction qui s’exécute en tant que compte d’utilisateur dans cet objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-115">The object can be passed as a parameter to a function that runs as the user account in that credential object.</span></span> <span data-ttu-id="ca935-116">Vous pouvez créer un objet d’informations d’identification de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="ca935-116">There are a few ways that you can create a credential object.</span></span> <span data-ttu-id="ca935-117">La première façon de créer un objet d’informations d’identification consiste à utiliser l’applet de commande PowerShell `Get-Credential`.</span><span class="sxs-lookup"><span data-stu-id="ca935-117">The first way to create a credential object is to use the PowerShell cmdlet `Get-Credential`.</span></span> <span data-ttu-id="ca935-118">Lorsque vous exécutez sans paramètres, vous êtes invité à entrer un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-118">When you run without parameters, it prompts you for a username and password.</span></span> <span data-ttu-id="ca935-119">Ou vous pouvez appeler l’applet de commande avec quelques paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="ca935-119">Or you can call the cmdlet with some optional parameters.</span></span>

<span data-ttu-id="ca935-120">Pour spécifier à l’avance le nom de domaine et le nom d’utilisateur, vous pouvez utiliser les paramètres **Credential** ou **UserName**.</span><span class="sxs-lookup"><span data-stu-id="ca935-120">To specify the domain name and username ahead of time you can use either the **Credential** or **UserName** parameters.</span></span> <span data-ttu-id="ca935-121">Quand vous utilisez le paramètre **UserName** , vous devez également fournir une valeur **Message**.</span><span class="sxs-lookup"><span data-stu-id="ca935-121">When you use the **UserName** parameter, you're also required to provide a **Message** value.</span></span> <span data-ttu-id="ca935-122">Le code ci-dessous montre l’utilisation de l’applet de commande.</span><span class="sxs-lookup"><span data-stu-id="ca935-122">The code below demonstrates using the cmdlet.</span></span> <span data-ttu-id="ca935-123">Vous pouvez également stocker l’objet d’informations d’identification dans une variable afin de pouvoir utiliser les informations d’identification plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="ca935-123">You can also store the credential object in a variable so that you can use the credential multiple times.</span></span> <span data-ttu-id="ca935-124">Dans l’exemple ci-dessous, l’objet d’informations d’identification est stocké dans la variable `$Cred`.</span><span class="sxs-lookup"><span data-stu-id="ca935-124">In the example below, the credential object is stored in the variable `$Cred`.</span></span>

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

<span data-ttu-id="ca935-125">Parfois, vous ne pouvez pas utiliser la méthode interactive de création d’objets d’informations d’identification présentée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="ca935-125">Sometimes, you can't use the interactive method of creating credential objects shown in the previous example.</span></span> <span data-ttu-id="ca935-126">La plupart des outils d’automatisation requièrent une méthode non interactive.</span><span class="sxs-lookup"><span data-stu-id="ca935-126">Most automation tools require a non-interactive method.</span></span> <span data-ttu-id="ca935-127">Pour créer des informations d’identification sans intervention de l’utilisateur, créez une chaîne sécurisée contenant le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-127">To create a credential without user interaction, create a secure string containing the password.</span></span> <span data-ttu-id="ca935-128">Passez ensuite la chaîne sécurisée et le nom d’utilisateur à la méthode `System.Management.Automation.PSCredential()`.</span><span class="sxs-lookup"><span data-stu-id="ca935-128">Then pass the secure string and user name to the `System.Management.Automation.PSCredential()` method.</span></span>

<span data-ttu-id="ca935-129">Utilisez la commande suivante pour créer une chaîne sécurisée contenant le mot de passe :</span><span class="sxs-lookup"><span data-stu-id="ca935-129">Use the following command to create a secure string containing the password:</span></span>

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

<span data-ttu-id="ca935-130">Les paramètres **AsPlainText** et **Force** sont requis.</span><span class="sxs-lookup"><span data-stu-id="ca935-130">Both the **AsPlainText** and **Force** parameters are required.</span></span> <span data-ttu-id="ca935-131">Sans ces paramètres, vous recevez un message d’avertissement indiquant que vous ne devez pas passer un texte brut dans une chaîne sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ca935-131">Without those parameters, you receive a message warning that you shouldn't pass plain text into a secure string.</span></span> <span data-ttu-id="ca935-132">PowerShell retourne cet avertissement, car le mot de passe en texte brut est enregistré dans différents journaux.</span><span class="sxs-lookup"><span data-stu-id="ca935-132">PowerShell returns this warning because the plain text password gets recorded in various logs.</span></span> <span data-ttu-id="ca935-133">Une fois que vous avez créé une chaîne sécurisée, vous devez la passer à la méthode `PSCredential()` pour créer l’objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-133">Once you have a secure string created, you need to pass it to the `PSCredential()` method to create the credential object.</span></span> <span data-ttu-id="ca935-134">Dans l’exemple suivant, la variable `$password` contient la chaîne sécurisée `$Cred` contenant l’objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-134">In the following example, the variable `$password` contains the secure string `$Cred` contains the credential object.</span></span>

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

<span data-ttu-id="ca935-135">Maintenant que vous savez comment créer des objets d’informations d’identification, vous pouvez ajouter des paramètres d’informations d’identification à vos fonctions PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca935-135">Now that you know how to create credential objects, you can add credential parameters to your PowerShell functions.</span></span>

## <a name="adding-a-credential-parameter"></a><span data-ttu-id="ca935-136">Ajout d’un paramètre Credential</span><span class="sxs-lookup"><span data-stu-id="ca935-136">Adding a Credential Parameter</span></span>

<span data-ttu-id="ca935-137">Comme tout autre paramètre, vous commencez par l’ajouter dans le bloc `param` de votre fonction.</span><span class="sxs-lookup"><span data-stu-id="ca935-137">Just like any other parameter, you start off by adding it in the `param` block of your function.</span></span>
<span data-ttu-id="ca935-138">Il est recommandé de nommer le paramètre `$Credential`, car il s’agit du nom que les applets de commande PowerShell existantes utilisent.</span><span class="sxs-lookup"><span data-stu-id="ca935-138">It's recommended that you name the parameter `$Credential` because that's what existing PowerShell cmdlets use.</span></span> <span data-ttu-id="ca935-139">Le type de paramètre devrait être `[System.Management.Automation.PSCredential]`.</span><span class="sxs-lookup"><span data-stu-id="ca935-139">The type of the parameter should be `[System.Management.Automation.PSCredential]`.</span></span>

<span data-ttu-id="ca935-140">L’exemple suivant montre le bloc de paramètres pour une fonction appelée `Get-Something`.</span><span class="sxs-lookup"><span data-stu-id="ca935-140">The following example shows the parameter block for a function called `Get-Something`.</span></span> <span data-ttu-id="ca935-141">Ce bloc contient deux paramètres : `$Name` et `$Credential`.</span><span class="sxs-lookup"><span data-stu-id="ca935-141">It has two parameters: `$Name` and `$Credential`.</span></span>

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

<span data-ttu-id="ca935-142">Le code de cet exemple est suffisant pour avoir un paramètre d’informations d’identification fonctionnel, mais il existe quelques éléments que vous pouvez ajouter pour le rendre plus robuste.</span><span class="sxs-lookup"><span data-stu-id="ca935-142">The code in this example is enough to have a working credential parameter, however there are a few things you can add to make it more robust.</span></span>

- <span data-ttu-id="ca935-143">Ajoutez l’attribut de validation `[ValidateNotNull()]` pour vérifier la valeur passée à **Credential**.</span><span class="sxs-lookup"><span data-stu-id="ca935-143">Add the `[ValidateNotNull()]` validation attribute to check that the value being passed to **Credential**.</span></span> <span data-ttu-id="ca935-144">Si la valeur du paramètre est null, cet attribut empêche la fonction de s’exécuter avec des informations d’identification non valides.</span><span class="sxs-lookup"><span data-stu-id="ca935-144">If the parameter value is null, this attribute prevents the function from executing with invalid credentials.</span></span>

- <span data-ttu-id="ca935-145">Ajoutez `[System.Management.Automation.Credential()]`.</span><span class="sxs-lookup"><span data-stu-id="ca935-145">Add `[System.Management.Automation.Credential()]`.</span></span> <span data-ttu-id="ca935-146">Cela vous permet de passer un nom d’utilisateur en tant que chaîne et d’obtenir une invite interactive pour le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-146">This allows you to pass in a username as a string and have an interactive prompt for the password.</span></span>

- <span data-ttu-id="ca935-147">Attribuez au paramètre `$Credential` la valeur par défaut `[System.Management.Automation.PSCredential]::Empty`.</span><span class="sxs-lookup"><span data-stu-id="ca935-147">Set a default value for the `$Credential` parameter to `[System.Management.Automation.PSCredential]::Empty`.</span></span> <span data-ttu-id="ca935-148">Votre fonction vous permet de passer cet objet `$Credential` à des applets de commande PowerShell existantes.</span><span class="sxs-lookup"><span data-stu-id="ca935-148">Your function you might be passing this `$Credential` object to existing PowerShell cmdlets.</span></span> <span data-ttu-id="ca935-149">Si vous fournissez une valeur null à l’applet de commande appelée à l’intérieur de votre fonction, une erreur se produit.</span><span class="sxs-lookup"><span data-stu-id="ca935-149">Providing a null value to the cmdlet called inside your function causes an error.</span></span> <span data-ttu-id="ca935-150">Pour éviter cette erreur, fournissez un objet d’informations d’identification vide.</span><span class="sxs-lookup"><span data-stu-id="ca935-150">Providing an empty credential object avoids this error.</span></span>

> [!TIP]
> <span data-ttu-id="ca935-151">Certaines applets de commande qui acceptent un paramètre Credential ne prennent pas en charge `[System.Management.Automation.PSCredential]::Empty` comme elles le devraient.</span><span class="sxs-lookup"><span data-stu-id="ca935-151">Some cmdlets that accept a credential parameter do not support `[System.Management.Automation.PSCredential]::Empty` as they should.</span></span> <span data-ttu-id="ca935-152">Pour obtenir une solution de contournement, consultez la section [Utilisation d’applets de commande héritées](#dealing-with-legacy-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="ca935-152">See the [Dealing with Legacy Cmdlets](#dealing-with-legacy-cmdlets) section for a workaround.</span></span>

## <a name="using-credential-parameters"></a><span data-ttu-id="ca935-153">Utilisation des paramètres d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="ca935-153">Using credential parameters</span></span>

<span data-ttu-id="ca935-154">L’exemple suivant illustre l’utilisation des paramètres d’informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-154">The following example demonstrates how to use credential parameters.</span></span> <span data-ttu-id="ca935-155">Cet exemple montre une fonction appelée `Set-RemoteRegistryValue`, tirée de [The Pester Book][].</span><span class="sxs-lookup"><span data-stu-id="ca935-155">This example shows a function called `Set-RemoteRegistryValue`, which is out of [The Pester Book][].</span></span> <span data-ttu-id="ca935-156">Cette fonction définit le paramètre d’informations d’identification à l’aide des techniques décrites dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="ca935-156">This function defines the credential parameter using the techniques describe in the previous section.</span></span> <span data-ttu-id="ca935-157">La fonction appelle `Invoke-Command` à l’aide de la variable `$Credential` créée par la fonction.</span><span class="sxs-lookup"><span data-stu-id="ca935-157">The function calls `Invoke-Command` using the `$Credential` variable created by the function.</span></span> <span data-ttu-id="ca935-158">Cela vous permet de modifier l’utilisateur qui exécute `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="ca935-158">This allows you to change the user who's running `Invoke-Command`.</span></span> <span data-ttu-id="ca935-159">Étant donné que la valeur par défaut de `$Credential` est une information d’identification vide, la fonction peut s’exécuter sans fournir d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-159">Because the default value of `$Credential` is an empty credential, the function can run without providing credentials.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

<span data-ttu-id="ca935-160">Les sections suivantes présentent différentes méthodes permettant de fournir des informations d’identification à `Set-RemoteRegistryValue`.</span><span class="sxs-lookup"><span data-stu-id="ca935-160">The following sections show different methods of providing credentials to `Set-RemoteRegistryValue`.</span></span>

### <a name="prompting-for-credentials"></a><span data-ttu-id="ca935-161">Demande d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="ca935-161">Prompting for credentials</span></span>

<span data-ttu-id="ca935-162">L’utilisation de `Get-Credential` entre parenthèses `()` au moment de l’exécution lance en premier l’exécution de `Get-credential`.</span><span class="sxs-lookup"><span data-stu-id="ca935-162">Using `Get-Credential` in parentheses `()` at run time causes the `Get-credential` to run first.</span></span> <span data-ttu-id="ca935-163">Vous êtes invité à entrer un nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-163">You are prompted for a username and password.</span></span> <span data-ttu-id="ca935-164">Vous pouvez utiliser les paramètres **Credential** ou **UserName** de `Get-credential` pour préremplir le nom d’utilisateur et le domaine.</span><span class="sxs-lookup"><span data-stu-id="ca935-164">You could use the **Credential** or **UserName** parameters of `Get-credential` to pre-populate the username and domain.</span></span> <span data-ttu-id="ca935-165">L’exemple suivant utilise une technique appelée « projection » pour passer des paramètres à la fonction `Set-RemoteRegistryValue`.</span><span class="sxs-lookup"><span data-stu-id="ca935-165">The following example uses a technique called splatting to pass parameters to the `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="ca935-166">Pour plus d’informations sur la projection, consultez l’article [about_Splatting][].</span><span class="sxs-lookup"><span data-stu-id="ca935-166">For more information about splatting, check out the [about_Splatting][] article.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Obtenir des informations d’identification au moment de l’exécution](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

<span data-ttu-id="ca935-168">L’utilisation de `(Get-Credential)` semble laborieuse.</span><span class="sxs-lookup"><span data-stu-id="ca935-168">Using `(Get-Credential)` seems cumbersome.</span></span> <span data-ttu-id="ca935-169">En règle générale, lorsque vous utilisez le paramètre **Credential** avec un nom d’utilisateur uniquement, l’applet de commande vous invite automatiquement à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-169">Normally, when you use the **Credential** parameter with only a username, the cmdlet automatically prompts for the password.</span></span> <span data-ttu-id="ca935-170">L’attribut `[System.Management.Automation.Credential()]` active ce comportement.</span><span class="sxs-lookup"><span data-stu-id="ca935-170">The `[System.Management.Automation.Credential()]` attribute enables this behavior.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Demander les informations d’identification](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> <span data-ttu-id="ca935-172">Pour définir la valeur de Registre indiquée, ces exemples supposent que vous avez installé les fonctionnalités **Serveur Web** de Windows.</span><span class="sxs-lookup"><span data-stu-id="ca935-172">To set the registry value shown, these examples assume you have the **Web Server** features of Windows installed.</span></span> <span data-ttu-id="ca935-173">Exécutez `Install-WindowsFeature Web-Server` et `Install-WindowsFeature web-mgmt-tools` si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ca935-173">Run `Install-WindowsFeature Web-Server` and `Install-WindowsFeature web-mgmt-tools` if required.</span></span>

### <a name="provide-credentials-in-a-variable"></a><span data-ttu-id="ca935-174">Fournir les informations d’identification dans une variable</span><span class="sxs-lookup"><span data-stu-id="ca935-174">Provide credentials in a variable</span></span>

<span data-ttu-id="ca935-175">Vous pouvez également remplir une variable d’informations d’identification à l’avance et la passer au paramètre **Credential** de la fonction `Set-RemoteRegistryValue`.</span><span class="sxs-lookup"><span data-stu-id="ca935-175">You can also populate a credential variable ahead of time and pass it to the **Credential** parameter of `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="ca935-176">Utilisez cette méthode avec les outils d’intégration continue / de déploiement continu (CI/CD) tels que Jenkins, TeamCity et Octopus Deploy.</span><span class="sxs-lookup"><span data-stu-id="ca935-176">Use this method with Continuous Integration / Continuous Deployment (CI/CD) tools such as Jenkins, TeamCity, and Octopus Deploy.</span></span> <span data-ttu-id="ca935-177">Pour obtenir un exemple d’utilisation de Jenkins, consultez le billet de blog de Hodge [Automating with Jenkins and PowerShell on Windows - Part 2][].</span><span class="sxs-lookup"><span data-stu-id="ca935-177">For an example using Jenkins, check out Hodge's blog post [Automating with Jenkins and PowerShell on Windows - Part 2][].</span></span>

<span data-ttu-id="ca935-178">Cet exemple utilise la méthode .NET pour créer l’objet d’informations d’identification et une chaîne sécurisée pour passer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-178">This example uses the .NET method to create the credential object and a secure string to pass in the password.</span></span>

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

<span data-ttu-id="ca935-179">Pour cet exemple, la chaîne sécurisée est créée à l’aide d’un mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="ca935-179">For this example, the secure string is created using a clear text password.</span></span> <span data-ttu-id="ca935-180">Tous les outils CI/CD mentionnés précédemment ont une méthode sécurisée pour fournir ce mot de passe au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ca935-180">All of the previously mentioned CI/CD have a secure method of providing that password at run time.</span></span> <span data-ttu-id="ca935-181">Lorsque vous utilisez ces outils, remplacez le mot de passe en texte brut par la variable définie dans l’outil CI/CD que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="ca935-181">When using those tools, replace the plain text password with the variable defined within the CI/CD tool you use.</span></span>

### <a name="run-without-credentials"></a><span data-ttu-id="ca935-182">Exécuter sans informations d’identification</span><span class="sxs-lookup"><span data-stu-id="ca935-182">Run without credentials</span></span>

<span data-ttu-id="ca935-183">Comme `$Credential` est défini par défaut sur un objet d’informations d’identification vide, vous pouvez exécuter la commande sans informations d’identification, comme illustré dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="ca935-183">Since `$Credential` defaults to an empty credential object, you can run the command without credentials, as shown in this example:</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a><span data-ttu-id="ca935-184">Utilisation d’applets de commande héritées</span><span class="sxs-lookup"><span data-stu-id="ca935-184">Dealing with legacy cmdlets</span></span>

<span data-ttu-id="ca935-185">Toutes les applets de commande ne prennent pas en charge les objets d’informations d’identification, ou n’autorisent pas les informations d’identification vides.</span><span class="sxs-lookup"><span data-stu-id="ca935-185">Not all cmdlets support credential objects or allow empty credentials.</span></span> <span data-ttu-id="ca935-186">Au lieu de cela, l’applet de commande exige que les paramètres de nom d'utilisateur et de mot de passe soient des chaînes.</span><span class="sxs-lookup"><span data-stu-id="ca935-186">Instead, the cmdlet wants username and password parameters as strings.</span></span> <span data-ttu-id="ca935-187">Il existe plusieurs façons de contourner cette limitation.</span><span class="sxs-lookup"><span data-stu-id="ca935-187">There are a few ways to work around this limitation.</span></span>

### <a name="using-if-else-to-handle-empty-credentials"></a><span data-ttu-id="ca935-188">Utilisation de if-else pour gérer les informations d’identification vides</span><span class="sxs-lookup"><span data-stu-id="ca935-188">Using if-else to handle empty credentials</span></span>

<span data-ttu-id="ca935-189">Dans ce scénario, l’applet de commande que vous souhaitez exécuter n’accepte pas d’objet d’informations d’identification vide.</span><span class="sxs-lookup"><span data-stu-id="ca935-189">In this scenario, the cmdlet you want to run doesn't accept an empty credential object.</span></span> <span data-ttu-id="ca935-190">Cet exemple ajoute le paramètre **Credential** à `Invoke-Command` uniquement s’il n’est pas vide.</span><span class="sxs-lookup"><span data-stu-id="ca935-190">This example adds the **Credential** parameter to `Invoke-Command` only if it's not empty.</span></span> <span data-ttu-id="ca935-191">Sinon, il exécute `Invoke-Command` sans le paramètre **Credential**.</span><span class="sxs-lookup"><span data-stu-id="ca935-191">Otherwise, it runs the `Invoke-Command` without the **Credential** parameter.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a><span data-ttu-id="ca935-192">Utilisation de la projection pour gérer les informations d’identification vides</span><span class="sxs-lookup"><span data-stu-id="ca935-192">Using splatting to handle empty credentials</span></span>

<span data-ttu-id="ca935-193">Cet exemple utilise la projection de paramètres pour appeler l’applet de commande héritée.</span><span class="sxs-lookup"><span data-stu-id="ca935-193">This example uses parameter splatting to call the legacy cmdlet.</span></span> <span data-ttu-id="ca935-194">L’objet `$Credential` est ajouté de manière conditionnelle à la table de hachage pour la projection, ce qui évite d’avoir à répéter le bloc de script `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="ca935-194">The `$Credential` object is conditionally added to the hash table for splatting and avoids the need to repeat the `Invoke-Command` script block.</span></span> <span data-ttu-id="ca935-195">Pour en savoir plus sur la projection à l’intérieur de fonctions, consultez le billet de blog [Splatting Parameters Inside Advanced Functions][].</span><span class="sxs-lookup"><span data-stu-id="ca935-195">To learn more about splatting inside functions, see the [Splatting Parameters Inside Advanced Functions][] blog post.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a><span data-ttu-id="ca935-196">Utilisation de mots de passe de chaînes</span><span class="sxs-lookup"><span data-stu-id="ca935-196">Working with string passwords</span></span>

<span data-ttu-id="ca935-197">L’applet de commande `Invoke-Sqlcmd` est un exemple d’applet de commande qui accepte une chaîne en tant que mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ca935-197">The `Invoke-Sqlcmd` cmdlet is an example of a cmdlet that accepts a string as a password.</span></span>
<span data-ttu-id="ca935-198">`Invoke-Sqlcmd` vous permet d’exécuter les instructions SQL simples insert, update et delete.</span><span class="sxs-lookup"><span data-stu-id="ca935-198">`Invoke-Sqlcmd` allows you to run simple SQL insert, update, and delete statements.</span></span> <span data-ttu-id="ca935-199">`Invoke-Sqlcmd` requiert un nom d’utilisateur et un mot de passe en texte clair plutôt qu’un objet d’informations d’identification plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="ca935-199">`Invoke-Sqlcmd` requires a clear-text username and password rather than a more secure credential object.</span></span> <span data-ttu-id="ca935-200">Cet exemple montre comment extraire le nom d’utilisateur et le mot de passe d’un objet d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="ca935-200">This example shows how to extract the username and password from a credential object.</span></span>

<span data-ttu-id="ca935-201">La fonction `Get-AllSQLDatabases` dans cet exemple appelle l’applet de commande `Invoke-Sqlcmd` pour interroger un serveur SQL Server afin d’obtenir toutes ses bases de données.</span><span class="sxs-lookup"><span data-stu-id="ca935-201">The `Get-AllSQLDatabases` function in this example calls the `Invoke-Sqlcmd` cmdlet to query a SQL server for all its databases.</span></span> <span data-ttu-id="ca935-202">La fonction définit un paramètre **Credential** avec le même attribut utilisé dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="ca935-202">The function defines a **Credential** parameter with the same attribute used in the previous examples.</span></span> <span data-ttu-id="ca935-203">Étant donné que le nom d’utilisateur et le mot de passe existent dans la variable `$Credential`, vous pouvez extraire ces valeurs afin de les utiliser avec `Invoke-Sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ca935-203">Since the username and password exist within the `$Credential` variable, you can extract those values for use with `Invoke-Sqlcmd`.</span></span>

<span data-ttu-id="ca935-204">Le nom d’utilisateur est disponible dans la propriété **UserName** de la variable `$Credential`.</span><span class="sxs-lookup"><span data-stu-id="ca935-204">The user name is available from the **UserName** property of the `$Credential` variable.</span></span> <span data-ttu-id="ca935-205">Pour obtenir le mot de passe, vous devez utiliser la méthode `GetNetworkCredential()` de l’objet `$Credential`.</span><span class="sxs-lookup"><span data-stu-id="ca935-205">To obtain the password, you have to use the `GetNetworkCredential()` method of the `$Credential` object.</span></span> <span data-ttu-id="ca935-206">Les valeurs sont extraites dans des variables ajoutées à une table de hachage utilisée pour les paramètres de projection vers `Invoke-Sqlcmd`.</span><span class="sxs-lookup"><span data-stu-id="ca935-206">The values are extracted into variables that are added to a hash table used for splatting parameters to `Invoke-Sqlcmd`.</span></span>

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a><span data-ttu-id="ca935-207">Apprentissage continu pour la gestion des informations d’identification</span><span class="sxs-lookup"><span data-stu-id="ca935-207">Continued learning credential management</span></span>

<span data-ttu-id="ca935-208">La création et le stockage d’objets d’informations d’identification de façon sécurisée peuvent être difficiles.</span><span class="sxs-lookup"><span data-stu-id="ca935-208">Creating and storing credential objects securely can be difficult.</span></span> <span data-ttu-id="ca935-209">Les ressources suivantes peuvent vous aider à gérer les informations d’identification PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca935-209">The following resources can help you maintain PowerShell credentials.</span></span>

- <span data-ttu-id="ca935-210">[BetterCredentials][]</span><span class="sxs-lookup"><span data-stu-id="ca935-210">[BetterCredentials][]</span></span>
- <span data-ttu-id="ca935-211">[Azure Key Vault][]</span><span class="sxs-lookup"><span data-stu-id="ca935-211">[Azure Key Vault][]</span></span>
- <span data-ttu-id="ca935-212">[Vault Project][]</span><span class="sxs-lookup"><span data-stu-id="ca935-212">[Vault Project][]</span></span>
- <span data-ttu-id="ca935-213">[Module SecretManagement][]</span><span class="sxs-lookup"><span data-stu-id="ca935-213">[SecretManagement module][]</span></span>

<!-- link references -->
[Version d’origine]: https://duffney.io/addcredentialstopowershellfunctions/
[original version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault Project]: https://www.vaultproject.io/
[Splatting Parameters Inside Advanced Functions]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[Module SecretManagement]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
[SecretManagement module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
