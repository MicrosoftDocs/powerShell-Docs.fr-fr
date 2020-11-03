---
description: WSMan
keywords: powershell,applet de commande
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_wsman_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Fournisseur WSMan
ms.openlocfilehash: 7c693d29c6cc7743f7a423ae347889abb10ad255
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208373"
---
# <a name="wsman-provider"></a>Fournisseur WSMan

## <a name="provider-name"></a>Nom du fournisseur

WSMan

## <a name="drives"></a>Lecteurs

`WSMan:`

## <a name="short-description"></a>Description courte

Fournit l'accès aux informations de configuration de WS-Management (Web Services for Management).

## <a name="detailed-description"></a>Description détaillée

Le fournisseur **WSMan** pour PowerShell vous permet d’ajouter, de modifier, d’effacer et de supprimer des WS-Management données de configuration sur des ordinateurs locaux ou distants.

Le fournisseur **WSMan** expose un lecteur PowerShell avec une structure de répertoires qui correspond à un regroupement logique de paramètres de configuration de WS-Management. Ces regroupements sont appelés des conteneurs.

À compter de Windows PowerShell 3,0, le fournisseur **WSMan** a été mis à jour pour prendre en charge de nouvelles propriétés pour les configurations de session, telles que **OutputBufferingMode** . Les configurations de session s’affichent sous la forme d’éléments dans le répertoire de plug-in du `WSMan:` lecteur et les propriétés apparaissent en tant qu’éléments dans chaque configuration de session.

Le fournisseur **WSMan** prend en charge les applets de commande suivantes, qui sont traitées dans cet article.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)

> [!NOTE]
> Vous pouvez utiliser les commandes du `WSMan:` lecteur pour modifier les valeurs des nouvelles propriétés. Toutefois, vous ne pouvez pas utiliser le `WSMan:` lecteur dans powershell 2,0 pour modifier les propriétés introduites dans Windows powershell 3,0.
> Bien qu’aucune erreur ne soit générée, les commandes ne sont pas efficaces pour modifier ces paramètres, utilisez le lecteur **WSMan** dans Windows PowerShell 3,0.

### <a name="organization-of-the-wsman-drive"></a>Organisation du lecteur WSMan :

- **Client** : vous pouvez configurer différents aspects du client WS-Management. Les informations de configuration sont stockées dans le Registre.

- **Service** : vous pouvez configurer différents aspects du service WS-Management.
  Les informations de configuration sont stockées dans le Registre.
  > [!NOTE]
  > La configuration du service est parfois appelée configuration du serveur.

- **Interpréteur** de commandes : vous pouvez configurer différents aspects de l’interpréteur de commandes WS-Management, comme le paramètre permettant l’accès au shell à distance ( **AllowRemoteShellAccess** ) et le nombre maximal d’utilisateurs simultanés autorisés ( **MaxConcurrentUsers** ).

- **Écouteur** : vous pouvez créer et configurer un écouteur. Un écouteur est un service de gestion qui implémente le protocole WS-Management pour envoyer et recevoir des messages.

- **Plug-in** : les plug-ins sont chargés et utilisés par le service WS-Management pour fournir différentes fonctions. Par défaut, PowerShell fournit trois plug-ins :
  - Plug-in de transfert d’événements.
  - Le plug-in Microsoft. PowerShell.
  - Le plug-in du fournisseur Windows Management Instrumentation (WMI).
  Ces trois plug-ins prennent en charge le transfert d’événements, la configuration et l’accès WMI.

- **ClientCertificate** : vous pouvez créer et configurer un certificat client.
  Un certificat client est utilisé quand le client WS-Management est configuré pour utiliser l'authentification par certificat.

### <a name="directory-hierarchy-of-the-wsman-provider"></a>Hiérarchie des répertoires du fournisseur WSMan

La hiérarchie de répertoires du fournisseur WSMan pour l’ordinateur local est la suivante.

```
WSMan:\localhost
--- Client
--- Service
--- Shell
--- Listener
------ <Specific_Listener>
--- Plugin
------ Event Forwarding Plugin
--------- InitializationParameters
--------- Resources
------------ Security
------ Microsoft.Powershell
--------- InitializationParameters
--------- Resources
------------ Security
------ WMI Provider
--------- InitializationParameters
--------- Resources
------------ Security
--- ClientCertificate
```

