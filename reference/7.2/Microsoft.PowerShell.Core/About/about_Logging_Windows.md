---
description: PowerShell journalise les opérations internes du moteur, des fournisseurs et des applets de commande dans le journal des événements Windows.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: d6ae50b50911417da8dd306cad69e3fc7129fedc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603460"
---
# <a name="about-logging-windows"></a><span data-ttu-id="33139-103">À propos des fenêtres de journalisation</span><span class="sxs-lookup"><span data-stu-id="33139-103">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="33139-104">Description courte</span><span class="sxs-lookup"><span data-stu-id="33139-104">Short description</span></span>
<span data-ttu-id="33139-105">PowerShell journalise les opérations internes du moteur, des fournisseurs et des applets de commande dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="33139-105">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="33139-106">Description longue</span><span class="sxs-lookup"><span data-stu-id="33139-106">Long description</span></span>

<span data-ttu-id="33139-107">PowerShell journalise des détails sur les opérations PowerShell, telles que le démarrage et l’arrêt du moteur et des fournisseurs, et l’exécution de commandes PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33139-107">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="33139-108">Les versions 3,0, 4,0, 5,0 et 5,1 de Windows PowerShell incluent des applets de commande **EventLog** pour les journaux des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="33139-108">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="33139-109">Dans ces versions, pour afficher la liste des applets de commande **EventLog** , tapez : `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="33139-109">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="33139-110">Pour plus d’informations, consultez la documentation sur les applets de commande et about_EventLogs pour votre version de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33139-110">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="33139-111">Affichage des entrées du journal des événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="33139-111">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="33139-112">Les journaux PowerShell peuvent être affichés à l’aide de Windows observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="33139-112">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="33139-113">Le journal des événements se trouve dans le groupe journaux des applications et des services et est nommé `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="33139-113">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="33139-114">Le fournisseur ETW associé `GUID` est `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` .</span><span class="sxs-lookup"><span data-stu-id="33139-114">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="33139-115">Lorsque la journalisation de blocs de script est activée, PowerShell enregistre les événements suivants dans le `PowerShellCore/Operational` Journal :</span><span class="sxs-lookup"><span data-stu-id="33139-115">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="33139-116">Champ</span><span class="sxs-lookup"><span data-stu-id="33139-116">Field</span></span>  |       <span data-ttu-id="33139-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="33139-117">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="33139-118">EventId</span><span class="sxs-lookup"><span data-stu-id="33139-118">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="33139-119">Canal</span><span class="sxs-lookup"><span data-stu-id="33139-119">Channel</span></span> | `Operational`     |
| <span data-ttu-id="33139-120">Level</span><span class="sxs-lookup"><span data-stu-id="33139-120">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="33139-121">Opcode</span><span class="sxs-lookup"><span data-stu-id="33139-121">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="33139-122">Tâche</span><span class="sxs-lookup"><span data-stu-id="33139-122">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="33139-123">Mot clé</span><span class="sxs-lookup"><span data-stu-id="33139-123">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="33139-124">Inscription du fournisseur d’événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="33139-124">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="33139-125">Contrairement à Linux ou macOS, Windows requiert l’inscription du fournisseur d’événements pour que les événements puissent être écrits dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="33139-125">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="33139-126">Pour activer le fournisseur d’événements PowerShell, exécutez la commande suivante à partir d’une invite PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="33139-126">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="33139-127">Annulation de l’inscription du fournisseur d’événements PowerShell sur Windows</span><span class="sxs-lookup"><span data-stu-id="33139-127">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="33139-128">L’inscription du fournisseur d’événements place un verrou dans la bibliothèque binaire utilisée pour décoder les événements.</span><span class="sxs-lookup"><span data-stu-id="33139-128">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="33139-129">Pour mettre à jour cette bibliothèque, le fournisseur doit être désinscrit pour libérer ce verrou.</span><span class="sxs-lookup"><span data-stu-id="33139-129">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="33139-130">Pour annuler l’inscription du fournisseur PowerShell, exécutez la commande suivante à partir d’une invite PowerShell avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="33139-130">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="33139-131">Après la mise à jour de PowerShell, exécutez `$PSHOME\RegisterManifest.ps1` pour inscrire le fournisseur d’événements mis à jour.</span><span class="sxs-lookup"><span data-stu-id="33139-131">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="33139-132">Activation de la journalisation des blocs de script</span><span class="sxs-lookup"><span data-stu-id="33139-132">Enabling Script Block Logging</span></span>

<span data-ttu-id="33139-133">Lorsque vous activez la journalisation de blocs de script, PowerShell enregistre le contenu de tous les blocs de script qu’il traite.</span><span class="sxs-lookup"><span data-stu-id="33139-133">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="33139-134">Une fois activé, toute nouvelle session PowerShell consigne ces informations.</span><span class="sxs-lookup"><span data-stu-id="33139-134">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="33139-135">Il est recommandé d’activer la journalisation des événements protégés, comme décrit ci-dessous, lors de l’utilisation de la journalisation par bloc de script pour tout autre chose que des Diagnostics.</span><span class="sxs-lookup"><span data-stu-id="33139-135">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="33139-136">La journalisation des blocs de script peut être activée via stratégie de groupe ou un paramètre du Registre.</span><span class="sxs-lookup"><span data-stu-id="33139-136">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="33139-137">Utilisation de la stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="33139-137">Using Group Policy</span></span>

<span data-ttu-id="33139-138">Pour activer la transcription automatique, activez la `Turn on PowerShell Script Block
Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="33139-138">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="33139-139">Utilisation du Registre</span><span class="sxs-lookup"><span data-stu-id="33139-139">Using the Registry</span></span>

