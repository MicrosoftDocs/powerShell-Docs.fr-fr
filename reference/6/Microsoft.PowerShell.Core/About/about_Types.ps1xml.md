---
description: Explique comment utiliser `Types.ps1xml` des fichiers pour étendre les types d’objets utilisés dans PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1xml
ms.openlocfilehash: 6b150626f41b61d4e91f20e7d5e93af04298369c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206829"
---
# <a name="about-typesps1xml"></a>À propos de Types.ps1XML

## <a name="short-description"></a>Description courte
Explique comment utiliser `Types.ps1xml` des fichiers pour étendre les types d’objets utilisés dans PowerShell.

## <a name="long-description"></a>Description longue

Les données de type étendus définissent des propriétés et des méthodes supplémentaires (« membres ») des types d’objets dans PowerShell. Il existe deux techniques pour ajouter des données de type étendu à une session PowerShell.

- `Types.ps1xml` fichier : fichier XML qui définit les données de type étendu.
- `Update-TypeData`: Applet de commande qui recharge des `Types.ps1xml` fichiers et définit des données étendues pour les types de la session active.

Cette rubrique décrit les `Types.ps1xml` fichiers. Pour plus d’informations sur l’utilisation `Update-TypeData` de l’applet de commande pour ajouter des données de type étendu dynamique à la session active [, consultez Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).

## <a name="about-extended-type-data"></a>À propos des données de type étendu

Les données de type étendus définissent des propriétés et des méthodes supplémentaires (« membres ») des types d’objets dans PowerShell. Vous pouvez étendre n’importe quel type pris en charge par PowerShell et utiliser les propriétés et les méthodes ajoutées de la même façon que vous utilisez les propriétés définies sur les types d’objets.

Par exemple, PowerShell ajoute une propriété **DateTime** à tous les `System.DateTime` objets, tels que ceux que l' `Get-Date` applet de commande retourne.

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

Vous ne trouverez pas la propriété **DateTime** dans la description de la structure [System. DateTime](/dotnet/api/system.datetime) , car PowerShell ajoute la propriété et n’est visible que dans PowerShell.

PowerShell définit en interne un ensemble de types étendus par défaut. Ces informations de type sont chargées dans chaque session PowerShell au démarrage. La propriété **DateTime** fait partie de cet ensemble par défaut. Avant PowerShell 6, les définitions de type étaient stockées `Types.ps1xml` dans le répertoire d’installation de PowerShell ( `$PSHOME` ).

## <a name="adding-extended-type-data-to-powershell"></a>Ajout de données de type étendu à PowerShell

Il existe trois sources de données de type étendu dans les sessions PowerShell.

- Le défini par PowerShell et est chargé automatiquement dans chaque session PowerShell. À partir de PowerShell 6, ces informations sont compilées dans PowerShell et ne sont plus fournies dans un `Types.ps1xml` fichier.

- Les `Types.ps1xml` fichiers que les modules exportent sont chargés quand le module est importé dans la session active.

- Les données de type étendu qui sont définies à l’aide de l' `Update-TypeData` applet de commande sont ajoutées uniquement à la session active. Il n’est pas enregistré dans un fichier.

Dans la session, les données de type étendu des trois sources sont appliquées aux objets de la même façon et sont disponibles sur tous les objets des types spécifiés.

## <a name="the-typedata-cmdlets"></a>Applets de commande TypeData

Les applets de commande suivantes sont incluses dans le module **Microsoft. PowerShell. Utility** dans PowerShell 3,0 et versions ultérieures.

- `Get-TypeData`: Obtient les données de type étendu dans la session active.
- `Update-TypeData`: Recharge les `Types.ps1xml` fichiers. Ajoute des données de type étendu à la session active.
- `Remove-TypeData`: Supprime les données de type étendu de la session active.

Pour plus d’informations sur ces applets de commande, consultez la rubrique d’aide pour chaque applet de commande.

## <a name="built-in-typesps1xml-files"></a>Fichiers XML Types.ps1intégrés

Les `Types.ps1xml` fichiers du `$PSHOME` répertoire sont ajoutés automatiquement à chaque session.