La hiérarchie des répertoires du fournisseur WSMan pour un ordinateur distant est identique à celle d'un ordinateur local. Cependant, pour pouvoir accéder aux paramètres de configuration d'un ordinateur distant, vous devez établir une connexion avec l'ordinateur distant en utilisant [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan). Une fois qu'une connexion est établie avec un ordinateur distant, le nom de l'ordinateur distant s'affiche dans le fournisseur.

```
WSMan:\<Remote_Computer_Name>
```

## <a name="navigating-the-wsman-drive"></a>Navigation dans le lecteur WSMan :

Cette commande utilise la `Set-Location` cmdlet pour modifier l’emplacement actuel sur le `WSMan:` lecteur.

```powershell
Set-Location WSMan:
```

Pour revenir à un lecteur du système de fichiers, tapez le nom du lecteur. Par exemple, tapez.

```powershell
Set-Location C:
```

### <a name="navigating-to-a-remote-system-store-location"></a>Navigation vers un emplacement du magasin système distant

Cette commande utilise la `Set-Location` commande pour remplacer l’emplacement actuel par l’emplacement racine dans l’emplacement du magasin système distant. Utilisez une barre oblique inverse `\` ou une barre oblique `/` pour indiquer un niveau du `WSMan:` lecteur.

```powershell
Set-Location -Path  WSMan:\SERVER01
```

> [!NOTE]
> La commande ci-dessus suppose qu'il existe déjà une connexion au système distant.

## <a name="displaying-the-contents-of-the-wsman-drive"></a>Affichage du contenu du lecteur WSMan :

Cette commande utilise l' `Get-Childitem` applet de commande pour afficher les WS-Management les magasins dans l’emplacement du magasin localhost.

```powershell
Get-ChildItem -path WSMan:\Localhost
```

Si vous êtes dans le `WSMan:` lecteur, vous pouvez omettre le nom du lecteur.

Cette commande utilise l' `Get-Childitem` applet de commande pour afficher les magasins de WS-Management dans l’emplacement du magasin « SERVEUR01 » de l’ordinateur distant.

```powershell
Get-ChildItem -path WSMan:\SERVER01
```

> [!NOTE]
> La commande ci-dessus suppose qu'il existe déjà une connexion au système distant.

## <a name="setting-the-value-of-items-in-the--wsman-drive"></a>Définition de la valeur des éléments dans le lecteur WSMAN :

Vous pouvez utiliser l' `Set-Item` applet de commande pour modifier les paramètres de configuration dans le `WSMAN` lecteur. L’exemple suivant définit la valeur **TrustedHosts** pour accepter tous les ordinateurs hôtes avec le suffixe « contoso.com ».

```powershell
# You do not need to specify the -Path parameter name when using Set-Item.
PS WSMAN:\localhost\Client> Set-Item .\TrustedHosts -Value "*.contoso.com"
```

L' `Set-Item` applet de commande prend en charge un paramètre supplémentaire `-Concatenate` qui ajoute une valeur au lieu de la modifier. L’exemple suivant ajoute une nouvelle valeur « *. domain2.com » à l’ancienne valeur stockée dans `TrustedHost:`

```powershell
Set-Item WSMAN:\localhost\Client\TrustedHosts *.domain2.com -Concatenate
```

## <a name="creating-items-in-the-wsman-drive"></a>Création d’éléments dans le lecteur WSMAN :

### <a name="creating-a-new-listener"></a>Création d’un nouvel écouteur

L' `New-Item` applet de commande crée des éléments dans un lecteur du fournisseur. Chaque fournisseur a des types d’éléments différents que vous pouvez créer. Dans le `WSMAN:` lecteur, vous pouvez créer des *écouteurs* que vous configurez pour recevoir les demandes distantes et y répondre. La commande suivante crée un nouvel écouteur HTTP à l’aide de l’applet de commande `New-Item` .

```powershell
New-Item -Path WSMan:\localhost\Listener -Address * -Transport HTTP -force
```

### <a name="creating-a-new-plug-in"></a>Création d’un nouveau plug-in

Cette commande crée (enregistre) un plug-in pour le service WS-Management.

```powershell
New-Item -Path WSMan:\localhost\Plugin `
         -Plugin TestPlugin `
         -FileName %systemroot%\system32\WsmWmiPl.dll `
         -Resource http://schemas.dmtf.org/wbem/wscim/2/cim-schema `
         -SDKVersion 1 `
         -Capability "Get","Put","Invoke","Enumerate" `
         -XMLRenderingType text
