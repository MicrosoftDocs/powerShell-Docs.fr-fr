---
title: Création d’un fournisseur de Navigation de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055068"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Création d’un fournisseur de navigation Windows PowerShell

Cette rubrique décrit comment créer un fournisseur de navigation de Windows PowerShell qui peut naviguer le magasin de données. Ce type de fournisseur prend en charge les commandes récursives, les conteneurs imbriqués et les chemins d’accès relatifs.

> [!NOTE]
> Vous pouvez télécharger le C# le fichier source (AccessDBSampleProvider05.cs) pour ce fournisseur en utilisant le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Les fichiers source téléchargé sont disponibles dans le  **\<exemples PowerShell >** directory.
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

Le fournisseur décrit ici permet le handle de l’utilisateur une base de données Access en tant que lecteur afin que l’utilisateur peut accéder aux tables de données dans la base de données. Lorsque vous créez votre propre fournisseur de navigation, vous pouvez implémenter des méthodes qui peuvent rendre qualifié par un lecteur de chemins d’accès requis pour la navigation, normaliser les chemins d’accès relatifs, déplacer des éléments de la banque de données, ainsi que les méthodes d’obtenir les noms des enfants, obtient le chemin d’accès du parent d’un élément et tester pour identifier si un élément est un conteneur.

> [!CAUTION]
> N’oubliez pas que cette conception suppose une base de données qui a un champ avec l’ID de nom, et que le type du champ est LongInteger.

La liste suivante comprend les sections de cette rubrique. Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur de navigation de Windows PowerShell, lire ces informations dans l’ordre dans lequel elle apparaît. Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur de navigation de Windows PowerShell, accédez directement aux informations dont vous avez besoin.

