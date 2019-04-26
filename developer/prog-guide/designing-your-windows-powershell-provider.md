---
title: Conception de votre fournisseur de PowerShell Windows | Microsoft Docs
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
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081816"
---
# <a name="designing-your-windows-powershell-provider"></a>Conception de votre fournisseur Windows PowerShell

Vous devez implémenter un fournisseur Windows PowerShell si votre produit ou une configuration expose un ensemble de données stockées, par exemple une base de données que l’utilisateur souhaite parcourent. En outre, si votre produit fournit un conteneur, même si elle n’est pas un conteneur à plusieurs niveaux, il est judicieux d’implémenter un fournisseur Windows PowerShell. Par exemple, vous souhaiterez peut-être implémenter un fournisseur de conteneur Windows PowerShell si le verbe de l’applet de commande copie, de déplacement, de changement de nom, nouveau ou de suppression est logique comme une opération sur les données de votre produit ou de configuration.

## <a name="windows-powershell-paths-identify-your-provider"></a>Votre fournisseur d’identité de chemins d’accès de Windows PowerShell

Le runtime de Windows PowerShell utilise des chemins d’accès Windows PowerShell pour accéder au fournisseur Windows PowerShell approprié. Quand une applet de commande spécifie un de ces chemins d’accès, le runtime sait que le fournisseur à utiliser pour accéder au magasin de données associées. Ces chemins d’accès comprennent des qualifiées par un lecteur chemins, qualifié par un fournisseur de chemins d’accès, chemins d’accès directs du fournisseur et les chemins d’accès interne au fournisseur. Chaque fournisseur Windows PowerShell doit prendre en charge un ou plusieurs de ces chemins d’accès.

Pour plus d’informations sur les chemins d’accès Windows PowerShell, voir le fonctionnement du PowerShell de Windows.

### <a name="defining-a-drive-qualified-path"></a>Définition d’un chemin d’accès complet au lecteur

Pour autoriser l’utilisateur à accéder aux données situées sur un lecteur physique, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès complet incluant le lecteur. Ce chemin d’accès commence par le nom du lecteur suivi du signe deux-points ( :),), par exemple, mydrive:\abc\bar.

### <a name="defining-a-provider-qualified-path"></a>Définition d’un chemin d’accès qualifié par un fournisseur

Pour permettre au runtime de Windows PowerShell initialiser et annuler l’initialisation du fournisseur, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès qualifié par un fournisseur. Par exemple, le système de fichiers ::\\\uncshare\abc\bar est le chemin d’accès qualifié par un fournisseur pour le fournisseur de système de fichiers fourni par Windows PowerShell.

### <a name="defining-a-provider-direct-path"></a>Définition d’un chemin d’accès Direct de fournisseur

Pour autoriser l’accès à distance à votre fournisseur Windows PowerShell, il doit prendre en charge un chemin d’accès de fournisseur directs pour passer directement au fournisseur Windows PowerShell pour l’emplacement actuel. Par exemple, le fournisseur de Windows PowerShell de Registre peut utiliser \\\server\regkeypath comme un chemin d’accès directs du fournisseur.

### <a name="defining-a-provider-internal-path"></a>Définition d’un chemin d’accès interne de fournisseur

Pour permettre à l’applet de commande du fournisseur accéder aux données à l’aide des interfaces de programmation d’applications (API) non - Windows PowerShell, votre fournisseur Windows PowerShell doit prendre en charge un chemin d’accès interne au fournisseur. Ce chemin d’accès est indiqué après le « :: » dans le chemin d’accès qualifié par un fournisseur. Par exemple, le chemin d’accès interne de fournisseur pour le fournisseur Windows PowerShell de système de fichiers est \\\uncshare\abc\bar.

## <a name="changing-stored-data"></a>Modification des données stockées

Lors de la substitution des méthodes qui modifient le magasin de données sous-jacent, vous devez toujours appeler la [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) méthode avec la version la plus récente de l’élément modifié par qui méthode. L’infrastructure de fournisseur détermine si l’objet d’élément doit être passé au pipeline, par exemple lorsque l’utilisateur spécifie le paramètre - PassThru. Si l’extraction de l’objet plus récente d’est une opération coûteuse (performante), vous pouvez tester la propriété Context.PassThru pour déterminer si vous devez réellement écrire l’élément qui en résulte.

## <a name="choose-a-base-class-for-your-provider"></a>Choisissez une classe de Base pour votre fournisseur

Windows PowerShell fournit plusieurs classes de base que vous pouvez utiliser pour implémenter votre propre fournisseur Windows PowerShell. Lorsque vous créez un fournisseur, choisissez la classe de base, décrite dans cette section, qui est la mieux adaptée à vos besoins.

