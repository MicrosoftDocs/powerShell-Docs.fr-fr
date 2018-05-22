---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 3679c13c2d28f28f3102b24f6369f1dc264d6884
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="installation-instructions"></a>Instructions d’installation

Téléchargez le package correspondant à votre système d’exploitation et à votre architecture :

| Système d'exploitation       | Architecture | Nom du package              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


**Pour installer WMF 5.0 à partir de l’Explorateur Windows (ou de l’Explorateur de fichiers dans Windows Server 2012 R2 et Windows 8.1) :**

1. Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.

2. Double-cliquez sur le fichier MSU pour l’exécuter.

**Pour installer WMF 5.0 à partir de l’invite de commandes :**

1. Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur). Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.

2. Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.0.

3. Exécutez l’une des commandes suivantes :
    - Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows Server 2012, exécutez **W2K12-KB3134759-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, exécutez **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez **Win8.1-KB3134758-x86.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows 7 SP1 x86, exécutez **Win7-KB3134760-x86.msu /quiet**.

**Notes d’installation supplémentaires pour Windows Server 2008 SP1 et Windows 7 SP1 :**

Vérifiez que les conditions préalables suivantes sont remplies :
- Le Service Pack le plus récent est installé.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) est installé.

*Dépendance de WinRM :* La Configuration de l’état souhaité (DSC) Windows PowerShell dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 et Windows 7. Pour activer WinRM, dans une session Windows PowerShell avec élévation des privilèges, exécutez **Set-WSManQuickConfig**.
