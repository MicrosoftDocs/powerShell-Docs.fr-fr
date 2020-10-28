---
ms.date: 12/23/2019
keywords: powershell,applet de commande
title: Exécution de tâches de mise en réseau
description: Cet article explique comment utiliser les classes WMI dans PowerShell pour gérer les paramètres de configuration réseau dans Windows.
ms.openlocfilehash: 95b05c193f4168cdcdf8414399c4f8c569bff754
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500247"
---
# <a name="performing-networking-tasks"></a>Exécution de tâches de mise en réseau

TCP/IP étant le protocole réseau le plus utilisé, la plupart des tâches d’administration de protocole réseau de bas niveau impliquent TCP/IP. Dans cette section, nous utilisons PowerShell et WMI pour effectuer ces tâches.

## <a name="listing-ip-addresses-for-a-computer"></a>Affichage de la liste des adresses IP pour un ordinateur

Pour obtenir toutes les adresses IP utilisées sur l’ordinateur local, entrez la commande suivante :

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

La sortie de cette commande diffère de la plupart des listes de propriétés, car les valeurs sont entourées d’accolades :

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

Pour comprendre pourquoi des accolades s’affichent, utilisez la cmdlet `Get-Member` pour examiner la propriété **IPAddress**  :

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

La propriété IPAddress pour chaque carte réseau est en réalité un tableau. Les accolades dans la définition indiquent qu’ **IPAddress** n’est pas une valeur **System.String** , mais un tableau de valeurs **System.String** .

## <a name="listing-ip-configuration-data"></a>Affichage de la liste des données de configuration IP

Pour afficher les données de configuration IP détaillées de chaque carte réseau, utilisez la commande suivante :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

L’affichage par défaut pour l’objet Configuration de la carte réseau est un jeu très réduit des informations disponibles. Pour une inspection et un dépannage approfondis, utilisez `Select-Object` ou une cmdlet de mise en forme, telle que `Format-List`, pour spécifier les propriétés à afficher.

Dans les réseaux TCP/IP modernes, vous n’êtes probablement pas intéressé par les propriétés IPX ou WINS. Vous pouvez utiliser le paramètre **ExcludeProperty** de `Select-Object` pour masquer les propriétés dont les noms commencent par « WINS » ou « IPX ».

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

Cette commande retourne des informations détaillées sur DHCP, DNS, le routage et d’autres propriétés de configuration IP secondaires.

## <a name="pinging-computers"></a>Test ping des ordinateurs

Vous pouvez effectuer un simple test ping sur un ordinateur à l’aide de la méthode **Win32_PingStatus** . La commande suivante exécute le test ping, mais retourne un résultat assez long :

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

Une forme plus utile pour les informations résumées est l’affichage des propriétés Address, ResponseTime et StatusCode, généré par la commande suivante. Le paramètre **Autosize** de `Format-Table` redimensionne les colonnes de la tablea fin qu’elles s’affichent correctement dans PowerShell.

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Un StatusCode de 0 indique un test ping réussi.

Vous pouvez utiliser un tableau pour effectuer un test ping de plusieurs ordinateurs avec une seule commande. Étant donné qu’il y a plusieurs adresses, utilisez la méthode `ForEach-Object` pour effectuer un test ping de chaque adresse séparément :

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

Vous pouvez utiliser le même format de commande pour effectuer un test ping de tous les ordinateurs d’un sous-réseau, tel qu’un réseau privé utilisant le numéro de réseau 192.168.1.0 et un masque de sous-réseau de classe C standard (255.255.255.0). Seules les adresses dans la plage de 192.168.1.1 à 192.168.1.254 sont des adresses locales légitimes (0 est toujours réservé au numéro de réseau et 255 est une adresse de diffusion de sous-réseau).

Pour représenter un tableau des nombres de 1 à 254 dans PowerShell, utilisez l’instruction **1..254.**
Vous pouvez effectuer un test ping d’un sous-réseau complet en générant le tableau, puis en ajoutant les valeurs sur une adresse partielle dans l’instruction ping :

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

Notez que cette technique pour la génération d’une plage d’adresses est également utilisable ailleurs. Vous pouvez générer un jeu complet d’adresses comme suit :

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Récupération des propriétés d’une carte réseau

Nous avons mentionné ci-dessus, qu’il est possible de récupérer des propriétés de configuration générale à l’aide de la classe **Win32_NetworkAdapterConfiguration** . Bien qu’il ne s’agisse pas strictement d’informations TCP/IP, les informations de carte réseau telles que les adresses MAC et les types de cartes peuvent être utiles pour comprendre ce qui se passe sur un ordinateur. Pour obtenir un résumé de ces informations, utilisez la commande suivante :

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Attribution de domaine DNS pour une carte réseau

Pour attribuer le domaine DNS pour une résolution de noms automatique, utilisez la méthode **SetDNSDomain** de **Win32_NetworkAdapterConfiguration** . Étant donné que vous attribuez le domaine DNS indépendamment pour chaque configuration de carte réseau, vous devez utiliser une instruction `ForEach-Object` pour attribuer le domaine à chaque carte :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

