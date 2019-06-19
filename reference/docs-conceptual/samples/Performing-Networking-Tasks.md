---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Exécution de tâches de mise en réseau
ms.openlocfilehash: e581296b4b7609b374f206c447c4f797e3e2c400
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030858"
---
# <a name="performing-networking-tasks"></a>Exécution de tâches de mise en réseau

TCP/IP étant le protocole réseau le plus utilisé, la plupart des tâches d’administration de protocole réseau de bas niveau impliquent TCP/IP. Dans cette section, nous utilisons Windows PowerShell et WMI pour effectuer ces tâches.

## <a name="listing-ip-addresses-for-a-computer"></a>Affichage de la liste des adresses IP pour un ordinateur

Pour obtenir toutes les adresses IP utilisées sur l’ordinateur local, entrez la commande suivante :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

La sortie de cette commande diffère de la plupart des listes de propriétés, car les valeurs sont entourées d’accolades :

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

Pour comprendre pourquoi des accolades s’affichent, utilisez l’applet de commande Get-Member pour examiner la propriété **IPAddress** :

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

La propriété IPAddress pour chaque carte réseau est en réalité un tableau. Les accolades dans la définition indiquent qu’**IPAddress** n’est pas une valeur **System.String**, mais un tableau de valeurs **System.String**.

## <a name="listing-ip-configuration-data"></a>Affichage de la liste des données de configuration IP

Pour afficher les données de configuration IP détaillées de chaque carte réseau, utilisez la commande suivante :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

L’affichage par défaut pour l’objet Configuration de la carte réseau est un jeu très réduit des informations disponibles. Pour une inspection et un dépannage approfondis, utilisez l’applet de commande Select-Object ou une applet de commande de mise en forme, telle que Format-List, pour spécifier les propriétés à afficher.

Si les propriétés IPX ou WINS ne vous intéressent pas (ce qui est probablement le cas dans un réseau TCP/IP moderne), vous pouvez utiliser le paramètre ExcludeProperty de l’applet de commande Select-Object pour masquer les propriétés dont les noms commencent par « WINS » ou « IPX ».

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Cette commande retourne des informations détaillées sur DHCP, DNS, le routage et d’autres propriétés de configuration IP secondaires.

## <a name="pinging-computers"></a>Test ping des ordinateurs

Vous pouvez effectuer un simple test ping sur un ordinateur à l’aide de la méthode **Win32_PingStatus**. La commande suivante exécute le test ping, mais retourne un résultat assez long :

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Une forme plus utile pour les informations résumées est l’affichage des propriétés Address, ResponseTime et StatusCode, généré par la commande suivante. Le paramètre Autosize de l’applet de commande Format-Table redimensionne les colonnes de la table afin qu’elles s’affichent correctement dans Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Un StatusCode de 0 indique un test ping réussi.

Vous pouvez utiliser un tableau pour effectuer un test ping de plusieurs ordinateurs avec une seule commande. Étant donné qu’il y a plusieurs adresses, utilisez la méthode **ForEach-Object** pour effectuer un test ping de chaque adresse séparément :

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Vous pouvez utiliser le même format de commande pour effectuer un test ping de tous les ordinateurs d’un sous-réseau, tel qu’un réseau privé utilisant le numéro de réseau 192.168.1.0 et un masque de sous-réseau de classe C standard (255.255.255.0). Seules les adresses dans la plage de 192.168.1.1 à 192.168.1.254 sont des adresses locales légitimes (0 est toujours réservé au numéro de réseau et 255 est une adresse de diffusion de sous-réseau).

Pour représenter un tableau des nombres 1 à 254 dans Windows PowerShell, utilisez l’instruction **1..254**. Vous pouvez effectuer un test ping d’un sous-réseau complet en générant le tableau, puis en ajoutant les valeurs sur une adresse partielle dans l’instruction ping :

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Notez que cette technique pour la génération d’une plage d’adresses est également utilisable ailleurs. Vous pouvez générer un jeu complet d’adresses comme suit :

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Récupération des propriétés d’une carte réseau

Plus haut dans ce guide, nous avons signalé que vous pouviez extraire des propriétés de configuration générale à l’aide de la méthode **Win32_NetworkAdapterConfiguration**. Bien qu’il ne s’agisse pas strictement d’informations TCP/IP, les informations de carte réseau telles que les adresses MAC et les types de cartes peuvent être utiles pour comprendre ce qui se passe sur un ordinateur. Pour obtenir un résumé de ces informations, utilisez la commande suivante :

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Attribution de domaine DNS pour une carte réseau

Pour attribuer le domaine DNS pour une résolution de noms automatique, utilisez la méthode **Win32_NetworkAdapterConfiguration SetDNSDomain**. Étant donné que vous attribuez le domaine DNS indépendamment pour chaque configuration de carte réseau, vous devez utiliser une instruction **ForEach-Object** pour attribuer le domaine à chaque carte :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

L’instruction de filtrage « IPEnabled=$true » est nécessaire car, même sur un réseau utilisant uniquement TCP/IP, certaines configurations de carte réseau sur un ordinateur ne sont pas de véritables cartes TCP/IP, mais des éléments logiciels généraux prenant en charge RAS, PPTP, QoS et d’autres services pour toutes les cartes, et n’ayant donc pas d’adresse propre.