Le `Types.ps1xml` fichier dans le répertoire d’installation de PowerShell ( `$PSHOME` ) est un fichier texte basé sur XML qui vous permet d’ajouter des propriétés et des méthodes aux objets utilisés dans PowerShell. PowerShell contient des fichiers intégrés `Types.ps1xml` qui ajoutent plusieurs éléments aux types .net, mais vous pouvez créer des `Types.ps1xml` fichiers supplémentaires pour étendre davantage les types.

Par exemple, par défaut, les objets de tableau ( `System.Array` ) ont une propriété **Length** qui indique le nombre d’objets dans le tableau. Toutefois, étant donné que la **longueur** du nom ne décrit pas clairement la propriété, PowerShell ajoute une propriété d’alias **Count nommée Count** qui affiche la même valeur. Le code XML suivant ajoute la propriété **Count** au `System.Array` type.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

Pour obtenir le nouvel **AliasProperty** , utilisez une `Get-Member` commande sur n’importe quel tableau, comme indiqué dans l’exemple suivant.

```powershell
Get-Member -InputObject (1,2,3,4)
```

La commande retourne les résultats suivants.

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

Par conséquent, vous pouvez utiliser la propriété **Count** ou la propriété **Length** des tableaux dans PowerShell. Par exemple :

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a>Création de fichiers XML Types.ps1

Les `.ps1xml` fichiers qui sont installés avec PowerShell sont signés numériquement pour empêcher la falsification, car la mise en forme peut inclure des blocs de script. Par conséquent, pour ajouter une propriété ou une méthode à un type .NET, créez vos propres `Types.ps1xml` fichiers, puis ajoutez-les à votre session PowerShell.

Pour créer un nouveau fichier, commencez par copier un `Types.ps1xml` fichier existant. Le nouveau fichier peut avoir n’importe quel nom, mais il doit avoir une `.ps1xml` extension de nom de fichier. Vous pouvez placer le nouveau fichier dans n’importe quel répertoire accessible à PowerShell, mais il est utile de placer les fichiers dans le répertoire d’installation de PowerShell ( `$PSHOME` ) ou dans un sous-répertoire du répertoire d’installation.

Une fois que vous avez enregistré le nouveau fichier, utilisez l' `Update-TypeData` applet de commande pour ajouter le nouveau fichier à votre session PowerShell. Si vous souhaitez que vos types aient la priorité sur les types intégrés définis, utilisez le paramètre **PrependData** de l’applet de commande `Update-TypeData` . `Update-TypeData` affecte uniquement la session active. Pour apporter la modification à toutes les sessions ultérieures, exportez la console ou ajoutez la `Update-TypeData` commande à votre profil PowerShell.

## <a name="typesps1xml-and-add-member"></a>Types.ps1XML et Add-Member

Les `Types.ps1xml` fichiers ajoutent des propriétés et des méthodes à toutes les instances des objets du type .net spécifié dans la session PowerShell concernée. Toutefois, si vous devez ajouter des propriétés ou des méthodes uniquement à une instance d’un objet, utilisez l’applet de commande `Add-Member` .

