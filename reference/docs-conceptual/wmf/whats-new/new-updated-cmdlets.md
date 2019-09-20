---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
title: Cmdlets nouvelles et mises à jour
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147589"
---
# <a name="new-and-updated-cmdlets"></a>Cmdlets nouvelles et mises à jour

Nous avons ajouté de nouvelles cmdlets et en avons mis à jour d’autres d’après les commentaires de la communauté.

## <a name="archive-cmdlets"></a>Applets de commande d’archive

Deux nouvelles applets de commande, `Compress-Archive` et `Expand-Archive`, permettent de compresser et de décompresser des fichiers ZIP.

Pour plus d’informations, voir la documentation du module [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).

## <a name="catalog-cmdlets"></a>Applets de commande de catalogue

Deux nouvelles cmdlets ont été ajoutées au module Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Elles génèrent et valident des fichiers catalogue Windows.

## <a name="clipboard-cmdlets"></a>Applets de commande de Presse-papiers

`Get-Clipboard` et `Set-Clipboard` permettent de transférer du contenu vers et à partir d’une session Windows PowerShell. Les applets de commande du Presse-papiers prennent en charge les images, les fichiers audio, les listes de fichiers et le texte.

Pour plus d’informations, voir :

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Applets de commande CMS (Cryptographic Message Syntax)