Vous pouvez filtrer la commande à l’aide de l’applet de commande **Where-Object**, au lieu d’utiliser le filtre **Get-WmiObject**.

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Exécution de tâches de configuration DHCP

La modification des détails DHCP implique l’utilisation d’un ensemble de cartes réseau, tout comme la configuration DNS. Vous pouvez effectuer diverses actions à l’aide de WMI. Nous allons en décrire quelques-unes parmi les plus courantes.

### <a name="determining-dhcp-enabled-adapters"></a>Détermination des cartes avec DHCP activé

Pour rechercher les cartes avec DHCP activé sur un ordinateur, utilisez la commande suivante :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

Pour exclure les cartes présentant des problèmes de configuration IP, vous pouvez récupérer uniquement les cartes avec IP activé :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a>Récupération des propriétés DHCP

Étant donné que les propriétés DHCP d’une carte commencent généralement par « DHCP », vous pouvez utiliser le paramètre Property de l’applet de commande Format-Table pour afficher uniquement ces propriétés :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Activation du protocole DHCP sur chaque carte

Pour activer le protocole DHCP sur toutes les cartes, utilisez la commande suivante :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Vous pouvez utiliser l’instruction **Filter** « IPEnabled=$true et DHCPEnabled=$false » pour éviter d’activer le protocole DHCP là où il est déjà activé, mais l’omission de cette étape ne génère pas d’erreurs.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Résiliation et renouvellement de baux DHCP sur des cartes spécifiques

La classe **Win32_NetworkAdapterConfiguration** dispose des méthodes **ReleaseDHCPLease** et **RenewDHCPLease**. Toutes deux sont utilisées de la même façon. En règle générale, utilisez ces méthodes si vous devez uniquement résilier ou renouveler des adresses pour une carte sur un sous-réseau spécifique. La manière la plus simple de filtrer des cartes sur un sous-réseau consiste à choisir uniquement les configurations de carte qui utilisent la passerelle pour ce sous-réseau. Par exemple, la commande suivante libère tous les baux DHCP sur les cartes de l’ordinateur local qui obtiennent des baux DHCP à partir de 192.168.1.254 :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

Le seul changement pour le renouvellement d’un bail DHCP consiste à utiliser la méthode **RenewDHCPLease** plutôt que la méthode **ReleaseDHCPLease** :

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Lorsque vous utilisez ces méthodes sur un ordinateur distant, n’oubliez pas que vous risquez de perdre l’accès au système distant si vous êtes connecté à celui-ci via la carte dont le bail a été résilié ou renouvelé.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Résiliation et renouvellement de baux DHCP sur toutes les cartes

Vous pouvez effectuer des résiliations ou renouvellements d’adresse DHCP sur toutes les cartes en utilisant les méthodes **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** et **RenewDHCPLeaseAll**. Toutefois, la commande doit s’appliquer à la classe WMI, plutôt qu’à une carte particulière, car la résiliation et le renouvellement de baux de façon globale sont effectuées sur la classe, et non sur une carte spécifique.

Vous pouvez obtenir une référence à une classe WMI plutôt qu’à des instances de classe, en répertoriant toutes les classes WMI, puis en sélectionnant uniquement la classe souhaitée par son nom. Par exemple, la commande suivante retourne la classe Win32_NetworkAdapterConfiguration :

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Vous pouvez traiter la commande entière comme la classe, puis appeler dessus la méthode **ReleaseDHCPAdapterLease**. Dans la commande suivante, les parenthèses entourant les éléments de pipeline **Get-WmiObject** et **Where-Object** indiquent à Windows PowerShell de les évaluer en priorité :

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

Vous pouvez utiliser le même format de commande pour appeler la méthode **RenewDHCPLeaseAll**:

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Création d’un partage réseau

Pour créer un partage réseau, utilisez la méthode **Win32_Share créer**:

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

Vous pouvez également créer le partage en utilisant la commande **net share** dans Windows PowerShell :

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Suppression d’un partage réseau

Vous pouvez supprimer un partage réseau avec la commande **Win32_Share**, mais le processus diffère légèrement de la création d’un partage, car vous devez récupérer le partage spécifique à supprimer, plutôt que la classe **Win32_Share**. L’instruction suivante supprime le partage « TempShare » :

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

La commande **net share** fonctionne également :

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Connexion d’un lecteur réseau accessible à Windows

L’applet de commande **New-PSDrive** crée un lecteur Windows PowerShell, mais les lecteurs créés de cette façon sont disponibles uniquement pour Windows PowerShell. Pour créer un lecteur réseau, vous pouvez utiliser l’objet COM **WScript.Network**. La commande suivante mappe le partage \\\\FPS01\\users au lecteur local B:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

La commande **net use** fonctionne également :

```powershell
net use B: \\FPS01\users
```

Les lecteurs mappés avec **WScript.Network** ou net use sont immédiatement disponibles pour Windows PowerShell.
