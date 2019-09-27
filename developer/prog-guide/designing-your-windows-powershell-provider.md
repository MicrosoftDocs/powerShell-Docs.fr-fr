---
title: Conception de votre fournisseur Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 962d2ba9fd892c297a633276b9ac07a5fa75ea87
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323275"
---
# <a name="designing-your-windows-powershell-provider"></a>Conception de votre fournisseur Windows PowerShell

Vous devez implémenter un fournisseur Windows PowerShell Si votre produit ou votre configuration expose un ensemble de données stockées, telles qu’une base de données que l’utilisateur souhaite parcourir ou parcourir. En outre, si votre produit fournit un conteneur, même s’il ne s’agit pas d’un conteneur à plusieurs niveaux, il est logique d’implémenter un fournisseur Windows PowerShell. Par exemple, vous souhaiterez peut-être implémenter un fournisseur de conteneurs Windows PowerShell si la copie, le déplacement, le changement de nom, le changement de nom, la nouvelle ou la suppression de l’applet de commande se justifie comme une opération sur votre produit ou vos données de configuration.

## <a name="windows-powershell-paths-identify-your-provider"></a>Les chemins d’accès Windows PowerShell identifient votre fournisseur

Le runtime Windows PowerShell utilise des chemins d’accès Windows PowerShell pour accéder au fournisseur Windows PowerShell approprié. Lorsqu’une applet de commande spécifie l’un de ces chemins d’accès, le runtime sait quel fournisseur utiliser pour accéder au magasin de données associé. Ces chemins d’accès incluent les chemins d’accès qualifiés par les lecteurs, les chemins d’accès qualifiés du fournisseur, les chemins d’accès directs du fournisseur et les chemins internes du fournisseur. Chaque fournisseur Windows PowerShell doit prendre en charge un ou plusieurs de ces chemins d’accès.

Pour plus d’informations sur les chemins d’accès Windows PowerShell, consultez fonctionnement de Windows PowerShell.

### <a name="defining-a-drive-qualified-path"></a>Définition d’un chemin d’accès complet au lecteur

Pour permettre à l’utilisateur d’accéder aux données situées sur un lecteur physique, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès complet au lecteur. Ce chemin d’accès commence par le nom du lecteur suivi d’un signe deux-points ( :), par exemple, MyDrive : \ abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Définition d’un chemin d’accès qualifié par le fournisseur

Pour permettre au runtime Windows PowerShell d’initialiser et d’initialiser le fournisseur, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès qualifié par le fournisseur. Par exemple, FileSystem ::\\\uncshare\abc\bar est le chemin d’accès qualifié par le fournisseur pour le fournisseur FileSystem fourni par Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Définition d’un chemin d’accès direct au fournisseur

Pour autoriser l’accès à distance à votre fournisseur Windows PowerShell, il doit prendre en charge un chemin d’accès direct au fournisseur pour passer directement au fournisseur Windows PowerShell pour l’emplacement actuel. Par exemple, le fournisseur Windows PowerShell du Registre peut \\utiliser \server\regkeypath comme chemin d’accès direct au fournisseur.

### <a name="defining-a-provider-internal-path"></a>Définition d’un chemin d’accès interne au fournisseur

Pour permettre à l’applet de commande du fournisseur d’accéder aux données à l’aide d’interfaces de programmation d’applications (API) non-Windows PowerShell, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès interne au fournisseur. Ce chemin d’accès est indiqué après «  :: » dans le chemin d’accès qualifié du fournisseur. Par exemple, le chemin d’accès interne du fournisseur pour le fournisseur de système \\de fichiers Windows PowerShell est \uncshare\abc\bar.

## <a name="changing-stored-data"></a>Modification des données stockées

Lors de la substitution de méthodes qui modifient le magasin de données sous-jacent, appelez toujours la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) avec la version la plus à jour de l’élément modifiée par cette méthode. L’infrastructure du fournisseur détermine si l’objet d’élément doit être passé au pipeline, par exemple lorsque l’utilisateur spécifie le paramètre-PassThru. Si la récupération de l’élément le plus à jour est une opération coûteuse (en termes de performances), vous pouvez tester la propriété Context. PassThru pour déterminer si vous devez réellement écrire l’élément résultant.

## <a name="choose-a-base-class-for-your-provider"></a>Choisir une classe de base pour votre fournisseur

Windows PowerShell fournit un certain nombre de classes de base que vous pouvez utiliser pour implémenter votre propre fournisseur Windows PowerShell. Lors de la conception d’un fournisseur, choisissez la classe de base, décrite dans cette section, qui est la plus adaptée à vos besoins.

