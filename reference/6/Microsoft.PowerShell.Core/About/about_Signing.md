---
description: Explique comment signer des scripts afin qu’ils soient conformes aux stratégies d’exécution de PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: ae0e9290696d8b50fce29137f98721220e7511c7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206865"
---
# <a name="about-signing"></a><span data-ttu-id="ba40d-104">À propos de la signature</span><span class="sxs-lookup"><span data-stu-id="ba40d-104">About Signing</span></span>

## <a name="short-description"></a><span data-ttu-id="ba40d-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="ba40d-105">Short description</span></span>
<span data-ttu-id="ba40d-106">Explique comment signer des scripts afin qu’ils soient conformes aux stratégies d’exécution de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ba40d-106">Explains how to sign scripts so that they comply with the PowerShell execution policies.</span></span>

## <a name="long-description"></a><span data-ttu-id="ba40d-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="ba40d-107">Long description</span></span>

<span data-ttu-id="ba40d-108">La stratégie d’exécution restreinte ne permet pas l’exécution de scripts.</span><span class="sxs-lookup"><span data-stu-id="ba40d-108">The Restricted execution policy does not permit any scripts to run.</span></span> <span data-ttu-id="ba40d-109">Les stratégies d’exécution **AllSigned** et **RemoteSigned** empêchent PowerShell d’exécuter des scripts qui n’ont pas de signature numérique.</span><span class="sxs-lookup"><span data-stu-id="ba40d-109">The **AllSigned** and **RemoteSigned** execution policies prevent PowerShell from running scripts that do not have a digital signature.</span></span>

<span data-ttu-id="ba40d-110">Cette rubrique explique comment exécuter des scripts sélectionnés qui ne sont pas signés, même si la stratégie d’exécution est **RemoteSigned** , et comment signer des scripts pour votre propre usage.</span><span class="sxs-lookup"><span data-stu-id="ba40d-110">This topic explains how to run selected scripts that are not signed, even while the execution policy is **RemoteSigned** , and how to sign scripts for your own use.</span></span>

<span data-ttu-id="ba40d-111">Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="ba40d-111">For more information about PowerShell execution policies, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="to-permit-signed-scripts-to-run"></a><span data-ttu-id="ba40d-112">Pour autoriser l’exécution de scripts signés</span><span class="sxs-lookup"><span data-stu-id="ba40d-112">To permit signed scripts to run</span></span>

<span data-ttu-id="ba40d-113">Lorsque vous démarrez PowerShell sur un ordinateur pour la première fois, la stratégie d’exécution **restreinte** (valeur par défaut) est susceptible d’être en vigueur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-113">When you start PowerShell on a computer for the first time, the **Restricted** execution policy (the default) is likely to be in effect.</span></span>

<span data-ttu-id="ba40d-114">La stratégie **restreinte** ne permet pas l’exécution de scripts.</span><span class="sxs-lookup"><span data-stu-id="ba40d-114">The **Restricted** policy does not permit any scripts to run.</span></span>

<span data-ttu-id="ba40d-115">Pour trouver la stratégie d’exécution effective sur votre ordinateur, tapez :</span><span class="sxs-lookup"><span data-stu-id="ba40d-115">To find the effective execution policy on your computer, type:</span></span>

```powershell
Get-ExecutionPolicy
```

<span data-ttu-id="ba40d-116">Pour exécuter des scripts non signés que vous écrivez sur votre ordinateur local et des scripts signés d’autres utilisateurs, démarrez PowerShell avec l’option Exécuter en tant qu’administrateur, puis utilisez la commande suivante pour modifier la stratégie d’exécution sur l’ordinateur en **RemoteSigned** :</span><span class="sxs-lookup"><span data-stu-id="ba40d-116">To run unsigned scripts that you write on your local computer and signed scripts from other users, start PowerShell with the Run as Administrator option and then use the following command to change the execution policy on the computer to **RemoteSigned** :</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

<span data-ttu-id="ba40d-117">Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande `Set-ExecutionPolicy` .</span><span class="sxs-lookup"><span data-stu-id="ba40d-117">For more information, see the help topic for the `Set-ExecutionPolicy` cmdlet.</span></span>

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a><span data-ttu-id="ba40d-118">Exécution de scripts non signés à l’aide de la stratégie d’exécution RemoteSigned</span><span class="sxs-lookup"><span data-stu-id="ba40d-118">Running unsigned scripts using the RemoteSigned execution policy</span></span>

