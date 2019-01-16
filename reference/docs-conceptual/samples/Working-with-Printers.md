---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation d’imprimantes
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401966"
---
# <a name="working-with-printers"></a><span data-ttu-id="d0058-103">Utilisation d’imprimantes</span><span class="sxs-lookup"><span data-stu-id="d0058-103">Working with Printers</span></span>

<span data-ttu-id="d0058-104">Vous pouvez utiliser Windows PowerShell pour gérer des imprimantes à l’aide de WMI et de l’objet COM WScript.Network de WSH.</span><span class="sxs-lookup"><span data-stu-id="d0058-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="d0058-105">Nous allons utiliser une combinaison de ces deux outils pour effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d0058-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="d0058-106">Affichage de la liste des connexions d’imprimante</span><span class="sxs-lookup"><span data-stu-id="d0058-106">Listing Printer Connections</span></span>

<span data-ttu-id="d0058-107">La manière la plus simple de répertorier les imprimantes installées sur un ordinateur consiste à utiliser la classe WMI **Win32_Printer** :</span><span class="sxs-lookup"><span data-stu-id="d0058-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="d0058-108">Vous pouvez également répertorier les imprimantes à l’aide de l’objet COM **WScript.Network** qui est généralement utilisé dans des scripts WSH :</span><span class="sxs-lookup"><span data-stu-id="d0058-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="d0058-109">Cette commande retournant une simple collection de chaînes correspondant à des noms de port et d’imprimante sans étiquettes distinctives, elle n’est pas facile à interpréter.</span><span class="sxs-lookup"><span data-stu-id="d0058-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="d0058-110">Ajout d’une imprimante réseau</span><span class="sxs-lookup"><span data-stu-id="d0058-110">Adding a Network Printer</span></span>

<span data-ttu-id="d0058-111">Pour ajouter une nouvelle imprimante réseau, utilisez l’objet COM **WScript.Network** :</span><span class="sxs-lookup"><span data-stu-id="d0058-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="d0058-112">Définition d’une imprimante par défaut</span><span class="sxs-lookup"><span data-stu-id="d0058-112">Setting a Default Printer</span></span>

<span data-ttu-id="d0058-113">Pour utiliser WMI afin de définir l’imprimante par défaut, recherchez l’imprimante dans la collection **Win32_Printer**, puis appelez la méthode **SetDefaultPrinter** :</span><span class="sxs-lookup"><span data-stu-id="d0058-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="d0058-114">L’objet COM **WScript.Network** est un peu plus simple à utiliser, car il dispose d’une méthode **SetDefaultPrinter** qui accepte uniquement le nom de l’imprimante en tant qu’argument :</span><span class="sxs-lookup"><span data-stu-id="d0058-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="d0058-115">Suppression d’une connexion d’imprimante</span><span class="sxs-lookup"><span data-stu-id="d0058-115">Removing a Printer Connection</span></span>

<span data-ttu-id="d0058-116">Pour supprimer une connexion d’imprimante, utilisez la méthode **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="d0058-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```