L’instruction de filtrage `IPEnabled=$true` est nécessaire car, même sur un réseau utilisant uniquement TCP/IP, certaines configurations de carte réseau sur un ordinateur ne sont pas de véritables adaptateurs TCP/IP, mais des éléments logiciels généraux prenant en charge RAS, PPTP, QoS et d’autres services pour tous les adaptateurs et n’ayant donc pas d’adresse propre.

Vous pouvez filtrer la commande à l’aide de la cmdlet `Where-Object` plutôt qu’en utilisant le filtre `Get-CimInstance`.

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Exécution de tâches de configuration DHCP

La modification des détails DHCP implique l’utilisation d’un ensemble de cartes réseau, tout comme la configuration DNS. Vous pouvez effectuer diverses actions à l’aide de WMI. Nous allons en décrire quelques-unes parmi les plus courantes.

### <a name="determining-dhcp-enabled-adapters"></a>Détermination des cartes avec DHCP activé

Pour rechercher les cartes avec DHCP activé sur un ordinateur, utilisez la commande suivante :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

Pour exclure les cartes présentant des problèmes de configuration IP, vous pouvez récupérer uniquement les cartes avec IP activé :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>Récupération des propriétés DHCP

Étant donné que les propriétés DHCP d’un adaptateur commencent généralement par `DHCP`, vous pouvez utiliser le paramètre Propriété de `Format-Table` pour afficher uniquement ces propriétés :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Activation du protocole DHCP sur chaque carte

Pour activer le protocole DHCP sur toutes les cartes, utilisez la commande suivante :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

Vous pouvez utiliser l’instruction **Filtre**`IPEnabled=$true and DHCPEnabled=$false` pour éviter d’activer le protocole DHCP là où il est déjà activé, mais l’omission de cette étape ne génère pas d’erreurs.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Résiliation et renouvellement de baux DHCP sur des cartes spécifiques

La classe **Win32_NetworkAdapterConfiguration** dispose des méthodes **ReleaseDHCPLease** et **RenewDHCPLease** . Toutes deux sont utilisées de la même façon. En règle générale, utilisez ces méthodes si vous devez uniquement résilier ou renouveler des adresses pour une carte sur un sous-réseau spécifique. La manière la plus simple de filtrer des cartes sur un sous-réseau consiste à choisir uniquement les configurations de carte qui utilisent la passerelle pour ce sous-réseau. Par exemple, la commande suivante libère tous les baux DHCP sur les cartes de l’ordinateur local qui obtiennent des baux DHCP à partir de 192.168.1.254 :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Le seul changement pour le renouvellement d’un bail DHCP consiste à utiliser la méthode **RenewDHCPLease** plutôt que la méthode **ReleaseDHCPLease**  :

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Lorsque vous utilisez ces méthodes sur un ordinateur distant, n’oubliez pas que vous risquez de perdre l’accès au système distant si vous êtes connecté à celui-ci via la carte dont le bail a été résilié ou renouvelé.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Résiliation et renouvellement de baux DHCP sur toutes les cartes

Vous pouvez effectuer des résiliations ou renouvellements d’adresse DHCP sur toutes les cartes en utilisant les méthodes **Win32_NetworkAdapterConfiguration** , **ReleaseDHCPLeaseAll** et **RenewDHCPLeaseAll** .
Toutefois, la commande doit s’appliquer à la classe WMI, plutôt qu’à une carte particulière, car la résiliation et le renouvellement de baux de façon globale sont effectuées sur la classe, et non sur une carte spécifique.

Vous pouvez obtenir une référence à une classe WMI plutôt qu’à des instances de classe, en répertoriant toutes les classes WMI, puis en sélectionnant uniquement la classe souhaitée par son nom. Par exemple, la commande suivante retourne la classe **Win32_NetworkAdapterConfiguration**  :

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Vous pouvez traiter la commande entière comme la classe, puis appeler dessus la méthode **ReleaseDHCPAdapterLease** . Dans la commande suivante, les parenthèses entourant les éléments de pipeline `Get-CimInstance` et `Where-Object` indiquent à PowerShell de les évaluer en priorité :

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

Vous pouvez utiliser le même format de commande pour appeler la méthode **RenewDHCPLeaseAll** :

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Création d’un partage réseau

Pour créer un partage réseau, utilisez la méthode **Créer** de **Win32_Share**  :

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

Vous pouvez également créer le partage en utilisant `net share` dans PowerShell sur Windows :

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Suppression d’un partage réseau

Vous pouvez supprimer un partage réseau avec la commande **Win32_Share** , mais le processus diffère légèrement de la création d’un partage, car vous devez récupérer le partage spécifique à supprimer, plutôt que la classe **Win32_Share** . L’instruction suivante supprime le partage **TempShare**  :

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

Dans Windows, `net share` fonctionne également :

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Connexion d’un lecteur réseau accessible à Windows

Les cmdlets `New-PSDrive` créent un lecteur PowerShell, mais les lecteurs créés de cette façon sont disponibles uniquement pour PowerShell. Pour créer un lecteur réseau, vous pouvez utiliser l’objet COM **WScript.Network** . La commande suivante mappe le partage `\\FPS01\users` au lecteur local `B:`,

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

Sur Windows, la commande `net use` fonctionne également :

```powershell
net use B: \\FPS01\users
```

Les lecteurs mappés avec **WScript.Network** ou `net use` sont immédiatement disponibles pour PowerShell.