<span data-ttu-id="ba40d-119">Si votre stratégie d’exécution de PowerShell est **RemoteSigned** , PowerShell n’exécutera pas les scripts non signés téléchargés à partir d’Internet, y compris les scripts non signés que vous recevez par courrier électronique et les programmes de messagerie instantanée.</span><span class="sxs-lookup"><span data-stu-id="ba40d-119">If your PowerShell execution policy is **RemoteSigned** , PowerShell will not run unsigned scripts that are downloaded from the internet, including unsigned scripts you receive through email and instant messaging programs.</span></span>

<span data-ttu-id="ba40d-120">Si vous essayez d’exécuter un script téléchargé, PowerShell affiche le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="ba40d-120">If you try to run a downloaded script, PowerShell displays the following error message:</span></span>

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

<span data-ttu-id="ba40d-121">Avant d’exécuter le script, passez en revue le code pour vous assurer qu’il est digne de confiance.</span><span class="sxs-lookup"><span data-stu-id="ba40d-121">Before you run the script, review the code to be sure that you trust it.</span></span>
<span data-ttu-id="ba40d-122">Les scripts ont le même effet que n’importe quel programme exécutable.</span><span class="sxs-lookup"><span data-stu-id="ba40d-122">Scripts have the same effect as any executable program.</span></span>

<span data-ttu-id="ba40d-123">Pour exécuter un script non signé, utilisez l’applet de commande Unblock-File ou utilisez la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="ba40d-123">To run an unsigned script, use the Unblock-File cmdlet or use the following procedure.</span></span>

1. <span data-ttu-id="ba40d-124">Enregistrez le fichier de script sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-124">Save the script file on your computer.</span></span>
2. <span data-ttu-id="ba40d-125">Cliquez sur Démarrer, sur Poste de travail, puis recherchez le fichier de script enregistré.</span><span class="sxs-lookup"><span data-stu-id="ba40d-125">Click Start, click My Computer, and locate the saved script file.</span></span>
3. <span data-ttu-id="ba40d-126">Cliquez avec le bouton droit sur le fichier de script, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="ba40d-126">Right-click the script file, and then click Properties.</span></span>
4. <span data-ttu-id="ba40d-127">Cliquez sur Débloquer.</span><span class="sxs-lookup"><span data-stu-id="ba40d-127">Click Unblock.</span></span>

<span data-ttu-id="ba40d-128">Si un script téléchargé à partir d’Internet est signé numériquement, mais que vous n’avez pas encore choisi d’approuver son serveur de publication, PowerShell affiche le message suivant :</span><span class="sxs-lookup"><span data-stu-id="ba40d-128">If a script that was downloaded from the internet is digitally signed, but you have not yet chosen to trust its publisher, PowerShell displays the following message:</span></span>

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

<span data-ttu-id="ba40d-129">Si vous faites confiance au serveur de publication, sélectionnez « Exécuter une fois » ou « toujours exécuter ».</span><span class="sxs-lookup"><span data-stu-id="ba40d-129">If you trust the publisher, select "Run once" or "Always run."</span></span> <span data-ttu-id="ba40d-130">Si vous ne faites pas confiance au serveur de publication, sélectionnez « jamais exécuté » ou « ne pas exécuter ».</span><span class="sxs-lookup"><span data-stu-id="ba40d-130">If you do not trust the publisher, select either "Never run" or "Do not run."</span></span> <span data-ttu-id="ba40d-131">Si vous sélectionnez « jamais exécuté » ou « toujours exécuter », PowerShell ne vous invitera plus à nouveau pour ce serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="ba40d-131">If you select "Never run" or "Always run," PowerShell will not prompt you again for this publisher.</span></span>

## <a name="methods-of-signing-scripts"></a><span data-ttu-id="ba40d-132">Méthodes de signature des scripts</span><span class="sxs-lookup"><span data-stu-id="ba40d-132">Methods of signing scripts</span></span>

