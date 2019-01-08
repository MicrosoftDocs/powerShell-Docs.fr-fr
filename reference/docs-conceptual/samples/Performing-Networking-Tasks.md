---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Exécution de tâches de mise en réseau
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 64c57c95a70bc4cad4b695a59d96673ed18afdf4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402020"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="9e3b8-103">Exécution de tâches de mise en réseau</span><span class="sxs-lookup"><span data-stu-id="9e3b8-103">Performing Networking Tasks</span></span>

<span data-ttu-id="9e3b8-104">TCP/IP étant le protocole réseau le plus utilisé, la plupart des tâches d’administration de protocole réseau de bas niveau impliquent TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="9e3b8-105">Dans cette section, nous utilisons Windows PowerShell et WMI pour effectuer ces tâches.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="9e3b8-106">Affichage de la liste des adresses IP pour un ordinateur</span><span class="sxs-lookup"><span data-stu-id="9e3b8-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="9e3b8-107">Pour obtenir toutes les adresses IP utilisées sur l’ordinateur local, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="9e3b8-108">La sortie de cette commande diffère de la plupart des listes de propriétés, car les valeurs sont entourées d’accolades :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="9e3b8-109">Pour comprendre pourquoi des accolades s’affichent, utilisez l’applet de commande Get-Member pour examiner la propriété **IPAddress** :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="9e3b8-110">La propriété IPAddress pour chaque carte réseau est en réalité un tableau.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="9e3b8-111">Les accolades dans la définition indiquent qu’**IPAddress** n’est pas une valeur **System.String**, mais un tableau de valeurs **System.String**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="9e3b8-112">Affichage de la liste des données de configuration IP</span><span class="sxs-lookup"><span data-stu-id="9e3b8-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="9e3b8-113">Pour afficher les données de configuration IP détaillées de chaque carte réseau, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="9e3b8-114">L’affichage par défaut pour l’objet Configuration de la carte réseau est un jeu très réduit des informations disponibles.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="9e3b8-115">Pour une inspection et un dépannage approfondis, utilisez l’applet de commande Select-Object ou une applet de commande de mise en forme, telle que Format-List, pour spécifier les propriétés à afficher.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="9e3b8-116">Si les propriétés IPX ou WINS ne vous intéressent pas (ce qui est probablement le cas dans un réseau TCP/IP moderne), vous pouvez utiliser le paramètre ExcludeProperty de l’applet de commande Select-Object pour masquer les propriétés dont les noms commencent par « WINS » ou « IPX ».</span><span class="sxs-lookup"><span data-stu-id="9e3b8-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="9e3b8-117">Cette commande retourne des informations détaillées sur DHCP, DNS, le routage et d’autres propriétés de configuration IP secondaires.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="9e3b8-118">Test ping des ordinateurs</span><span class="sxs-lookup"><span data-stu-id="9e3b8-118">Pinging Computers</span></span>

