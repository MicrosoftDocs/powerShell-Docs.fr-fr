---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Ressource File DSC
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077328"
---
# <a name="dsc-file-resource"></a>Ressource File DSC

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

La ressource File dans DSC Windows PowerShell fournit un mécanisme permettant de gérer les fichiers et les dossiers sur un nœud cible. **DestinationPath** et **SourcePath** doivent être accessibles par le nœud cible.

## <a name="syntax"></a>Syntaxe

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Propriétés

|Propriété       |Description                                                                   |Obligatoire|Par défaut|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|L’emplacement, sur le nœud cible, qui doit être défini sur `Present` ou `Absent`.|Oui|Non|
|Attributes     |L’état souhaité des attributs du fichier ou du répertoire cible. Les valeurs valides sont **Archive**, **Hidden**, **ReadOnly** et **System**.|Non|Aucune|
|Checksum      |Le type de somme de contrôle à utiliser pour déterminer si deux fichiers sont identiques. Les valeurs valides sont les suivantes : SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|Non|Seul le nom du fichier ou répertoire est comparé.|
|Contents       |Valide uniquement si utilisé avec le type `File`. Indique que le contenu de la valeur Ensure affiche `Present` ou `Absent` à partir du fichier cible. |Non|Aucune|
|Credential     |Les informations d’identification nécessaires pour accéder aux ressources, telles que des fichiers sources.|Non|Le compte de l’ordinateur du nœud cible. (*voir la remarque*)|
|Ensure         |L’état souhaité du fichier ou répertoire cible. |Non|**Present**|
|Force          |Remplace les opérations d’accès qui entraîneraient une erreur (par exemple, le remplacement d’un fichier ou la suppression d’un répertoire qui n’est pas vide).|Non|`$false`|
|Recurse        |Valide uniquement si utilisé avec le type `Directory`. Exécute l’opération d’état de manière récursive sur tous les sous-répertoires.|Non|`$false`|
|DependsOn      |Définit une dépendance sur les ressources spécifiées. Cette ressource s’exécute uniquement après l’exécution réussie de toutes les ressources dépendantes. Vous pouvez spécifier les ressources dépendantes à l’aide de la syntaxe `"[ResourceType]ResourceName"`. Voir [about_DependsOn](../../../configurations/resource-depends-on.md)|Non|Aucune|
|SourcePath     |Chemin à partir duquel copier la ressource de fichier ou de dossier.|Non|Aucune|
|Type           |Le type de ressource en cours de configuration. Les valeurs valides sont `Directory` et `File`.|Non|`File`|
|MatchSource    |Détermine si la ressource doit contrôler les nouveaux fichiers ajoutés au répertoire source après la copie initiale. La valeur `$true` indique que, après la copie initiale, les nouveaux fichiers source doivent être copiés dans la destination. Si la valeur est définie sur `$False`, la ressource met en cache le contenu du répertoire source et ignore les fichiers ajoutés après la copie initiale.|Non|`$false`|

> [!WARNING]
> Si vous ne spécifiez aucune valeur pour `Credential` ou `PSRunAsCredential` (PS V.5), la ressource utilisera le compte d’ordinateur du nœud cible pour accéder à `SourcePath`.  Si `SourcePath` représente un partage UNC, cela peut entraîner une erreur « Accès refusé ». Vérifiez que vos autorisations sont définies en conséquence, ou utilisez les propriétés `Credential` ou `PSRunAsCredential` pour spécifier le compte qui doit être utilisé.

## <a name="present-vs-absent"></a>Présent / Absent

Chaque ressource DSC effectue des opérations différentes selon la valeur que vous spécifiez pour la propriété `Ensure`. Les valeurs que vous spécifiez pour les propriétés ci-dessus déterminent l’opération d’état effectuée.

### <a name="existence"></a>Existence

Lorsque vous spécifiez uniquement un `DestinationPath`, la ressource s’assure que le chemin d’accès existe (`Present`) ou n’existe pas (`Absent`).

### <a name="copy-operations"></a>Opérations de copie

Lorsque vous spécifiez un `SourcePath` et un `DestinationPath` avec une valeur `Type` comme **Directory**, la ressource copie le répertoire source dans le chemin d’accès de destination. Les propriétés `Recurse`, `Force` et `MatchSource` modifient le type d’opération de copie effectuée, tandis que `Credential` détermine le compte à utiliser pour accéder au répertoire source.

### <a name="limitations"></a>Limitations

Si vous avez spécifié une valeur de `ReadOnly` pour la propriété `Attributes` en même temps qu’un `DestinationPath`, `Ensure = "Present"` crée le chemin d’accès spécifié, tandis que `Contents` définit le contenu du fichier.  Une opération d’état `Absent` ignore entièrement la propriété `Attributes` et supprime tous les fichiers dans le chemin spécifié.

## <a name="example"></a>Exemple

L’exemple suivant copie un répertoire et ses sous-répertoires d’un serveur Pull vers à un nœud cible à l’aide de la ressource File. Si l’opération réussit, la ressource Log consigne un message de confirmation dans le journal des événements.

Le répertoire source est un chemin d’accès UNC (`\\PullServer\DemoSource`) partagé à partir du serveur Pull. La propriété `Recurse` s’assure que tous les sous-répertoires sont également copiés.

> [!IMPORTANT]
> Le gestionnaire de configuration local (LCM) sur le nœud cible s’exécute dans le contexte du compte système local par défaut. Pour autoriser l’accès à **SourcePath**, accordez les autorisations appropriées au compte d’ordinateur du nœud cible. Les deux valeurs **Credential** et **PSDSCRunAsCredential** (v5) modifient le contexte utilisé par le LCM pour accéder à **SourcePath**. Vous devez quand même accorder l’accès au compte qui sera utilisé pour accéder à **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Pour plus d’informations sur l’utilisation de **Credentials** dans DSC, consultez [Run As User](../../../configurations/runAsUser.md) (Exécuter en tant qu’utilisateur) ou [Config Data Credentials](../../../configurations/configDataCredentials.md) (Informations d’identification des données de configuration).