```

### <a name="creating-a-new-resource-entry"></a>Création d’une nouvelle entrée de ressource

Cette commande crée une entrée de ressource dans le répertoire Resources d’un TestPlugin. Cette commande suppose qu’un TestPlugin a été créé à l’aide d’une commande distincte.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\Resources `
         -ResourceUri http://schemas.dmtf.org/wbem/wscim/3/cim-schema `
         -Capability "Enumerate"

```

### <a name="creating-a-new-security-entry-for-a-resource"></a>Création d’une nouvelle entrée de sécurité pour une ressource

Cette commande crée une entrée de sécurité dans le répertoire Security de Resource_5967683 (une ressource spécifique). Cette commande suppose que l’entrée de ressource a été créée à l’aide d’une commande distincte.

```powershell
$path = "WSMan:\localhost\Plugin\TestPlugin\Resources\Resource_5967683"
New-Item -Path $path\Security `
         -Sddl "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GWGX;;;WD)"
```

### <a name="creating-a-new-client-certificate"></a>Création d’un certificat client

Cette commande crée l’entrée **ClientCertificate** qui peut être utilisée par le client WS-Management. Le nouveau **ClientCertificate** s’affichera sous le répertoire **ClientCertificate** en tant que « ClientCertificate_1234567890 ». Tous les paramètres sont obligatoires. L' **émetteur** doit être l’empreinte numérique du certificat de l’émetteur.

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* `
         -Credential $cred;
```

### <a name="creating-a-new-initialization-parameter"></a>Création d’un paramètre d’initialisation

Cette commande crée un paramètre d’initialisation nommé « testparametername » dans le répertoire « InitializationParameters ». Cette commande suppose que « TestPlugin » a été créé à l’aide d’une commande distincte.

```powershell
New-Item -Path WSMan:\localhost\Plugin\TestPlugin\InitializationParameters `
         -ParamName testparametername `
         -ParamValue testparametervalue
```

## <a name="dynamic-parameters"></a>Paramètres dynamiques

Les paramètres dynamiques sont des paramètres d’applet de commande qui sont ajoutés par un fournisseur PowerShell et sont disponibles uniquement lorsque l’applet de commande est utilisée dans le lecteur activé par le fournisseur.

### <a name="address-string"></a>Address \<String\>

Spécifie l'adresse pour laquelle cet écouteur a été créé. Il peut s'agir de l'une des valeurs suivantes :

- Chaîne littérale « * ». (Le caractère générique ( `*` ) permet à la commande de lier toutes les adresses IP sur toutes les cartes réseau.)
- Chaîne littérale « IP : » suivie d’une adresse IP valide au format décimal délimité par des points IPv4 ou au format hexadécimal cloné IPv6.
- Chaîne littérale « MAC : » suivie de l’adresse MAC d’un adaptateur.
  Par exemple : MAC : 32-a3-58 -90-a-CC.

> [!NOTE]
> La valeur de Address est définie lors de la création d'un écouteur.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="capability-enumeration"></a>Capability \<Enumeration\>

Quand vous utilisez des *plug-ins* , ce paramètre spécifie une opération prise en charge sur cet Uniform Resource Identifier (Uri). Vous devez créer une entrée pour chaque type d'opération pris en charge par l'URI. Vous pouvez spécifier des attributs valides pour une opération donnée, si l’opération la prend en charge.

Ces attributs incluent **SupportsFiltering** et **SupportsFragment** .