<span data-ttu-id="9e3b8-119">Vous pouvez effectuer un simple test ping sur un ordinateur à l’aide de la méthode **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="9e3b8-120">La commande suivante exécute le test ping, mais retourne un résultat assez long :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="9e3b8-121">Une forme plus utile pour les informations résumées est l’affichage des propriétés Address, ResponseTime et StatusCode, généré par la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="9e3b8-122">Le paramètre Autosize de l’applet de commande Format-Table redimensionne les colonnes de la table afin qu’elles s’affichent correctement dans Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="9e3b8-123">Un StatusCode de 0 indique un test ping réussi.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="9e3b8-124">Vous pouvez utiliser un tableau pour effectuer un test ping de plusieurs ordinateurs avec une seule commande.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="9e3b8-125">Étant donné qu’il y a plusieurs adresses, utilisez la méthode **ForEach-Object** pour effectuer un test ping de chaque adresse séparément :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="9e3b8-126">Vous pouvez utiliser le même format de commande pour effectuer un test ping de tous les ordinateurs d’un sous-réseau, tel qu’un réseau privé utilisant le numéro de réseau 192.168.1.0 et un masque de sous-réseau de classe C standard (255.255.255.0). Seules les adresses dans la plage de 192.168.1.1 à 192.168.1.254 sont des adresses locales légitimes (0 est toujours réservé au numéro de réseau et 255 est une adresse de diffusion de sous-réseau).</span><span class="sxs-lookup"><span data-stu-id="9e3b8-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="9e3b8-127">Pour représenter un tableau des nombres 1 à 254 dans Windows PowerShell, utilisez l’instruction **1..254**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="9e3b8-128">Vous pouvez effectuer un test ping d’un sous-réseau complet en générant le tableau, puis en ajoutant les valeurs sur une adresse partielle dans l’instruction ping :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="9e3b8-129">Notez que cette technique pour la génération d’une plage d’adresses est également utilisable ailleurs.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="9e3b8-130">Vous pouvez générer un jeu complet d’adresses comme suit :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="9e3b8-131">Récupération des propriétés d’une carte réseau</span><span class="sxs-lookup"><span data-stu-id="9e3b8-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="9e3b8-132">Plus haut dans ce guide, nous avons signalé que vous pouviez extraire des propriétés de configuration générale à l’aide de la méthode **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="9e3b8-133">Bien qu’il ne s’agisse pas strictement d’informations TCP/IP, les informations de carte réseau telles que les adresses MAC et les types de cartes peuvent être utiles pour comprendre ce qui se passe sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="9e3b8-134">Pour obtenir un résumé de ces informations, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="9e3b8-135">Attribution de domaine DNS pour une carte réseau</span><span class="sxs-lookup"><span data-stu-id="9e3b8-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="9e3b8-136">Pour attribuer le domaine DNS pour une résolution de noms automatique, utilisez la méthode **Win32_NetworkAdapterConfiguration SetDNSDomain**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="9e3b8-137">Étant donné que vous attribuez le domaine DNS indépendamment pour chaque configuration de carte réseau, vous devez utiliser une instruction **ForEach-Object** pour attribuer le domaine à chaque carte :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="9e3b8-138">L’instruction de filtrage « IPEnabled=$true » est nécessaire car, même sur un réseau utilisant uniquement TCP/IP, certaines configurations de carte réseau sur un ordinateur ne sont pas de véritables cartes TCP/IP, mais des éléments logiciels généraux prenant en charge RAS, PPTP, QoS et d’autres services pour toutes les cartes, et n’ayant donc pas d’adresse propre.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="9e3b8-139">Vous pouvez filtrer la commande à l’aide de l’applet de commande **Where-Object**, au lieu d’utiliser le filtre **Get-WmiObject**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="9e3b8-140">Exécution de tâches de configuration DHCP</span><span class="sxs-lookup"><span data-stu-id="9e3b8-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="9e3b8-141">La modification des détails DHCP implique l’utilisation d’un ensemble de cartes réseau, tout comme la configuration DNS.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="9e3b8-142">Vous pouvez effectuer diverses actions à l’aide de WMI. Nous allons en décrire quelques-unes parmi les plus courantes.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="9e3b8-143">Détermination des cartes avec DHCP activé</span><span class="sxs-lookup"><span data-stu-id="9e3b8-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="9e3b8-144">Pour rechercher les cartes avec DHCP activé sur un ordinateur, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="9e3b8-145">Pour exclure les cartes présentant des problèmes de configuration IP, vous pouvez récupérer uniquement les cartes avec IP activé :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="9e3b8-146">Récupération des propriétés DHCP</span><span class="sxs-lookup"><span data-stu-id="9e3b8-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="9e3b8-147">Étant donné que les propriétés DHCP d’une carte commencent généralement par « DHCP », vous pouvez utiliser le paramètre Property de l’applet de commande Format-Table pour afficher uniquement ces propriétés :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="9e3b8-148">Activation du protocole DHCP sur chaque carte</span><span class="sxs-lookup"><span data-stu-id="9e3b8-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="9e3b8-149">Pour activer le protocole DHCP sur toutes les cartes, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="9e3b8-150">Vous pouvez utiliser l’instruction **Filter** « IPEnabled=$true et DHCPEnabled=$false » pour éviter d’activer le protocole DHCP là où il est déjà activé, mais l’omission de cette étape ne génère pas d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="9e3b8-151">Résiliation et renouvellement de baux DHCP sur des cartes spécifiques</span><span class="sxs-lookup"><span data-stu-id="9e3b8-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="9e3b8-152">La classe **Win32_NetworkAdapterConfiguration** dispose des méthodes **ReleaseDHCPLease** et **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="9e3b8-153">Toutes deux sont utilisées de la même façon.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-153">Both are used in the same way.</span></span> <span data-ttu-id="9e3b8-154">En règle générale, utilisez ces méthodes si vous devez uniquement résilier ou renouveler des adresses pour une carte sur un sous-réseau spécifique.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="9e3b8-155">La manière la plus simple de filtrer des cartes sur un sous-réseau consiste à choisir uniquement les configurations de carte qui utilisent la passerelle pour ce sous-réseau.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="9e3b8-156">Par exemple, la commande suivante libère tous les baux DHCP sur les cartes de l’ordinateur local qui obtiennent des baux DHCP à partir de 192.168.1.254 :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="9e3b8-157">Le seul changement pour le renouvellement d’un bail DHCP consiste à utiliser la méthode **RenewDHCPLease** plutôt que la méthode **ReleaseDHCPLease** :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="9e3b8-158">Lorsque vous utilisez ces méthodes sur un ordinateur distant, n’oubliez pas que vous risquez de perdre l’accès au système distant si vous êtes connecté à celui-ci via la carte dont le bail a été résilié ou renouvelé.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="9e3b8-159">Résiliation et renouvellement de baux DHCP sur toutes les cartes</span><span class="sxs-lookup"><span data-stu-id="9e3b8-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="9e3b8-160">Vous pouvez effectuer des résiliations ou renouvellements d’adresse DHCP sur toutes les cartes en utilisant les méthodes **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** et **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="9e3b8-161">Toutefois, la commande doit s’appliquer à la classe WMI, plutôt qu’à une carte particulière, car la résiliation et le renouvellement de baux de façon globale sont effectuées sur la classe, et non sur une carte spécifique.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="9e3b8-162">Vous pouvez obtenir une référence à une classe WMI plutôt qu’à des instances de classe, en répertoriant toutes les classes WMI, puis en sélectionnant uniquement la classe souhaitée par son nom.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="9e3b8-163">Par exemple, la commande suivante retourne la classe Win32_NetworkAdapterConfiguration :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="9e3b8-164">Vous pouvez traiter la commande entière comme la classe, puis appeler dessus la méthode **ReleaseDHCPAdapterLease**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="9e3b8-165">Dans la commande suivante, les parenthèses entourant les éléments de pipeline **Get-WmiObject** et **Where-Object** indiquent à Windows PowerShell de les évaluer en priorité :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="9e3b8-166">Vous pouvez utiliser le même format de commande pour appeler la méthode **RenewDHCPLeaseAll**:</span><span class="sxs-lookup"><span data-stu-id="9e3b8-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="9e3b8-167">Création d’un partage réseau</span><span class="sxs-lookup"><span data-stu-id="9e3b8-167">Creating a Network Share</span></span>