- [Définition d’une classe de fournisseur de Navigation PS](#Define-the-Windows-PowerShell-provider)

- [Définition des fonctionnalités de Base](#Defining-Base-Functionality)

- [Création d’un chemin d’accès PS](#Creating-a-Windows-PowerShell-Path)

- [Récupérer le chemin d’accès Parent](#Retrieving-the-Parent-Path)

- [Extraction du nom de chemin d’accès d’enfant](#Retrieve-the-Child-Path-Name)

- [Déterminer si un élément est un conteneur](#Determining-if-an-Item-is-a-Container)

- [Déplacement d’un élément](#Moving-an-Item)

- [Attachement des paramètres dynamiques à la `Move-Item` applet de commande](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Normalisation d’un chemin d’accès relatif](#Normalizing-a-Relative-Path)

- [Exemple de code](#Code-Sample)

- [Définition des Types d’objets et mise en forme](#Defining-Object-Types-and-Formatting)

- [Construction du fournisseur PowerShell de Windows](#Building-the-Windows-PowerShell-provider)

- [Test du fournisseur PowerShell de Windows](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Définir le fournisseur Windows PowerShell

Un fournisseur de navigation de Windows PowerShell doit créer une classe .NET qui dérive de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe de base. Voici la définition de classe pour le fournisseur de navigation décrite dans cette section.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Notez que dans ce fournisseur, le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut inclut deux paramètres. Le premier paramètre spécifie un nom convivial pour le fournisseur qui est utilisé par Windows PowerShell. Le deuxième paramètre spécifie les fonctionnalités spécifiques de Windows PowerShell que le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Pour ce fournisseur, il n’existe aucun capacités spécifiques de Windows PowerShell qui sont ajoutées.

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de Base

Comme décrit dans [votre fournisseur-PS de conception](./designing-your-windows-powershell-provider.md), le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) dérive de la classe de base à partir de plusieurs autres classes fourni autre fournisseur fonctionnalité. Un fournisseur de navigation de Windows PowerShell, par conséquent, doive définir toutes les fonctionnalités fournies par les classes.

Pour implémenter des fonctionnalités permettant d’ajouter des informations d’initialisation spécifiques à la session et pour libérer les ressources utilisées par le fournisseur, consultez [création d’un fournisseur de PS base](./creating-a-basic-windows-powershell-provider.md). Toutefois, la plupart des fournisseurs (y compris le fournisseur décrit ici) peuvent utiliser l’implémentation par défaut de cette fonctionnalité fournie par Windows PowerShell.

Pour obtenir l’accès au magasin de données via un lecteur Windows PowerShell, vous devez implémenter les méthodes de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de lecteur Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Pour manipuler les éléments d’un magasin de données, telles que l’obtention de paramètre et effacement des éléments, le fournisseur doit implémenter les méthodes fournies par le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur d’éléments de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Pour obtenir les éléments enfants, ou leurs noms, de la banque de données, ainsi que les méthodes qui créent, copient, renomment et supprimer des éléments, vous devez implémenter les méthodes fournies par le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)classe de base. Pour plus d’informations sur l’implémentation de ces méthodes, consultez [création d’un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Création d’un chemin d’accès de Windows PowerShell

Fournisseur de navigation de Windows PowerShell utilisez un chemin d’accès Windows PowerShell interne de fournisseur pour parcourir les éléments du magasin de données. Pour créer un chemin d’accès interne au fournisseur le fournisseur doit implémenter la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) appels de méthode pour prendre en charge de l’applet de commande combiner-chemin d’accès. Cette méthode combine un chemin d’accès parent et enfant dans un chemin d’accès interne au fournisseur, à l’aide d’un séparateur de chemin d’accès spécifique au fournisseur entre les chemins d’accès parent et enfant.

L’implémentation par défaut accepte les chemins d’accès avec « / » ou «\\« comme séparateur de chemin d’accès normalise le séparateur de chemin d’accès à »\\», combine les parties de chemin d’accès parent et enfant avec le séparateur entre eux, puis retourne une chaîne qui contienne le chemins d’accès combinés.

Ce fournisseur de navigation n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) (méthode).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Points à retenir sur l’implémentation MakePath

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Votre implémentation de la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) méthode ne doit pas valider le chemin d’accès comme un chemin qualifié complet valide dans l’espace de noms du fournisseur. N’oubliez pas que chaque paramètre ne peut représenter une partie d’un chemin d’accès et les parties combinés peut ne pas génèrent un chemin d’accès qualifié complet. Par exemple, le [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) méthode pour le fournisseur de système de fichiers peut recevoir des « windows\system32 » dans le `parent` paramètre et « abc.dll » dans le `child` paramètre. La méthode regroupe ces valeurs avec le «\\« séparateur et retourne « windows\system32\abc.dll », qui n’est pas un chemin d’accès de système de fichier complet.

  > [!IMPORTANT]
  > Les parties du chemin d’accès fournis dans l’appel à [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) peut contenir des caractères non autorisés dans l’espace de noms du fournisseur. Ces caractères sont très probablement utilisés pour le développement des caractères génériques et l’implémentation de cette méthode ne doit pas les supprimer.

## <a name="retrieving-the-parent-path"></a>Récupérer le chemin d’accès Parent

Implémentent des fournisseurs de navigation de Windows PowerShell le [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) pour récupérer la partie parent du complet ou partielle (méthode) chemin d’accès spécifique au fournisseur. La méthode supprime le composant du chemin d’accès et retourne le parent de partie de chemin d’accès. Le `root` paramètre spécifie le chemin d’accès complet à la racine d’un lecteur. Ce paramètre peut être null ou vide si un lecteur monté n’est pas en cours d’utilisation pour l’opération de récupération. Si une racine est spécifiée, la méthode doit retourner un chemin d’accès à un conteneur dans la même arborescence comme racine.

L’exemple de fournisseur de navigation ne remplace pas cette méthode, mais utilise l’implémentation par défaut. Il accepte les chemins d’accès qui utilisent toutes deux « / » et «\\» comme séparateurs de chemin d’accès. Elle normalise tout d’abord le chemin d’accès pour que seul «\\» séparateurs, puis fractionne le chemin d’accès parent désactivé à la dernière «\\» et retourne le chemin d’accès parent.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>À retenir sur l’implémentation GetParentPath

Votre implémentation de la [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) méthode doit fractionner le chemin d’accès lexicalement sur le séparateur de chemin d’accès pour l’espace de noms du fournisseur. Par exemple, le fournisseur de système de fichiers utilise cette méthode pour rechercher le dernier «\\» et retourne tous les éléments à gauche du séparateur.

## <a name="retrieve-the-child-path-name"></a>Récupérer le nom de chemin d’accès d’enfant

Votre implémente de fournisseur de navigation le [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) méthode pour récupérer le nom (élément feuille) de l’enfant de l’élément situé à la version complète indiquée ou spécifique au fournisseur de chemin d’accès partiel.

L’exemple de fournisseur de navigation ne remplace pas cette méthode. L’implémentation par défaut est indiquée ci-dessous. Il accepte les chemins d’accès qui utilisent toutes deux « / » et «\\» comme séparateurs de chemin d’accès. Elle normalise tout d’abord le chemin d’accès pour que seul «\\» séparateurs, puis fractionne le chemin d’accès parent désactivé à la dernière «\\» et retourne le nom de l’enfant partie du chemin d’accès.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Points à retenir sur l’implémentation GetChildName

Votre implémentation de la [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) méthode doit fractionner le chemin d’accès lexicalement sur le séparateur de chemin d’accès. Si le chemin d’accès fourni contient sans séparateurs de chemin d’accès, la méthode doit retourner le chemin d’accès tels quels.

> [!IMPORTANT]
> Le chemin d’accès fourni dans l’appel à cette méthode peut contenir des caractères qui ne sont pas autorisés dans l’espace de noms du fournisseur. Ces caractères sont probables utilisé pour le développement des caractères génériques ou une correspondance d’expression régulière, et l’implémentation de cette méthode ne doit pas les supprimer.

## <a name="determining-if-an-item-is-a-container"></a>Déterminer si un élément est un conteneur

Le fournisseur de navigation peut implémenter la [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) méthode pour déterminer si le chemin d’accès spécifié indique un conteneur. Elle retourne true si le chemin d’accès représente un conteneur et false sinon. L’utilisateur a besoin de cette méthode pour être en mesure d’utiliser le `Test-Path` applet de commande pour le chemin d’accès fourni.

Le code suivant illustre la [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) mise en œuvre dans notre exemple de fournisseur de navigation. La méthode vérifie que le chemin d’accès spécifié est correct et si la table existe et retourne la valeur true si le chemin d’accès indique un conteneur.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Points à retenir sur l’implémentation IsItemContainer

Votre fournisseur de navigation classe .NET peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) doit s’assurer que le chemin d’accès transmis répond aux exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propriété.

## <a name="moving-an-item"></a>Déplacement d’un élément

À l’appui de la `Move-Item` applet de commande, votre fournisseur de navigation implémente le [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (méthode). Cette méthode déplace l’élément spécifié par le `path` paramètre vers le conteneur dans le chemin d’accès fourni dans le `destination` paramètre.

L’exemple de fournisseur de navigation ne remplace pas le [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (méthode). Voici l’implémentation par défaut.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Points à retenir sur l’implémentation MoveItem

Votre fournisseur de navigation classe .NET peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) devez vous assurer que le chemin d’accès transmis répond aux exigences. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le **CmdletProvider.Exclude** propriété.

Par défaut, les substitutions de cette méthode ne devraient pas déplacer les objets sur des objets existants, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Par exemple, le fournisseur filesystem ne copiera pas c:\temp\abc.txt sur un fichier c:\bar.txt existant, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Si le chemin d’accès spécifié dans le `destination` paramètre existe et est un conteneur, le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété n’est pas obligatoire. Dans ce cas, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) doit déplacer l’élément indiqué par le `path` paramètre vers le conteneur indiqué par le `destination` paramètre en tant qu’enfant.

Votre implémentation de la [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée à l’état du système, par exemple, la suppression de fichiers. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte les paramètres de ligne de commande ou les variables de préférence dans déterminer ce qui doit être affiché à l’utilisateur.

Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, le [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message à l’utilisateur pour que les commentaires de dire si l’opération doit être poursuivie. Votre fournisseur doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) une vérification supplémentaire pour les modifications du système potentiellement dangereux.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Move-Item

Parfois le `Move-Item` applet de commande requiert des paramètres supplémentaires qui sont fournies de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de navigation doit implémenter le [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) pour obtenir les valeurs de paramètre obligatoire (méthode) à partir de l’élément au niveau du chemin d’accès indiqué et retournent un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet.

Ce fournisseur de navigation n’implémente pas cette méthode. Toutefois, le code suivant est l’implémentation par défaut de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalisation d’un chemin d’accès relatif

Votre implémente de fournisseur de navigation le [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) méthode pour normaliser le chemin d’accès qualifié complet est indiqué dans le `path` paramètre comme étant relatif au chemin spécifié par le `basePath` paramètre. La méthode retourne une chaîne représentant le chemin d’accès normalisé. Enregistre une erreur si le `path` paramètre spécifie un chemin d’accès qui n’existe pas.

L’exemple de fournisseur de navigation ne remplace pas cette méthode. Voici l’implémentation par défaut.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Points à retenir sur l’implémentation NormalizeRelativePath

Votre implémentation de [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) doit analyser le `path` paramètre, mais il ne doit pas utiliser l’analyse syntaxique. Vous sont encouragés à la conception de cette méthode à utiliser le chemin d’accès pour rechercher les informations de chemin d’accès dans le magasin de données et créer un chemin d’accès qui correspond à la casse et normalisé de syntaxe de chemin d’accès.

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Définition des Types d’objets et mise en forme

Il est possible pour un fournisseur pour ajouter des membres à des objets existants ou définir de nouveaux objets. Pour plus d’informations, consultez[étendant les Types d’objets et de mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Construction du fournisseur Windows PowerShell

Pour plus d’informations, consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Lorsque votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande, y compris les applets de commande mises à disposition par dérivation. Cet exemple testera l’exemple de fournisseur de navigation.

1. Exécutez votre nouvel interpréteur de commandes et utilisez le `Set-Location` applet de commande pour définir le chemin d’accès pour indiquer la base de données Access.

   ```powershell
   Set-Location mydb:
   ```

2. Exécutez maintenant le `Get-Childitem` applet de commande pour récupérer une liste des éléments de base de données, qui sont les tables de base de données disponible. Pour chaque table, cette applet de commande récupère également le nombre de lignes de la table.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Utilisez le `Set-Location` applet de commande pour définir l’emplacement de la table de données d’employés.

   ```powershell
   Set-Location Employees
   ```

4. Nous allons maintenant utiliser le `Get-Location` applet de commande pour récupérer le chemin d’accès à la table Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. À présent utiliser le `Get-Childitem` applet de commande dirigée vers le `Format-Table` applet de commande. Cet ensemble d’applets de commande récupère les éléments de la table de données employés, qui correspondent aux lignes de table. Ils sont mis en forme comme spécifié par le `Format-Table` applet de commande.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Vous pouvez maintenant exécuter le `Get-Item` applet de commande pour récupérer les éléments de la ligne 0 de la table de données d’employés.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Utilisez le `Get-Item` applet de commande pour récupérer les données employé pour les éléments dans la ligne 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fournisseur de votre Windows PowerShell de conception](./designing-your-windows-powershell-provider.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implémenter un fournisseur de conteneur Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guide du programmeur Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)