<span data-ttu-id="33139-140">Exécutez la fonction suivante :</span><span class="sxs-lookup"><span data-stu-id="33139-140">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="33139-141">Journalisation des événements protégés</span><span class="sxs-lookup"><span data-stu-id="33139-141">Protected Event Logging</span></span>

<span data-ttu-id="33139-142">L’augmentation du niveau de journalisation sur un système augmente la possibilité que du contenu journalisé puisse contenir des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="33139-142">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="33139-143">Par exemple, avec la journalisation des scripts activée, les informations d’identification ou d’autres données sensibles utilisées par un script peuvent être écrites dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="33139-143">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="33139-144">Lorsqu’un ordinateur qui a des données sensibles journalisées est compromis, les journaux peuvent fournir une personne malveillante avec les informations nécessaires pour étendre leur portée.</span><span class="sxs-lookup"><span data-stu-id="33139-144">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="33139-145">Pour protéger ces informations, Windows 10 introduit la journalisation des événements protégés.</span><span class="sxs-lookup"><span data-stu-id="33139-145">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="33139-146">L’enregistrement des événements protégés permet aux applications participantes de chiffrer des données sensibles écrites dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="33139-146">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="33139-147">Plus tard, vous pourrez déchiffrer et traiter ces journaux sur un collecteur de journaux plus sécurisé et centralisé.</span><span class="sxs-lookup"><span data-stu-id="33139-147">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="33139-148">Le contenu du journal des événements est protégé à l’aide de la norme CMS (Cryptographic Message Syntax) de l’IETF.</span><span class="sxs-lookup"><span data-stu-id="33139-148">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="33139-149">CMS utilise le chiffrement à clé publique.</span><span class="sxs-lookup"><span data-stu-id="33139-149">CMS uses public key cryptography.</span></span> <span data-ttu-id="33139-150">Les clés utilisées pour chiffrer le contenu et déchiffrer le contenu sont conservées séparément.</span><span class="sxs-lookup"><span data-stu-id="33139-150">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="33139-151">La clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="33139-151">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="33139-152">Tout contenu chiffré avec cette clé publique peut uniquement être déchiffré par la clé privée.</span><span class="sxs-lookup"><span data-stu-id="33139-152">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="33139-153">Pour plus d’informations sur le chiffrement à clé publique, consultez [wikipedia-Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="33139-153">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="33139-154">Pour activer une stratégie d’enregistrement des événements protégée, déployez une clé publique sur tous les ordinateurs qui ont des données du journal des événements à protéger.</span><span class="sxs-lookup"><span data-stu-id="33139-154">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="33139-155">La clé privée correspondante est utilisée pour effectuer un traitement ultérieur des journaux des événements dans un emplacement plus sécurisé, tel qu’un collecteur de journaux des événements centraux ou un agrégateur [Siem][] .</span><span class="sxs-lookup"><span data-stu-id="33139-155">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="33139-156">Vous pouvez configurer SIEM dans Azure.</span><span class="sxs-lookup"><span data-stu-id="33139-156">You can set up SIEM in Azure.</span></span> <span data-ttu-id="33139-157">Pour plus d’informations, consultez [intégration Siem générique](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="33139-157">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="33139-158">Activation de la journalisation des événements protégés via stratégie de groupe</span><span class="sxs-lookup"><span data-stu-id="33139-158">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="33139-159">Pour activer la journalisation des événements protégés, activez la `Enable Protected Event Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="33139-159">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="33139-160">Ce paramètre requiert un certificat de chiffrement, que vous pouvez fournir de l’une des formes suivantes :</span><span class="sxs-lookup"><span data-stu-id="33139-160">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="33139-161">Contenu d’un certificat X. 509 encodé en base 64 (par exemple, tel qu’il est fourni par l' `Export` option dans le gestionnaire de certificats).</span><span class="sxs-lookup"><span data-stu-id="33139-161">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="33139-162">Empreinte numérique d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).</span><span class="sxs-lookup"><span data-stu-id="33139-162">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="33139-163">Le chemin d’accès complet à un certificat (peut être local ou un partage distant).</span><span class="sxs-lookup"><span data-stu-id="33139-163">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="33139-164">Chemin d’accès à un répertoire contenant un ou des certificats (peut être local ou un partage distant).</span><span class="sxs-lookup"><span data-stu-id="33139-164">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="33139-165">Nom du sujet d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).</span><span class="sxs-lookup"><span data-stu-id="33139-165">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="33139-166">Le certificat obtenu doit avoir `Document Encryption` une utilisation améliorée de la clé ( `1.3.6.1.4.1.311.80.1` ), et `Data Encipherment` les `Key
Encipherment` utilisations de clés ou sont activées.</span><span class="sxs-lookup"><span data-stu-id="33139-166">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="33139-167">La clé privée ne doit pas être déployée sur les événements de journalisation des machines.</span><span class="sxs-lookup"><span data-stu-id="33139-167">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="33139-168">Elle doit être conservée dans un emplacement sécurisé où vous déchiffrez les messages.</span><span class="sxs-lookup"><span data-stu-id="33139-168">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="33139-169">Déchiffrement des messages d’enregistrement des événements protégés</span><span class="sxs-lookup"><span data-stu-id="33139-169">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="33139-170">Le script suivant récupère et déchiffre, en supposant que vous disposiez de la clé privée :</span><span class="sxs-lookup"><span data-stu-id="33139-170">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="33139-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33139-171">See also</span></span>

[<span data-ttu-id="33139-172">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="33139-172">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="33139-173">PowerShell l’équipe Blue Team</span><span class="sxs-lookup"><span data-stu-id="33139-173">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="33139-174">Intégration de SIEM générique</span><span class="sxs-lookup"><span data-stu-id="33139-174">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