- **Créer** : les opérations Create sont prises en charge sur l’URI.
  - L’attribut **SupportFragment**  est utilisé si l’opération de création prend en charge le concept.
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations Create et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Delete** : les opérations de suppression sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** est utilisé si l’opération de suppression prend en charge le concept.
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations DELETE et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Énumérer** : les opérations d’énumération sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** n’est pas pris en charge pour les opérations d’énumération et doit avoir la valeur false.
  - L’attribut **SupportFiltering** est valide, et si le plug-in prend en charge le filtrage, cet attribut doit avoir la valeur « true ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Obtient** : les opérations d’extraction sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** est utilisé si l’opération d’extraction prend en charge le concept.
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations d’extraction et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Invoke** : les opérations d’appel sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** n’est pas pris en charge pour les opérations d’appel et doit avoir la valeur false.
  - L’attribut **SupportFiltering** n’est pas valide et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Put** : les opérations put sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** est utilisé si l’opération put prend en charge le concept.
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations put et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Subscribe** : les opérations d’abonnement sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** n’est pas pris en charge pour les opérations subscribe et doit être défini sur false.
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations subscribe et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n'est pas valide pour un URI si des opérations de l'interpréteur de commandes sont également prises en charge.
- **Shell** : les opérations Shell sont prises en charge sur l’URI.
  - L’attribut **SupportFragment** n’est pas pris en charge pour les opérations de Shell et doit être défini sur « false ».
  - L’attribut **SupportFiltering** n’est pas valide pour les opérations de Shell et doit être défini sur « false ».
  > [!NOTE]
  > Cette opération n’est pas valide pour un URI si une autre opération est également prise en charge.
  > [!NOTE]
  > Si une opération Shell est configurée pour un URI, les opérations Get, Put, Create, Delete, Invoke et Enumerate sont traitées en interne dans le service WS-Management (WinRM) pour gérer les interpréteurs de commandes. Par conséquent, le plug-in ne peut pas gérer les opérations.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="certificatethumbprint-string"></a>CertificateThumbprint \<String\>

Spécifie l'empreinte numérique du certificat de service.

Cette valeur représente la chaîne de valeurs hexadécimales à deux chiffres du champ Thumbprint du certificat. Elle spécifie le certificat de clé publique numérique (X509) d'un compte d'utilisateur qui a l'autorisation d'effectuer cette action. Les certificats sont utilisés dans l'authentification par certificat client. Ils peuvent être mappés uniquement à des comptes d'utilisateurs locaux ; ils ne fonctionnent pas avec des comptes de domaine. Pour obtenir une empreinte numérique de certificat, utilisez les `Get-Item` `Get-ChildItem` applets de commande ou dans le `Cert:` lecteur PowerShell.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="enabled-boolean"></a>Enabled \<Boolean\>

Spécifie si l'écouteur est activé ou désactivé. La valeur par défaut est True.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="filename-plugin-string"></a>FileName (Plugin) \<String\>

Spécifie le nom de fichier du plug-in d’opérations. Toutes les variables d’environnement qui sont placées dans cette entrée seront étendues dans le contexte de l’utilisateur lors de la réception d’une demande. Étant donné que chaque utilisateur peut avoir une version différente de la même variable d’environnement, chaque utilisateur peut avoir un plug-in différent. Cette entrée ne peut pas être vide et doit pointer vers un plug-in valide.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="hostname-string"></a>HostName \<String\>

Spécifie le nom d'hôte de l'ordinateur sur lequel s'exécute le service WS-Management (WinRM).

La valeur doit être un nom de domaine complet, une chaîne littérale IPv4 ou IPv6, ou un caractère générique.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="issuer-string"></a>Issuer \<String\>

Spécifie le nom de l'autorité de certification qui a émis le certificat.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="plugin--ws-management-plug-ins-are-native-dynamic-link-libraries-dlls"></a>\<\>Les plug-ins WS-Management plug-ins sont des bibliothèques de liens dynamiques (dll) natives

Cela permet de s’intégrer à et d’étendre les fonctionnalités de WS-Management. L’API de plug-in WSW-Management fournit des fonctionnalités qui permettent à un utilisateur d’écrire des plug-ins en implémentant certaines API pour les opérations et les URI de ressources pris en charge. Une fois les plug-ins configurés pour le service WS-Management (WinRM) ou pour IIS (Internet Information Services), ces plug-ins sont chargés respectivement dans l'hôte de WS-Management ou dans l'hôte IIS. Les requêtes distantes sont routées vers ces points d'entrée du plug-in pour effectuer des opérations.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="port-unsigned-short-integer"></a>Port \<Unsigned Short Integer\>

Spécifie le port TCP pour lequel cet écouteur est créé. Vous pouvez spécifier n'importe quelle valeur comprise entre 1 et 65 535.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

