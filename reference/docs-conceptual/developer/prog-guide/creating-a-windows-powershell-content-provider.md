---
title: Création d’un fournisseur de contenu Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: 2d48c18cb41dcca372b1e12e1f3abc4c3f5e4bee
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870725"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Création d’un fournisseur de contenu Windows PowerShell

Cette rubrique explique comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler le contenu des éléments dans un magasin de données. Par conséquent, un fournisseur qui peut manipuler le contenu des éléments est appelé fournisseur de contenu Windows PowerShell.

> [!NOTE]
> Vous pouvez télécharger le C# fichier source (AccessDBSampleProvider06.cs) pour ce fournisseur à l’aide du kit de développement logiciel (SDK) Microsoft Windows pour Windows Vista et .NET Framework les composants d’exécution 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Les fichiers sources téléchargés sont disponibles dans le répertoire des **exemples de >\<PowerShell** . Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Définir la classe de fournisseur de contenu Windows PowerShell

Un fournisseur de contenu Windows PowerShell doit créer une classe .NET qui prend en charge l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) . Voici la définition de classe pour le fournisseur d’éléments décrit dans cette section.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33
"AccessDBProviderSample06.cs")]

Notez que dans cette définition de classe, l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) comprend deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose au runtime Windows PowerShell pendant le traitement de la commande. Pour ce fournisseur, aucune fonctionnalité spécifique de Windows PowerShell n’est ajoutée.

## <a name="define-functionality-of-base-class"></a>Définir les fonctionnalités de la classe de base

Comme décrit dans [concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) dérive de plusieurs autres classes qui offraient des fonctionnalités de fournisseur différentes. Un fournisseur de contenu Windows PowerShell définit donc généralement toutes les fonctionnalités fournies par ces classes.

Pour plus d’informations sur la façon d’implémenter des fonctionnalités pour ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur Windows PowerShell de base](./creating-a-basic-windows-powershell-provider.md).
Toutefois, la plupart des fournisseurs, y compris le fournisseur décrit ici, peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

Pour accéder au magasin de données, le fournisseur doit implémenter les méthodes de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteurs Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, tels que l’obtention, la définition et l’effacement des éléments, le fournisseur doit implémenter les méthodes fournies par la classe de base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Pour travailler sur des magasins de données multicouches, le fournisseur doit implémenter les méthodes fournies par la classe de base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de conteneurs Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Pour prendre en charge les commandes récursives, les conteneurs imbriqués et les chemins d’accès relatifs, le fournisseur doit implémenter la classe de base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . En outre, ce fournisseur de contenu Windows PowerShell peut attacher l’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) à la classe de base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) et doit donc implémenter les méthodes fournies par cette classe. Pour plus d’informations, consultez Implémentation de ces méthodes, consultez [implémentation d’un fournisseur Windows PowerShell de navigation](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implémentation d’un lecteur de contenu

Pour lire le contenu d’un élément, un fournisseur doit implémenter une classe de lecteur de contenu qui dérive de [System. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).
Le lecteur de contenu pour ce fournisseur autorise l’accès au contenu d’une ligne dans une table de données. La classe de lecteur de contenu définit une méthode de **lecture** qui récupère les données de la ligne indiquée et retourne une liste qui représente ces données, une méthode **Seek** qui déplace le lecteur de contenu, une méthode **Close** qui ferme le lecteur de contenu et une méthode **dispose** .

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241
"AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implémentation d’un writer de contenu

Pour écrire du contenu dans un élément, un fournisseur doit implémenter une classe de writer de contenu dérivée de [System. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).
La classe du writer de contenu définit une méthode d' **écriture** qui écrit le contenu de ligne spécifié, une méthode **Seek** qui déplace le writer de contenu, une méthode **Close** qui ferme le writer de contenu et une méthode **dispose** .

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Récupération du lecteur de contenu

Pour récupérer du contenu à partir d’un élément, le fournisseur doit implémenter [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour prendre en charge l’applet de commande `Get-Content`. Cette méthode retourne le lecteur de contenu pour l’élément situé dans le chemin d’accès spécifié. L’objet lecteur peut ensuite être ouvert pour lire le contenu.

Voici l’implémentation de [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour cette méthode pour ce fournisseur.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Points à retenir concernant l’implémentation de GetContentReader

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Lors de la définition de la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. GetContentReader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) soit définie sur `true`. Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande d’extraction de contenu

L’applet de commande `Get-Content` peut nécessiter des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de contenu Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Ce fournisseur de conteneurs Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Récupération du writer de contenu

Pour écrire du contenu dans un élément, le fournisseur doit implémenter [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) pour prendre en charge les applets de commande `Set-Content` et `Add-Content`. Cette méthode retourne le writer de contenu pour l’élément situé dans le chemin d’accès spécifié.

Voici l’implémentation de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) pour cette méthode.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Points à retenir concernant l’implémentation de GetContentWriter

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Lors de la définition de la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un writer pour les objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Attachement de paramètres dynamiques aux applets de commande Add-Content et Set-Content

Les applets de commande `Add-Content` et `Set-Content` peuvent nécessiter des paramètres dynamiques supplémentaires qui sont ajoutés à un Runtime. Pour fournir ces paramètres dynamiques, le fournisseur de contenu Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) pour gérer ces paramètres. Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres aux applets de commande.

Ce fournisseur de conteneurs Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Effacement du contenu

Votre fournisseur de contenu implémente la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) pour la prise en charge de l’applet de commande `Clear-Content`. Cette méthode supprime le contenu de l’élément au niveau du chemin d’accès spécifié, mais laisse l’élément intact.

Voici l’implémentation de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) pour ce fournisseur.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Points à retenir concernant l’implémentation de ClearContent

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Lors de la définition de la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas effacer le contenu des objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true`. Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false`.

- Votre implémentation de la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée au magasin de données, comme l’effacement du contenu. La méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell qui gère les paramètres de ligne de commande ou les variables de préférence pour déterminer ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message à l’utilisateur pour permettre aux commentaires de vérifier si l’opération doit être poursuivie. L’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire des modifications système potentiellement dangereuses.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Clear-Content

L’applet de commande `Clear-Content` peut nécessiter des paramètres dynamiques supplémentaires qui sont ajoutés au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de contenu Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) pour gérer ces paramètres. Cette méthode récupère les paramètres pour l’élément au chemin d’accès indiqué. Cette méthode récupère les paramètres dynamiques pour l’élément au chemin d’accès indiqué et retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Ce fournisseur de conteneurs Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des types d’objets et de la mise en forme

Lors de l’écriture d’un fournisseur, il peut être nécessaire d’ajouter des membres à des objets existants ou de définir de nouveaux objets. Une fois cette opération effectuée, vous devez créer un fichier de types que Windows PowerShell peut utiliser pour identifier les membres de l’objet et un fichier de format qui définit le mode d’affichage de l’objet. Pour plus d’informations, consultez [extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Génération du fournisseur Windows PowerShell

Découvrez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande. Par exemple, testez l’exemple de fournisseur de contenu.

Utilisez l’applet de commande `Get-Content` pour récupérer le contenu de l’élément spécifié dans la table de base de données à l’emplacement spécifié par le paramètre `Path`. Le paramètre `ReadCount` spécifie le nombre d’éléments à lire par le lecteur de contenu défini (par défaut, 1). Avec l’entrée de commande suivante, l’applet de commande récupère deux lignes (éléments) de la table et affiche leur contenu. Notez que l’exemple de sortie suivant utilise une base de données d’accès fictif.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Implémenter un fournisseur de navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)