Chaque classe de base du fournisseur Windows PowerShell propose un ensemble d’applets de commande. Cette section décrit les applets de commande, mais il ne décrit pas leurs paramètres.

À l’aide de l’état de session, le runtime Windows PowerShell a plusieurs applets de commande location disponibles pour certains fournisseurs Windows PowerShell, comme le `Get-Location`, `Set-Location`, `Pop-Location`, et `Push-Location` applets de commande. Vous pouvez utiliser le `Get-Help` applet de commande pour obtenir des informations sur ces applets de commande location.

### <a name="cmdletprovider-base-class"></a>Classe de Base de CmdletProvider

Le [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe définit un fournisseur de base de Windows PowerShell. Cette classe prend en charge la déclaration du fournisseur et fournit un certain nombre de propriétés et méthodes qui sont disponibles pour tous les fournisseurs Windows PowerShell. La classe est appelée par le `Get-PSProvider` applet de commande pour répertorier tous les fournisseurs disponibles pour une session. L’implémentation de cette applet de commande est fournie par l’état de session.

> [!NOTE]
> Les fournisseurs Windows PowerShell sont disponibles pour toutes les étendues de langage Windows PowerShell.

### <a name="drivecmdletprovider-base-class"></a>Classe de Base de DriveCmdletProvider

Le [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe définit un fournisseur de lecteur Windows PowerShell qui prend en charge des opérations pour ajouter de nouveaux disques, supprimer les lecteurs existants et l’initialisation par défaut des lecteurs. Par exemple, le fournisseur de système de fichiers fourni par Windows PowerShell initialise des lecteurs pour tous les volumes sont montés, tels que les disques durs et les lecteurs de périphérique CD/DVD.

Cette classe est dérivée de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe de base. Le tableau suivant répertorie les applets de commande exposées par cette classe. En plus de celles répertoriées, le `Get-PSDrive` applet de commande (exposé par l’état de session) est une applet de commande connexe qui est utilisée pour récupérer des lecteurs disponibles.

|Applet de commande|Définition|
|------------|----------------|
|`New-PSDrive`|Crée un nouveau lecteur pour la session et diffuse des informations sur le lecteur.|
|`Remove-PSDrive`|Supprime un lecteur de la session.|

### <a name="itemcmdletprovider-base-class"></a>Classe de Base de ItemCmdletProvider

Le [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe définit un fournisseur d’éléments de Windows PowerShell qui effectue des opérations sur les éléments individuels du magasin de données, et il ne suppose pas que n’importe quel conteneur ou fonctionnalités de navigation. Cette classe est dérivée de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe de base. Le tableau suivant répertorie les applets de commande exposées par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|`Clear-Item`|Efface le contenu actuel d’éléments à l’emplacement spécifié et le remplace par la valeur « effacer » spécifiée par le fournisseur. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Get-Item`|Récupère des éléments à partir de l’emplacement spécifié et transmet les objets résultants.|
|`Invoke-Item`|Appelle l’action par défaut pour l’élément dans le chemin spécifié.|
|`Set-Item`|Définit un élément à l’emplacement spécifié avec la valeur indiquée. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Resolve-Path`|Résout les caractères génériques pour un chemin d’accès Windows PowerShell et des informations de chemin d’accès de flux.|
|`Test-Path`|Teste le chemin d’accès spécifié et retourne `true` si elle existe et `false` dans le cas contraire. Cette applet de commande est implémentée pour prendre en charge la `IsContainer` paramètre pour le [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (méthode).|

### <a name="containercmdletprovider-base-class"></a>Classe de Base de ContainerCmdletProvider

Le [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe définit un fournisseur de conteneur de Windows PowerShell qui expose un conteneur, pour les éléments de magasin de données, à l’utilisateur. N’oubliez pas qu’un fournisseur de conteneur de Windows PowerShell peut être utilisé uniquement s’il existe un conteneur (aucun conteneurs imbriqués) avec les éléments qu’il contient. S’il existe des conteneurs imbriqués, vous devez implémenter un fournisseur de navigation de Windows PowerShell.

Cette classe est dérivée de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe de base. Le tableau suivant définit les applets de commande implémentée par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|`Copy-Item`|Copie les éléments d’un emplacement vers un autre. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Get-Childitem`|Récupère les éléments enfants à l’emplacement spécifié et les transmet en tant qu’objets.|
|`New-Item`|Crée de nouveaux éléments à l’emplacement spécifié et transmet l’objet résultant.|
|`Remove-Item`|Supprime les éléments de l’emplacement spécifié.|
|`Rename-Item`|Renomme un élément à l’emplacement spécifié. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|

### <a name="navigationcmdletprovider-base-class"></a>Classe de Base de NavigationCmdletProvider

Le [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe définit un fournisseur de navigation de Windows PowerShell qui effectue des opérations pour les éléments qui utilisent plusieurs conteneurs. Cette classe est dérivée de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classe de base. Le tableau suivant répertorie les applets de commande exposées par cette classe.

|Applet de commande|Définition|
|------------|----------------|
|Chemin d’accès de combinaison|Combine deux chemins d’accès en un seul chemin d’accès à l’aide d’un délimiteur spécifique au fournisseur entre les chemins d’accès. Cette applet de commande diffuse des chaînes.|
|`Move-Item`|Déplace les éléments à l’emplacement spécifié. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|

Une applet de commande associée est l’applet de commande de base analyse-chemin d’accès fourni par Windows PowerShell. Cette applet de commande peut être utilisé pour analyser un chemin d’accès Windows PowerShell pour prendre en charge la `Parent` paramètre. Il transmet la chaîne de chemin d’accès parent.

## <a name="select-provider-interfaces-to-support"></a>Sélectionnez les Interfaces de fournisseur pour prendre en charge

En plus de dériver une des classes de base Windows PowerShell, votre fournisseur Windows PowerShell peut prendre en charge les autres fonctionnalités en dérivant à partir d’un ou plusieurs des interfaces de fournisseur suivantes. Cette section définit ces interfaces et les applets de commande pris en charge par chacun. Il ne décrit pas les paramètres pour les applets de commande d’interface prise en charge. Informations de paramètre d’applet de commande sont disponibles en ligne à l’aide de la `Get-Command` et `Get-Help` applets de commande.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

Le [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface définit un fournisseur de contenu qui effectue des opérations sur le contenu d’un élément de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Add-Content`|Ajoute les longueurs de la valeur indiquée pour le contenu de l’élément spécifié. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Clear-Content`|Définit le contenu de l’élément spécifié à la valeur « effacer ». Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Get-Content`|Récupère le contenu des éléments spécifiés et transmet les objets résultants.|
|`Set-Content`|Remplace le contenu existant pour les éléments spécifiés. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

Le [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface définit un fournisseur Windows PowerShell de propriétés qui effectue des opérations sur les propriétés des éléments dans le magasin de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

> [!NOTE]
> Le `Path` paramètre sur ces applets de commande indique un chemin d’accès à un élément au lieu d’identifier une propriété.

|Applet de commande|Définition|
|------------|----------------|
|`Clear-ItemProperty`|Définit les propriétés des éléments spécifiés à la valeur « effacer ». Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Get-ItemProperty`|Récupère les propriétés d’éléments spécifiés et transmet les objets résultants.|
|`Set-ItemProperty`|Définit les propriétés des éléments spécifiés avec les valeurs indiquées. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

Le [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) interface, dérivée de [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), définit un fournisseur qui spécifie les paramètres dynamiques pour ses applets de commande pris en charge. Ce type de fournisseur gère les opérations dont les propriétés peuvent être définies au moment de l’exécution, par exemple, une nouvelle opération de propriété. Ces opérations ne sont pas possibles sur les éléments ayant des propriétés défini de manière statique. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Copy-ItemProperty`|Copie une propriété à partir de l’élément spécifié dans un autre élément. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`Move-ItemProperty`|Déplace une propriété à partir de l’élément spécifié à un autre élément. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|
|`New-ItemProperty`|Crée une propriété sur les éléments spécifiés et transmet les objets résultants.|
|`Remove-ItemProperty`|Supprime une propriété pour les éléments spécifiés.|
|`Rename-ItemProperty`|Renomme la propriété des éléments spécifiés. Cette applet de commande ne passe pas d’un objet de sortie via le pipeline, sauf si son `PassThru` est précisé.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

Le [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) interface ajoute des fonctionnalités de descripteur de sécurité à un fournisseur. Cette interface permet à l’utilisateur obtenir et définir les informations de descripteur de sécurité pour un élément dans le magasin de données. Le tableau suivant répertorie les applets de commande exposées par cette interface.

|Applet de commande|Définition|
|------------|----------------|
|`Get-Acl`|Récupère les informations contenues dans une liste de contrôle d’accès (ACL), qui fait partie d’un descripteur de sécurité utilisé pour la protection des ressources de système d’exploitation, par exemple, un fichier ou un objet.|
|`Set-Acl`|Définit les informations d’une liste ACL. Il est sous la forme d’une instance de [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) sur l’ou les éléments désigné pour le chemin d’accès spécifié. Cette applet de commande peut définir des informations sur les fichiers, les clés et les sous-clés dans le Registre, ou tout autre élément de fournisseur, si le fournisseur Windows PowerShell prend en charge le paramètre d’informations de sécurité.|

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Fonctionnement de Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)