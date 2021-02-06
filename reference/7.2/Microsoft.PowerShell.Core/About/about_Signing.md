---
description: Explique comment signer des scripts afin qu’ils soient conformes aux stratégies d’exécution de PowerShell.
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 560ecc385e970224a23af7a1195c99d8423f503f
ms.sourcegitcommit: 021ea294327dec542ec040619dac0d2171397a90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2020
ms.locfileid: "99596749"
---
# <a name="about-signing"></a>À propos de la signature

## <a name="short-description"></a>Description courte
Explique comment signer des scripts afin qu’ils soient conformes aux stratégies d’exécution de PowerShell.

## <a name="long-description"></a>Description longue

La stratégie d’exécution restreinte ne permet pas l’exécution de scripts. Les stratégies d’exécution **AllSigned** et **RemoteSigned** empêchent PowerShell d’exécuter des scripts qui n’ont pas de signature numérique.

Cette rubrique explique comment exécuter des scripts sélectionnés qui ne sont pas signés, même si la stratégie d’exécution est **RemoteSigned**, et comment signer des scripts pour votre propre usage.

Pour plus d’informations sur les stratégies d’exécution de PowerShell, consultez [about_Execution_Policies](about_Execution_Policies.md).

## <a name="to-permit-signed-scripts-to-run"></a>Pour autoriser l’exécution de scripts signés

Lorsque vous démarrez PowerShell sur un ordinateur pour la première fois, la stratégie d’exécution **restreinte** (valeur par défaut) est susceptible d’être en vigueur.

La stratégie **restreinte** ne permet pas l’exécution de scripts.

Pour trouver la stratégie d’exécution effective sur votre ordinateur, tapez :

```powershell
Get-ExecutionPolicy
```

Pour exécuter des scripts non signés que vous écrivez sur votre ordinateur local et des scripts signés d’autres utilisateurs, démarrez PowerShell avec l’option Exécuter en tant qu’administrateur, puis utilisez la commande suivante pour modifier la stratégie d’exécution sur l’ordinateur en **RemoteSigned**:

```powershell
Set-ExecutionPolicy RemoteSigned
```

Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande `Set-ExecutionPolicy` .

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>Exécution de scripts non signés à l’aide de la stratégie d’exécution RemoteSigned

Si votre stratégie d’exécution de PowerShell est **RemoteSigned**, PowerShell n’exécutera pas les scripts non signés téléchargés à partir d’Internet, y compris les scripts non signés que vous recevez par courrier électronique et les programmes de messagerie instantanée.

Si vous essayez d’exécuter un script téléchargé, PowerShell affiche le message d’erreur suivant :

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

Avant d’exécuter le script, passez en revue le code pour vous assurer qu’il est digne de confiance.
Les scripts ont le même effet que n’importe quel programme exécutable.

Pour exécuter un script non signé, utilisez l’applet de commande Unblock-File ou utilisez la procédure suivante.

1. Enregistrez le fichier de script sur votre ordinateur.
2. Cliquez sur Démarrer, sur Poste de travail, puis recherchez le fichier de script enregistré.
3. Cliquez avec le bouton droit sur le fichier de script, puis cliquez sur Propriétés.
4. Cliquez sur Débloquer.

Si un script téléchargé à partir d’Internet est signé numériquement, mais que vous n’avez pas encore choisi d’approuver son serveur de publication, PowerShell affiche le message suivant :

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

Si vous faites confiance au serveur de publication, sélectionnez « Exécuter une fois » ou « toujours exécuter ». Si vous ne faites pas confiance au serveur de publication, sélectionnez « jamais exécuté » ou « ne pas exécuter ». Si vous sélectionnez « jamais exécuté » ou « toujours exécuter », PowerShell ne vous invitera plus à nouveau pour ce serveur de publication.

## <a name="methods-of-signing-scripts"></a>Méthodes de signature des scripts

Vous pouvez signer les scripts que vous écrivez et les scripts que vous obtenez à partir d’autres sources. Avant de signer un script, examinez chaque commande pour vérifier qu’elle peut être exécutée en toute sécurité.

