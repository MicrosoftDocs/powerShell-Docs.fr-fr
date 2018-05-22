---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: ce68bc57a5da049cf895165420ba7c4e21b3e63b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="system-requirements"></a>Configuration requise

- Installez les dernières mises à jour de Windows avant d’installer WMF 5.0 RTM.
- Vous pouvez installer WMF 5.0 RTM uniquement sur les systèmes d’exploitation suivants :

    | Système d'exploitation       | Éditions         | Conditions préalables        |  Liens de package |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | Tous, sauf IA64 | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) et [.NET Framework 4.5 ou version ultérieure](https://msdn.microsoft.com/library/5a4x27ek.aspx) sont installés| [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Professionnel, Entreprise | | **x64 :**  [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86 :**  [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | Tous | [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) et [.NET Framework 4.5 ou version ultérieure](https://msdn.microsoft.com/library/5a4x27ek.aspx) sont installés | **x64 :**  [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86 :**  [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# <a name="installation-instructions"></a>Instructions d’installation

### <a name="to-install-wmf-50-from-windows-explorer-or-file-explorer"></a>Pour installer WMF 5.0 à partir de l’Explorateur Windows (ou de l’Explorateur de fichiers)

1. Accédez au dossier dans lequel vous avez téléchargé le fichier MSU.

2. Double-cliquez sur le fichier MSU pour l’exécuter.

### <a name="to-install-wmf-50-from-command-prompt"></a>Pour installer WMF 5.0 à partir de l’invite de commandes

1. Après avoir téléchargé le package correspondant à l’architecture de votre ordinateur, ouvrez une fenêtre d’invite de commandes avec des droits d’utilisateur élevés (Exécuter en tant qu’administrateur). Dans les options d’installation Server Core de Windows Server 2012 R2, Windows Server 2012 ou Windows Server 2008 R2 SP1, une invite de commandes s’ouvre avec des droits d’utilisateur avec élévation de privilèges par défaut.

2. Accédez au dossier dans lequel vous avez téléchargé ou copié le package d’installation WMF 5.0.

3. Exécutez l’une des commandes suivantes :
    - Sur les ordinateurs qui exécutent Windows Server 2012 R2 ou Windows 8.1 x64, exécutez **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows Server 2012, exécutez **W2K12-KB3134759-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows Server 2008 R2 SP1 ou Windows 7 SP1 x64, exécutez **Win7AndW2K8R2-KB3134760-x64.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows 8.1 x86, exécutez **Win8.1-KB3134758-x86.msu /quiet**.
    - Sur les ordinateurs qui exécutent Windows 7 SP1 x86, exécutez **Win7-KB3134760-x86.msu /quiet**.

### <a name="additional-installation-notes-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a>Notes d’installation supplémentaires pour Windows Server 2008 R2 SP1 et Windows 7 SP1 :

Vérifiez que les conditions préalables suivantes sont remplies :
- Le Service Pack le plus récent est installé.
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) est installé.
- [.NET Framework 4.5 ou version ultérieure](https://msdn.microsoft.com/library/5a4x27ek.aspx) est installé.

**Dépendance de WMF 4.0**

Les systèmes Windows Server 2008 R2 SP1 et Windows 7 SP1 ont intégré PowerShell 2.0, WinRM et WMI. Les packages WMF 3.0 et WMF 4.0, qui mettent à jour ces composants intégrés, ont été publiés après la sortie de Windows Server 2008 R2 SP1 et Windows 7 SP1. L’installation et la désinstallation des packages WMF 3.0 et WMF 4.0 ont révélé des problèmes dans le chemin de mise à niveau suivant :

- Intégré --> WMF 4.0
- Intégré --> WMF 3.0 --> WMF4.0.

Nous avons résolu tous ces problèmes dans les packages WMF 4.0. Par conséquent, WMF 4.0 est nécessaire pour installer WMF 5.0 sur Windows Server 2008 R2 SP1 et Windows 7 SP1. Voici les problèmes spécifiques que vous pouvez rencontrer si vous n’installez pas WMF 4.0 avant la mise à niveau vers WMF 5.0 :

- Le journal des événements transférés n’est pas disponible et le journal EventCollector n’apparaît pas dans l’Observateur d’événements après la désinstallation de WMF 3.0 ou WMF 5.0 (si WMF 4.0 n’est pas installé) dans Windows 7 SP1 et Windows Server 2008 R2 SP1 ([KB2809215](https://support.microsoft.com/en-us/kb/2809215)).
- La personnalisation de la variable d’environnement *PSModulePath* est réinitialisée à sa valeur par défaut quand vous effectuez la mise à niveau directement de PowerShell 2.0 intégré vers WMF 5.0 ([KB2872035](https://support.microsoft.com/en-us/kb/2872035)) ou de WMF 3.0 vers WMF 5.0. ([KB2872047](https://support.microsoft.com/en-us/kb/2872047)) dans Windows 7 SP1 et Windows Server 2008 R2 SP1.

**Dépendance de WinRM**

Windows PowerShell Desired State Configuration (DSC) dépend de WinRM. WinRM n’est pas activé par défaut sur Windows Server 2008 R2 SP1 et Windows 7 SP1. Pour activer WinRM, dans une session Windows PowerShell avec élévation des privilèges, exécutez **Set-WSManQuickConfig**.

# <a name="uninstallation-instructions"></a>Instructions de désinstallation

### <a name="using-command-prompt"></a>Utilisation de l’invite de commandes

1.  Ouvrez une **invite de commandes.**

2.  Exécutez le [Lanceur autonome Windows Update](https://support.microsoft.com/en-us/kb/934307) comme indiqué ci-dessous :

Sur Windows Server 2012 R2 et Windows 8.1 :
```powershell
wusa /uninstall /kb:3134758
```
Sur Windows Server 2012 :
```powershell
wusa /uninstall /kb:3134759
```
Sur Windows Server 2008 R2 SP1 et Windows 7 SP1 :
```powershell
wusa /uninstall /kb:3134760
```

### <a name="using-control-panel"></a>Utilisation du Panneau de configuration

1.  Ouvrez le **Panneau de configuration.**

2.  Ouvrez **Programmes**, puis **Désinstaller un programme.**

3.  Cliquez sur **Afficher les mises à jour installées.**

4.  Sélectionnez **Windows Management Framework 5.0** dans la liste des mises à jour installées. Cela correspond à *KB3134758*, *KB3134759* ou *KB3134760*. Cliquez sur **Désinstaller.**
