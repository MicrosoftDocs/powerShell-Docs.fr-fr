---
description: PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: dbc11e15642673d3159d4f02a40147e68fbf1d7d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206514"
---
# <a name="about-logging-windows"></a><span data-ttu-id="f7474-104">À propos des fenêtres de journalisation</span><span class="sxs-lookup"><span data-stu-id="f7474-104">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="f7474-105">Description courte</span><span class="sxs-lookup"><span data-stu-id="f7474-105">Short description</span></span>

<span data-ttu-id="f7474-106">PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.</span><span class="sxs-lookup"><span data-stu-id="f7474-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="f7474-107">Description longue</span><span class="sxs-lookup"><span data-stu-id="f7474-107">Long description</span></span>

<span data-ttu-id="f7474-108">PowerShell journalise des détails sur les opérations PowerShell, telles que le démarrage et l’arrêt du moteur et des fournisseurs, et l’exécution de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7474-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="f7474-109">Les versions 3,0, 4,0, 5,0 et 5,1 de Windows PowerShell incluent des applets de commande **EventLog** pour les journaux des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="f7474-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="f7474-110">Dans ces versions, pour afficher la liste des applets de commande **EventLog** , tapez : `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="f7474-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="f7474-111">Pour plus d’informations, consultez la documentation sur les applets de commande et about_EventLogs pour votre version de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7474-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="f7474-112">Affichage des entrées du journal des événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="f7474-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="f7474-113">Les journaux PowerShell peuvent être affichés à l’aide de Windows observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="f7474-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="f7474-114">Le journal des événements se trouve dans le groupe journaux des applications et des services et est nommé `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="f7474-114">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="f7474-115">Le fournisseur ETW associé `GUID` est `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` .</span><span class="sxs-lookup"><span data-stu-id="f7474-115">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="f7474-116">Lorsque la journalisation de blocs de script est activée, PowerShell enregistre les événements suivants dans le `PowerShellCore/Operational` Journal :</span><span class="sxs-lookup"><span data-stu-id="f7474-116">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|<span data-ttu-id="f7474-117">Champ</span><span class="sxs-lookup"><span data-stu-id="f7474-117">Field</span></span>| <span data-ttu-id="f7474-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="f7474-118">Value</span></span>|
|-|-|
|<span data-ttu-id="f7474-119">EventId</span><span class="sxs-lookup"><span data-stu-id="f7474-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="f7474-120">Channel</span><span class="sxs-lookup"><span data-stu-id="f7474-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="f7474-121">Level</span><span class="sxs-lookup"><span data-stu-id="f7474-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="f7474-122">Opcode</span><span class="sxs-lookup"><span data-stu-id="f7474-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="f7474-123">Tâche</span><span class="sxs-lookup"><span data-stu-id="f7474-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="f7474-124">Mot clé</span><span class="sxs-lookup"><span data-stu-id="f7474-124">Keyword</span></span>|`Runspace`|

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="f7474-125">Inscription du fournisseur d’événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="f7474-125">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="f7474-126">Contrairement à Linux ou macOS, Windows requiert l’inscription du fournisseur d’événements pour que les événements puissent être écrits dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="f7474-126">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="f7474-127">Pour activer le fournisseur d’événements PowerShell, exécutez la commande suivante à partir d’une invite PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f7474-127">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="f7474-128">Annulation de l’inscription du fournisseur d’événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="f7474-128">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="f7474-129">L’inscription du fournisseur d’événements place un verrou dans la bibliothèque binaire utilisée pour décoder les événements.</span><span class="sxs-lookup"><span data-stu-id="f7474-129">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="f7474-130">Pour mettre à jour cette bibliothèque, le fournisseur doit être désinscrit pour libérer ce verrou.</span><span class="sxs-lookup"><span data-stu-id="f7474-130">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="f7474-131">Pour annuler l’inscription du fournisseur PowerShell, exécutez la commande suivante à partir d’une invite PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="f7474-131">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="f7474-132">Après la mise à jour de PowerShell, exécutez `$PSHOME\RegisterManifest.ps1` pour inscrire le fournisseur d’événements mis à jour.</span><span class="sxs-lookup"><span data-stu-id="f7474-132">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="f7474-133">Activation de la journalisation des blocs de script</span><span class="sxs-lookup"><span data-stu-id="f7474-133">Enabling Script Block Logging</span></span>

<span data-ttu-id="f7474-134">Lorsque vous activez la journalisation de blocs de script, PowerShell enregistre le contenu de tous les blocs de script qu’il traite.</span><span class="sxs-lookup"><span data-stu-id="f7474-134">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="f7474-135">Une fois activé, toute nouvelle session PowerShell consigne ces informations.</span><span class="sxs-lookup"><span data-stu-id="f7474-135">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="f7474-136">Il est recommandé d’activer la journalisation des événements protégés, comme décrit ci-dessous, lors de l’utilisation de la journalisation par bloc de script pour tout autre chose que des Diagnostics.</span><span class="sxs-lookup"><span data-stu-id="f7474-136">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="f7474-137">La journalisation des blocs de script peut être activée via stratégie de groupe ou un paramètre du Registre.</span><span class="sxs-lookup"><span data-stu-id="f7474-137">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="f7474-138">Utilisation de la stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="f7474-138">Using Group Policy</span></span>

<span data-ttu-id="f7474-139">Pour activer la transcription automatique, activez la `Turn on PowerShell Script Block
Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="f7474-139">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="f7474-140">Utilisation du Registre</span><span class="sxs-lookup"><span data-stu-id="f7474-140">Using the Registry</span></span>

