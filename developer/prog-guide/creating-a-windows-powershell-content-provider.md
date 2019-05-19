---
title: Création d’un fournisseur de contenu PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: d7e237514b4db4bce3366836d3b6e0cd340bf107
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855017"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Création d’un fournisseur de contenu Windows PowerShell

Cette rubrique décrit comment créer un fournisseur Windows PowerShell qui permet à l’utilisateur de manipuler le contenu des éléments dans un magasin de données. Par conséquent, un fournisseur qui permet de manipuler le contenu d’éléments est appelé un fournisseur de contenu Windows PowerShell.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider06.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Définir la classe de fournisseur Windows PowerShell contenu

Un fournisseur de contenu Windows PowerShell doit créer une classe .NET qui prend en charge la [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface. Voici la définition de classe pour le fournisseur d’éléments décrit dans cette section.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Notez que, dans cette définition, de la classe la [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut inclut deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Pour ce fournisseur, il n’existe aucun ajout capacités spécifiques de Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Définir des fonctionnalités de classe de Base

Comme décrit dans [fournisseur Design Your Windows PowerShell](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe est dérivée de plusieurs autres classes fourni fonctionnalités de l’autre fournisseur. Un fournisseur de contenu Windows PowerShell, par conséquent, généralement définit toutes les fonctionnalités fournies par les classes.

Pour plus d’informations sur la façon d’implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PowerShell Windows base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs, y compris le fournisseur décrit ici, peut utiliser l’implémentation par défaut de cette fonctionnalité est fournie par Windows PowerShell.

Pour accéder à la banque de données, le fournisseur doit implémenter les méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, telles que l’obtention de paramètre et effacement des éléments, le fournisseur doit implémenter les méthodes fournies par le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Pour travailler sur des magasins de données de plusieurs couches, le fournisseur doit implémenter les méthodes fournies par le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Pour prendre en charge les commandes récursives, les conteneurs imbriqués et les chemins d’accès relatifs, le fournisseur doit implémenter la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe de base. En outre, ce fournisseur de contenu Windows PowerShell peut attache [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface pour le [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe de base et doit donc implémenter les méthodes fournies par cette classe. Pour plus d’informations, consultez l’implémentation de ces méthodes, consultez [implémenter un fournisseur de PowerShell Navigation Windows](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implémentation d’un lecteur de contenu

Pour lire le contenu à partir d’un élément, un fournisseur doit implémente une classe de lecteur de contenu qui dérive de [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). Le lecteur de contenu pour ce fournisseur autorise l’accès au contenu d’une ligne dans une table de données. La classe du lecteur de contenu définit un **en lecture** méthode qui Récupère les données à partir de la ligne indiquée et retourne une liste de ces données, un **recherche** méthode qui déplace le lecteur de contenu, un  **Fermer** méthode qui ferme le lecteur de contenu, et un **Dispose** (méthode).

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implémentation d’un Writer de contenu

Pour écrire du contenu à un élément, un fournisseur doit implémenter un contenu dérive de la classe du writer [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Définit la classe de contenu writer un **écrire** méthode qui écrit le contenu de la ligne spécifiée, un **recherche** méthode qui déplace l’enregistreur de contenu, un **fermer** méthode ferme le writer de contenu et un **Dispose** (méthode).

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Récupération du lecteur de contenu

Pour obtenir le contenu à partir d’un élément, le fournisseur doit implémenter la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour prendre en charge la `Get-Content` applet de commande. Cette méthode retourne le lecteur de contenu pour l’élément situé dans le chemin d’accès spécifié. L’objet de lecteur peut ensuite être ouvert pour lire le contenu.

Voici l’implémentation de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) pour cette méthode pour ce fournisseur.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Points à retenir sur l’implémentation GetContentReader

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) méthode devez vous assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Get-Content

Le `Get-Content` applet de commande peut-être nécessiter des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de contenu de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) (méthode). Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Ce fournisseur de conteneur Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Récupération de l’enregistreur de contenu

Pour écrire du contenu à un élément, le fournisseur doit implémenter la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) pour prendre en charge la `Set-Content` et `Add-Content` applets de commande. Cette méthode retourne le writer de contenu pour l’élément situé dans le chemin d’accès spécifié.

Voici l’implémentation de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) pour cette méthode.

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

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Points à retenir sur l’implémentation GetContentWriter

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) méthode devez vous assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un enregistreur pour les objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Attachement des paramètres dynamiques pour les applets de commande Add-Content et Set-Content

Le `Add-Content` et `Set-Content` applets de commande peut nécessiter des paramètres dynamiques supplémentaires qui sont ajoutés à un runtime. Pour fournir ces paramètres dynamiques, le fournisseur de contenu de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) gérer ces (méthode) paramètres. Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres aux applets de commande.

Ce fournisseur de conteneur Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Effacement du contenu

Votre fournisseur de contenu d’implémente le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode à l’appui de la `Clear-Content` applet de commande. Cette méthode supprime le contenu de l’élément dans le chemin spécifié, mais toucher à l’élément.

Voici l’implémentation de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode pour ce fournisseur.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Points à retenir sur l’implémentation ClearContent

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de contenu Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode devez vous assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas effacer le contenu des objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

- Votre implémentation de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée au magasin de données, telles que l’effacement du contenu. Le [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) méthode envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell de gestion des paramètres de ligne de commande ni préférence variables de déterminer ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message à l’utilisateur pour que les commentaires vérifier si l’opération doit être poursuivie. L’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permet une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Clear-Content

Le `Clear-Content` applet de commande peut-être nécessiter des paramètres dynamiques supplémentaires qui sont ajoutés lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de contenu de Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) gérer ces (méthode) paramètres. Cette méthode récupère les paramètres de l’article sur le chemin d’accès indiqué. Cette méthode récupère les paramètres dynamiques pour l’élément dans le chemin d’accès indiqué et retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Ce fournisseur de conteneur Windows PowerShell n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de cette méthode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Lorsque vous écrivez un fournisseur, il peut être nécessaire d’ajouter des membres à des objets existants ou définir de nouveaux objets. Dans ce cas, vous devez créer un fichier de Types que Windows PowerShell peut utiliser pour identifier les membres de l’objet et un fichier de Format qui définit comment l’objet est affiché. Pour plus d’informations, consultez [étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Construction du fournisseur PowerShell de Windows

Consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur PowerShell de Windows

Lorsque votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande. Par exemple, tester l’exemple de fournisseur de contenu.

Utilisez le `Get-Content` applet de commande pour récupérer le contenu de l’élément spécifié dans la table de base de données sur le chemin d’accès spécifié par le `Path` paramètre. Le `ReadCount` paramètre spécifie le nombre d’éléments pour le lecteur de contenu défini à lire (par défaut 1). Avec l’entrée de commande suivante, l’applet de commande extrait les deux lignes (éléments) de la table et affiche leur contenu. Notez que l’exemple suivant utilise une base de données Access fictive.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
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

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fournisseur de votre Windows PowerShell de conception](./designing-your-windows-powershell-provider.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implémenter un fournisseur de Navigation Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)
