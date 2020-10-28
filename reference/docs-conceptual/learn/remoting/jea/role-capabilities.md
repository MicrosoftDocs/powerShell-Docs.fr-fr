---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Capacités de rôle JEA
description: Une capacité de rôle est un fichier de données PowerShell avec l’extension .psrc qui liste toutes les applets de commande, toutes les fonctions, tous les fournisseurs et tous les programmes externes qui sont disponibles pour les utilisateurs qui se connectent.
ms.openlocfilehash: 233d9081f4a8f977f0959addb5573c4566f885d0
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499992"
---
# <a name="jea-role-capabilities"></a>Capacités de rôle JEA

Quand vous créez un point de terminaison JEA, vous devez définir une ou plusieurs capacités de rôle, qui décrivent ce que quelqu’un peut faire dans une session JEA. Une capacité de rôle est un fichier de données PowerShell avec l’extension `.psrc` qui liste toutes les applets de commande, toutes les fonctions, tous les fournisseurs et tous les programmes externes qui sont disponibles pour les utilisateurs qui se connectent.

## <a name="determine-which-commands-to-allow"></a>Déterminer les commandes à autoriser

La première étape de la création d’un fichier de capacités de rôle est de considérer ce à quoi les utilisateurs ont besoin d’accéder. Ce processus de collecte de ce qui est nécessaire peut prendre un certain temps, mais il est très important. En donnant accès aux utilisateurs à trop peu de fonctions et d’applets de commande, vous les empêchez de faire leur travail. Autoriser l’accès à un trop grand nombre d’applets de commande et de fonctions peut permettre aux utilisateurs d’en faire plus que prévu et d’affaiblir la situation de votre sécurité.

La façon dont vous allez procéder dépend de votre organisation et de vos objectifs. Les conseils suivants peuvent vous aider à garantir que vous êtes sur la bonne voie.

1. **Identifiez** les commandes que les utilisateurs emploient pour effectuer leur travail. Ceci peut impliquer d’observer le personnel informatique, de consulter les scripts d’automatisation, ou d’analyser les journaux et les transcriptions des sessions PowerShell.
2. **Transposez** l’utilisation des outils de ligne de commande en leurs équivalents PowerShell là où c’est possible, pour assurer la meilleure expérience d’audit et de personnalisation de JEA. Les programmes externes ne peuvent pas avoir de contraintes aussi granulaires que les fonctions et applets de commande PowerShell natives dans JEA.
3. **Restreignez** l’étendue des applets de commande en autorisant seulement des paramètres ou des valeurs de paramètres spécifiques. Ceci est particulièrement important si les utilisateurs doivent gérer seulement une partie d’un système.
4. **Créez** des fonctions personnalisées pour remplacer des commandes complexes ou difficiles à contraindre dans JEA. Une fonction simple qui inclut une commande complexe dans un wrapper ou applique une logique de validation supplémentaire peut offrir des contrôles supplémentaires aux administrateurs et plus de simplicité aux utilisateurs finaux.
5. **Testez** la liste délimitée des commandes admissibles avec vos utilisateurs et/ou vos services d’automatisation, et effectuez les ajustements nécessaires.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemples de commandes potentiellement dangereuses

Une sélection rigoureuse des commandes est essentielle pour que le point de terminaison JEA ne permette pas à l’utilisateur connecté d’élever ses autorisations.

> [!IMPORTANT]
> Informations essentielles nécessaires pour tout fonctionne bien pour l’utilisateur Dans une session JEA, les commandes sont souvent exécutées avec des privilèges élevés.

Le tableau suivant contient des exemples de commandes qui peuvent être utilisées à des fins malveillantes si elles sont autorisées sans contraintes. Cette liste n’est pas exhaustive et ne doit être utilisée que comme point de départ pour prendre les précautions qui s’imposent.

|                                            Risque                                            |                                Exemple                                |                                                                              Commandes associées                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Accorder des privilèges Administrateur à l’utilisateur connecté pour contourner JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Exécuter du code arbitraire, notamment des logiciels malveillants, du code malveillant exploitant une faille de sécurité ou des scripts personnalisés afin de contourner les protections | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Créer un fichier de capacités de rôle

Vous pouvez créer un fichier de capacités de rôle PowerShell avec l’applet de commande [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile).

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Le fichier de capacités de rôle qui en résulte doit être modifié pour autoriser les commandes nécessaires pour le rôle. La documentation d’aide PowerShell contient plusieurs exemples de configuration du fichier.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Autoriser les fonctions et les applets de commande PowerShell