Chaque classe de base du fournisseur Windows PowerShell met à disposition un ensemble d’applets de commande. Cette section décrit les applets de commande, mais ne décrit pas leurs paramètres.

À l’aide de l’état de session, le runtime Windows PowerShell met plusieurs applets de commande d’emplacement à la disposition `Get-Location`de certains `Pop-Location`fournisseurs Windows `Push-Location` PowerShell, tels que les applets de commande, `Set-Location`, et. Vous pouvez utiliser l' `Get-Help` applet de commande pour obtenir des informations sur ces applets de commande d’emplacement.

### <a name="cmdletprovider-base-class"></a>Classe de base CmdletProvider

La classe [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) définit un fournisseur Windows PowerShell de base. Cette classe prend en charge la déclaration du fournisseur et fournit un certain nombre de propriétés et de méthodes qui sont disponibles pour tous les fournisseurs Windows PowerShell. La classe est appelée par l' `Get-PSProvider` applet de commande pour répertorier tous les fournisseurs disponibles pour une session. L’implémentation de cette applet de commande est fournie par l’état de session.

> [!NOTE]
> Les fournisseurs Windows PowerShell sont disponibles pour toutes les étendues de langage Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe de base DriveCmdletProvider

La classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) définit un fournisseur de lecteurs Windows PowerShell qui prend en charge les opérations d’ajout de nouveaux lecteurs, la suppression de lecteurs existants et l’initialisation de lecteurs par défaut. Par exemple, le fournisseur FileSystem fourni par Windows PowerShell initialise les lecteurs pour tous les volumes montés, tels que les disques durs et les lecteurs de CD/DVD.

Cette classe dérive de la classe de base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . Le tableau suivant répertorie les applets de commande exposées par cette classe. En plus de ceux répertoriés, `Get-PSDrive` l’applet de commande (exposée par l’état de session) est une applet de commande associée qui est utilisée pour récupérer les lecteurs disponibles.

|Applet de commande|Définition|
|------------|----------------|
|`New-PSDrive`|Crée un nouveau lecteur pour la session et diffuse des informations sur le lecteur.|
|`Remove-PSDrive`|Supprime un lecteur de la session.|

### <a name="itemcmdletprovider-base-class"></a>Classe de base ItemCmdletProvider