Les applets de commande Cryptographic Message Syntax prennent en charge le chiffrement et le déchiffrement de contenu au format IETF pour la protection par chiffrement des messages comme documenté dans la [RFC5652](https://tools.ietf.org/html/rfc5652.html).

Le standard CMS implémente un chiffrement à clé publique, selon lequel la clé servant à chiffrer le contenu (la *clé publique*) et la clé servant à le déchiffrer (la *clé privée*) sont distinctes.

La clé publique, qui ne constitue pas une donnée sensible, est partageable à grande échelle. Le contenu chiffré avec la clé publique ne peut être déchiffré qu’avec la clé privée. Pour plus d’informations, consultez [Cryptographie asymétrique](https://en.wikipedia.org/wiki/Public-key_cryptography).

Pour plus d’informations, voir :

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

Les certificats ont besoin d’un identificateur EKU (utilisation améliorée de la clé), comme « signature du code » ou « courrier chiffré », pour être identifiés comme certificats de chiffrement de données dans PowerShell. Pour afficher des certificats de chiffrement de document dans le fournisseur de certificats, vous pouvez utiliser le paramètre dynamique **DocumentEncryptionCert** `Get-ChildItem` :

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extraire et analyser des objets structurés à partir de contenu de type chaîne

### <a name="convertfrom-string"></a>ConvertFrom-String

La nouvelle cmdlet `ConvertFrom-String` prend en charge deux modes :

- Analyse délimitée de base
- Analyse générée automatiquement et axée sur des exemples

Par défaut, l’analyse délimitée fractionne l’entrée au niveau de l’espace blanc et elle affecte des noms de propriétés aux groupes résultants.

Le paramètre **-UpdateTemplate** enregistre les résultats de l’algorithme d’apprentissage sous forme de commentaire dans le fichier de modèle. Ainsi, le processus d’apprentissage (l’étape la plus lente) a un coût unique. L’exécution de `ConvertFrom-String` avec un modèle contenant l’algorithme d’apprentissage encodé est maintenant presque instantanée.

Pour plus d’informations, voir [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` permet de fournir des exemples avant/après de l’apparence souhaitée du texte. La cmdlet met automatiquement le texte en forme.

Pour plus d’informations, voir [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Mises à jour de l’objet FileInfo

Les informations de version de fichier peuvent prêter à confusion, notamment dans les cas où le fichier a été corrigé. WMF 5.0 ajoute de nouvelles propriétés de script **FileVersionRaw** et **ProductVersionRaw** aux objets **FileInfo**.
Voici les propriétés telles qu’elles sont affichées pour powershell.exe (en supposant que $pid est l’ID du processus PowerShell) :

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` permet d’afficher du texte ou des données binaires au format hexadécimal.

Pour plus d’informations, voir [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem a un paramètre -Depth

`Get-ChildItem` comporte maintenant un paramètre **Depth** qui permet de limiter la récursivité lorsqu’il est utilisé avec **Recurse** :

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Prise en charge des modules pour la déclaration des plages de versions (1.*, etc.)

Il est maintenant possible de combiner **MinimumVersion** et  **MaximumVersion** pour importer le module dans une plage spécifique. Les paramètres prennent également en charge les caractères génériques.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

Un identificateur unique est nécessaire dans de nombreux scénarios. La cmdlet `New-GUID` permet de créer un nouveau GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Paramètre NoNewLine

`Out-File`, `Add-Content` et `Set-Content` comportent maintenant un nouveau commutateur **NoNewline** qui omet la nouvelle ligne après la sortie. Par exemple :

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Sans **NoNewline**, chacun des fragments serait sur une ligne distincte :

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interagir avec des liens symboliques à l’aide des applets de commande Item améliorées

La cmdlet Item et quelques cmdlets associées ont été étendues de façon à prendre en charge les liens symboliques.

### <a name="symbolic-link-files"></a>Fichiers de liens symboliques

Dans cet exemple, nous créons dans C:\Temp un fichier SYLK nommé MySymLinkFile.txt, qui établit un lien avec $pshome\profile.ps1. Les trois exemples produisent le même résultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Répertoires de liens symboliques

Dans cet exemple, nous créons dans C:\Temp un répertoire SYLK nommé MySymLinkDir, qui établit un lien avec le dossier $pshome. Les trois exemples produisent le même résultat.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>liens physiques ;

Les combinaisons autorisées de **Path** et de **Name** décrites ci-dessus.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Jonctions de répertoires

Les combinaisons autorisées de **Path** et de **Name** décrites ci-dessus.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` affiche maintenant un « l » dans la propriété **Mode** pour indiquer un fichier ou un répertoire SYLK.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

La suppression des liens symboliques fonctionne comme pour n’importe quel type d’élément.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Utilisez le paramètre **Force** pour supprimer les fichiers du répertoire cible et le lien symbolique.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

Parfois, dans vos scripts, vous devez créer un fichier temporaire. C’est maintenant possible avec la commande `New-TemporaryFile` :

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Gestion du commutateur réseau avec PowerShell

Les applets de commande du commutateur réseau, introduites dans WMF 5.0, permettent d’appliquer une configuration de port de commutateur réseau local virtuel (VLAN) et de commutateur réseau de base de couche 2 à des commutateurs réseau certifiés par logo Windows Server 2012 R2. Ces applets de commande vous permettent d’effectuer les opérations suivantes :

- Configuration globale du commutateur, par exemple :
  - Définir le nom d’hôte
  - Définir la bannière de commutateur
  - Conserver la configuration
  - Activer ou désactiver une fonctionnalité

- Configuration de réseau local virtuel :
  - Créer ou supprimer un réseau local virtuel
  - Activer ou désactiver un réseau local virtuel
  - Énumérer les réseaux locaux virtuels
  - Définir le nom convivial d’un réseau local virtuel

- Configuration de port de couche 2 :
  - Énumérer les ports
  - Activer ou désactiver des ports
  - Définir les propriétés et les modes des ports
  - Ajouter ou associer un réseau local virtuel à Trunk ou Accès sur le port

Pour plus d’informations, voir la documentation [NetworkSwitchManager](/powershell/module/networkswitchmanager/).

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Générer des cmdlets PowerShell basées sur un point de terminaison OData avec ODataUtils

Le module ODataUtils permet de générer des cmdlets PowerShell à partir de points de terminaison REST qui prennent en charge OData. Le module Microsoft.PowerShell.ODataUtils comporte les fonctionnalités suivantes :

- Informations supplémentaires sur les canaux du point de terminaison côté serveur vers le côté client.
- Prise en charge de la pagination côté client
- Filtrage côté serveur à l’aide du paramètre -Select
- Prise en charge des en-têtes de demande web

Les cmdlets de proxy générées par la cmdlet `Export-ODataEndPointProxy` fournissent des informations supplémentaires provenant du point de terminaison OData côté serveur sur le flux **Information**.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

Dans l’exemple suivant, nous récupérons les meilleurs produits et capturons la sortie dans la variable `$infoStream`.

En spécifiant le paramètre **IncludeTotalResponseCount**, nous obtenons le nombre total d’enregistrements **Product** disponibles sur le serveur.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Il est possible de récupérer les enregistrements provenant du serveur par lots grâce à la prise en charge de la pagination côté client. C’est utile quand vous devez obtenir une grande quantité de données à partir du serveur par le biais du réseau.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Les cmdlets de proxy générées prennent en charge le paramètre**Select**, qui sert de filtre pour ne recevoir que les propriétés d’enregistrements nécessaires au client. Le filtrage s’effectue sur le serveur, ce qui réduit la quantité de données transférées sur le réseau.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

La cmdlet `Export-ODataEndpointProxy` et les cmdlets de proxy qu’elle génère prennent maintenant en charge le paramètre **Headers**. L’en-tête peut servir à canaliser des informations supplémentaires attendues par le point de terminaison OData.

Dans l’exemple suivant, une table de hachage contenant une clé d’abonnement est fournie au paramètre **Headers**. Il s’agit d’un exemple classique pour des services qui attendent une clé d’abonnement à des fins d’authentification.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