Pour autoriser les utilisateurs à exécuter des fonctions ou des applets de commande PowerShell, ajoutez le nom de l’applet de commande ou de la fonction au champ VisibleFunctions ou VisibleFunctions. Si vous ne savez pas si une commande est une applet de commande ou une fonction, vous pouvez exécuter `Get-Command <name>` et vérifier la propriété **CommandType** dans la sortie.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

La portée d’une applet de commande ou d’une fonction donnée est parfois trop vaste pour les besoins de vos utilisateurs. Un administrateur DNS, par exemple, n’a probablement besoin que de l’accès nécessaire pour redémarrer le service DNS. Dans les environnements multilocataire, les locataires ont accès aux outils de gestion en libre-service. Ils doivent être limités à la gestion de leurs propres ressources. Dans ce cas, vous pouvez restreindre les paramètres exposés à partir de l’applet de commande ou de la fonction.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

Dans des scénarios plus avancés, il peut également être nécessaire de restreindre les valeurs que les utilisateurs peuvent utiliser avec ces paramètres. Les capacités de rôle vous permettent de définir un ensemble de valeurs ou un modèle d’expression régulière qui déterminent si une entrée est autorisée.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Les [paramètres PowerShell communs](/powershell/module/microsoft.powershell.core/about/about_commonparameters) sont toujours autorisés, même si vous limitez les paramètres disponibles.
> Vous ne devez pas les lister explicitement dans le champ Paramètres.

Le tableau ci-dessous décrit les différentes façons de personnaliser une fonction ou une applet de commande visible.
Vous pouvez associer les méthodes suivantes comme vous le souhaitez dans le champ **VisibleCmdlets** .

|                                           Exemple                                           |                                                             Cas d’utilisation                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` ou `@{ Name = 'My-Func' }`                                                      | Permet à l’utilisateur d’exécuter `My-Func` sans aucune restriction sur les paramètres.                                                      |
| `'MyModule\My-Func'`                                                                        | Permet à l’utilisateur d’exécuter `My-Func` à partir du module `MyModule` sans aucune restriction sur les paramètres.                           |
| `'My-*'`                                                                                    | Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le verbe `My`.                                                                 |
| `'*-Func'`                                                                                  | Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le nom `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Permet à l’utilisateur d’exécuter `My-Func` avec les paramètres `Param1` et `Param2`. Toutes les valeurs peuvent être transmises aux paramètres.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`. Seules les valeurs « Value1 » et « Value2 » peuvent être transmises au paramètre.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`. Toutes les valeurs commençant par « contoso » peuvent être transmises au paramètre. |

> [!WARNING]
> Les meilleures pratiques de sécurité déconseillent d’utiliser des caractères génériques pour définir des fonctions ou des applets de commande visibles. Au contraire, listez explicitement chaque commande approuvée de façon qu’aucune autre commande partageant le même schéma d’affectation de noms ne soit autorisée par inadvertance.

Vous ne pouvez pas appliquer à la fois un **ValidatePattern** et un **ValidateSet** à la même applet de commande ou la même fonction.

Si vous le faites, le **ValidatePattern** l’emporte sur le **ValidateSet** .

Pour plus d’informations sur **ValidatePattern** , consultez [ce billet *Hey, Scripting Guy!* ](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) et le contenu de référence de [Expressions régulières PowerShell](/powershell/module/microsoft.powershell.core/about/about_regular_expressions).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Autoriser des commandes externes et des scripts PowerShell

Pour permettre aux utilisateurs de lancer des exécutables et des scripts PowerShell (.ps1) dans une session JEA, vous devez ajouter le chemin complet de chaque programme dans le champ **VisibleExternalCommands** .

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Là où c’est possible, utilisez des applets de commande/fonctions PowerShell équivalentes pour les exécutables externes que vous autorisez, car vous contrôlez les paramètres autorisés avec les applets de commande et les fonctions PowerShell.

De nombreux exécutables permettent de lire l’état actuel, puis de le modifier en fournissant d’autres paramètres.

Par exemple, considérez le rôle d’administrateur de serveur de fichiers qui gère des partages réseau hébergés sur un système. Une façon de gérer les partages est d’utiliser `net share`. Cependant, autoriser **net.exe** est dangereux, car l’administrateur pourrait utiliser la commande pour obtenir des privilèges d’administration avec `net group Administrators unprivilegedjeauser /add`. Une option plus sécurisée est d’autoriser [Get-SmbShare](/powershell/module/smbshare/get-smbshare), qui donne le même résultat, mais a une étendue bien plus limitée.