<span data-ttu-id="ba40d-133">Vous pouvez signer les scripts que vous écrivez et les scripts que vous obtenez à partir d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="ba40d-133">You can sign the scripts that you write and the scripts that you obtain from other sources.</span></span> <span data-ttu-id="ba40d-134">Avant de signer un script, examinez chaque commande pour vérifier qu’elle peut être exécutée en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="ba40d-134">Before you sign any script, examine each command to verify that it is safe to run.</span></span>

<span data-ttu-id="ba40d-135">Pour connaître les meilleures pratiques relatives à la signature de code, consultez [meilleures pratiques pour la signature de code](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ba40d-135">For best practices about code signing, see [Code-Signing Best Practices](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).</span></span>

<span data-ttu-id="ba40d-136">Pour plus d’informations sur la façon de signer un fichier de script, consultez [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span><span class="sxs-lookup"><span data-stu-id="ba40d-136">For more information about how to sign a script file, see [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).</span></span>

<span data-ttu-id="ba40d-137">L' `New-SelfSignedCertificate` applet de commande, introduite dans le module PKI de PowerShell 3,0, crée un certificat auto-signé approprié pour le test.</span><span class="sxs-lookup"><span data-stu-id="ba40d-137">The `New-SelfSignedCertificate` cmdlet, introduced in the PKI module in PowerShell 3.0, creates a self-signed certificate that is Appropriate for testing.</span></span> <span data-ttu-id="ba40d-138">Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande New-SelfSignedCertificate.</span><span class="sxs-lookup"><span data-stu-id="ba40d-138">For more information, see the help topic for the New-SelfSignedCertificate cmdlet.</span></span>

<span data-ttu-id="ba40d-139">Pour ajouter une signature numérique à un script, vous devez la signer avec un certificat de signature de code.</span><span class="sxs-lookup"><span data-stu-id="ba40d-139">To add a digital signature to a script, you must sign it with a code signing certificate.</span></span> <span data-ttu-id="ba40d-140">Deux types de certificats conviennent pour la signature d’un fichier de script :</span><span class="sxs-lookup"><span data-stu-id="ba40d-140">Two types of certificates are suitable for signing a script file:</span></span>

- <span data-ttu-id="ba40d-141">Certificats créés par une autorité de certification : pour des frais, une autorité de certification publique vérifie votre identité et vous donne un certificat de signature de code.</span><span class="sxs-lookup"><span data-stu-id="ba40d-141">Certificates that are created by a certification authority: For a fee, a public certification authority verifies your identity and gives you a code signing certificate.</span></span> <span data-ttu-id="ba40d-142">Lorsque vous achetez votre certificat auprès d’une autorité de certification reconnue, vous pouvez partager votre script avec des utilisateurs sur d’autres ordinateurs qui exécutent Windows, car ces autres ordinateurs approuvent l’autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="ba40d-142">When you purchase your certificate from a reputable certification authority, you are able to share your script with users on other computers that are running Windows because those other computers trust the certification authority.</span></span>

- <span data-ttu-id="ba40d-143">Certificats que vous créez : vous pouvez créer un certificat auto-signé pour lequel votre ordinateur est l’autorité qui crée le certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-143">Certificates that you create: You can create a self-signed certificate for which your computer is the authority that creates the certificate.</span></span> <span data-ttu-id="ba40d-144">Ce certificat est gratuit et vous permet d’écrire, signer et exécuter des scripts sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-144">This certificate is free of charge and enables you to write, sign, and run scripts on your computer.</span></span> <span data-ttu-id="ba40d-145">Toutefois, un script signé par un certificat auto-signé ne s’exécutera pas sur d’autres ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="ba40d-145">However, a script signed by a self-signed certificate will not run on other computers.</span></span>

<span data-ttu-id="ba40d-146">En règle générale, vous utilisez un certificat auto-signé uniquement pour signer des scripts que vous écrivez pour votre propre usage et pour signer des scripts que vous avez vérifiés à partir d’autres sources que vous avez vérifiées comme sécurisées.</span><span class="sxs-lookup"><span data-stu-id="ba40d-146">Typically, you would use a self-signed certificate only to sign scripts that you write for your own use and to sign scripts that you get from other sources that you have verified to be safe.</span></span> <span data-ttu-id="ba40d-147">Il n’est pas approprié pour les scripts qui seront partagés, même au sein d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="ba40d-147">It is not appropriate for scripts that will be shared, even within an enterprise.</span></span>

<span data-ttu-id="ba40d-148">Si vous créez un certificat auto-signé, veillez à activer la protection renforcée par clé privée sur votre certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-148">If you create a self-signed certificate, be sure to enable strong private key protection on your certificate.</span></span> <span data-ttu-id="ba40d-149">Cela empêche les programmes malveillants de signer des scripts en votre nom.</span><span class="sxs-lookup"><span data-stu-id="ba40d-149">This prevents malicious programs from signing scripts on your behalf.</span></span> <span data-ttu-id="ba40d-150">Les instructions sont incluses à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ba40d-150">The instructions are included at the end of this topic.</span></span>

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="ba40d-151">Créer un certificat auto-signé</span><span class="sxs-lookup"><span data-stu-id="ba40d-151">Create a self-signed certificate</span></span>

<span data-ttu-id="ba40d-152">Pour créer un certificat auto-signé, utilisez l' `New-SelfSignedCertificate` applet de commande dans le module PKI.</span><span class="sxs-lookup"><span data-stu-id="ba40d-152">To create a self-signed certificate use the `New-SelfSignedCertificate` cmdlet in the PKI module.</span></span> <span data-ttu-id="ba40d-153">Ce module est introduit dans PowerShell 3,0 et est inclus dans Windows 8 et Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="ba40d-153">This module is introduced in PowerShell 3.0 and is included in Windows 8 and Windows Server 2012.</span></span> <span data-ttu-id="ba40d-154">Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande `New-SelfSignedCertificate` .</span><span class="sxs-lookup"><span data-stu-id="ba40d-154">For more information, see the help topic for the `New-SelfSignedCertificate` cmdlet.</span></span>

<span data-ttu-id="ba40d-155">Pour créer un certificat auto-signé dans des versions antérieures de Windows, utilisez l’outil de création de certificat `MakeCert.exe` .</span><span class="sxs-lookup"><span data-stu-id="ba40d-155">To create a self-signed certificate in earlier versions of Windows, use the Certificate Creation tool `MakeCert.exe`.</span></span> <span data-ttu-id="ba40d-156">Cet outil est inclus dans le kit de développement logiciel (SDK) Microsoft .NET (versions 1,1 et ultérieures) et dans le Microsoft Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="ba40d-156">This tool is included in the Microsoft .NET SDK (versions 1.1 and later) and in the Microsoft Windows SDK.</span></span>

<span data-ttu-id="ba40d-157">Pour plus d’informations sur la syntaxe et les descriptions des paramètres de l’outil MakeCert.exe, consultez [outil de création de certificats (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="ba40d-157">For more information about the syntax and the parameter descriptions of the MakeCert.exe tool, see [Certificate Creation Tool (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).</span></span>

<span data-ttu-id="ba40d-158">Pour utiliser l’outil MakeCert.exe pour créer un certificat, exécutez les commandes suivantes dans une fenêtre d’invite de commandes du kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="ba40d-158">To use the MakeCert.exe tool to create a certificate, run the following commands in an SDK Command Prompt window.</span></span>

<span data-ttu-id="ba40d-159">Remarque : la première commande crée une autorité de certification locale pour votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-159">Note: The first command creates a local certification authority for your computer.</span></span> <span data-ttu-id="ba40d-160">La deuxième commande génère un certificat personnel à partir de l’autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="ba40d-160">The second command generates a personal certificate from the certification authority.</span></span>

<span data-ttu-id="ba40d-161">Remarque : vous pouvez copier ou taper les commandes exactement telles qu’elles apparaissent.</span><span class="sxs-lookup"><span data-stu-id="ba40d-161">Note: You can copy or type the commands exactly as they appear.</span></span> <span data-ttu-id="ba40d-162">Aucune substitution n’est nécessaire, même si vous pouvez modifier le nom du certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-162">No substitutions are necessary, although you can change the certificate name.</span></span>

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

<span data-ttu-id="ba40d-163">L’outil MakeCert.exe vous invite à entrer un mot de passe de clé privée.</span><span class="sxs-lookup"><span data-stu-id="ba40d-163">The MakeCert.exe tool will prompt you for a private key password.</span></span> <span data-ttu-id="ba40d-164">Le mot de passe garantit qu’aucun d’entre eux ne peut utiliser le certificat ou y accéder sans votre consentement.</span><span class="sxs-lookup"><span data-stu-id="ba40d-164">The password ensures that no one can use or access the certificate without your consent.</span></span>
<span data-ttu-id="ba40d-165">Créez et entrez un mot de passe que vous pouvez mémoriser.</span><span class="sxs-lookup"><span data-stu-id="ba40d-165">Create and enter a password that you can remember.</span></span> <span data-ttu-id="ba40d-166">Vous utiliserez ce mot de passe ultérieurement pour récupérer le certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-166">You will use this password later to retrieve the certificate.</span></span>

<span data-ttu-id="ba40d-167">Pour vérifier que le certificat a été généré correctement, utilisez la commande suivante pour récupérer le certificat dans le magasin de certificats sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-167">To verify that the certificate was generated correctly, use the following command to get the certificate in the certificate store on the computer.</span></span> <span data-ttu-id="ba40d-168">Vous ne trouverez pas de fichier de certificat dans le répertoire du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="ba40d-168">You will not find a certificate file in the file system directory.</span></span>

<span data-ttu-id="ba40d-169">À l’invite PowerShell, tapez :</span><span class="sxs-lookup"><span data-stu-id="ba40d-169">At the PowerShell prompt, type:</span></span>

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

<span data-ttu-id="ba40d-170">Cette commande utilise le fournisseur de certificats PowerShell pour afficher des informations sur le certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-170">This command uses the PowerShell Certificate provider to view information about the certificate.</span></span>

<span data-ttu-id="ba40d-171">Si le certificat a été créé, la sortie affiche l' **empreinte** qui identifie le certificat dans un affichage qui ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ba40d-171">If the certificate was created, the output shows the **thumbprint** that identifies the certificate in a display that resembles the following:</span></span>

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a><span data-ttu-id="ba40d-172">Signer un script</span><span class="sxs-lookup"><span data-stu-id="ba40d-172">Sign a script</span></span>

<span data-ttu-id="ba40d-173">Une fois que vous avez créé un certificat auto-signé, vous pouvez signer des scripts.</span><span class="sxs-lookup"><span data-stu-id="ba40d-173">After you create a self-signed certificate, you can sign scripts.</span></span> <span data-ttu-id="ba40d-174">Si vous utilisez la stratégie d’exécution **AllSigned** , la signature d’un script vous permet d’exécuter le script sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba40d-174">If you use the **AllSigned** execution policy, signing a script permits you to run the script on your computer.</span></span>

<span data-ttu-id="ba40d-175">L’exemple de script suivant, `Add-Signature.ps1` , signe un script.</span><span class="sxs-lookup"><span data-stu-id="ba40d-175">The following sample script, `Add-Signature.ps1`, signs a script.</span></span> <span data-ttu-id="ba40d-176">Toutefois, si vous utilisez la stratégie d’exécution **AllSigned** , vous devez signer le `Add-Signature.ps1` script avant de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="ba40d-176">However, if you are using the **AllSigned** execution policy, you must sign the `Add-Signature.ps1` script before you run it.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba40d-177">Le script doit être enregistré à l’aide de l’encodage ASCII ou UTF8NoBOM. Vous pouvez signer un fichier de script qui utilise un encodage différent.</span><span class="sxs-lookup"><span data-stu-id="ba40d-177">The script must be saved using ASCII or UTF8NoBOM encoding.You can sign a script file that uses a different encoding.</span></span> <span data-ttu-id="ba40d-178">Toutefois, le script ne peut pas s’exécuter ou le module contenant le script ne peut pas être importé.</span><span class="sxs-lookup"><span data-stu-id="ba40d-178">But the script fails to run or the module containing the script fails to import.</span></span>

<span data-ttu-id="ba40d-179">Pour utiliser ce script, copiez le texte suivant dans un fichier texte, puis nommez-le `Add-Signature.ps1` .</span><span class="sxs-lookup"><span data-stu-id="ba40d-179">To use this script, copy the following text into a text file, and name it `Add-Signature.ps1`.</span></span>

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

<span data-ttu-id="ba40d-180">Pour signer le `Add-Signature.ps1` fichier de script, tapez les commandes suivantes à l’invite de commandes PowerShell :</span><span class="sxs-lookup"><span data-stu-id="ba40d-180">To sign the `Add-Signature.ps1` script file, type the following commands at the PowerShell command prompt:</span></span>

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

<span data-ttu-id="ba40d-181">Une fois le script signé, vous pouvez l’exécuter sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="ba40d-181">After the script is signed, you can run it on the local computer.</span></span> <span data-ttu-id="ba40d-182">Toutefois, le script ne s’exécute pas sur les ordinateurs sur lesquels la stratégie d’exécution de PowerShell requiert une signature numérique d’une autorité de confiance.</span><span class="sxs-lookup"><span data-stu-id="ba40d-182">However, the script will not run on computers on which the PowerShell execution policy requires a digital signature from a trusted authority.</span></span> <span data-ttu-id="ba40d-183">Si vous essayez, PowerShell affiche le message d’erreur suivant :</span><span class="sxs-lookup"><span data-stu-id="ba40d-183">If you try, PowerShell displays the following error message:</span></span>

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

<span data-ttu-id="ba40d-184">Si PowerShell affiche ce message lorsque vous exécutez un script que vous n’avez pas écrit, traitez le fichier comme vous le feriez pour tout script non signé.</span><span class="sxs-lookup"><span data-stu-id="ba40d-184">If PowerShell displays this message when you run a script that you did not write, treat the file as you would treat any unsigned script.</span></span> <span data-ttu-id="ba40d-185">Examinez le code pour déterminer si vous pouvez faire confiance au script.</span><span class="sxs-lookup"><span data-stu-id="ba40d-185">Review the code to determine whether you can trust the script.</span></span>

## <a name="enable-strong-private-key-protection-for-your-certificate"></a><span data-ttu-id="ba40d-186">Activer la protection renforcée par clé privée pour votre certificat</span><span class="sxs-lookup"><span data-stu-id="ba40d-186">Enable strong private key protection for your certificate</span></span>

<span data-ttu-id="ba40d-187">Si vous disposez d’un certificat privé sur votre ordinateur, des programmes malveillants peuvent être en mesure de signer des scripts à votre place, ce qui permet à PowerShell de les exécuter.</span><span class="sxs-lookup"><span data-stu-id="ba40d-187">If you have a private certificate on your computer, malicious programs might be able to sign scripts on your behalf, which authorizes PowerShell to run them.</span></span>

<span data-ttu-id="ba40d-188">Pour empêcher la signature automatique en votre nom, utilisez le gestionnaire `Certmgr.exe` de certificats pour exporter votre certificat de signature dans un `.pfx` fichier.</span><span class="sxs-lookup"><span data-stu-id="ba40d-188">To prevent automated signing on your behalf, use Certificate Manager `Certmgr.exe` to export your signing certificate to a `.pfx` file.</span></span> <span data-ttu-id="ba40d-189">Le gestionnaire de certificats est inclus dans le kit de développement logiciel (SDK) Microsoft .NET, le Microsoft Windows SDK et dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="ba40d-189">Certificate Manager is included in the Microsoft .NET SDK, the Microsoft Windows SDK, and in internet Explorer.</span></span>

<span data-ttu-id="ba40d-190">Pour exporter le certificat :</span><span class="sxs-lookup"><span data-stu-id="ba40d-190">To export the certificate:</span></span>

1. <span data-ttu-id="ba40d-191">Démarrez le gestionnaire de certificats.</span><span class="sxs-lookup"><span data-stu-id="ba40d-191">Start Certificate Manager.</span></span>
2. <span data-ttu-id="ba40d-192">Sélectionnez le certificat émis par la racine du certificat local PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ba40d-192">Select the certificate issued by PowerShell Local Certificate Root.</span></span>
3. <span data-ttu-id="ba40d-193">Cliquez sur Exporter pour démarrer l’Assistant exportation de certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-193">Click Export to start the Certificate Export Wizard.</span></span>
4. <span data-ttu-id="ba40d-194">Sélectionnez « Oui, exporter la clé privée », puis cliquez sur suivant.</span><span class="sxs-lookup"><span data-stu-id="ba40d-194">Select "Yes, export the private key", and then click Next.</span></span>
5. <span data-ttu-id="ba40d-195">Sélectionnez « Activer la protection renforcée ».</span><span class="sxs-lookup"><span data-stu-id="ba40d-195">Select "Enable strong protection."</span></span>
6. <span data-ttu-id="ba40d-196">Tapez un mot de passe, puis tapez-le à nouveau pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="ba40d-196">Type a password, and then type it again to confirm.</span></span>
7. <span data-ttu-id="ba40d-197">Tapez un nom de fichier avec l’extension de nom de fichier. pfx.</span><span class="sxs-lookup"><span data-stu-id="ba40d-197">Type a file name that has the .pfx file name extension.</span></span>
8. <span data-ttu-id="ba40d-198">Cliquez sur Finish.</span><span class="sxs-lookup"><span data-stu-id="ba40d-198">Click Finish.</span></span>

<span data-ttu-id="ba40d-199">Pour réimporter le certificat :</span><span class="sxs-lookup"><span data-stu-id="ba40d-199">To re-import the certificate:</span></span>

1. <span data-ttu-id="ba40d-200">Démarrez le gestionnaire de certificats.</span><span class="sxs-lookup"><span data-stu-id="ba40d-200">Start Certificate Manager.</span></span>
2. <span data-ttu-id="ba40d-201">Cliquez sur Importer pour démarrer l’Assistant importation de certificat.</span><span class="sxs-lookup"><span data-stu-id="ba40d-201">Click Import to start the Certificate Import Wizard.</span></span>
3. <span data-ttu-id="ba40d-202">Ouvrez l’emplacement du fichier. pfx que vous avez créé pendant le processus d’exportation.</span><span class="sxs-lookup"><span data-stu-id="ba40d-202">Open to the location of the .pfx file that you created during the export process.</span></span>
4. <span data-ttu-id="ba40d-203">Sur la page mot de passe, sélectionnez Activer la protection renforcée par clé privée, puis entrez le mot de passe que vous avez affecté pendant le processus d’exportation.</span><span class="sxs-lookup"><span data-stu-id="ba40d-203">On the Password page, select "Enable strong private key protection", and then enter the password that you assigned during the export process.</span></span>
5. <span data-ttu-id="ba40d-204">Sélectionnez le magasin de certificats personnel.</span><span class="sxs-lookup"><span data-stu-id="ba40d-204">Select the Personal certificate store.</span></span>
6. <span data-ttu-id="ba40d-205">Cliquez sur Finish.</span><span class="sxs-lookup"><span data-stu-id="ba40d-205">Click Finish.</span></span>

## <a name="prevent-the-signature-from-expiring"></a><span data-ttu-id="ba40d-206">Empêcher l’expiration de la signature</span><span class="sxs-lookup"><span data-stu-id="ba40d-206">Prevent the signature from expiring</span></span>

<span data-ttu-id="ba40d-207">La signature numérique d’un script est valide jusqu’à ce que le certificat de signature expire ou tant qu’un serveur d’horodatage peut vérifier que le script a été signé alors que le certificat de signature est valide.</span><span class="sxs-lookup"><span data-stu-id="ba40d-207">The digital signature in a script is valid until the signing certificate expires or as long as a timestamp server can verify that the script was signed while the signing certificate was valid.</span></span>

<span data-ttu-id="ba40d-208">Étant donné que la plupart des certificats de signature sont valides uniquement pendant un an, l’utilisation d’un serveur d’horodatage garantit que les utilisateurs peuvent utiliser votre script pendant de nombreuses années.</span><span class="sxs-lookup"><span data-stu-id="ba40d-208">Because most signing certificates are valid for one year only, using a time stamp server ensures that users can use your script for many years to come.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba40d-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba40d-209">See also</span></span>

[<span data-ttu-id="ba40d-210">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="ba40d-210">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="ba40d-211">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ba40d-211">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ba40d-212">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ba40d-212">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="ba40d-213">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ba40d-213">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="ba40d-214">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="ba40d-214">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

<span data-ttu-id="ba40d-215">[Présentation de la signature de code](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ba40d-215">[Introduction to Code Signing](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))</span></span>
