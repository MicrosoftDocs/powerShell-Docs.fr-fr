---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 80852bf750700d549de24e150ffd89ac55b7bf88
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2017
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="33d19-102">Gestion du commutateur réseau avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="33d19-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="33d19-103">L’applet de commande **Get-NetworkSwitchEthernetPort** retourne les informations supplémentaires suivantes avec les instances :</span><span class="sxs-lookup"><span data-stu-id="33d19-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="33d19-104">IPAddress : adresse IP associée au port</span><span class="sxs-lookup"><span data-stu-id="33d19-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="33d19-105">PortMode : mode du port (accès, itinéraire ou trunk)</span><span class="sxs-lookup"><span data-stu-id="33d19-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="33d19-106">AccessVLAN : ID du réseau local virtuel associé à ce port en mode accès</span><span class="sxs-lookup"><span data-stu-id="33d19-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="33d19-107">TrunkedVLANList : liste des ID des réseaux locaux virtuels associés à ce port en mode trunk</span><span class="sxs-lookup"><span data-stu-id="33d19-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="33d19-108">Gestion fondamentale du commutateur réseau avec Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="33d19-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="33d19-109">Les applets de commande du commutateur réseau, introduites dans WMF 5.0, permettent d’appliquer une configuration de port de commutateur réseau local virtuel (VLAN) et de commutateur réseau de base de couche 2 à des commutateurs réseau certifiés par logo Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="33d19-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="33d19-110">Microsoft s’engage à prendre en charge la vision DAL ([Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) Layer) et à démontrer la valeur à nos clients et partenaires dans cet espace.</span><span class="sxs-lookup"><span data-stu-id="33d19-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/en-us/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="33d19-111">Ces applets de commande vous permettent d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="33d19-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="33d19-112">Configuration globale du commutateur, par exemple :</span><span class="sxs-lookup"><span data-stu-id="33d19-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="33d19-113">Définir le nom d’hôte</span><span class="sxs-lookup"><span data-stu-id="33d19-113">Set host name</span></span>
    - <span data-ttu-id="33d19-114">Définir la bannière de commutateur</span><span class="sxs-lookup"><span data-stu-id="33d19-114">Set switch banner</span></span>
    - <span data-ttu-id="33d19-115">Conserver la configuration</span><span class="sxs-lookup"><span data-stu-id="33d19-115">Persist configuration</span></span>
    - <span data-ttu-id="33d19-116">Activer ou désactiver une fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="33d19-116">Enable or disable feature</span></span>

- <span data-ttu-id="33d19-117">Configuration de réseau local virtuel :</span><span class="sxs-lookup"><span data-stu-id="33d19-117">VLAN configuration:</span></span>
    - <span data-ttu-id="33d19-118">Créer ou supprimer un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="33d19-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="33d19-119">Activer ou désactiver un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="33d19-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="33d19-120">Énumérer les réseaux locaux virtuels</span><span class="sxs-lookup"><span data-stu-id="33d19-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="33d19-121">Définir le nom convivial d’un réseau local virtuel</span><span class="sxs-lookup"><span data-stu-id="33d19-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="33d19-122">Configuration de port de couche 2 :</span><span class="sxs-lookup"><span data-stu-id="33d19-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="33d19-123">Énumérer les ports</span><span class="sxs-lookup"><span data-stu-id="33d19-123">Enumerate ports</span></span>
    - <span data-ttu-id="33d19-124">Activer ou désactiver des ports</span><span class="sxs-lookup"><span data-stu-id="33d19-124">Enable or disable ports</span></span>
    - <span data-ttu-id="33d19-125">Définir les propriétés et les modes des ports</span><span class="sxs-lookup"><span data-stu-id="33d19-125">Set port modes and properties</span></span>
    - <span data-ttu-id="33d19-126">Ajouter ou associer un réseau local virtuel à Trunk ou Accès sur le port</span><span class="sxs-lookup"><span data-stu-id="33d19-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="33d19-127">Commencez à explorer en recherchant toutes les applets de commande NetworkSwitch !</span><span class="sxs-lookup"><span data-stu-id="33d19-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="33d19-128">Vous trouverez des informations supplémentaires dans le billet de blog de Jeffrey Snover sur WMF 5.0 Preview : <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="33d19-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