<span data-ttu-id="9e3b8-168">Pour créer un partage réseau, utilisez la méthode **Win32_Share créer**:</span><span class="sxs-lookup"><span data-stu-id="9e3b8-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="9e3b8-169">Vous pouvez également créer le partage en utilisant la commande **net share** dans Windows PowerShell :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="9e3b8-170">Suppression d’un partage réseau</span><span class="sxs-lookup"><span data-stu-id="9e3b8-170">Removing a Network Share</span></span>

<span data-ttu-id="9e3b8-171">Vous pouvez supprimer un partage réseau avec la commande **Win32_Share**, mais le processus diffère légèrement de la création d’un partage, car vous devez récupérer le partage spécifique à supprimer, plutôt que la classe **Win32_Share**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="9e3b8-172">L’instruction suivante supprime le partage « TempShare » :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="9e3b8-173">La commande **net share** fonctionne également :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="9e3b8-174">Connexion d’un lecteur réseau accessible à Windows</span><span class="sxs-lookup"><span data-stu-id="9e3b8-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="9e3b8-175">L’applet de commande **New-PSDrive** crée un lecteur Windows PowerShell, mais les lecteurs créés de cette façon sont disponibles uniquement pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="9e3b8-176">Pour créer un lecteur réseau, vous pouvez utiliser l’objet COM **WScript.Network**.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="9e3b8-177">La commande suivante mappe le partage \\\\FPS01\\users au lecteur local B:</span><span class="sxs-lookup"><span data-stu-id="9e3b8-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="9e3b8-178">La commande **net use** fonctionne également :</span><span class="sxs-lookup"><span data-stu-id="9e3b8-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="9e3b8-179">Les lecteurs mappés avec **WScript.Network** ou net use sont immédiatement disponibles pour Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e3b8-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>