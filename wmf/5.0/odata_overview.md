---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057806"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="cb0cb-102">Générer des applets de commande PowerShell basées sur un point de terminaison OData</span><span class="sxs-lookup"><span data-stu-id="cb0cb-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="cb0cb-103">Générer des applets de commande Windows PowerShell basées sur un point de terminaison OData</span><span class="sxs-lookup"><span data-stu-id="cb0cb-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="cb0cb-104">**Export-ODataEndpointProxy** est une applet de commande qui génère un ensemble d’applets de commande Windows PowerShell basé sur les fonctionnalités exposées par un point de terminaison OData donné.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="cb0cb-105">L’exemple suivant montre comment utiliser cette nouvelle applet de commande :</span><span class="sxs-lookup"><span data-stu-id="cb0cb-105">The following example shows how to use this new cmdlet:</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="cb0cb-106">Certaines parties des principaux cas d’usage de cette fonctionnalité sont toujours en développement, y compris :</span><span class="sxs-lookup"><span data-stu-id="cb0cb-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="cb0cb-107">Associations</span><span class="sxs-lookup"><span data-stu-id="cb0cb-107">Associations</span></span>
-   <span data-ttu-id="cb0cb-108">Transfert de flux</span><span class="sxs-lookup"><span data-stu-id="cb0cb-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="cb0cb-109">Générer des applets de commande Windows PowerShell basées sur un point de terminaison OData avec ODataUtils</span><span class="sxs-lookup"><span data-stu-id="cb0cb-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="cb0cb-110">Le module ODataUtils permet de générer des applets de commande Windows PowerShell à partir de points de terminaison REST qui prennent en charge OData.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="cb0cb-111">Le module Windows PowerShell Microsoft.PowerShell.ODataUtils offre les améliorations incrémentielles suivantes.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="cb0cb-112">Informations supplémentaires sur les canaux du point de terminaison côté serveur vers le côté client.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="cb0cb-113">Prise en charge de la pagination côté client</span><span class="sxs-lookup"><span data-stu-id="cb0cb-113">Client-side paging support</span></span>
-   <span data-ttu-id="cb0cb-114">Filtrage côté serveur à l’aide du paramètre -Select</span><span class="sxs-lookup"><span data-stu-id="cb0cb-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="cb0cb-115">Prise en charge des en-têtes de demande web</span><span class="sxs-lookup"><span data-stu-id="cb0cb-115">Support for web request headers</span></span>

<span data-ttu-id="cb0cb-116">Les applets de commande du proxy générées par l’applet de commande Export-ODataEndPointProxy fournissent des informations supplémentaires (non mentionnées dans les métadonnées utilisées lors de la génération du proxy côté client) à partir du point de terminaison OData côté serveur sur le flux d’informations (une nouvelle fonctionnalité de Windows PowerShell 5.0).</span><span class="sxs-lookup"><span data-stu-id="cb0cb-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="cb0cb-117">Voici un exemple qui montre comment obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-117">Here is an example of how to get that information.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="cb0cb-118">Vous pouvez obtenir les enregistrements à partir du côté serveur par lots grâce à la prise en charge de la pagination côté client.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="cb0cb-119">C’est utile quand vous devez obtenir une grande quantité de données à partir du serveur par le biais du réseau.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="cb0cb-120">Les applets de commande du proxy générées prennent en charge le paramètre –Select, que vous pouvez utiliser comme filtre pour recevoir uniquement les propriétés d’enregistrements dont le client a besoin.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="cb0cb-121">Cela réduit la quantité de données transférées sur le réseau, car le filtrage s’effectue sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="cb0cb-122">L’applet de commande Export-ODataEndpointProxy et les applets de commande du proxy qu’elle génère prennent désormais en charge le paramètre Headers (fournissez des valeurs sous forme de table de hachage), que vous pouvez utiliser pour transmettre toute information supplémentaire attendue par le point de terminaison OData côté serveur.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="cb0cb-123">Dans l’exemple suivant, vous pouvez transmettre une clé d’abonnement par le biais de Headers pour les services qui attendent une clé d’abonnement pour l’authentification.</span><span class="sxs-lookup"><span data-stu-id="cb0cb-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