Pour connaître les meilleures pratiques relatives à la signature de code, consultez [meilleures pratiques pour la signature de code](/previous-versions/windows/hardware/design/dn653556(v=vs.85)).

Pour plus d’informations sur la façon de signer un fichier de script, consultez [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature).

L' `New-SelfSignedCertificate` applet de commande, introduite dans le module PKI de PowerShell 3,0, crée un certificat auto-signé approprié pour le test. Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande New-SelfSignedCertificate.

Pour ajouter une signature numérique à un script, vous devez la signer avec un certificat de signature de code. Deux types de certificats conviennent pour la signature d’un fichier de script :

- Certificats créés par une autorité de certification : pour des frais, une autorité de certification publique vérifie votre identité et vous donne un certificat de signature de code. Lorsque vous achetez votre certificat auprès d’une autorité de certification reconnue, vous pouvez partager votre script avec des utilisateurs sur d’autres ordinateurs qui exécutent Windows, car ces autres ordinateurs approuvent l’autorité de certification.

- Certificats que vous créez : vous pouvez créer un certificat auto-signé pour lequel votre ordinateur est l’autorité qui crée le certificat. Ce certificat est gratuit et vous permet d’écrire, signer et exécuter des scripts sur votre ordinateur. Toutefois, un script signé par un certificat auto-signé ne s’exécutera pas sur d’autres ordinateurs.

En règle générale, vous utilisez un certificat auto-signé uniquement pour signer des scripts que vous écrivez pour votre propre usage et pour signer des scripts que vous avez vérifiés à partir d’autres sources que vous avez vérifiées comme sécurisées. Il n’est pas approprié pour les scripts qui seront partagés, même au sein d’une entreprise.

Si vous créez un certificat auto-signé, veillez à activer la protection renforcée par clé privée sur votre certificat. Cela empêche les programmes malveillants de signer des scripts en votre nom. Les instructions sont incluses à la fin de cette rubrique.

## <a name="create-a-self-signed-certificate"></a>Créer un certificat auto-signé

Pour créer un certificat auto-signé, utilisez l' `New-SelfSignedCertificate` applet de commande dans le module PKI. Ce module est introduit dans PowerShell 3,0 et est inclus dans Windows 8 et Windows Server 2012. Pour plus d’informations, consultez la rubrique d’aide de l’applet de commande `New-SelfSignedCertificate` .

Pour créer un certificat auto-signé dans des versions antérieures de Windows, utilisez l’outil de création de certificat `MakeCert.exe` . Cet outil est inclus dans le kit de développement logiciel (SDK) Microsoft .NET (versions 1,1 et ultérieures) et dans le Microsoft Windows SDK.

Pour plus d’informations sur la syntaxe et les descriptions des paramètres de l’outil MakeCert.exe, consultez [outil de création de certificats (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80)).

Pour utiliser l’outil MakeCert.exe pour créer un certificat, exécutez les commandes suivantes dans une fenêtre d’invite de commandes du kit de développement SDK.

Remarque : la première commande crée une autorité de certification locale pour votre ordinateur. La deuxième commande génère un certificat personnel à partir de l’autorité de certification.

Remarque : vous pouvez copier ou taper les commandes exactement telles qu’elles apparaissent. Aucune substitution n’est nécessaire, même si vous pouvez modifier le nom du certificat.

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

L’outil MakeCert.exe vous invite à entrer un mot de passe de clé privée. Le mot de passe garantit qu’aucun d’entre eux ne peut utiliser le certificat ou y accéder sans votre consentement.
Créez et entrez un mot de passe que vous pouvez mémoriser. Vous utiliserez ce mot de passe ultérieurement pour récupérer le certificat.

Pour vérifier que le certificat a été généré correctement, utilisez la commande suivante pour récupérer le certificat dans le magasin de certificats sur l’ordinateur. Vous ne trouverez pas de fichier de certificat dans le répertoire du système de fichiers.

À l’invite PowerShell, tapez :

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

Cette commande utilise le fournisseur de certificats PowerShell pour afficher des informations sur le certificat.

