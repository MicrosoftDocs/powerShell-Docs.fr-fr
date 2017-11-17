---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Sécurisation du fichier MOF"
ms.openlocfilehash: dc900f53c954637a407fbd026d24d20c2fdabf6e
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2017
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="748a6-103">Sécurisation du fichier MOF</span><span class="sxs-lookup"><span data-stu-id="748a6-103">Securing the MOF File</span></span>

><span data-ttu-id="748a6-104">S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="748a6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="748a6-105">DSC indique aux nœuds cibles la configuration qu’ils doivent appliquer en envoyant à chaque nœud un fichier MOF contenant ces informations, dans lequel le gestionnaire de configuration local implémente la configuration souhaitée.</span><span class="sxs-lookup"><span data-stu-id="748a6-105">DSC tells the target nodes what configuration they should have by sending a MOF file with that information to each node, where the Local Configuration Manager (LCM) implements the desired configuration.</span></span> <span data-ttu-id="748a6-106">Étant donné que ce fichier contient les détails de la configuration, il est important qu’il soit sécurisé.</span><span class="sxs-lookup"><span data-stu-id="748a6-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span> <span data-ttu-id="748a6-107">Pour ce faire, vous pouvez paramétrer le LCM pour qu’il vérifie les informations d’identification d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="748a6-107">To do this, you can set the LCM to check the credentials of a user.</span></span> <span data-ttu-id="748a6-108">Cette rubrique décrit comment transmettre ces informations d’identification en toute sécurité au nœud cible en les chiffrant avec des certificats.</span><span class="sxs-lookup"><span data-stu-id="748a6-108">This topic describes how to transmit those credentials securely to the target node by encrypting them with certificates.</span></span>

><span data-ttu-id="748a6-109">**Remarque :** cette rubrique présente les certificats utilisés pour le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="748a6-109">**Note:** This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="748a6-110">Pour le chiffrement, un certificat auto-signé est suffisant, car la clé privée est toujours gardée secrète et le chiffrement n’implique pas d’approbation du document.</span><span class="sxs-lookup"><span data-stu-id="748a6-110">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="748a6-111">Les certificats auto-signés ne doivent *pas* être utilisés à des fins d’authentification.</span><span class="sxs-lookup"><span data-stu-id="748a6-111">Self-signed certificates should *not* be used for authentication purposes.</span></span> <span data-ttu-id="748a6-112">Pour l’authentification, vous devez utiliser un certificat d’une Autorité de certification (CA) approuvée.</span><span class="sxs-lookup"><span data-stu-id="748a6-112">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="748a6-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="748a6-113">Prerequisites</span></span>

