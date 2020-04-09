---
title: Création d’un fournisseur Windows PowerShell de base | Microsoft Docs
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
ms.openlocfilehash: 0f8621cd22ca402f3a564ccdfb36c97da68dac6a
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978506"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Création d’un fournisseur Windows PowerShell de base

Cette rubrique est le point de départ pour apprendre à créer un fournisseur Windows PowerShell. Le fournisseur de base décrit ici fournit des méthodes pour démarrer et arrêter le fournisseur, et bien que ce fournisseur ne fournisse pas de moyen d’accéder à un magasin de données ou d’obtenir ou de définir les données dans le magasin de données, il fournit les fonctionnalités de base requises par tous les fournisseurs.

Comme mentionné précédemment, le fournisseur de base décrit ici implémente des méthodes pour démarrer et arrêter le fournisseur. Le runtime Windows PowerShell appelle ces méthodes pour initialiser et désinitialiser le fournisseur.

> [!NOTE]
> Vous trouverez un exemple de ce fournisseur dans le fichier AccessDBSampleProvider01.cs fourni par Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>Définition de la classe de fournisseur Windows PowerShell

La première étape de la création d’un fournisseur Windows PowerShell consiste à définir sa classe .NET. Ce fournisseur de base définit une classe appelée `AccessDBProvider` qui dérive de la classe de base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

Il est recommandé de placer vos classes de fournisseur dans un espace de noms `Providers` de votre espace de noms d’API, par exemple, xxx. PowerShell. Providers. Ce fournisseur utilise l’espace de noms `Microsoft.Samples.PowerShell.Provider` dans lequel tous les exemples du fournisseur Windows PowerShell s’exécutent.

> [!NOTE]
> La classe d’un fournisseur Windows PowerShell doit être explicitement marquée comme publique. Les classes qui ne sont pas marquées comme étant publiques seront par défaut internes et ne seront pas trouvées par le runtime Windows PowerShell.

Voici la définition de classe pour ce fournisseur de base :

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="23-24":::

Juste avant la définition de classe, vous devez déclarer l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , avec la syntaxe [CmdletProvider ()].

Vous pouvez définir des mots clés d’attribut pour déclarer davantage la classe si nécessaire. Notez que l’attribut [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) déclaré ici comprend deux paramètres. Le premier paramètre d’attribut spécifie le nom convivial par défaut du fournisseur, que l’utilisateur peut modifier par la suite. Le deuxième paramètre spécifie les fonctionnalités définies par Windows PowerShell que le fournisseur expose au runtime Windows PowerShell pendant le traitement de la commande. Les valeurs possibles pour les fonctionnalités du fournisseur sont définies par l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Comme il s’agit d’un fournisseur de base, il ne prend en charge aucune fonctionnalité.

> [!NOTE]
> Le nom qualifié complet du fournisseur Windows PowerShell comprend le nom de l’assembly et d’autres attributs déterminés par Windows PowerShell lors de l’inscription du fournisseur.

## <a name="defining-provider-specific-state-information"></a>Définition des informations d’État spécifiques au fournisseur

La classe de base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) et toutes les classes dérivées sont considérées comme sans État, car le runtime Windows PowerShell ne crée des instances de fournisseur que si nécessaire. Par conséquent, si votre fournisseur requiert un contrôle total et une maintenance de l’État pour les données spécifiques au fournisseur, il doit dériver une classe de la classe [System. Management. Automation. providerinfo retourné par](/dotnet/api/System.Management.Automation.ProviderInfo) . Votre classe dérivée doit définir les membres nécessaires pour maintenir l’État afin que les données spécifiques au fournisseur soient accessibles lorsque le runtime Windows PowerShell appelle la méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) pour initialiser le fournisseur.

Un fournisseur Windows PowerShell peut également conserver un État basé sur la connexion. Pour plus d’informations sur la gestion de l’état de la connexion, consultez [création d’un fournisseur de lecteurs PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Initialisation du fournisseur

Pour initialiser le fournisseur, le runtime Windows PowerShell appelle la méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) au démarrage de Windows PowerShell. Pour l’essentiel, votre fournisseur peut utiliser l’implémentation par défaut de cette méthode, qui retourne simplement l’objet [System. Management. Automation. providerinfo retourné par](/dotnet/api/System.Management.Automation.ProviderInfo) qui décrit votre fournisseur. Toutefois, dans le cas où vous souhaitez ajouter des informations d’initialisation supplémentaires, vous devez implémenter votre propre méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) qui retourne une version modifiée de l’objet [System. Management. Automation. providerinfo retourné par](/dotnet/api/System.Management.Automation.ProviderInfo) transmis à votre fournisseur. En général, cette méthode doit retourner l’objet [System. Management. Automation. providerinfo retourné par](/dotnet/api/System.Management.Automation.ProviderInfo) fourni ou un objet [System. Management. Automation. providerinfo retourné par](/dotnet/api/System.Management.Automation.ProviderInfo) modifié qui contient d’autres informations d’initialisation.

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant illustre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Le fournisseur peut conserver l’état des informations spécifiques au fournisseur, comme décrit dans définition de l' [État des données spécifiques au fournisseur](#defining-provider-specific-state-information). Dans ce cas, votre implémentation doit substituer la méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) pour retourner une instance de la classe dérivée.

## <a name="start-dynamic-parameters"></a>Démarrer les paramètres dynamiques

L’implémentation de votre fournisseur de la méthode [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) peut nécessiter des paramètres supplémentaires. Dans ce cas, le fournisseur doit substituer la méthode [System. Management. Automation. Provider. Cmdletprovider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) et retourner un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant illustre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Désinitialisation du fournisseur

Pour libérer les ressources utilisées par le fournisseur Windows PowerShell, votre fournisseur doit implémenter sa propre méthode [System. Management. Automation. Provider. Cmdletprovider. Stop *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) . Cette méthode est appelée par le runtime Windows PowerShell pour désinitialiser le fournisseur à la fermeture d’une session.

Ce fournisseur de base ne remplace pas cette méthode. Toutefois, le code suivant illustre l’implémentation par défaut de cette méthode :

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Exemple de code

Pour obtenir un exemple de code complet, consultez [exemple de code AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Test du fournisseur Windows PowerShell

Une fois que votre fournisseur Windows PowerShell a été inscrit auprès de Windows PowerShell, vous pouvez le tester en exécutant les applets de commande prises en charge sur la ligne de commande. Pour ce fournisseur de base, exécutez le nouvel interpréteur de commandes et utilisez l’applet de commande `Get-PSProvider` pour récupérer la liste des fournisseurs et vérifier que le fournisseur AccessDb est présent.

```powershell
Get-PSProvider
```

Vous obtenez la sortie suivante :

```Output
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

[Création de fournisseurs Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)
