---
title: Création d’un fournisseur de propriété PowerShell Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081833"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Création d’un fournisseur de propriété Windows PowerShell

Cette rubrique décrit comment créer un fournisseur qui permet à l’utilisateur de manipuler les propriétés des éléments dans un magasin de données. Par conséquent, ce type de fournisseur est appelé un fournisseur de propriétés Windows PowerShell. Par exemple, le fournisseur de Registre fourni par les valeurs de clé de Registre Windows PowerShell gère en tant que propriétés de l’élément clé de Registre. Ce type de fournisseur doit ajouter la [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface à l’implémentation de la classe .NET.

> [!NOTE]
> Windows PowerShell fournit un fichier de modèle que vous pouvez utiliser pour développer un fournisseur Windows PowerShell. Le fichier TemplateProvider.cs est disponible sur le Microsoft Windows Software Development Kit pour Windows Vista et les composants d’exécution .NET Framework 3.0. Pour obtenir des instructions de téléchargement, consultez [comment PowerShell de Windows Installer et de télécharger le Kit de développement logiciel de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Le modèle téléchargé est disponible dans le  **\<exemples PowerShell >** directory. Vous devez effectuer une copie de ce fichier et utiliser la copie pour la création d’un nouveau fournisseur Windows PowerShell, en supprimant toutes les fonctionnalités que vous n’avez pas besoin.
>
> Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Les méthodes de votre fournisseur de propriétés doivent écrire tous les objets à l’aide de la [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) (méthode).

La liste suivante contient les sections de cette rubrique. Si vous n’êtes pas familiarisé avec l’écriture d’un fournisseur de propriétés Windows PowerShell, lire ces informations dans l’ordre dans lequel elle apparaît. Toutefois, si vous êtes familiarisé avec l’écriture d’un fournisseur de propriétés Windows PowerShell, accédez directement aux informations dont vous avez besoin.

- [Définir le fournisseur PowerShell Windows](#Defining-the-Windows-PowerShell-provider)

- [Définition des fonctionnalités de Base](#Defining-Base-Functionality)

- [Récupération des propriétés](#Retrieving-Properties)

- [Attachement des paramètres dynamiques à la `Get-ItemProperty` applet de commande](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Définition des propriétés](#Setting-Properties)

- [Attachement des paramètres dynamiques à la `Set-ItemProperty` applet de commande](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Effacement d’une propriété](#Clearing-Properties)

- [Attachement des paramètres dynamiques à la `Clear-ItemProperty` applet de commande](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Construction du fournisseur PowerShell de Windows](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Définir le fournisseur Windows PowerShell

Un fournisseur de propriétés doit créer une classe .NET qui prend en charge la [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface. Voici la déclaration de classe par défaut à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de Base

Le [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interface peut être attachée à toutes les classes de base du fournisseur, à l’exception de la [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Ajouter les fonctionnalités de base qui sont requis par la classe de base que vous utilisez. Pour plus d’informations sur les classes de base, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Récupération des propriétés

Pour récupérer les propriétés, le fournisseur doit implémenter la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) méthode pour prendre en charge les appels à partir de la `Get-ItemProperty` applet de commande. Cette méthode récupère les propriétés de l’élément situé dans le chemin d’accès interne de fournisseur spécifié (complet).

Le `providerSpecificPickList` paramètre indique les propriétés à récupérer. Si ce paramètre est `null` ou vide, la méthode doit récupérer toutes les propriétés. En outre, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) écrit une instance d’un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objet qui représente un sac de propriétés récupérées. La méthode doit renvoyer aucun résultat.

Il est recommandé que l’implémentation de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) prend en charge le développement des caractères génériques de noms de propriétés pour chaque élément dans la liste de choix. Pour ce faire, utilisez le [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) classe pour effectuer le filtrage des caractères génériques.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Points à retenir sur l’implémentation GetProperty

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Get-ItemProperty

Le `Get-ItemProperty` applet de commande peut-être nécessiter des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) (méthode). Le `path` paramètre indique un complet interne de fournisseur de chemin d’accès, tandis que le `providerSpecificPickList` paramètre spécifie les propriétés spécifiques au fournisseur entrées sur la ligne de commande. Ce paramètre peut être `null` ou vide si les propriétés sont dirigées vers l’applet de commande. Dans ce cas, cette méthode retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Définition des propriétés

Pour définir les propriétés, le fournisseur de propriétés Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) méthode pour prendre en charge les appels à partir de la `Set-ItemProperty` applet de commande. Cette méthode définit une ou plusieurs propriétés de l’élément dans le chemin spécifié et remplace les propriétés fournies en fonction des besoins. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) également écrit une instance d’un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objet qui représente un jeu de propriétés de la mise à jour Propriétés.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Points à retenir sur l’implémentation de Set-ItemProperty

Les conditions suivantes peuvent s’appliquer à une implémentation de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) méthode devez vous assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

- Votre implémentation de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération lorsqu’une modification est apportée à l’état du système, par exemple, renommer les fichiers. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell et de gérer les paramètres de ligne de commande ou les variables de préférence dans la détermination ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, si vous pouvez apporter des modifications de système potentiellement dangereux, les [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message de confirmation à l’utilisateur pour que les commentaires supplémentaires indiquer que l’opération doit être poursuivie.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Attachement des paramètres dynamiques pour l’applet de commande Set-ItemProperty

Le `Set-ItemProperty` applet de commande peut-être nécessiter des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) (méthode). Cette méthode retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le `null` valeur peut être retournée si aucun des paramètres dynamiques ne doivent être ajoutées.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Propriétés de l’effacement

Pour effacer les propriétés, le fournisseur de propriétés Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) méthode pour prendre en charge les appels à partir de la `Clear-ItemProperty` applet de commande. Cette méthode définit une ou plusieurs propriétés de l’élément situé dans le chemin d’accès spécifié.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Point à retenir sur l’implémentation ClearProperty

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Lorsque vous définissez la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des capacités du fournisseur de ExpandWildcards, filtre, Include ou Exclude, à partir de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) énumération. Dans ce cas, l’implémentation de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) méthode doit s’assurer que le chemin d’accès transmis à la méthode remplit les conditions de l’élément spécifié fonctionnalités. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, le [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propriétés.

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à partir de l’utilisateur, sauf si le [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propriété est définie sur `true`. Une erreur doit être écrits si le chemin d’accès représente un élément est masqué pour l’utilisateur et [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) est défini sur `false`.

- Votre implémentation de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) méthode doit appeler [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération avant une modification est apportée à l’état du système, telles que l’effacement du contenu. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime de Windows PowerShell en prenant en compte les paramètres de ligne de commande ou les variables de préférence dans déterminer ce qui doit être affiché.

  Après l’appel à [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true`, si vous pouvez apporter des modifications de système potentiellement dangereux, les [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) méthode doit appeler la [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (méthode). Cette méthode envoie un message de confirmation à l’utilisateur pour que les commentaires supplémentaires indiquer que l’opération potentiellement dangereuse doit être poursuivie.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Attachement des paramètres dynamiques à l’applet de commande Clear-ItemProperty

Le `Clear-ItemProperty` applet de commande peut-être nécessiter des paramètres supplémentaires qui sont spécifiés de manière dynamique lors de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter le [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) (méthode). Cette méthode retourne un objet qui a les propriétés et champs avec l’analyse des attributs similaires à une classe de l’applet de commande ou un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objet. Le `null` valeur peut être retournée si aucun des paramètres dynamiques ne doivent être ajoutées.

Voici l’implémentation par défaut de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Construction du fournisseur Windows PowerShell

Consultez [comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Voir aussi

[Fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Fournisseur de votre Windows PowerShell de conception](./designing-your-windows-powershell-provider.md)

[Extension des Types d’objets et mise en forme](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Comment inscrire les applets de commande, fournisseurs et héberger des Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)