<span data-ttu-id="f7474-141">Exécutez la fonction suivante :</span><span class="sxs-lookup"><span data-stu-id="f7474-141">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="f7474-142">Journalisation des événements protégés</span><span class="sxs-lookup"><span data-stu-id="f7474-142">Protected Event Logging</span></span>

<span data-ttu-id="f7474-143">L’augmentation du niveau de journalisation sur un système augmente la possibilité que du contenu journalisé puisse contenir des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="f7474-143">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="f7474-144">Par exemple, avec la journalisation des scripts activée, les informations d’identification ou d’autres données sensibles utilisées par un script peuvent être écrites dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="f7474-144">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="f7474-145">Lorsqu’un ordinateur qui a des données sensibles journalisées est compromis, les journaux peuvent fournir une personne malveillante avec les informations nécessaires pour étendre leur portée.</span><span class="sxs-lookup"><span data-stu-id="f7474-145">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="f7474-146">Pour protéger ces informations, Windows 10 introduit la journalisation des événements protégés.</span><span class="sxs-lookup"><span data-stu-id="f7474-146">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="f7474-147">L’enregistrement des événements protégés permet aux applications participantes de chiffrer des données sensibles écrites dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="f7474-147">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="f7474-148">Plus tard, vous pourrez déchiffrer et traiter ces journaux sur un collecteur de journaux plus sécurisé et centralisé.</span><span class="sxs-lookup"><span data-stu-id="f7474-148">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="f7474-149">Le contenu du journal des événements est protégé à l’aide de la norme CMS (Cryptographic Message Syntax) de l’IETF.</span><span class="sxs-lookup"><span data-stu-id="f7474-149">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="f7474-150">CMS utilise le chiffrement à clé publique.</span><span class="sxs-lookup"><span data-stu-id="f7474-150">CMS uses public key cryptography.</span></span> <span data-ttu-id="f7474-151">Les clés utilisées pour chiffrer le contenu et déchiffrer le contenu sont conservées séparément.</span><span class="sxs-lookup"><span data-stu-id="f7474-151">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="f7474-152">La clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="f7474-152">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="f7474-153">Tout contenu chiffré avec cette clé publique peut uniquement être déchiffré par la clé privée.</span><span class="sxs-lookup"><span data-stu-id="f7474-153">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="f7474-154">Pour plus d’informations sur le chiffrement à clé publique, consultez [wikipedia-Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="f7474-154">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="f7474-155">Pour activer une stratégie d’enregistrement des événements protégée, déployez une clé publique sur tous les ordinateurs qui ont des données du journal des événements à protéger.</span><span class="sxs-lookup"><span data-stu-id="f7474-155">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="f7474-156">La clé privée correspondante est utilisée pour effectuer un traitement ultérieur des journaux des événements dans un emplacement plus sécurisé, tel qu’un collecteur de journaux des événements centraux ou un agrégateur [Siem][] .</span><span class="sxs-lookup"><span data-stu-id="f7474-156">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="f7474-157">Vous pouvez configurer SIEM dans Azure.</span><span class="sxs-lookup"><span data-stu-id="f7474-157">You can set up SIEM in Azure.</span></span> <span data-ttu-id="f7474-158">Pour plus d’informations, consultez [intégration Siem générique](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="f7474-158">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="f7474-159">Activation de la journalisation des événements protégés via stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="f7474-159">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="f7474-160">Pour activer la journalisation des événements protégés, activez la `Enable Protected Event Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="f7474-160">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="f7474-161">Ce paramètre requiert un certificat de chiffrement, que vous pouvez fournir de l’une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7474-161">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="f7474-162">Contenu d’un certificat X. 509 encodé en base 64 (par exemple, tel qu’il est fourni par l' `Export` option dans le gestionnaire de certificats).</span><span class="sxs-lookup"><span data-stu-id="f7474-162">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="f7474-163">Empreinte numérique d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).</span><span class="sxs-lookup"><span data-stu-id="f7474-163">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="f7474-164">Le chemin d’accès complet à un certificat (peut être local ou un partage distant).</span><span class="sxs-lookup"><span data-stu-id="f7474-164">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="f7474-165">Chemin d’accès à un répertoire contenant un ou des certificats (peut être local ou un partage distant).</span><span class="sxs-lookup"><span data-stu-id="f7474-165">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="f7474-166">Nom du sujet d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).</span><span class="sxs-lookup"><span data-stu-id="f7474-166">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="f7474-167">Le certificat obtenu doit avoir `Document Encryption` une utilisation améliorée de la clé ( `1.3.6.1.4.1.311.80.1` ), et `Data Encipherment` les `Key
Encipherment` utilisations de clés ou sont activées.</span><span class="sxs-lookup"><span data-stu-id="f7474-167">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="f7474-168">La clé privée ne doit pas être déployée sur les événements de journalisation des machines.</span><span class="sxs-lookup"><span data-stu-id="f7474-168">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="f7474-169">Elle doit être conservée dans un emplacement sécurisé où vous déchiffrez les messages.</span><span class="sxs-lookup"><span data-stu-id="f7474-169">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="f7474-170">Déchiffrement des messages d’enregistrement des événements protégés</span><span class="sxs-lookup"><span data-stu-id="f7474-170">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="f7474-171">Le script suivant récupère et déchiffre, en supposant que vous disposiez de la clé privée :</span><span class="sxs-lookup"><span data-stu-id="f7474-171">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="f7474-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7474-172">See also</span></span>

[<span data-ttu-id="f7474-173">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="f7474-173">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="f7474-174">PowerShell l’équipe Blue Team</span><span class="sxs-lookup"><span data-stu-id="f7474-174">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="f7474-175">Intégration de SIEM générique</span><span class="sxs-lookup"><span data-stu-id="f7474-175">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management

