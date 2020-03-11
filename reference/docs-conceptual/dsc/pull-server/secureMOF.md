---
ms.date: 10/31/2017
keywords: dsc,powershell,configuration,installation
title: Sécurisation du fichier MOF
ms.openlocfilehash: ab03db8bf4ed7d412691ae87fd12da5131607886
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278463"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="6bb86-103">Sécurisation du fichier MOF</span><span class="sxs-lookup"><span data-stu-id="6bb86-103">Securing the MOF File</span></span>

> <span data-ttu-id="6bb86-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6bb86-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6bb86-105">DSC gère la configuration des nœuds de serveur en appliquant les informations stockées dans un fichier MOF, où le Gestionnaire de configuration local implémente l’état de fin souhaitée.</span><span class="sxs-lookup"><span data-stu-id="6bb86-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="6bb86-106">Étant donné que ce fichier contient les détails de la configuration, il est important qu’il soit sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6bb86-106">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="6bb86-107">Cette rubrique décrit comment s’assurer que le nœud cible a chiffré le fichier.</span><span class="sxs-lookup"><span data-stu-id="6bb86-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="6bb86-108">À partir de PowerShell version 5.0, la totalité du fichier MOF est chiffrée par défaut quand il est appliqué au nœud à l’aide de l’applet de commande `Start-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="6bb86-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="6bb86-109">Le processus décrit dans cet article est nécessaire uniquement lors de l’implémentation d’une solution utilisant le protocole de service de tirage si les certificats ne sont pas gérés, afin de s’assurer que les configurations téléchargées par le nœud cible peuvent être déchiffrées et lues par le système avant d’être appliquées (par exemple, le service de tirage disponible dans Windows Server).</span><span class="sxs-lookup"><span data-stu-id="6bb86-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="6bb86-110">Sur les nœuds inscrits auprès [d’Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview), des certificats sont automatiquement installés et gérés par le service sans aucune surcharge administrative nécessaire.</span><span class="sxs-lookup"><span data-stu-id="6bb86-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="6bb86-111">Cette rubrique traite des certificats utilisés pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6bb86-111">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="6bb86-112">Pour le chiffrement, un certificat auto-signé est suffisant, car la clé privée est toujours gardée secrète et le chiffrement n’implique pas d’approbation du document.</span><span class="sxs-lookup"><span data-stu-id="6bb86-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="6bb86-113">Les certificats auto-signés ne doivent *pas* être utilisés à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="6bb86-113">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="6bb86-114">Pour l’authentification, vous devez utiliser un certificat d’une Autorité de certification (CA) approuvée.</span><span class="sxs-lookup"><span data-stu-id="6bb86-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6bb86-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="6bb86-115">Prerequisites</span></span>

