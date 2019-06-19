---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Utilisation d’imprimantes
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030682"
---
# <a name="working-with-printers"></a>Utilisation d’imprimantes

Vous pouvez utiliser Windows PowerShell pour gérer des imprimantes à l’aide de WMI et de l’objet COM WScript.Network de WSH. Nous allons utiliser une combinaison de ces deux outils pour effectuer des tâches spécifiques.

## <a name="listing-printer-connections"></a>Affichage de la liste des connexions d’imprimante

La manière la plus simple de répertorier les imprimantes installées sur un ordinateur consiste à utiliser la classe WMI **Win32_Printer** :

```powershell
Get-WmiObject -Class Win32_Printer
```

Vous pouvez également répertorier les imprimantes à l’aide de l’objet COM **WScript.Network** qui est généralement utilisé dans des scripts WSH :

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Cette commande retournant une simple collection de chaînes correspondant à des noms de port et d’imprimante sans étiquettes distinctives, elle n’est pas facile à interpréter.

## <a name="adding-a-network-printer"></a>Ajout d’une imprimante réseau

Pour ajouter une nouvelle imprimante réseau, utilisez l’objet COM **WScript.Network** :

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Définition d’une imprimante par défaut

Pour utiliser WMI afin de définir l’imprimante par défaut, recherchez l’imprimante dans la collection **Win32_Printer**, puis appelez la méthode **SetDefaultPrinter** :

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

L’objet COM **WScript.Network** est un peu plus simple à utiliser, car il dispose d’une méthode **SetDefaultPrinter** qui accepte uniquement le nom de l’imprimante en tant qu’argument :

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Suppression d’une connexion d’imprimante

Pour supprimer une connexion d’imprimante, utilisez la méthode **WScript.Network RemovePrinterConnection**:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
