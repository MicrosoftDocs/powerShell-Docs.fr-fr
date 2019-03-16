---
title: Création d’un fournisseur de lecteur PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055647"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Création d’un fournisseur de lecteur Windows PowerShell

Cette rubrique décrit comment créer un fournisseur de lecteur Windows PowerShell qui fournit un moyen pour accéder à un magasin de données via un lecteur Windows PowerShell. Ce type de fournisseur est également appelé fournisseurs du lecteur Windows PowerShell. Les lecteurs Windows PowerShell utilisées par le fournisseur fournissent les moyens de se connecter au magasin de données.

Le fournisseur du lecteur Windows PowerShell décrit ici fournit l’accès à une base de données Microsoft Access. Pour ce fournisseur, le lecteur Windows PowerShell représente la base de données (il est possible d’ajouter n’importe quel nombre de lecteurs à un fournisseur de lecteur), les conteneurs de niveau supérieur du lecteur représentent les tables dans la base de données et les éléments des conteneurs représentent les lignes dans les tables.

Voici une liste des sections dans cette rubrique. Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur de lecteur Windows PowerShell, lisez ces sections dans l’ordre où ils apparaissent. Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur de lecteur, accédez directement aux informations dont vous avez besoin.

- [Définition de la classe de fournisseur PowerShell Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Définition des fonctionnalités de Base](#Defining-Base-Functionality)

- [Création d’informations sur l’état du lecteur](#Creating-Drive-State-Information)

- [Création d’un lecteur](#Creating-a-Drive)

- [Attachement des paramètres dynamiques à NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Retrait d’un lecteur](#Removing-a-Drive)

- [L’initialisation par défaut de lecteurs](#Initializing-Default-Drives)

- [Exemple de code](#Code-Sample)

- [Test du fournisseur de lecteur PowerShell Windows](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Définition de la classe de fournisseur PowerShell Windows

Votre fournisseur du lecteur doit définir une classe .NET qui dérive de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base. Voici la définition de classe pour ce fournisseur de lecteur :

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Notez que dans cet exemple, le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut spécifie un nom convivial pour le fournisseur et les capacités spécifiques de Windows PowerShell qui le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Les valeurs possibles pour les fonctionnalités de fournisseur sont définies par le [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Ce fournisseur de lecteur ne prennent pas en charge ces fonctionnalités.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de Base

Comme décrit dans [fournisseur Design Your Windows PowerShell](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe dérive de la [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe de base qui définit les méthodes nécessaires pour initialiser et désinitialiser le fournisseur. Pour implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité est fournie par Windows PowerShell.

## <a name="creating-drive-state-information"></a>Création d’informations sur l’état du lecteur

Tous les fournisseurs Windows PowerShell sont considérées comme sans état, ce qui signifie que votre fournisseur du lecteur doit créer les informations d’état requises par le runtime Windows PowerShell quand il appelle votre fournisseur.

Pour ce fournisseur du lecteur, les informations d’état incluent la connexion à la base de données est conservée en tant que partie des informations sur le lecteur. Voici le code qui montre comment ces informations sont stockées dans le [à savoir System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objet qui décrit le lecteur :

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Création d’un lecteur

Pour permettre au runtime de Windows PowerShell créer un lecteur, le fournisseur du lecteur doit implémenter le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) (méthode). Le code suivant montre l’implémentation de la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) méthode pour ce fournisseur de lecteur :

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

La substitution de cette méthode doit effectuer les opérations suivantes :

- Vérifiez que le [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membre existe et qu’une connexion au magasin de données peut être établie.

- Créer un lecteur et de remplir le membre de la connexion, à l’appui de la `New-PSDrive` applet de commande.

- Valider la [à savoir System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objet pour le lecteur proposé.

- Modifier le [à savoir System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur avec des performances requises ou des informations de la fiabilité de l’objet, ou fournir des données supplémentaires pour les appelants à l’aide du lecteur.

- Gérer les défaillances à l’aide de la [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) (méthode) et les renvoyer ensuite `null`.

  Cette méthode retourne des informations de lecteur qui a été passées à la méthode ou une version spécifique au fournisseur.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Attachement des paramètres dynamiques à NewDrive

Le `New-PSDrive` applet de commande pris en charge par votre fournisseur de lecteur peut-être nécessiter des paramètres supplémentaires. Pour attacher ces paramètres dynamiques à l’applet de commande, le fournisseur implémente la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (méthode). Cette méthode retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet.

Ce fournisseur de lecteur ne remplace pas cette méthode. Toutefois, le code suivant montre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Retrait d’un lecteur

Pour fermer la connexion de base de données, le fournisseur du lecteur doit implémenter le [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (méthode). Cette méthode ferme la connexion sur le disque après le nettoyage de toutes les informations spécifiques au fournisseur.

Le code suivant montre l’implémentation de la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) méthode pour ce fournisseur de lecteur :

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Si le lecteur peut être supprimé, la méthode doit retourner les informations passées à la méthode via la `drive` paramètre. Si le lecteur ne peut pas être supprimé, la méthode doit écrire une exception, puis renvoyer `null`. Si votre fournisseur ne remplace pas cette méthode, l’implémentation par défaut de cette méthode retourne uniquement les informations de lecteur passées en tant qu’entrée.

## <a name="initializing-default-drives"></a>L’initialisation par défaut de lecteurs

Votre implémente de fournisseur de lecteur la [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) permet de monter des lecteurs. Par exemple, le fournisseur Active Directory peut-être monter un disque pour la valeur par défaut de contexte d’appellation si l’ordinateur est joint à un domaine.

Cette méthode retourne une collection d’informations de lecteur sur les lecteurs initialisés, ou une collection vide. L’appel à cette méthode est effectué après les appels de runtime Windows PowerShell le [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode pour initialiser le fournisseur.

Ce fournisseur de lecteur ne remplace pas le [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) (méthode). Toutefois, le code suivant montre l’implémentation par défaut, qui retourne une collection vide lecteur :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Points à retenir sur l’implémentation InitializeDefaultDrives

Tous les fournisseurs de lecteur doivent monter un lecteur racine pour aider l’utilisateur avec la fonctionnalité de découverte. Le lecteur racine peut répertorier les emplacements qui servent de racines pour les autres lecteurs montés. Par exemple, le fournisseur Active Directory peut créer un lecteur qui répertorie les contextes d’affectation de noms trouvés dans le `namingContext` attributs sur l’environnement de système distribué (DSE) racine. Cela permet aux utilisateurs de découvrir les points de montage pour les autres lecteurs.

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Test du fournisseur de lecteur PowerShell Windows

Lorsque votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande, y compris les applets de commande mises à disposition par dérivation. Nous allons tester l’exemple de fournisseur de lecteur.

1. Exécutez le `Get-PSProvider` applet de commande pour récupérer la liste des fournisseurs pour vous assurer que le fournisseur du lecteur AccessDB est présent :

   **PS> `Get-PSProvider`**

   La sortie suivante apparaît :

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Assurez-vous qu’un nom de serveur de base de données (DSN) existe pour la base de données en accédant à la **des Sources de données** partie de la **outils d’administration** du système d’exploitation. Dans le **DSN utilisateur** table, double-cliquez sur **base de données MS Access** et ajoutez le chemin d’accès de lecteur C:\ps\northwind.mdb.

3. Créer un nouveau lecteur à l’aide de l’exemple de fournisseur de lecteur :

   **PS > Nouveau-psdrive-nom mydb-racine c:\ps\northwind.mdb - psprovider AccessDb**

   La sortie suivante apparaît :

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Valider la connexion. Étant donné que la connexion est définie en tant que membre du lecteur, vous pouvez le vérifier à l’aide de l’applet de commande Get-PDDrive.

   > [!NOTE]
   > L’utilisateur ne peut pas encore interagir avec le fournisseur en tant que lecteur, comme le fournisseur a besoin de fonctionnalités de conteneur pour cette interaction. Pour plus d’informations, consultez [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > (get-psdrive mydb) .connection**

   La sortie suivante apparaît :

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Retirez le lecteur et quitter l’interpréteur de commandes :

   **PS > remove-psdrive mydb**

   **PS > Quitter**

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Concevoir votre fournisseur de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Création d’un fournisseur PowerShell de base Windows](./creating-a-basic-windows-powershell-provider.md)