Pour plus d’informations, consultez [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a>Exemple : ajout d’un membre Age à des objets FileInfo

Cet exemple montre comment ajouter une propriété **Age** aux objets **System. IO. FileInfo** . L’ancienneté d’un fichier correspond à la différence entre son heure de création et l’heure actuelle en jours.

Étant donné que la propriété **Age** est calculée à l’aide d’un bloc de script, recherchez une `<ScriptProperty>` balise à utiliser comme modèle pour la nouvelle propriété **Age** .

Enregistrez le code XML suivant dans le fichier `$PSHOME\MyTypes.ps1xml` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

Exécutez `Update-TypeData` pour ajouter le nouveau `Types.ps1xml` fichier à la session active. La commande utilise le paramètre **PrependData** pour placer le nouveau fichier dans un ordre de priorité plus élevé que les définitions d’origine.

Pour plus d’informations sur `Update-TypeData` , voir [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

Pour tester la modification, exécutez une `Get-ChildItem` commande pour obtenir le PowerShell.exe fichier dans le `$PSHOME` répertoire, puis dirigez le fichier vers l' `Format-List` applet de commande pour répertorier toutes les propriétés du fichier. Suite à la modification, la propriété **Age** apparaît dans la liste.

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a>XML dans Types.ps1fichiers XML

La définition de schéma complète se trouve dans [types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) dans le référentiel de code source PowerShell sur GitHub.

La `<Types>` balise englobe tous les types définis dans le fichier. Il ne doit y avoir qu’une seule `<Types>` balise.

Chaque type .NET mentionné dans le fichier doit être représenté par une `<Type>` balise.

Les balises de type doivent contenir les balises suivantes :

`<Name>`: Encadre le nom du type .NET affecté.

`<Members>`: Encadre les balises pour les nouvelles propriétés et méthodes définies pour le type .NET.

Les balises de membre suivantes peuvent se trouver à l’intérieur de la `<Members>` balise.

`<AliasProperty>`: Définit un nouveau nom pour une propriété existante.

La `<AliasProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<ReferencedMemberName>` balise qui spécifie la propriété existante.

Par exemple, la propriété **Count** alias est un alias pour la propriété **Length** des objets Array.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

`<CodeMethod>`: Référence une méthode statique d’une classe .NET.

La `<CodeMethod>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle méthode et une `<GetCodeReference>` balise qui spécifie le code dans lequel la méthode est définie.

Par exemple, la propriété **mode** d' `System.IO.DirectoryInfo` objets est une propriété de code définie dans le fournisseur de système de fichiers PowerShell.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<CodeProperty>`: Référence une méthode statique d’une classe .NET.

La `<CodeProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<GetCodeReference>` balise qui spécifie le code dans lequel la propriété est définie.

Par exemple, la propriété **mode** d' `System.IO.DirectoryInfo` objets est une propriété de code définie dans le fournisseur de système de fichiers PowerShell.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<MemberSet>`: Définit une collection de membres (propriétés et méthodes).

Les `<MemberSet>` balises apparaissent dans les `<Members>` balises primaires. Les balises doivent contenir une `<Name>` balise entourant le nom de l’ensemble de membres et une `<Members>` balise secondaire qui entoure les membres (propriétés et méthodes) dans le jeu. Les balises qui créent une propriété (telle que `<NoteProperty>` ou `<ScriptProperty>` ) ou une méthode (telle que `<Method>` ou `<ScriptMethod>` ) peuvent être membres du jeu.

Dans `Types.ps1xml` les fichiers, la `<MemberSet>` balise est utilisée pour définir les vues par défaut des objets .net dans PowerShell. Dans ce cas, le nom du jeu de membres (la valeur dans les `<Name>` balises) est toujours **PsStandardMembers** et les noms des propriétés (la valeur de la `<Name>` balise) sont l’un des éléments suivants :

- `DefaultDisplayProperty`: Propriété unique d’un objet.

- `DefaultDisplayPropertySet`: Une ou plusieurs propriétés d’un objet.

- `DefaultKeyPropertySet`: Une ou plusieurs propriétés clés d’un objet. Une propriété de clé identifie des instances de valeurs de propriété, telles que le nombre d’ID d’éléments dans un historique de session.

Par exemple, le code XML suivant définit l’affichage par défaut des services ( `System.ServiceProcess.ServiceController` objets) retournés par l’applet de commande `Get-Service` . Il définit un jeu de membres nommé **PsStandardMembers** qui se compose d’une propriété par défaut définie avec les propriétés **Status** , **Name** et **DisplayName** .

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<Method>`: Référence une méthode native de l’objet sous-jacent.

`<Methods>`: Collection des méthodes de l’objet.

`<NoteProperty>`: Définit une propriété avec une valeur statique.

La `<NoteProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<Value>` balise qui spécifie la valeur de la propriété.

Par exemple, le code XML suivant crée une propriété **Status** pour les objets **System. IO. DirectoryInfo** . La valeur de la propriété **Status** est toujours **Success** .

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

`<ParameterizedProperty>`: Les propriétés qui acceptent des arguments et retournent une valeur.

`<Properties>`: Collection des propriétés de l’objet.

`<Property>`: Propriété de l’objet de base.

`<PropertySet>`: Définit une collection de propriétés de l’objet.

La `<PropertySet>` balise doit avoir une `<Name>` balise qui spécifie le nom du jeu de propriétés et une `<ReferencedProperty>` étiquette qui spécifie les propriétés. Les noms des propriétés sont placés dans la `<Name>` balise.

Dans `Types.ps1xml` , les `<PropertySet>` balises sont utilisées pour définir des ensembles de propriétés pour l’affichage par défaut d’un objet. Vous pouvez identifier la valeur par défaut affichée par la valeur **PsStandardMembers** dans la `<Name>` balise d’une `<MemberSet>` balise.

Par exemple, le code XML suivant crée une propriété **Status** pour l' `System.IO.DirectoryInfo` objet. La valeur de la propriété **Status** est toujours **Success** .

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<ScriptMethod>`: Définit une méthode dont la valeur est la sortie d’un script.

La `<ScriptMethod>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle méthode et une `<Script>` balise qui encadre le bloc de script qui retourne le résultat de la méthode.

Par exemple, les `ConvertToDateTime` `ConvertFromDateTime` méthodes et de Management Objects ( `System.System.Management.ManagementObject` ) sont des méthodes de script qui utilisent les `ToDateTime` `ToDmtfDateTime` méthodes statiques et de la `System.Management.ManagementDateTimeConverter` classe.

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

`<ScriptProperty>`: Définit une propriété dont la valeur est la sortie d’un script.

La `<ScriptProperty>` balise doit avoir une `<Name>` balise qui spécifie le nom de la nouvelle propriété et une `<GetScriptBlock>` balise qui encadre le bloc de script qui retourne la valeur de la propriété.

Par exemple, la **propriété VERSIONINFO** de l' **objet System. IO. FileInfo** est une propriété de script qui résulte de l’utilisation de la propriété **FullName** de la méthode statique **GetVersionInfo** des objets **System. Diagnostics. FileVersionInfo** .

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

Pour plus d’informations, consultez le [Kit de développement logiciel (SDK) Windows PowerShell](/powershell/scripting/developer/windows-powershell).

## <a name="update-typedata"></a>Update-TypeData

Pour charger vos `Types.ps1xml` fichiers dans une session PowerShell, exécutez l' `Update-TypeData` applet de commande. Si vous souhaitez que les types de votre fichier aient la priorité sur les types dans le `Types.ps1xml` fichier intégré, ajoutez le paramètre **PrependData** de `Update-TypeData` . `Update-TypeData` affecte uniquement la session active. Pour apporter la modification à toutes les sessions ultérieures, exportez la session ou ajoutez la `Update-TypeData` commande à votre profil PowerShell.

Les exceptions qui se produisent dans les propriétés, ou à partir de l’ajout de propriétés à une `Update-TypeData` commande, ne signalent pas les erreurs à `StdErr` . Cela permet de supprimer des exceptions qui se produisent dans de nombreux types courants durant la mise en forme et la sortie. Si vous obtenez des propriétés .NET, vous pouvez contourner la suppression des exceptions en utilisant la syntaxe de méthode à la place, comme indiqué dans l’exemple suivant :

```powershell
"hello".get_Length()
```

Notez que la syntaxe de méthode peut uniquement être utilisée avec des propriétés .NET. Les propriétés ajoutées en exécutant l’applet de commande `Update-TypeData` ne peuvent pas utiliser la syntaxe de méthode.

## <a name="signing-a-typesps1xml-file"></a>Signature d’un fichier XML Types.ps1

Pour protéger les utilisateurs de votre `Types.ps1xml` fichier, vous pouvez signer le fichier à l’aide d’une signature numérique. Pour plus d’informations, consultez [about_Signing](about_Signing.md).

## <a name="see-also"></a>Voir aussi

[about_Signing](about_Signing.md)

[Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)

[Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member)

[Get-TypeData](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[Remove-TypeData](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)