Si le certificat a été créé, la sortie affiche l' **empreinte** qui identifie le certificat dans un affichage qui ressemble à ce qui suit :

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>Signer un script

Une fois que vous avez créé un certificat auto-signé, vous pouvez signer des scripts. Si vous utilisez la stratégie d’exécution **AllSigned** , la signature d’un script vous permet d’exécuter le script sur votre ordinateur.

L’exemple de script suivant, `Add-Signature.ps1` , signe un script. Toutefois, si vous utilisez la stratégie d’exécution **AllSigned** , vous devez signer le `Add-Signature.ps1` script avant de l’exécuter.

> [!IMPORTANT]
> Le script doit être enregistré à l’aide de l’encodage ASCII ou UTF8NoBOM. Vous pouvez signer un fichier de script qui utilise un encodage différent. Toutefois, le script ne peut pas s’exécuter ou le module contenant le script ne peut pas être importé.

Pour utiliser ce script, copiez le texte suivant dans un fichier texte, puis nommez-le `Add-Signature.ps1` .

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

Pour signer le `Add-Signature.ps1` fichier de script, tapez les commandes suivantes à l’invite de commandes PowerShell :

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

Une fois le script signé, vous pouvez l’exécuter sur l’ordinateur local. Toutefois, le script ne s’exécute pas sur les ordinateurs sur lesquels la stratégie d’exécution de PowerShell requiert une signature numérique d’une autorité de confiance. Si vous essayez, PowerShell affiche le message d’erreur suivant :

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

Si PowerShell affiche ce message lorsque vous exécutez un script que vous n’avez pas écrit, traitez le fichier comme vous le feriez pour tout script non signé. Examinez le code pour déterminer si vous pouvez faire confiance au script.

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>Activer la protection renforcée par clé privée pour votre certificat

Si vous disposez d’un certificat privé sur votre ordinateur, des programmes malveillants peuvent être en mesure de signer des scripts à votre place, ce qui permet à PowerShell de les exécuter.

Pour empêcher la signature automatique en votre nom, utilisez le gestionnaire `Certmgr.exe` de certificats pour exporter votre certificat de signature dans un `.pfx` fichier. Le gestionnaire de certificats est inclus dans le kit de développement logiciel (SDK) Microsoft .NET, le Microsoft Windows SDK et dans Internet Explorer.

Pour exporter le certificat :

1. Démarrez le gestionnaire de certificats.
2. Sélectionnez le certificat émis par la racine du certificat local PowerShell.
3. Cliquez sur Exporter pour démarrer l’Assistant exportation de certificat.
4. Sélectionnez « Oui, exporter la clé privée », puis cliquez sur suivant.
5. Sélectionnez « Activer la protection renforcée ».
6. Tapez un mot de passe, puis tapez-le à nouveau pour confirmer.
7. Tapez un nom de fichier avec l’extension de nom de fichier. pfx.
8. Cliquez sur Finish.

Pour réimporter le certificat :

1. Démarrez le gestionnaire de certificats.
2. Cliquez sur Importer pour démarrer l’Assistant importation de certificat.
3. Ouvrez l’emplacement du fichier. pfx que vous avez créé pendant le processus d’exportation.
4. Sur la page mot de passe, sélectionnez Activer la protection renforcée par clé privée, puis entrez le mot de passe que vous avez affecté pendant le processus d’exportation.
5. Sélectionnez le magasin de certificats personnel.
6. Cliquez sur Finish.

## <a name="prevent-the-signature-from-expiring"></a>Empêcher l’expiration de la signature

La signature numérique d’un script est valide jusqu’à ce que le certificat de signature expire ou tant qu’un serveur d’horodatage peut vérifier que le script a été signé alors que le certificat de signature est valide.

Étant donné que la plupart des certificats de signature sont valides uniquement pendant un an, l’utilisation d’un serveur d’horodatage garantit que les utilisateurs peuvent utiliser votre script pendant de nombreuses années.

## <a name="see-also"></a>Voir aussi

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[Présentation de la signature de code](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