Quand vous rendez des commandes externes disponibles pour les utilisateurs dans une session JEA, spécifiez toujours le chemin complet du fichier exécutable. Ceci empêche l’exécution de programmes potentiellement malveillants portant le même nom et situés ailleurs dans le système.

### <a name="allowing-access-to-powershell-providers"></a>Autoriser l’accès aux fournisseurs PowerShell

Par défaut, les fournisseurs PowerShell sont disponibles dans les sessions JEA. Ceci réduit le risque de divulgation d’informations sensibles et de paramètres de configuration à l’utilisateur qui se connecte.

Si nécessaire, vous pouvez autoriser l’accès aux fournisseurs de PowerShell à l’aide de la commande `VisibleProviders`. Pour obtenir la liste complète des fournisseurs, exécutez `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Pour des tâches simples qui nécessitent l’accès au système de fichiers, au Registre, au magasin de certificats ou à d’autres fournisseurs sensibles, envisagez d’écrire une fonction personnalisée qui fonctionne avec le fournisseur pour le compte de l’utilisateur. Les fonctions, applets de commande et programmes externes disponibles dans une session JEA ne sont pas soumis aux mêmes contraintes que JEA. Ils peuvent accéder à tous les fournisseurs par défaut. Envisagez également d’utiliser le [lecteur utilisateur](session-configurations.md#user-drive) quand la copie de fichiers vers/depuis un point de terminaison JEA est nécessaire.

### <a name="creating-custom-functions"></a>Créer des fonctions personnalisées

Vous pouvez créer des fonctions personnalisées dans un fichier de capacités de rôle pour simplifier les tâches complexes de vos utilisateurs finaux. Les fonctions personnalisées sont également utiles lorsque vous avez besoin d’une logique de validation avancée pour les valeurs de paramètres des applets de commande. Vous pouvez écrire des fonctions simples dans le champ **FunctionDefinitions** :

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> N’oubliez pas d’ajouter le nom de vos fonctions personnalisées au champ **VisibleFunctions** pour qu’elles puissent être exécutées par les utilisateurs JEA.

Le corps (bloc de script) des fonctions personnalisées s’exécute dans le mode de langage par défaut du système et n’est pas soumis aux contraintes de langage de JEA. Cela signifie que les fonctions peuvent accéder au système de fichiers et au Registre, et exécuter des commandes qui n’étaient pas visibles dans le fichier de capacités de rôle. Prenez soin d’éviter l’exécution de code arbitraire lors de l’utilisation de paramètres. Évitez de transférer une entrée utilisateur via un canal directement dans des applets de commande comme `Invoke-Expression`.

Dans l’exemple ci-dessus, notez que le nom du module complet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` a été utilisé à la place du nom raccourci `Select-Object`.
Les fonctions définies dans les fichiers de capacités de rôle sont toujours soumises à la portée des sessions JEA, qui comprend les fonctions de proxy créées par JEA pour contraindre les commandes existantes.