<span data-ttu-id="748a6-114">Afin de chiffrer correctement les informations d’identification utilisées pour sécuriser une configuration DSC, assurez-vous d’avoir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="748a6-114">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="748a6-115">**Un moyen d’émettre et de distribuer des certificats**.</span><span class="sxs-lookup"><span data-stu-id="748a6-115">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="748a6-116">Cette rubrique et ses exemples supposent que vous utilisez une autorité de certification Active Directory.</span><span class="sxs-lookup"><span data-stu-id="748a6-116">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="748a6-117">Pour plus d’informations sur les services de certificats Active Directory, consultez [Vue d’ensemble des services de certificats Active Directory](https://technet.microsoft.com/library/hh831740.aspx) et [Services de certificat Active Directory](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="748a6-117">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="748a6-118">**Un accès d’administrateur à un ou plusieurs nœuds cibles**.</span><span class="sxs-lookup"><span data-stu-id="748a6-118">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="748a6-119">**Chaque nœud cible dispose d’un certificat de chiffrement compatible enregistré dans son magasin personnel**.</span><span class="sxs-lookup"><span data-stu-id="748a6-119">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="748a6-120">Dans Windows PowerShell, le chemin du magasin est Cert:\LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="748a6-120">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="748a6-121">Les exemples de cette rubrique utilisent le modèle « Authentification de station de travail », disponible (ainsi que d’autres modèles de certificat) dans la page [Modèles de certificat par défaut](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="748a6-121">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="748a6-122">Si vous comptez exécuter cette configuration sur un ordinateur autre que le nœud cible, **exportez la clé publique du certificat**, puis importez-la sur l’ordinateur à partir duquel vous allez exécuter la configuration.</span><span class="sxs-lookup"><span data-stu-id="748a6-122">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="748a6-123">Assurez-vous d’exporter uniquement la clé **publique** et sécurisez la clé privée.</span><span class="sxs-lookup"><span data-stu-id="748a6-123">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="748a6-124">Processus général</span><span class="sxs-lookup"><span data-stu-id="748a6-124">Overall process</span></span>

 1. <span data-ttu-id="748a6-125">Configurez les certificats, les clés et les empreintes numériques en vous assurant que chaque nœud cible possède des copies du certificat et que l’ordinateur de configuration possède l’empreinte numérique et la clé publique.</span><span class="sxs-lookup"><span data-stu-id="748a6-125">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="748a6-126">Créez un bloc de données de configuration qui contient le chemin et l’empreinte numérique de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="748a6-126">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="748a6-127">Créez un script de configuration qui définit votre configuration souhaitée pour le nœud cible et configure le déchiffrement sur les nœuds cibles en ordonnant au gestionnaire de configuration local de déchiffrer les données de configuration à l’aide du certificat et de son empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="748a6-127">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="748a6-128">Exécutez la configuration qui définit les paramètres du gestionnaire de configuration local et lancez la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="748a6-128">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="748a6-130">Exigences de certificat</span><span class="sxs-lookup"><span data-stu-id="748a6-130">Certificate Requirements</span></span>

<span data-ttu-id="748a6-131">Pour activer le chiffrement des informations d’identification, un certificat de clé publique doit être disponible sur le _nœud cible_, qui est **approuvé** par l’ordinateur utilisé pour créer la configuration DSC.</span><span class="sxs-lookup"><span data-stu-id="748a6-131">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="748a6-132">Pour pouvoir être utilisé, ce certificat de clé publique doit répondre à des exigences spécifiques pour le chiffrement des informations d’identification DSC :</span><span class="sxs-lookup"><span data-stu-id="748a6-132">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="748a6-133">**Utilisation de la clé** :</span><span class="sxs-lookup"><span data-stu-id="748a6-133">**Key Usage**:</span></span>
   - <span data-ttu-id="748a6-134">Doit contenir : « KeyEncipherment » et « DataEncipherment ».</span><span class="sxs-lookup"><span data-stu-id="748a6-134">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="748a6-135">Ne doit _pas_ contenir : « Digital Signature ».</span><span class="sxs-lookup"><span data-stu-id="748a6-135">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="748a6-136">**Utilisation améliorée de la clé** :</span><span class="sxs-lookup"><span data-stu-id="748a6-136">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="748a6-137">Doit contenir : chiffrement de document (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="748a6-137">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="748a6-138">Ne doit _pas_ contenir : Client Authentication (1.3.6.1.5.5.7.3.2) et Server Authentication (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="748a6-138">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="748a6-139">La clé privée du certificat est disponible sur le *Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="748a6-139">The Private Key for the certificate is available on the *Target Node_.</span></span>
 4. <span data-ttu-id="748a6-140">Le **fournisseur** pour le certificat doit être « Fournisseur de services de chiffrement Microsoft RSA SChannel ».</span><span class="sxs-lookup"><span data-stu-id="748a6-140">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>
 
><span data-ttu-id="748a6-141">**Bonne pratique recommandée :** bien que vous puissiez utiliser un certificat contenant une utilisation de clé de type « Digital Signature » ou une authentification d’utilisation améliorée de la clé, la clé de chiffrement est plus facilement utilisée à mauvais escient et vulnérable aux attaques.</span><span class="sxs-lookup"><span data-stu-id="748a6-141">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="748a6-142">Par conséquent, il est recommandé d’utiliser un certificat créé spécifiquement pour les besoins de sécurisation des informations d’identification DSC, qui omet ces paramètres Utilisation de la clé et Utilisation améliorée de la clé.</span><span class="sxs-lookup"><span data-stu-id="748a6-142">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>
  
<span data-ttu-id="748a6-143">Tous les certificats existants sur le _Nœud cible_ qui répondent à ces critères peuvent être utilisés pour sécuriser les informations d’identification DSC.</span><span class="sxs-lookup"><span data-stu-id="748a6-143">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="748a6-144">Création du certificat</span><span class="sxs-lookup"><span data-stu-id="748a6-144">Certificate creation</span></span>

<span data-ttu-id="748a6-145">Il existe deux approches pour créer et utiliser le certificat de chiffrement requis (paire de clés publique-privée).</span><span class="sxs-lookup"><span data-stu-id="748a6-145">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="748a6-146">Créer le certificat sur le **nœud cible** et exporter uniquement la clé publique vers le **nœud de création**</span><span class="sxs-lookup"><span data-stu-id="748a6-146">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="748a6-147">Créer le certificat sur le **nœud de création** et exporter l’intégralité de la paire de clés vers le **nœud cible**</span><span class="sxs-lookup"><span data-stu-id="748a6-147">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="748a6-148">La première méthode est recommandée, car la clé privée utilisée pour déchiffrer les informations d’identification dans le fichier MOF reste sur le nœud cible en permanence.</span><span class="sxs-lookup"><span data-stu-id="748a6-148">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="748a6-149">Création du certificat sur le nœud cible</span><span class="sxs-lookup"><span data-stu-id="748a6-149">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="748a6-150">La clé privée doit être gardée secrète, car elle est utilisée pour déchiffrer le fichier MOF sur le **nœud cible**. Le moyen le plus simple pour ce faire consiste à créer le certificat de clé privée sur le **nœud cible**, puis à copier le **certificat de clé publique** sur l’ordinateur utilisé pour créer la configuration DSC dans un fichier MOF.</span><span class="sxs-lookup"><span data-stu-id="748a6-150">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="748a6-151">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="748a6-151">The following example:</span></span>
 1. <span data-ttu-id="748a6-152">crée un certificat sur le **nœud cible** ;</span><span class="sxs-lookup"><span data-stu-id="748a6-152">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="748a6-153">exporte le certificat de clé publique sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="748a6-153">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="748a6-154">importe le certificat de clé publique dans le magasin de certificats **my** sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="748a6-154">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="748a6-155">Sur le nœud cible : créer et exporter le certificat</span><span class="sxs-lookup"><span data-stu-id="748a6-155">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="748a6-156">Nœud de création : Windows Server 2016 et Windows 10</span><span class="sxs-lookup"><span data-stu-id="748a6-156">Authoring Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="748a6-157">Une fois exporté, le fichier ```DscPublicKey.cer``` doit être copié vers le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="748a6-157">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="748a6-158">Nœud de création : Windows Server 2012 R2/Windows 8.1 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="748a6-158">Authoring Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="748a6-159">Étant donné que l’applet de commande New-SelfSignedCertificate sur les systèmes d’exploitation Windows antérieurs à Windows 10 et Windows Server 2016 ne prend pas en charge le paramètre **Type**, une autre méthode de création de ce certificat est requise sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="748a6-159">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="748a6-160">Dans ce cas, vous pouvez utiliser ```makecert.exe``` ou ```certutil.exe``` pour créer le certificat.</span><span class="sxs-lookup"><span data-stu-id="748a6-160">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="748a6-161">Une autre méthode consiste à [télécharger le script New-SelfSignedCertificateEx.ps1 à partir du centre de scripts Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) et à l’utiliser pour créer le certificat à la place :</span><span class="sxs-lookup"><span data-stu-id="748a6-161">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="748a6-162">Une fois exporté, le fichier ```DscPublicKey.cer``` doit être copié vers le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="748a6-162">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="748a6-163">Sur le nœud de création : importer la clé publique du certificat</span><span class="sxs-lookup"><span data-stu-id="748a6-163">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="748a6-164">Création du certificat sur le nœud de création</span><span class="sxs-lookup"><span data-stu-id="748a6-164">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="748a6-165">Vous pouvez également créer le certificat de chiffrement sur le **nœud de création**, l’exporter avec la **clé privée** sous la forme d’un fichier PFX, puis l’importer sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="748a6-165">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="748a6-166">Il s’agit de la méthode actuelle pour implémenter le chiffrement des informations d’identification DSC sur _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="748a6-166">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="748a6-167">Même si le fichier PFX est sécurisé avec un mot de passe, il doit être conservé en lieu sûr pendant le transit.</span><span class="sxs-lookup"><span data-stu-id="748a6-167">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="748a6-168">L’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="748a6-168">The following example:</span></span>
 1. <span data-ttu-id="748a6-169">crée un certificat sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="748a6-169">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="748a6-170">exporte le certificat, avec la clé privée, sur le **nœud de création**.</span><span class="sxs-lookup"><span data-stu-id="748a6-170">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="748a6-171">supprime la clé privée du **nœud de création**, mais conserve le certificat de clé publique dans le magasin **my** ;</span><span class="sxs-lookup"><span data-stu-id="748a6-171">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="748a6-172">importe le certificat de clé privée dans le magasin de certificats racines sur le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="748a6-172">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="748a6-173">Il doit être ajouté au magasin racine pour être approuvé par le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="748a6-173">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="748a6-174">Sur le nœud de création : créer et exporter le certificat</span><span class="sxs-lookup"><span data-stu-id="748a6-174">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="748a6-175">Nœud cible : Windows Server 2016 et Windows 10</span><span class="sxs-lookup"><span data-stu-id="748a6-175">Target Node: Windows Server 2016 and Windows 10</span></span>

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
<span data-ttu-id="748a6-176">Une fois exporté, le fichier ```DscPrivateKey.pfx``` doit être copié vers le **nœud cible**.</span><span class="sxs-lookup"><span data-stu-id="748a6-176">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="748a6-177">Nœud cible : Windows Server 2012 R2/Windows 8.1 et versions antérieures</span><span class="sxs-lookup"><span data-stu-id="748a6-177">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="748a6-178">Étant donné que l’applet de commande New-SelfSignedCertificate sur les systèmes d’exploitation Windows antérieurs à Windows 10 et Windows Server 2016 ne prend pas en charge le paramètre **Type**, une autre méthode de création de ce certificat est requise sur ces systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="748a6-178">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="748a6-179">Dans ce cas, vous pouvez utiliser ```makecert.exe``` ou ```certutil.exe``` pour créer le certificat.</span><span class="sxs-lookup"><span data-stu-id="748a6-179">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="748a6-180">Une autre méthode consiste à [télécharger le script New-SelfSignedCertificateEx.ps1 à partir du centre de scripts Microsoft](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) et à l’utiliser pour créer le certificat à la place :</span><span class="sxs-lookup"><span data-stu-id="748a6-180">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="748a6-181">Sur le nœud cible : importer la clé privée du certificat en tant que racine de confiance</span><span class="sxs-lookup"><span data-stu-id="748a6-181">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\Root -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="748a6-182">Données de configuration</span><span class="sxs-lookup"><span data-stu-id="748a6-182">Configuration data</span></span>

<span data-ttu-id="748a6-183">Le bloc de données de configuration définit les nœuds cibles concernés par l’opération, s’il faut ou non déchiffrer les informations d’identification, les moyens de chiffrement et d’autres informations.</span><span class="sxs-lookup"><span data-stu-id="748a6-183">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="748a6-184">Pour plus d’informations sur le bloc de données de configuration, consultez [Séparation des données de configuration et d’environnement](configData.md).</span><span class="sxs-lookup"><span data-stu-id="748a6-184">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="748a6-185">Les éléments pouvant être configurés pour chaque nœud et qui sont liés au chiffrement des informations d’identification sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="748a6-185">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="748a6-186">**NodeName** : nom du nœud cible pour lequel le chiffrement des informations d’identification est configuré.</span><span class="sxs-lookup"><span data-stu-id="748a6-186">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="748a6-187">**PsDscAllowPlainTextPassword** : indique si des informations d’identification non chiffrées peuvent être transmises à ce nœud.</span><span class="sxs-lookup"><span data-stu-id="748a6-187">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="748a6-188">Cela **n’est pas recommandé**.</span><span class="sxs-lookup"><span data-stu-id="748a6-188">This is **not recommended**.</span></span>
* <span data-ttu-id="748a6-189">**Thumbprint** : empreinte du certificat utilisée pour déchiffrer les informations d’identification dans la configuration DSC sur le _Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="748a6-189">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="748a6-190">**Ce certificat doit exister dans le magasin de certificats de l’ordinateur local sur le nœud cible.**</span><span class="sxs-lookup"><span data-stu-id="748a6-190">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="748a6-191">**CertificateFile** : fichier de certificat (contenant uniquement la clé publique) qui doit être utilisé pour chiffrer les informations d’identification pour le _Nœud cible_.</span><span class="sxs-lookup"><span data-stu-id="748a6-191">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="748a6-192">Le fichier de certificat doit être au format X.509 binaire encodé DER ou X.509 encodé base 64.</span><span class="sxs-lookup"><span data-stu-id="748a6-192">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="748a6-193">Cet exemple montre un bloc de données de configuration qui spécifie le nœud cible concerné nommé targetNode, le chemin du fichier de certificat de clé publique (nommé targetNode.cer) et l’empreinte numérique de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="748a6-193">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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


## <a name="configuration-script"></a><span data-ttu-id="748a6-194">Script de configuration</span><span class="sxs-lookup"><span data-stu-id="748a6-194">Configuration script</span></span>

<span data-ttu-id="748a6-195">Dans le script de configuration lui-même, utilisez le paramètre `PsCredential` pour vous assurer que les informations d’identification sont stockées le moins longtemps possible.</span><span class="sxs-lookup"><span data-stu-id="748a6-195">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="748a6-196">Quand vous exécutez l’exemple fourni, DSC vous invite à entrer des informations d’identification, puis chiffre le fichier MOF à l’aide du fichier de certificat associé au nœud cible dans le bloc de données de configuration.</span><span class="sxs-lookup"><span data-stu-id="748a6-196">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="748a6-197">Cet exemple de code copie un fichier d’un partage sécurisé vers un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="748a6-197">This code example copies a file from a share that is secured to a user.</span></span>

```
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

## <a name="setting-up-decryption"></a><span data-ttu-id="748a6-198">Configuration du déchiffrement</span><span class="sxs-lookup"><span data-stu-id="748a6-198">Setting up decryption</span></span>

<span data-ttu-id="748a6-199">Pour que [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) puisse fonctionner, vous devez indiquer au gestionnaire de configuration local sur chaque nœud cible le certificat à utiliser pour déchiffrer les informations d’identification, en utilisant la ressource CertificateID pour vérifier l’empreinte du certificat.</span><span class="sxs-lookup"><span data-stu-id="748a6-199">Before [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="748a6-200">Cet exemple de fonction recherche le certificat local approprié (vous devez peut-être la personnaliser pour qu’elle recherche le certificat exact que vous souhaitez utiliser) :</span><span class="sxs-lookup"><span data-stu-id="748a6-200">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="748a6-201">Une fois le certificat identifié par son empreinte numérique, le script de configuration peut être mis à jour pour utiliser la valeur suivante :</span><span class="sxs-lookup"><span data-stu-id="748a6-201">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="748a6-202">Exécution de la configuration</span><span class="sxs-lookup"><span data-stu-id="748a6-202">Running the configuration</span></span>

<span data-ttu-id="748a6-203">À ce stade, vous pouvez exécuter la configuration qui produira deux fichiers :</span><span class="sxs-lookup"><span data-stu-id="748a6-203">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="748a6-204">Un fichier *.meta.mof qui configure le gestionnaire de configuration local de façon à déchiffrer les informations d’identification à l’aide du certificat stocké dans le magasin de l’ordinateur local et identifié par son empreinte numérique.</span><span class="sxs-lookup"><span data-stu-id="748a6-204">A *.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="748a6-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applique le fichier *.meta.mof.</span><span class="sxs-lookup"><span data-stu-id="748a6-205">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applies the *.meta.mof file.</span></span>
 * <span data-ttu-id="748a6-206">Un fichier MOF qui applique la configuration.</span><span class="sxs-lookup"><span data-stu-id="748a6-206">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="748a6-207">Start-DscConfiguration applique la configuration.</span><span class="sxs-lookup"><span data-stu-id="748a6-207">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="748a6-208">Ces commandes accomplissent les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="748a6-208">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="748a6-209">Cet exemple transmet la configuration DSC au nœud cible.</span><span class="sxs-lookup"><span data-stu-id="748a6-209">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="748a6-210">La configuration DSC peut également être appliquée à l’aide d’un serveur collecteur DSC, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="748a6-210">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="748a6-211">Pour plus d’informations sur l’application des configurations DSC à l’aide d’un serveur collecteur DSC, voir [Configuration d’un client collecteur DSC](pullClient.md).</span><span class="sxs-lookup"><span data-stu-id="748a6-211">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="748a6-212">Exemple de module de chiffrement d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="748a6-212">Credential Encryption Module Example</span></span>

<span data-ttu-id="748a6-213">Voici un exemple complet qui incorpore toutes ces étapes, ainsi qu’une applet de commande d’assistance qui exporte et copie les clés publiques :</span><span class="sxs-lookup"><span data-stu-id="748a6-213">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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

