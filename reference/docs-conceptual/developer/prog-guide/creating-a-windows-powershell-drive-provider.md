---
title: Création d’un fournisseur de lecteurs Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366828"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Création d’un fournisseur de lecteur Windows PowerShell

Cette rubrique explique comment créer un fournisseur de lecteurs Windows PowerShell qui fournit un moyen d’accéder à un magasin de données via un lecteur Windows PowerShell. Ce type de fournisseur est également appelé fournisseurs de lecteurs Windows PowerShell. Les lecteurs Windows PowerShell utilisés par le fournisseur permettent de se connecter au magasin de données.

Le fournisseur de lecteur Windows PowerShell décrit ici permet d’accéder à une base de données Microsoft Access. Pour ce fournisseur, le lecteur Windows PowerShell représente la base de données (il est possible d’ajouter un nombre quelconque de lecteurs à un fournisseur de lecteur), les conteneurs de niveau supérieur du lecteur représentent les tables de la base de données, et les éléments des conteneurs représentent les lignes dans tables.

## <a name="defining-the-windows-powershell-provider-class"></a>Définition de la classe de fournisseur Windows PowerShell

Votre fournisseur de lecteurs doit définir une classe .NET qui dérive de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Voici la définition de classe pour ce fournisseur de lecteurs :

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Notez que dans cet exemple, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) spécifie un nom convivial pour le fournisseur et les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à Windows Runtime PowerShell pendant le traitement des commandes. Les valeurs possibles pour les fonctionnalités du fournisseur sont définies par l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Ce fournisseur de lecteurs ne prend en charge aucune de ces fonctionnalités.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de base

Comme décrit dans [concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) dérive de la classe de base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) qui définit les méthodes nécessaires pour initialiser et désinitialiser le fournisseur. Pour implémenter les fonctionnalités d’ajout d’informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

## <a name="creating-drive-state-information"></a>Création d’informations sur l’état du lecteur

Tous les fournisseurs Windows PowerShell sont considérés comme sans État, ce qui signifie que le fournisseur de votre lecteur doit créer les informations d’État requises par le runtime Windows PowerShell lorsqu’il appelle votre fournisseur.

Pour ce fournisseur de lecteur, les informations d’État incluent la connexion à la base de données qui est conservée dans le cadre des informations sur le lecteur. Voici le code qui montre comment ces informations sont stockées dans l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur :

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Création d’un lecteur

Pour autoriser le runtime Windows PowerShell à créer un lecteur, le fournisseur de lecteur doit implémenter la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) . Le code suivant illustre l’implémentation de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. les *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) pour ce fournisseur de lecteurs :

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Votre remplacement de cette méthode doit effectuer les opérations suivantes :

- Vérifiez que le membre [System. Management. Automation. PSDriveinfo. root *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) existe et qu’une connexion au magasin de données peut être établie.

- Créez un lecteur et renseignez le membre de la connexion, à la prise en charge de l’applet de commande `New-PSDrive`.

- Validez l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) pour le lecteur proposé.

- Modifiez l’objet [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) qui décrit le lecteur avec les informations de performances ou de fiabilité requises, ou fournissez des données supplémentaires aux appelants à l’aide du lecteur.

- Gérez les échecs à l’aide de la méthode [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) , puis retournez `null`.

  Cette méthode retourne soit les informations de lecteur qui ont été passées à la méthode, soit une version spécifique au fournisseur.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Attachement de paramètres dynamiques à les

L’applet de commande `New-PSDrive` prise en charge par votre fournisseur de lecteurs peut nécessiter des paramètres supplémentaires. Pour attacher ces paramètres dynamiques à l’applet de commande, le fournisseur implémente la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) . Cette méthode retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Ce fournisseur de lecteurs ne remplace pas cette méthode. Toutefois, le code suivant illustre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Suppression d’un lecteur

Pour fermer la connexion à la base de données, le fournisseur de lecteur doit implémenter la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) . Cette méthode ferme la connexion au lecteur après le nettoyage des informations spécifiques au fournisseur.

Le code suivant illustre l’implémentation de la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) pour ce fournisseur de lecteurs :

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Si le lecteur peut être supprimé, la méthode doit retourner les informations transmises à la méthode par le biais du paramètre `drive`. Si le lecteur ne peut pas être supprimé, la méthode doit écrire une exception, puis retourner `null`. Si votre fournisseur ne remplace pas cette méthode, l’implémentation par défaut de cette méthode retourne simplement les informations de lecteur passées comme entrée.

## <a name="initializing-default-drives"></a>Initialisation des lecteurs par défaut

Votre fournisseur de lecteur implémente la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) pour monter des lecteurs. Par exemple, le fournisseur de Active Directory peut monter un lecteur pour le contexte d’appellation par défaut si l’ordinateur est joint à un domaine.

Cette méthode retourne une collection d’informations sur les lecteurs initialisés, ou une collection vide. L’appel à cette méthode est effectué après que le runtime Windows PowerShell a appelé la méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) pour initialiser le fournisseur.

Ce fournisseur de lecteurs ne remplace pas la méthode [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) . Toutefois, le code suivant montre l’implémentation par défaut, qui retourne une collection de lecteurs vide :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Points à retenir concernant l’implémentation de InitializeDefaultDrives

Tous les fournisseurs de lecteurs doivent monter un lecteur racine pour aider l’utilisateur à se découvrir. Le lecteur racine peut répertorier les emplacements qui servent de racines pour d’autres lecteurs montés. Par exemple, le fournisseur de Active Directory peut créer un lecteur qui répertorie les contextes d’attribution de noms trouvés dans les attributs `namingContext` sur l’environnement de système distribué (DSE) racine. Cela permet aux utilisateurs de découvrir des points de montage pour d’autres lecteurs.

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Test du fournisseur de lecteurs Windows PowerShell

Lorsque votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande, y compris les applets de commande rendues disponibles par dérivation. Nous allons tester l’exemple de fournisseur de lecteur.

1. Exécutez l’applet de commande `Get-PSProvider` pour récupérer la liste des fournisseurs afin de vérifier que le fournisseur de lecteurs AccessDB est présent :

   **@No__t de > PS-1**

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

2. Assurez-vous qu’un nom de serveur de base de données existe pour la base de données en accédant à la partie **sources de données** des **Outils d’administration** du système d’exploitation. Dans la table **DSN utilisateur** , double-cliquez sur **base de données MS Access** et ajoutez le chemin d’accès au lecteur C:\ps\northwind.mdb.

3. Créez un lecteur à l’aide de l’exemple de fournisseur de lecteur :

   **PS > New-PSDrive-Name MyDB-root c:\ps\northwind.mdb-PSProvider AccessDb**

   La sortie suivante apparaît :

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Validez la connexion. Étant donné que la connexion est définie en tant que membre du lecteur, vous pouvez la vérifier à l’aide de l’applet de commande PDDrive.

   > [!NOTE]
   > L’utilisateur ne peut pas encore interagir avec le fournisseur en tant que lecteur, car le fournisseur a besoin de la fonctionnalité de conteneur pour cette interaction. Pour plus d’informations, consultez [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **> PS (obten-PSDrive MyDB). connexion**

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

5. Retirez le lecteur et quittez l’interpréteur de commandes :

   **Bloc de > PS-Remove-PSDrive MyDB**

   **Sortie de la > PS**

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md)
