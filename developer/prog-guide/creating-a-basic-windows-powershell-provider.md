---
title: Création d’un fournisseur PowerShell de base Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 5ebc22067b20f0e1d35d31d5f33e599f50cb7564
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855064"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Création d’un fournisseur Windows PowerShell de base

Cette rubrique est le point de départ pour apprendre à créer un fournisseur Windows PowerShell. Le fournisseur de base décrit ici fournit des méthodes pour démarrer et arrêter le fournisseur, et bien que ce fournisseur ne fournit pas un moyen pour accéder à un magasin de données ou à obtenir ou définir les données dans le magasin de données, il ne fournit les fonctionnalités de base qui sont requis par tous les fournisseurs.

Comme mentionné précédemment, le fournisseur de base décrit ici implémente des méthodes pour démarrer et arrêter le fournisseur. Le runtime de Windows PowerShell appelle ces méthodes pour initialiser et annuler l’initialisation du fournisseur.

> [!NOTE]
> Vous trouverez un exemple de ce fournisseur dans le fichier AccessDBSampleProvider01.cs fourni par Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>Définition de la classe de fournisseur PowerShell Windows

La première étape de création d’un fournisseur Windows PowerShell consiste à définir sa classe .NET. Ce fournisseur de base définit une classe appelée `AccessDBProvider` qui dérive de la [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe de base.

Il est recommandé de placer vos classes de fournisseur dans un `Providers` espace de noms de votre espace de noms API, par exemple, xxx. PowerShell.Providers. Ce fournisseur utilise le `Microsoft.Samples.PowerShell.Provider` espace de noms dans lequel s’exécutent tous les exemples de fournisseurs de Windows PowerShell.

> [!NOTE]
> La classe pour un fournisseur Windows PowerShell doit être explicitement marquée comme étant publique. Classes ne pas marquées comme publique seront internes par défaut et seront introuvable par le runtime de Windows PowerShell.

Voici la définition de classe pour ce fournisseur de base :

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Juste avant la définition de classe, vous devez déclarer le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut, avec la syntaxe [CmdletProvider()].

Vous pouvez définir des mots clés des attributs pour déclarer plus de la classe si nécessaire. Notez que le [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut déclaré ici inclut deux paramètres. Le premier paramètre d’attribut spécifie le nom convivial de la valeur par défaut pour le fournisseur, l’utilisateur peut modifier ultérieurement. Le deuxième paramètre spécifie les fonctions définies par Windows PowerShell que le fournisseur expose à l’exécution de Windows PowerShell au cours du traitement de commande. Les valeurs possibles pour les fonctionnalités de fournisseur sont définies par le [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Comme il s’agit d’un fournisseur de base, il prend en charge aucune fonctionnalité.

> [!NOTE]
> Le nom qualifié complet du fournisseur Windows PowerShell inclut le nom d’assembly et d’autres attributs déterminés par Windows PowerShell une fois l’inscription du fournisseur.

## <a name="defining-provider-specific-state-information"></a>Définition des informations d’état spécifique au fournisseur

Le [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe de base et toutes les classes dérivées font sans état, car le runtime Windows PowerShell crée des instances de fournisseur uniquement en fonction des besoins. Par conséquent, si votre fournisseur requiert un contrôle total et la maintenance d’état pour les données spécifiques au fournisseur, elle doit dériver une classe à partir de la [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) classe. Votre classe dérivée doit définir les membres nécessaires pour maintenir l’état afin que les données spécifiques au fournisseur sont accessibles lors de l’exécution de Windows PowerShell appelle le [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode pour initialiser le fournisseur.

Un fournisseur Windows PowerShell peut également conserver état basée sur la connexion. Pour plus d’informations sur la gestion de l’état de connexion, consultez [création d’un fournisseur de lecteur PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>L’initialisation du fournisseur

Pour initialiser le fournisseur, le runtime de Windows PowerShell appelle le [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode au démarrage de Windows PowerShell. La plupart du temps, votre fournisseur peut utiliser l’implémentation par défaut de cette méthode, qui renvoie simplement le [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objet qui décrit votre fournisseur. Toutefois, dans le cas où vous souhaitez ajouter les informations d’initialisation supplémentaires, vous devez implémenter votre propre [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode qui retourne une version modifiée de la [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objet qui est passé à votre fournisseur. En règle générale, cette méthode doit retourner le texte fourni [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objet passé ou modifiée [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objet contient d’autres informations d’initialisation.

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant montre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Le fournisseur peut maintenir l’état des informations propres au fournisseur comme décrit dans [état des données spécifiques au fournisseur définition](#defining-provider-specific-state-information). Dans ce cas, votre implémentation doit remplacer le [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode pour retourner une instance de la classe dérivée.

## <a name="start-dynamic-parameters"></a>Démarrer des paramètres dynamiques

Votre implémentation de fournisseur de la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) méthode peut nécessiter des paramètres supplémentaires. Dans ce cas, le fournisseur doit remplacer le [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) (méthode) et retourner un objet qui a les propriétés et champs avec l’analyse des attributs similaires à un classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet.

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant montre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Annulation de l’initialisation du fournisseur

Pour libérer des ressources qui utilise le fournisseur Windows PowerShell, votre fournisseur doit implémenter son propre [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) (méthode). Cette méthode est appelée par l’exécution de Windows PowerShell pour annuler l’initialisation du fournisseur à la fin d’une session.

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant montre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Exemple de code

Pour l’exemple de code complet, consultez [exemple de Code AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur PowerShell de Windows

Une fois que votre fournisseur de Windows PowerShell a été enregistré avec Windows PowerShell, vous pouvez le tester en exécutant les applets de commande pris en charge sur la ligne de commande. Pour ce fournisseur de base, exécutez le nouveau shell et utiliser le `Get-PSProvider` applet de commande pour récupérer la liste des fournisseurs et vous assurer que le fournisseur AccessDb est présent.

```powershell
Get-PSProvider
```

La sortie suivante apparaît :

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Voir aussi

[Création de fournisseurs de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception de votre fournisseur de PowerShell Windows](./designing-your-windows-powershell-provider.md)