La classe [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) définit un fournisseur d’éléments Windows PowerShell qui effectue des opérations sur les éléments individuels du magasin de données, et ne prend pas en part les fonctionnalités de conteneur ou de navigation. Cette classe dérive de la classe de base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Le tableau suivant répertorie les applets de commande exposées par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|`Clear-Item`|Efface le contenu actuel des éléments à l’emplacement spécifié et le remplace par la valeur « Clear » spécifiée par le fournisseur. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Get-Item`|Récupère des éléments à partir de l’emplacement spécifié et diffuse en continu les objets résultants.|
|`Invoke-Item`|Appelle l’action par défaut pour l’élément au niveau du chemin d’accès spécifié.|
|`Set-Item`|Définit un élément à l’emplacement spécifié avec la valeur indiquée. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Resolve-Path`|Résout les caractères génériques pour un chemin d’accès Windows PowerShell et les informations de chemin d’accès de flux.|
|`Test-Path`|Teste le chemin d’accès spécifié et `true` retourne s’il `false` existe ; sinon,. Cette applet de commande est implémentée `IsContainer` pour prendre en charge le paramètre de la méthode [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .|

### <a name="containercmdletprovider-base-class"></a>Classe de base ContainerCmdletProvider

La classe [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) définit un fournisseur de conteneurs Windows PowerShell qui expose un conteneur pour les éléments de magasin de données à l’utilisateur. N’oubliez pas qu’un fournisseur de conteneurs Windows PowerShell ne peut être utilisé qu’en présence d’éléments dans un conteneur (sans conteneurs imbriqués). S’il existe des conteneurs imbriqués, vous devez implémenter un fournisseur de navigation Windows PowerShell.

Cette classe dérive de la classe de base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Le tableau suivant définit les applets de commande implémentées par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|`Copy-Item`|Copie des éléments d’un emplacement vers un autre. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Get-Childitem`|Récupère les éléments enfants à l’emplacement spécifié et les diffuse sous forme d’objets.|
|`New-Item`|Crée de nouveaux éléments à l’emplacement spécifié et diffuse l’objet résultant.|
|`Remove-Item`|Supprime des éléments de l’emplacement spécifié.|
|`Rename-Item`|Renomme un élément à l’emplacement spécifié. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|

### <a name="navigationcmdletprovider-base-class"></a>Classe de base NavigationCmdletProvider

La classe [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) définit un fournisseur de navigation Windows PowerShell qui effectue des opérations pour les éléments qui utilisent plusieurs conteneurs. Cette classe dérive de la classe de base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Le tableau suivant répertorie les applets de commande exposées par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|Combinaison-chemin|Combine deux chemins d’accès en un seul chemin d’accès, à l’aide d’un délimiteur spécifique au fournisseur entre les chemins d’accès. Cette applet de commande diffuse des chaînes.|
|`Move-Item`|Déplace les éléments à l’emplacement spécifié. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|

Une applet de commande associée est l’applet de commande Basic parse-Path fournie par Windows PowerShell. Cette applet de commande peut être utilisée pour analyser un chemin d’accès Windows `Parent` PowerShell afin de prendre en charge le paramètre. Il diffuse en continu la chaîne du chemin d’accès parent.

## <a name="select-provider-interfaces-to-support"></a>Sélectionner les interfaces de fournisseur à prendre en charge

En plus de dériver de l’une des classes de base Windows PowerShell, votre fournisseur Windows PowerShell peut prendre en charge d’autres fonctionnalités en dérivant d’une ou plusieurs des interfaces de fournisseur suivantes. Cette section définit ces interfaces et les applets de commande prises en charge par chaque. Elle ne décrit pas les paramètres des applets de commande prises en charge par l’interface. Les informations sur les paramètres d’applet de `Get-Command` commande `Get-Help` sont disponibles en ligne à l’aide des applets de commande et.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

L’interface [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) définit un fournisseur de contenu qui effectue des opérations sur le contenu d’un élément de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Add-Content`|Ajoute les longueurs de valeur indiquées au contenu de l’élément spécifié. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Clear-Content`|Définit le contenu de l’élément spécifié sur la valeur « Clear ». Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Get-Content`|Récupère le contenu des éléments spécifiés et diffuse en continu les objets résultants.|
|`Set-Content`|Remplace le contenu existant pour les éléments spécifiés. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

L’interface [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) définit un fournisseur Windows PowerShell de propriété qui effectue des opérations sur les propriétés des éléments dans le magasin de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

> [!NOTE]
> Le `Path` paramètre sur ces applets de commande indique un chemin d’accès à un élément au lieu d’identifier une propriété.

|Applet de commande|Définition|
|------------|----------------|
|`Clear-ItemProperty`|Affecte à la valeur « Clear » les propriétés des éléments spécifiés. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Get-ItemProperty`|Récupère les propriétés des éléments spécifiés et diffuse en continu les objets résultants.|
|`Set-ItemProperty`|Définit les propriétés des éléments spécifiés avec les valeurs indiquées. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

L’interface [System. Management. Automation. Provider. Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) , dérivée de [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), définit un fournisseur qui spécifie des paramètres dynamiques pour son applets de commande prises en charge. Ce type de fournisseur gère les opérations pour lesquelles des propriétés peuvent être définies au moment de l’exécution, par exemple, une nouvelle opération de propriété. Ces opérations ne sont pas possibles sur les éléments ayant des propriétés définies statiquement. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Copy-ItemProperty`|Copie une propriété de l’élément spécifié vers un autre élément. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`Move-ItemProperty`|Déplace une propriété de l’élément spécifié vers un autre élément. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|
|`New-ItemProperty`|Crée une propriété sur les éléments spécifiés et diffuse en continu les objets résultants.|
|`Remove-ItemProperty`|Supprime une propriété pour les éléments spécifiés.|
|`Rename-ItemProperty`|Renomme une propriété des éléments spécifiés. Cette applet de commande ne transmet pas d’objet de sortie via le `PassThru` pipeline, à moins que son paramètre ne soit spécifié.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

L’interface [System. Management. Automation. Provider. Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) ajoute des fonctionnalités de descripteur de sécurité à un fournisseur. Cette interface permet à l’utilisateur d’obtenir et de définir des informations de descripteur de sécurité pour un élément dans le magasin de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Get-Acl`|Récupère les informations contenues dans une liste de contrôle d’accès (ACL), qui fait partie d’un descripteur de sécurité utilisé pour protéger les ressources de système d’exploitation, par exemple, un fichier ou un objet.|
|`Set-Acl`|Définit les informations pour une liste de contrôle d’accès. Il se présente sous la forme d’une instance de [System. Security. AccessControl. objet ObjectSecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) sur le ou les éléments désignés pour le chemin d’accès spécifié. Cette applet de commande peut définir des informations sur les fichiers, les clés et les sous-clés du Registre, ou tout autre élément de fournisseur, si le fournisseur Windows PowerShell prend en charge le paramètre des informations de sécurité.|

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fonctionnement de Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)