Par défaut, `Select-Object` est une applet de commande contrainte dans toutes les sessions JEA, qui ne vous permet pas la sélection de propriétés arbitraires sur des objets. Pour utiliser `Select-Object` sans contraintes dans les fonctions, vous devez demander explicitement l’implémentation complète en spécifiant le nom du module complet. Une applet de commande contrainte dans une session JEA a les mêmes contraintes que quand elle est appelée à partir d’une fonction. Pour plus d’informations, consultez [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Si vous écrivez de nombreuses fonctions personnalisées, il peut être plus pratique de les placer dans un module de script PowerShell. Vous rendez ces fonctions visibles dans la session JEA en utilisant le champ **VisibleFunctions** , comme avec des modules intégrés et de tiers.

Pour que la complétion avec la touche TAB fonctionne correctement dans les sessions JEA, vous devez inclure la fonction intégrée `tabexpansion2` dans la liste **VisibleFunctions** .

## <a name="make-the-role-capabilities-available-to-a-configuration"></a>Rendre les fonctionnalités de rôle disponibles pour une configuration

Avant PowerShell 6, pour que PowerShell trouve un fichier de capacités de rôle, celui-ci doit être stocké dans le dossier **RoleCapabilities** d’un module PowerShell. Le module peut être stocké dans un dossier inclus dans la variable d’environnement `$env:PSModulePath` ; cependant, vous ne devez pas le placer dans `$env:SystemRoot\System32` ou dans un dossier où des utilisateurs non fiables pourraient modifier les fichiers.

L’exemple suivant crée un module de script PowerShell appelé **ContosoJEA** dans le chemin `$env:ProgramFiles` pour héberger le fichier de capacités de rôle.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Pour plus d’informations sur les modules PowerShell, consultez [Comprendre un module PowerShell](/powershell/scripting/developer/windows-powershell).

À compter de PowerShell 6, la propriété **RoleDefinitions** a été ajoutée au fichier de configuration de session. Cette propriété vous permet de spécifier l’emplacement d’un fichier de configuration de rôle pour votre définition de rôle. Consultez les exemples dans [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile).

## <a name="updating-role-capabilities"></a>Mettre à jour les capacités de rôle

Vous pouvez modifier à tout moment un fichier de capacités de rôle pour mettre à jour les paramètres. Les nouvelles sessions JEA lancées après la mise à jour de la capacité du rôle reflèteront les fonctionnalités modifiées.

C’est pourquoi il est très important de contrôler l’accès au dossier de capacités de rôle. Seuls les administrateurs approuvés doivent pouvoir modifier les fichiers de capacités de rôle. Si un utilisateur non approuvé peut modifier les fichiers de capacités de rôle, il peut facilement s’accorder l’accès aux applets de commande qui lui permettent d’élever ses privilèges.

Les administrateurs qui souhaitent verrouiller l’accès aux capacités de rôle doivent vérifier que le système local a un accès en lecture aux fichiers de capacités de rôle et aux modules qui les contiennent.

## <a name="how-role-capabilities-are-merged"></a>Fusionner les capacités de rôle

Les utilisateurs sont autorisés à accéder à toutes les capacités de rôle correspondantes dans le [fichier de configuration de session](session-configurations.md) quand ils entrent dans une session JEA. JEA tente de donner à l’utilisateur l’ensemble de commandes le plus permissif autorisé par les rôles.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets et VisibleFunctions

La logique de fusion la plus complexe affecte les applets de commande et les fonctions, dont les paramètres et les valeurs de paramètres peuvent être limités dans JEA.

Les règles sont les suivantes :

1. Si une applet de commande n’est visible que dans un seul rôle, elle est visible par l’utilisateur avec les contraintes de paramètres applicables.
2. Si une applet de commande est visible dans plusieurs rôles, et que chaque rôle a les mêmes contraintes sur l’applet de commande, l’applet de commande est visible par l’utilisateur avec ces contraintes.
3. Si une applet de commande est visible dans plusieurs rôles, et que les rôles autorisent différents ensembles de paramètres, l’applet de commande et tous les paramètres définis sur tous les rôles sont visibles par l’utilisateur.
   Si un rôle n’a pas de contraintes sur les paramètres, tous les paramètres sont autorisés.
4. Si un rôle définit un ensemble ou un modèle de validation d’un paramètre d’applet de commande, et qu’un autre rôle autorise le paramètre mais ne contraint pas les valeurs du paramètre, l’ensemble ou le modèle de validation est ignoré.
5. Si un ensemble de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs de tous les ensembles de validation sont autorisées.
6. Si un modèle de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs qui correspondent aux modèles sont autorisées.
7. Si un ensemble de validation est défini dans un ou plusieurs rôles, et qu’un modèle de validation est défini dans un autre rôle pour le même paramètre d’applet de commande, l’ensemble de validation est ignoré et la règle (6) s’applique aux modèles de validation restants.

Vous trouverez ci-dessous un exemple de la façon dont les rôles sont fusionnés en fonction de ces règles :

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Tous les autres champs du fichier de capacités de rôle sont ajoutés à un ensemble cumulatif de commandes externes admissibles, d’alias, de fournisseurs et de scripts de démarrage. Les commandes, alias, fournisseurs ou scripts disponibles dans une capacité de rôle sont disponibles pour l’utilisateur JEA.

Veillez à ce que l’ensemble combiné de fournisseurs d’une capacité de rôle et les applets de commande/fonctions/commandes d’une autre n’autorisent pas les utilisateurs à accéder involontairement à des ressources système.
Par exemple, si un rôle autorise l’applet de commande `Remove-Item` et un autre le fournisseur `FileSystem`, il existe un risque qu’un utilisateur JEA supprime des fichiers arbitraires sur votre ordinateur. Vous trouverez des informations supplémentaires sur l’identification des autorisations effectives des utilisateurs dans l’article [Audit de JEA](audit-and-report.md).

## <a name="next-steps"></a>Étapes suivantes

[Créer un fichier de configuration de session](session-configurations.md)