<span data-ttu-id="6bb86-116">Afin de chiffrer correctement les informations d’identification utilisées pour sécuriser une configuration DSC, assurez-vous d’avoir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6bb86-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="6bb86-117">**Un moyen d’émettre et de distribuer des certificats**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="6bb86-118">Cette rubrique et ses exemples supposent que vous utilisez une autorité de certification Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6bb86-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="6bb86-119">Pour plus d’informations sur les services de certificats Active Directory, consultez [Vue d’ensemble des services de certificats Active Directory](https://technet.microsoft.com/library/hh831740.aspx) et [Services de certificat Active Directory](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="6bb86-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="6bb86-120">**Un accès d’administrateur à un ou plusieurs nœuds cibles**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="6bb86-121">**Chaque nœud cible dispose d’un certificat de chiffrement compatible enregistré dans son magasin personnel**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="6bb86-122">Dans Windows PowerShell, le chemin du magasin est Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="6bb86-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="6bb86-123">Les exemples de cette rubrique utilisent le modèle « Authentification de station de travail », qui est disponible (avec d’autres modèles de certificat) dans la page [Modèles de certificat par défaut](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="6bb86-123">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="6bb86-124">Si vous comptez exécuter cette configuration sur un ordinateur autre que le nœud cible, **exportez la clé publique du certificat**, puis importez-la sur l’ordinateur à partir duquel vous allez exécuter la configuration.</span><span class="sxs-lookup"><span data-stu-id="6bb86-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="6bb86-125">Assurez-vous d’exporter uniquement la clé **publique** et sécurisez la clé privée.</span><span class="sxs-lookup"><span data-stu-id="6bb86-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="6bb86-126">Procédure générale</span><span class="sxs-lookup"><span data-stu-id="6bb86-126">Overall process</span></span>

 1. <span data-ttu-id="6bb86-127">Configurez les certificats, les clés et les empreintes numériques en vous assurant que chaque nœud cible possède des copies du certificat et que l’ordinateur de configuration possède l’empreinte numérique et la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6bb86-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="6bb86-128">Créez un bloc de données de configuration qui contient le chemin et l’empreinte numérique de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6bb86-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="6bb86-129">Créez un script de configuration qui définit votre configuration souhaitée pour le nœud cible et configure le déchiffrement sur les nœuds cibles en ordonnant au gestionnaire de configuration local de déchiffrer les données de configuration à l’aide du certificat et de son empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="6bb86-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="6bb86-130">Exécutez la configuration qui définit les paramètres du gestionnaire de configuration local et lancez la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="6bb86-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="6bb86-132">Conditions requises des certificats</span><span class="sxs-lookup"><span data-stu-id="6bb86-132">Certificate Requirements</span></span>

<span data-ttu-id="6bb86-133">Pour activer le chiffrement des informations d’identification, un certificat de clé publique doit être disponible sur le _nœud cible_, qui est **approuvé** par l’ordinateur utilisé pour créer la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="6bb86-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="6bb86-134">Pour pouvoir être utilisé, ce certificat de clé publique doit répondre à des exigences spécifiques pour le chiffrement des informations d’identification DSC :</span><span class="sxs-lookup"><span data-stu-id="6bb86-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="6bb86-135">**Utilisation de la clé** :</span><span class="sxs-lookup"><span data-stu-id="6bb86-135">**Key Usage**:</span></span>
   - <span data-ttu-id="6bb86-136">Doit contenir : « KeyEncipherment » et « DataEncipherment ».</span><span class="sxs-lookup"><span data-stu-id="6bb86-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="6bb86-137">Ne peut _pas_ contenir : 'Signature numérique'.</span><span class="sxs-lookup"><span data-stu-id="6bb86-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="6bb86-138">**Utilisation améliorée de la clé** :</span><span class="sxs-lookup"><span data-stu-id="6bb86-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="6bb86-139">Doit contenir : Chiffrement de document (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="6bb86-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="6bb86-140">Ne peut _pas_ contenir : Authentification de client (1.3.6.1.5.5.7.3.2) et authentification de serveur (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="6bb86-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="6bb86-141">La clé privée du certificat est disponible sur le \*Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="6bb86-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="6bb86-142">Le **fournisseur** pour le certificat doit être « Fournisseur de services de chiffrement Microsoft RSA SChannel ».</span><span class="sxs-lookup"><span data-stu-id="6bb86-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6bb86-143">Bien que vous puissiez utiliser un certificat contenant une utilisation de clé de type « Digital Signature » ou une authentification d’utilisation améliorée de la clé, la clé de chiffrement est plus facilement utilisée à mauvais escient et vulnérable aux attaques.</span><span class="sxs-lookup"><span data-stu-id="6bb86-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="6bb86-144">Par conséquent, il est recommandé d’utiliser un certificat créé spécifiquement pour les besoins de sécurisation des informations d’identification DSC, qui omet ces paramètres Utilisation de la clé et Utilisation améliorée de la clé.</span><span class="sxs-lookup"><span data-stu-id="6bb86-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="6bb86-145">Tous les certificats existants sur le _Nœud cible_ qui répondent à ces critères peuvent être utilisés pour sécuriser les informations d’identification DSC.</span><span class="sxs-lookup"><span data-stu-id="6bb86-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="6bb86-146">Création du certificat</span><span class="sxs-lookup"><span data-stu-id="6bb86-146">Certificate creation</span></span>

<span data-ttu-id="6bb86-147">Il existe deux approches pour créer et utiliser le certificat de chiffrement requis (paire de clés publique-privée).</span><span class="sxs-lookup"><span data-stu-id="6bb86-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="6bb86-148">Créer le certificat sur le **nœud cible** et exporter uniquement la clé publique vers le **nœud de création**</span><span class="sxs-lookup"><span data-stu-id="6bb86-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="6bb86-149">Créer le certificat sur le **nœud de création** et exporter l’intégralité de la paire de clés vers le **nœud cible**</span><span class="sxs-lookup"><span data-stu-id="6bb86-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="6bb86-150">La première méthode est recommandée, car la clé privée utilisée pour déchiffrer les informations d’identification dans le fichier MOF reste sur le nœud cible en permanence.</span><span class="sxs-lookup"><span data-stu-id="6bb86-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="6bb86-151">Création du certificat sur le nœud cible</span><span class="sxs-lookup"><span data-stu-id="6bb86-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="6bb86-152">La clé privée doit être gardée secrète, car elle est utilisée pour déchiffrer le fichier MOF sur le **nœud cible**. Le moyen le plus simple pour ce faire consiste à créer le certificat de clé privée sur le **nœud cible**, puis à copier le **certificat de clé publique** sur l’ordinateur utilisé pour créer la configuration DSC dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="6bb86-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="6bb86-153">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6bb86-153">The following example:</span></span>

1. <span data-ttu-id="6bb86-154">crée un certificat sur le **nœud cible** ;</span><span class="sxs-lookup"><span data-stu-id="6bb86-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="6bb86-155">exporte le certificat de clé publique sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="6bb86-156">importe le certificat de clé publique dans le magasin de certificats **my** sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="6bb86-157">Sur le nœud cible : créer et exporter le certificat</span><span class="sxs-lookup"><span data-stu-id="6bb86-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="6bb86-158">Nœud cible : Windows Server 2016 et Windows 10</span><span class="sxs-lookup"><span data-stu-id="6bb86-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="6bb86-159">Une fois exporté, le fichier `DscPublicKey.cer` doit être copié vers le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="6bb86-160">Nœud cible : Windows Server 2012 R2/Windows 8.1 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="6bb86-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="6bb86-161">Étant donné que l’applet de commande `New-SelfSignedCertificate` sur les systèmes d’exploitation Windows antérieurs à Windows 10 et Windows Server 2016 ne prend pas en charge le paramètre **Type**, une autre méthode de création de ce certificat est nécessaire sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6bb86-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="6bb86-162">Dans ce cas, vous pouvez utiliser `makecert.exe` ou `certutil.exe` pour créer le certificat.</span><span class="sxs-lookup"><span data-stu-id="6bb86-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="6bb86-163">Une autre méthode consiste à [télécharger le script New-SelfSignedCertificateEx.ps1 à partir du centre de scripts Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) et à l’utiliser pour créer le certificat à la place :</span><span class="sxs-lookup"><span data-stu-id="6bb86-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="6bb86-164">Une fois exporté, le fichier ```DscPublicKey.cer``` doit être copié vers le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="6bb86-165">Sur le nœud de création : importer la clé publique du certificat</span><span class="sxs-lookup"><span data-stu-id="6bb86-165">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="6bb86-166">Création du certificat sur le nœud de création</span><span class="sxs-lookup"><span data-stu-id="6bb86-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="6bb86-167">Vous pouvez également créer le certificat de chiffrement sur le **nœud de création**, l’exporter avec la **clé privée** sous la forme d’un fichier PFX, puis l’importer sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span> <span data-ttu-id="6bb86-168">Il s’agit de la méthode actuelle pour implémenter le chiffrement des informations d’identification DSC sur _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="6bb86-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span> <span data-ttu-id="6bb86-169">Même si le fichier PFX est sécurisé avec un mot de passe, il doit être conservé en lieu sûr pendant le transit.</span><span class="sxs-lookup"><span data-stu-id="6bb86-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="6bb86-170">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="6bb86-170">The following example:</span></span>

1. <span data-ttu-id="6bb86-171">crée un certificat sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="6bb86-172">exporte le certificat, avec la clé privée, sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="6bb86-173">supprime la clé privée du **nœud de création**, mais conserve le certificat de clé publique dans le magasin **my** ;</span><span class="sxs-lookup"><span data-stu-id="6bb86-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="6bb86-174">importe le certificat de clé privée dans le magasin de certificats racines My(Personal) sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="6bb86-175">Il doit être ajouté au magasin racine pour être approuvé par le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="6bb86-176">Sur le nœud de création : créer et exporter le certificat</span><span class="sxs-lookup"><span data-stu-id="6bb86-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="6bb86-177">Nœud cible : Windows Server 2016 et Windows 10</span><span class="sxs-lookup"><span data-stu-id="6bb86-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="6bb86-178">Une fois exporté, le fichier `DscPrivateKey.pfx` doit être copié vers le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="6bb86-179">Nœud cible : Windows Server 2012 R2/Windows 8.1 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="6bb86-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="6bb86-180">Étant donné que l’applet de commande `New-SelfSignedCertificate` sur les systèmes d’exploitation Windows antérieurs à Windows 10 et Windows Server 2016 ne prend pas en charge le paramètre **Type**, une autre méthode de création de ce certificat est nécessaire sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="6bb86-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="6bb86-181">Dans ce cas, vous pouvez utiliser `makecert.exe` ou `certutil.exe` pour créer le certificat.</span><span class="sxs-lookup"><span data-stu-id="6bb86-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="6bb86-182">Une autre méthode consiste à [télécharger le script New-SelfSignedCertificateEx.ps1 à partir du centre de scripts Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) et à l’utiliser pour créer le certificat à la place :</span><span class="sxs-lookup"><span data-stu-id="6bb86-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="6bb86-183">Sur le nœud cible : importer la clé privée du certificat comme racine de confiance</span><span class="sxs-lookup"><span data-stu-id="6bb86-183">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="6bb86-184">Données de configuration</span><span class="sxs-lookup"><span data-stu-id="6bb86-184">Configuration data</span></span>

<span data-ttu-id="6bb86-185">Le bloc de données de configuration définit les nœuds cibles concernés par l’opération, s’il faut ou non déchiffrer les informations d’identification, les moyens de chiffrement et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="6bb86-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="6bb86-186">Pour plus d’informations sur le bloc de données de configuration, consultez [Séparation des données de configuration et d’environnement](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="6bb86-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="6bb86-187">Les éléments pouvant être configurés pour chaque nœud et qui sont liés au chiffrement des informations d’identification sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="6bb86-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="6bb86-188">**NodeName** : nom du nœud cible pour lequel le chiffrement des informations d’identification est configuré.</span><span class="sxs-lookup"><span data-stu-id="6bb86-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="6bb86-189">**PsDscAllowPlainTextPassword** : indique si des informations d’identification non chiffrées peuvent être transmises à ce nœud.</span><span class="sxs-lookup"><span data-stu-id="6bb86-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="6bb86-190">Cela **n’est pas recommandé**.</span><span class="sxs-lookup"><span data-stu-id="6bb86-190">This is **not recommended**.</span></span>
- <span data-ttu-id="6bb86-191">**Thumbprint** : empreinte du certificat utilisée pour déchiffrer les informations d’identification dans la configuration DSC sur le _Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="6bb86-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="6bb86-192">**Ce certificat doit exister dans le magasin de certificats de l’ordinateur local sur le nœud cible.**</span><span class="sxs-lookup"><span data-stu-id="6bb86-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="6bb86-193">**CertificateFile** : fichier de certificat (contenant uniquement la clé publique) qui doit être utilisé pour chiffrer les informations d’identification pour le _Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="6bb86-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="6bb86-194">Le fichier de certificat doit être au format X.509 binaire encodé DER ou X.509 encodé base 64.</span><span class="sxs-lookup"><span data-stu-id="6bb86-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="6bb86-195">Cet exemple montre un bloc de données de configuration qui spécifie le nœud cible concerné nommé targetNode, le chemin du fichier de certificat de clé publique (nommé targetNode.cer) et l’empreinte numérique de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6bb86-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="6bb86-196">Script de configuration</span><span class="sxs-lookup"><span data-stu-id="6bb86-196">Configuration script</span></span>

<span data-ttu-id="6bb86-197">Dans le script de configuration lui-même, utilisez le paramètre `PsCredential` pour vous assurer que les informations d’identification sont stockées le moins longtemps possible.</span><span class="sxs-lookup"><span data-stu-id="6bb86-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="6bb86-198">Quand vous exécutez l’exemple fourni, DSC vous invite à entrer des informations d’identification, puis chiffre le fichier MOF à l’aide du fichier de certificat associé au nœud cible dans le bloc de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="6bb86-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="6bb86-199">Cet exemple de code copie un fichier d’un partage sécurisé vers un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6bb86-199">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="6bb86-200">Configuration du déchiffrement</span><span class="sxs-lookup"><span data-stu-id="6bb86-200">Setting up decryption</span></span>

<span data-ttu-id="6bb86-201">Pour que [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) puisse fonctionner, vous devez indiquer au Gestionnaire de configuration local sur chaque nœud cible le certificat à utiliser pour déchiffrer les informations d’identification, en utilisant la ressource CertificateID pour vérifier l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="6bb86-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="6bb86-202">Cet exemple de fonction recherche le certificat local approprié (vous devez peut-être la personnaliser pour qu’elle recherche le certificat exact que vous souhaitez utiliser) :</span><span class="sxs-lookup"><span data-stu-id="6bb86-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="6bb86-203">Une fois le certificat identifié par son empreinte numérique, le script de configuration peut être mis à jour pour utiliser la valeur suivante :</span><span class="sxs-lookup"><span data-stu-id="6bb86-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="6bb86-204">Exécution de la configuration</span><span class="sxs-lookup"><span data-stu-id="6bb86-204">Running the configuration</span></span>

<span data-ttu-id="6bb86-205">À ce stade, vous pouvez exécuter la configuration qui produira deux fichiers :</span><span class="sxs-lookup"><span data-stu-id="6bb86-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="6bb86-206">Un fichier \*.meta.mof qui configure le gestionnaire de configuration local de façon à déchiffrer les informations d’identification à l’aide du certificat stocké dans le magasin de l’ordinateur local et identifié par son empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="6bb86-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="6bb86-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applique le fichier \*.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="6bb86-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="6bb86-208">Un fichier MOF qui applique la configuration.</span><span class="sxs-lookup"><span data-stu-id="6bb86-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="6bb86-209">Start-DscConfiguration applique la configuration.</span><span class="sxs-lookup"><span data-stu-id="6bb86-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="6bb86-210">Ces commandes accomplissent les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bb86-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="6bb86-211">Cet exemple transmet la configuration DSC au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="6bb86-211">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="6bb86-212">La configuration DSC peut également être appliquée à l’aide d’un serveur collecteur DSC, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="6bb86-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="6bb86-213">Pour plus d’informations sur l’application des configurations DSC à l’aide d’un serveur collecteur DSC, voir [Configuration d’un client collecteur DSC](pullClient.md).</span><span class="sxs-lookup"><span data-stu-id="6bb86-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="6bb86-214">Exemple de module de chiffrement d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="6bb86-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="6bb86-215">Voici un exemple complet qui incorpore toutes ces étapes, ainsi qu’une applet de commande d’assistance qui exporte et copie les clés publiques :</span><span class="sxs-lookup"><span data-stu-id="6bb86-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