Spécifie un point de terminaison qui représente un type distinct d'opération ou de valeur de gestion. Un service expose une ou plusieurs ressources, et des ressources peuvent avoir plusieurs instances. Une ressource de gestion est similaire à une classe WMI ou à une table de base de données, et une instance est similaire à une instance de la classe ou à une ligne dans la table. Par exemple, la classe **Win32_LogicalDisk** représente une ressource. `Win32_LogicalDisk="C:\\"` est une instance spécifique de la ressource.

Un URI contient un préfixe et un chemin d'accès à une ressource.
Par exemple :

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="resource-string"></a>Resource \<String\>

Spécifie l'URI (Uniform Resource Identifier) qui identifie un type de ressource spécifique, comme un disque ou un processus, sur un ordinateur.

Un URI se compose d'un préfixe et d'un chemin d'accès à une ressource. Par exemple :

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sdkversion-string"></a>SDKVersion \<String\>

Spécifie la version du Kit de développement logiciel (SDK) du plug-in WS-Management. La seule valeur valide est 
1.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="subject-string"></a>Subject \<String\>

Spécifie l'entité qui est identifiée par le certificat.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="transport-string"></a>Transport \<String\>

Spécifie le transport à utiliser pour envoyer et recevoir les demandes et les réponses du protocole WS-Management. La valeur doit être HTTP ou HTTPS.

Remarque : la valeur de transport est définie lors de la création d’un écouteur.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="uri-string"></a>URI \<String\>

Identifie l'URI pour lequel l'accès est autorisé en fonction de la valeur du paramètre Sddl.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="urlprefix-string"></a>URLPrefix \<String\>

Un préfixe d'URL sur laquelle accepter les demandes HTTP ou HTTPS. Il s’agit d’une chaîne contenant uniquement les caractères,,, le trait de `[a-z]` `[A-Z]` `[9-0]` soulignement ( `_` ) et la barre oblique inverse ( `/` ). La chaîne ne doit pas commencer par une barre oblique inverse () ni se terminer par une barre oblique inverse ( `/` ). Par exemple, si le nom de l’ordinateur est « Exempleordinateur », le client WS-Management spécifie `http://SampleMachine/URLPrefix` dans l’adresse de destination.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="value-string"></a>Value \<String\>

Spécifie la valeur d'un paramètre d'initialisation, qui est une valeur spécifique au plug-in et qui est utilisée pour spécifier des options de configuration.

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="xmlrenderingtype-string"></a>XMLRenderingType \<String\>

Spécifie le format dans lequel le code XML est passé aux plug-ins via l’objet **WSMAN_DATA** . Les valeurs valides sont les suivantes :

- Texte : les données XML entrantes sont contenues dans une structure **WSMAN_DATA_TYPE_TEXT** , qui représente le XML sous la forme d’une mémoire tampon **PCWSTR** .
- XMLReader : les données XML entrantes sont contenues dans une structure **WSMAN_DATA_TYPE_WS_XML_READER** , qui représente le XML sous la forme d’un objet **XmlReader** , qui est défini dans le fichier d’en-tête « WebServices. h ».

#### <a name="cmdlets-supported"></a>Applets de commande prises en charge

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>Utilisation du pipeline

Les applets de commande du fournisseur acceptent l’entrée du pipeline. Vous pouvez utiliser le pipeline pour simplifier la tâche en envoyant les données du fournisseur d’une applet de commande à une autre applet de commande du fournisseur.
Pour en savoir plus sur l’utilisation du pipeline avec les applets de commande du fournisseur, consultez les références des applets de commande fournies dans cet article.

## <a name="getting-help"></a>Obtenir de l’aide

Depuis Windows PowerShell 3.0, vous pouvez obtenir des rubriques d'aide personnalisées pour les applets de commande du fournisseur, qui expliquent comment ces applets de commande se comportent dans un lecteur du système de fichiers.

Pour obtenir les rubriques d’aide personnalisées pour le lecteur du système de fichiers, exécutez une commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) dans un lecteur du système de fichiers ou utilisez le `-Path` paramètre de la commande [obtenir-Help](xref:Microsoft.PowerShell.Core.Get-Help) pour spécifier un lecteur du système de fichiers.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path wsman:
```

## <a name="see-also"></a>Voir aussi

[about_Providers](../../Microsoft.PowerShell.Core/About/about_Providers.md)

