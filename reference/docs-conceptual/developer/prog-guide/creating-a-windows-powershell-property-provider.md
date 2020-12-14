---
ms.date: 09/13/2016
ms.topic: reference
title: Création d’un fournisseur de propriété Windows PowerShell
description: Création d’un fournisseur de propriété Windows PowerShell
ms.openlocfilehash: 5370624afa784598ca784b201f7e7345eb958ff9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "94390913"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Création d’un fournisseur de propriété Windows PowerShell

Cette rubrique explique comment créer un fournisseur qui permet à l’utilisateur de manipuler les propriétés des éléments d’un magasin de données. Par conséquent, ce type de fournisseur est appelé fournisseur de propriétés Windows PowerShell. Par exemple, le fournisseur de registre fourni par Windows PowerShell gère les valeurs de clé de registre en tant que propriétés de l’élément de clé de registre. Ce type de fournisseur doit ajouter l’interface [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) à l’implémentation de la classe .net.

> [!NOTE]
> Windows PowerShell fournit un fichier de modèle que vous pouvez utiliser pour développer un fournisseur Windows PowerShell. Le fichier TemplateProvider.cs est disponible sur le kit de développement logiciel (SDK) Microsoft Windows pour les composants d’exécution de Windows Vista et .NET Framework 3,0. Pour obtenir des instructions de téléchargement, consultez [Comment installer Windows PowerShell et télécharger le kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Le modèle téléchargé est disponible dans le **\<PowerShell Samples>** répertoire. Vous devez effectuer une copie de ce fichier et utiliser la copie pour créer un nouveau fournisseur Windows PowerShell, en supprimant toutes les fonctionnalités dont vous n’avez pas besoin. Pour plus d’informations sur les autres implémentations du fournisseur Windows PowerShell, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Les méthodes de votre fournisseur de propriétés doivent écrire tous les objets à l’aide de la méthode [System. Management. Automation. Provider. Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>Définition du fournisseur Windows PowerShell

Un fournisseur de propriétés doit créer une classe .NET qui prend en charge l’interface [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) . Voici la déclaration de classe par défaut du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Définition des fonctionnalités de base

L’interface [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) peut être attachée à l’une des classes de base du fournisseur, à l’exception de la classe [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Ajoutez la fonctionnalité de base requise par la classe de base que vous utilisez. Pour plus d’informations sur les classes de base, consultez [conception de votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Récupération de propriétés

Pour récupérer des propriétés, le fournisseur doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) pour prendre en charge les appels de l’applet de commande `Get-ItemProperty` . Cette méthode récupère les propriétés de l’élément situé dans le chemin d’accès interne au fournisseur spécifié (qualifié complet).

Le `providerSpecificPickList` paramètre indique les propriétés à récupérer. Si ce paramètre est `null` ou vide, la méthode doit récupérer toutes les propriétés. En outre, [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) écrit une instance d’un objet [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) qui représente un conteneur de propriétés des propriétés récupérées. La méthode ne doit retourner rien.

Il est recommandé que l’implémentation de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) prenne en charge l’expansion de caractères génériques des noms de propriétés pour chaque élément de la liste de choix. Pour ce faire, utilisez la classe [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) pour effectuer la correspondance de modèle de caractère générique.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Points à retenir concernant l’implémentation de GetProperty

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Lors de la définition de la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true` . Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false` .

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Get-ItemProperty

L' `Get-ItemProperty` applet de commande peut nécessiter des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) . Le `path` paramètre indique un chemin d’accès interne au fournisseur complet, tandis que le `providerSpecificPickList` paramètre spécifie les propriétés spécifiques au fournisseur entrées sur la ligne de commande. Ce paramètre peut être `null` ou vide si les propriétés sont dirigées vers l’applet de commande. Dans ce cas, cette méthode retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Le runtime Windows PowerShell utilise l’objet retourné pour ajouter les paramètres à l’applet de commande.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Définition de propriétés

Pour définir des propriétés, le fournisseur de propriétés Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) pour prendre en charge les appels à partir de l’applet de commande `Set-ItemProperty` . Cette méthode définit une ou plusieurs propriétés de l’élément au niveau du chemin d’accès spécifié, et remplace les propriétés fournies selon les besoins.
[System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) écrit également une instance d’un objet [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) qui représente un conteneur de propriétés des propriétés mises à jour.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Points à retenir concernant l’implémentation de Set-ItemProperty

Les conditions suivantes peuvent s’appliquer à une implémentation de [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Lors de la définition de la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true` . Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false` .

- Votre implémentation de la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération quand une modification est apportée à l’état du système, par exemple, renommer des fichiers.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell et en gérant les paramètres de ligne de commande ou les variables de préférence pour déterminer ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true` , si des modifications du système potentiellement dangereuses peuvent être effectuées, la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message de confirmation à l’utilisateur afin d’autoriser des commentaires supplémentaires pour indiquer que l’opération doit être poursuivie.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Attachement de paramètres dynamiques pour l’applet de commande Set-ItemProperty

L' `Set-ItemProperty` applet de commande peut nécessiter des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) . Cette méthode retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . La `null` valeur peut être retournée si aucun paramètre dynamique ne doit être ajouté.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Effacement des propriétés

Pour effacer les propriétés, le fournisseur de propriétés Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) pour prendre en charge les appels de l’applet de commande `Clear-ItemProperty` . Cette méthode définit une ou plusieurs propriétés pour l’élément situé dans le chemin d’accès spécifié.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>À retenir à propos de l’implémentation de ClearProperty

Les conditions suivantes peuvent s’appliquer à votre implémentation de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Lors de la définition de la classe de fournisseur, un fournisseur de propriétés Windows PowerShell peut déclarer des fonctionnalités de fournisseur de ExpandWildcards, Filter, include ou Exclude, à partir de l’énumération [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dans ces cas, l’implémentation de la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) doit garantir que le chemin d’accès passé à la méthode répond aux exigences des fonctionnalités spécifiées. Pour ce faire, la méthode doit accéder à la propriété appropriée, par exemple, les propriétés [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) et [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- Par défaut, les substitutions de cette méthode ne doivent pas récupérer un lecteur pour les objets qui sont masqués à l’utilisateur, à moins que la propriété [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ait la valeur `true` . Une erreur doit être écrite si le chemin d’accès représente un élément masqué de l’utilisateur et que [System. Management. Automation. Provider. Cmdletprovider. force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) a la valeur `false` .

- Votre implémentation de la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) doit appeler [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) et vérifier sa valeur de retour avant d’apporter des modifications au magasin de données. Cette méthode est utilisée pour confirmer l’exécution d’une opération avant qu’une modification soit apportée à l’état du système, comme l’effacement du contenu.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envoie le nom de la ressource à modifier à l’utilisateur, avec le runtime Windows PowerShell en tenant compte des paramètres de ligne de commande ou des variables de préférence pour déterminer ce qui doit être affiché.

  Une fois que l’appel à [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) retourne `true` , si des modifications du système potentiellement dangereuses peuvent être effectuées, la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) doit appeler la méthode [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Cette méthode envoie un message de confirmation à l’utilisateur afin d’autoriser des commentaires supplémentaires pour indiquer que l’opération potentiellement dangereuse doit être poursuivie.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Attachement de paramètres dynamiques à l’applet de commande Clear-ItemProperty

L' `Clear-ItemProperty` applet de commande peut nécessiter des paramètres supplémentaires spécifiés de manière dynamique au moment de l’exécution. Pour fournir ces paramètres dynamiques, le fournisseur de propriétés Windows PowerShell doit implémenter la méthode [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . Cette méthode retourne un objet qui a des propriétés et des champs avec des attributs d’analyse similaires à une classe d’applet de commande ou à un objet [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . La `null` valeur peut être retournée si aucun paramètre dynamique ne doit être ajouté.

Voici l’implémentation par défaut de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) à partir du fichier TemplateProvider.cs fourni par Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Génération du fournisseur Windows PowerShell

Découvrez [comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85)).

## <a name="see-also"></a>Voir aussi

[fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Concevoir votre fournisseur Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extension des types d’objets et de la mise en forme](/previous-versions//ms714665(v=vs.85))

[Comment inscrire des applets de commande, des fournisseurs et des applications hôtes](/previous-versions//ms714644(v=vs.85))
