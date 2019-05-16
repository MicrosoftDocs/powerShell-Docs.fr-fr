---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Capacités de rôle JEA
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229555"
---
# <a name="jea-role-capabilities"></a>Capacités de rôle JEA

> S'applique à : Windows PowerShell 5.0

Lorsque vous créez un point de terminaison JEA, vous devez définir une ou plusieurs « capacités de rôle », qui décrivent *ce que* quelqu’un peut faire dans une session JEA.
Une capacité de rôle est un fichier de données PowerShell avec l’extension .psrc qui liste toutes les applets de commande, toutes les fonctions, tous les fournisseurs et tous les programmes externes devant être accessibles aux utilisateurs qui se connectent.

Cette rubrique décrit comment créer un fichier de capacités de rôle PowerShell pour vos utilisateurs JEA.

## <a name="determine-which-commands-to-allow"></a>Déterminer les commandes à autoriser

La première étape de la création d’un fichier de capacités de rôle consiste à prendre en considération ce à quoi les utilisateurs de ce rôle auront besoin d’accéder.
Ce processus de collecte des exigences peut prendre un certain temps, mais il est très important.
En donnant accès aux utilisateurs à trop peu de fonctions et d’applets de commande, vous les empêchez de faire leur travail.
Si vous autorisez l’accès à un trop grand nombre d’applets de commande et de fonctions, les utilisateurs pourront faire plus que prévu avec leurs privilèges Administrateur implicites, ce qui affaiblira votre position en matière de sécurité.

Vos choix vis-à-vis de ce processus dépendent de votre organisation et de vos objectifs, mais les conseils suivants peuvent vous aider à vérifier que vous êtes sur la bonne voie.

1. **Identifiez** les commandes que les utilisateurs emploient pour effectuer leur travail. Cela peut impliquer d’observer le personnel informatique, de consulter les scripts d’automatisation et d’analyser les journaux ou les transcriptions de sessions PowerShell.
2. **Transposez** l’utilisation des outils de ligne de commande à leurs équivalents PowerShell, si possible, pour assurer la meilleure expérience d’audit et de personnalisation JEA. Les programmes externes ne peuvent pas avoir de contraintes aussi granulaires que les fonctions et applets de commande PowerShell natives de JEA.
3. **Restreignez** si nécessaire la portée des applets de commande pour n’autoriser que des paramètres ou des valeurs de paramètres spécifiques. C’est particulièrement important si les utilisateurs ne doivent pouvoir gérer qu’une partie d’un système.
4. **Créez** des fonctions personnalisées pour remplacer des commandes complexes ou difficiles à contraindre dans JEA. Une fonction simple qui inclut une commande complexe dans un wrapper ou applique une logique de validation supplémentaire peut offrir des contrôles supplémentaires aux administrateurs et plus de simplicité aux utilisateurs finaux.
5. **Testez** la liste étendue des commandes admissibles avec vos utilisateurs et/ou services d’automatisation et effectuez les ajustements nécessaires.

N’oubliez pas que les commandes d’une session JEA sont souvent exécutées avec des privilèges Administrateur (ou avec élévation de privilèges autre).
Une sélection rigoureuse des commandes disponibles est essentielle pour que le point de terminaison JEA n’autorise pas l’utilisateur connecté à élever ses autorisations.
Voici quelques exemples de commandes qui peuvent être utilisées à des fins malveillantes si elles sont autorisées sans contraintes.
Notez que cette liste n’est pas exhaustive et ne doit être utilisée que comme point de départ pour prendre les précautions qui s’imposent.

### <a name="examples-of-potentially-dangerous-commands"></a>Exemples de commandes potentiellement dangereuses

Risque | Exemple | Commandes associées
-----|---------|-----------------
Accorder des privilèges Administrateur à l’utilisateur connecté pour contourner JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Exécuter du code arbitraire, notamment des logiciels malveillants, du code malveillant exploitant une faille de sécurité ou des scripts personnalisés afin de contourner les protections | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Créer un fichier de capacités de rôle

Vous pouvez créer un fichier de capacités de rôle PowerShell avec l’applet de commande [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Le fichier de capacités de rôle résultant peut être ouvert dans un éditeur de texte et modifié pour autoriser les commandes souhaitées pour le rôle.
La documentation d’aide PowerShell contient plusieurs exemples de configuration du fichier.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Autoriser les fonctions et les applets de commande PowerShell

Pour autoriser les utilisateurs à exécuter des fonctions ou des applets de commande PowerShell, ajoutez le nom de l’applet de commande ou de la fonction au champ VisibleFunctions ou VisibleFunctions.
Si vous ne savez pas si une commande est une applet de commande ou une fonction, vous pouvez exécuter `Get-Command <name>` et vérifier la propriété « CommandType » dans la sortie.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

La portée d’une applet de commande ou d’une fonction donnée est parfois trop vaste pour les besoins de vos utilisateurs.
Un administrateur DNS, par exemple, n’a probablement besoin que de l’accès nécessaire pour redémarrer le service DNS.
Dans un environnement mutualisé où les locataires ont accès à des outils de gestion en libre-service, ils doivent être limités à la gestion de leurs propres ressources.
Dans ce cas, vous pouvez restreindre les paramètres exposés à partir de l’applet de commande ou de la fonction.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Dans des scénarios plus avancés, vous devrez peut-être également restreindre les valeurs que les utilisateurs peuvent fournir à ces paramètres.
Les capacités de rôle vous permettent de définir un ensemble de valeurs autorisées ou un modèle d’expression régulière évalué pour déterminer si une entrée donnée est autorisée.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Les [paramètres PowerShell communs](https://technet.microsoft.com/library/hh847884.aspx) sont toujours autorisés, même si vous limitez les paramètres disponibles.
> Vous ne devez pas les lister explicitement dans le champ Paramètres.

Le tableau ci-dessous décrit les différentes façons de personnaliser une fonction ou une applet de commande visible.
Vous pouvez associer les méthodes suivantes comme vous le souhaitez dans le champ VisibleCmdlets.

Exemple                                                                                      | Cas d’usage
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` ou `@{ Name = 'My-Func' }`                                                       | Permet à l’utilisateur d’exécuter `My-Func` sans aucune restriction sur les paramètres.
`'MyModule\My-Func'`                                                                         | Permet à l’utilisateur d’exécuter `My-Func` à partir du module `MyModule` sans aucune restriction sur les paramètres.
`'My-*'`                                                                                     | Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le verbe `My`.
`'*-Func'`                                                                                   | Permet à l’utilisateur d’exécuter toutes les applets de commande ou fonctions avec le nom `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Permet à l’utilisateur d’exécuter `My-Func` avec les paramètres `Param1` et/ou `Param2`. Toutes les valeurs peuvent être transmises aux paramètres.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`. Seules les valeurs « Value1 » et « Value2 » peuvent être transmises au paramètre.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Permet à l’utilisateur d’exécuter `My-Func` avec le paramètre `Param1`. Toutes les valeurs commençant par « contoso » peuvent être transmises au paramètre.

> [!WARNING]
> Les meilleures pratiques de sécurité déconseillent d’utiliser des caractères génériques pour définir des fonctions ou des applets de commande visibles.
> Au contraire, listez explicitement chaque commande approuvée de façon qu’aucune autre commande partageant le même schéma d’affectation de noms ne soit autorisée par inadvertance.

Vous ne pouvez pas appliquer à la fois un ValidatePattern et un ValidateSet à la même applet de commande ou fonction.

Si vous le faites, le ValidatePattern remplacera le ValidateSet.

Pour plus d’informations sur ValidatePattern, consultez [cet article *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) et le contenu de référence [Expressions régulières PowerShell](https://technet.microsoft.com/library/hh847880.aspx).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Autoriser des commandes externes et des scripts PowerShell

Pour permettre aux utilisateurs de lancer des exécutables et des scripts PowerShell (.ps1) dans une session JEA, vous devez ajouter le chemin d’accès complet de chaque programme dans le champ VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Il est recommandé, si possible, d’utiliser des applets de commande/fonctions PowerShell équivalentes de tous les exécutables externes que vous autorisez, car vous contrôlez les paramètres autorisés avec les applets de commande/fonctions PowerShell.

De nombreux exécutables permettent de lire l’état actuel puis de le modifier en fournissant simplement d’autres paramètres.

Par exemple, prenons le rôle d’un administrateur de serveurs de fichiers qui souhaite connaître les partages réseau hébergés par l’ordinateur local.
Il est possible pour cela d’utiliser `net share`.
Toutefois, autoriser net.exe est très dangereux, car l’administrateur pourrait tout aussi facilement utiliser la commande pour obtenir des privilèges Administrateur avec `net group Administrators unprivilegedjeauser /add`.
Il est préférable d’autoriser [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx), qui donne le même résultat mais a une portée bien plus limitée.

Quand vous mettez des commandes externes à la disposition des utilisateurs dans une session JEA, spécifiez toujours le chemin complet de l’exécutable pour éviter qu’un programme portant le même nom (et potentiellement malveillant), placé ailleurs sur le système, ne soit exécuté à la place.

### <a name="allowing-access-to-powershell-providers"></a>Autoriser l’accès aux fournisseurs PowerShell

Par défaut, les fournisseurs PowerShell sont disponibles dans les sessions JEA.

Il s’agit principalement de réduire le risque de divulgation d’informations sensibles et de paramètres de configuration à l’utilisateur qui établit la connexion.

Si nécessaire, vous pouvez autoriser l’accès aux fournisseurs de PowerShell à l’aide de la commande `VisibleProviders`.
Pour obtenir la liste complète des fournisseurs, exécutez `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Pour des tâches simples qui requièrent l’accès au système de fichiers, au registre, au magasin de certificats ou à d’autres fournisseurs sensibles, vous pouvez également envisager d’écrire une fonction personnalisée qui fonctionne avec le fournisseur au nom de l’utilisateur.
Les fonctions, applets de commande et programmes externes disponibles dans une session JEA ne sont pas soumis aux mêmes contraintes que JEA : ils peuvent accéder à tous les fournisseurs par défaut.
Envisagez également d’utiliser le [lecteur utilisateur](session-configurations.md#user-drive) lorsqu’il est nécessaire de copier des fichiers vers/à partir d’un point de terminaison JEA.

### <a name="creating-custom-functions"></a>Créer des fonctions personnalisées

Vous pouvez créer des fonctions personnalisées dans un fichier de capacités de rôle pour simplifier les tâches complexes de vos utilisateurs finaux.
Les fonctions personnalisées sont également utiles lorsque vous avez besoin d’une logique de validation avancée pour les valeurs de paramètres des applets de commande.
Vous pouvez écrire des fonctions simples dans le champ **FunctionDefinitions** :

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> N’oubliez pas d’ajouter le nom de vos fonctions personnalisées au champ **VisibleFunctions** pour qu’elles puissent être exécutées par les utilisateurs JEA.

Le corps (bloc de script) des fonctions personnalisées s’exécute dans le mode de langage par défaut du système et n’est pas soumis aux contraintes de langage de JEA.
Cela signifie que les fonctions peuvent accéder au système de fichiers et au registre, puis exécuter des commandes qui n’étaient pas visibles dans le fichier de capacités de rôle.
Prenez soin d’éviter d’autoriser l’exécution de code arbitraire lorsque vous utilisez les paramètres et d’éviter d’injecter directement l’entrée utilisateur dans des applets de commande comme `Invoke-Expression`.

Dans l’exemple ci-dessus, vous remarquerez que le nom du module complet (FQMN) `Microsoft.PowerShell.Utility\Select-Object` a été utilisé à la place du nom raccourci `Select-Object`.
Les fonctions définies dans les fichiers de capacités de rôle sont toujours soumises à la portée des sessions JEA, qui comprend les fonctions de proxy créées par JEA pour contraindre les commandes existantes.

Select-Object est une applet de commande contrainte par défaut dans toutes les sessions JEA qui ne vous permet pas de sélectionner des propriétés arbitraires sur les objets.
Pour utiliser Select-Object sans contraintes dans les fonctions, vous devez demander explicitement l’implémentation complète en spécifiant le FQMN.
Une applet de commande contrainte dans une session JEA présente le même comportement lorsqu’elle est appelée à partir d’une fonction, conformément à la [précédence des commandes](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) de PowerShell.

Si vous écrivez de nombreuses fonctions personnalisées, il peut être plus facile de les placer dans un [Module de script PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Vous pouvez ensuite rendre ces fonctions visibles dans la session JEA à l’aide du champ VisibleFunctions, comme avec des modules intégrés et tiers.

Pour que la complétion avec la touche TAB fonctionne correctement dans les sessions JEA, vous devez inclure la fonction intégrée `tabexpansion2` dans la liste **VisibleFunctions**.

## <a name="place-role-capabilities-in-a-module"></a>Placer les capacités de rôle dans un module

Pour que PowerShell trouve un fichier de capacités de rôle, celui-ci doit être stocké dans le dossier « RoleCapabilities » d’un module PowerShell.
Le module peut être stocké dans un dossier inclus dans la variable d’environnement `$env:PSModulePath`, cependant vous ne devez pas le placer dans System32 (réservé aux modules intégrés) ou dans un dossier où des utilisateurs non fiables qui établissent la connexion pourraient modifier les fichiers.
Voici un exemple de création d’un module de script PowerShell de base, appelé *ContosoJEA* dans le chemin d’accès « Program Files ».

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Consultez la page [Comprendre un module PowerShell](https://msdn.microsoft.com/library/dd878324.aspx) pour plus d’informations sur les modules PowerShell, les manifestes de modules et la variable d’environnement PSModulePath.

## <a name="updating-role-capabilities"></a>Mettre à jour les capacités de rôle

Vous pouvez mettre à jour un fichier de capacités de rôle à tout moment en enregistrant simplement les modifications dans le fichier de capacités de rôle.
Les nouvelles sessions JEA lancées après la mise à jour de la capacité du rôle reflèteront les fonctionnalités modifiées.

C’est pourquoi il est très important de contrôler l’accès au dossier de capacités de rôle.
Seuls les administrateurs de confiance doivent pouvoir modifier les fichiers de capacités de rôle.
Si un utilisateur non fiable peut modifier les fichiers de capacités de rôle, il peut facilement s’accorder l’accès aux applets de commande qui lui permettront d’élever ses privilèges.

Les administrateurs qui souhaitent verrouiller l’accès aux capacités de rôle doivent vérifier que le système local a un accès en lecture aux fichiers de capacités de rôle et aux modules qui les contiennent.

## <a name="how-role-capabilities-are-merged"></a>Fusionner les capacités de rôle

Les utilisateurs peuvent accéder à plusieurs capacités de rôle lorsqu’ils intègrent une session JEA en fonction du mappage des rôles dans le [fichier de configuration de session](session-configurations.md).
Dans ce cas, JEA tente de donner à l’utilisateur l’ensemble de commandes *le plus permissif* autorisé par les rôles.

**VisibleCmdlets et VisibleFunctions**

La logique de fusion la plus complexe affecte les applets de commande et les fonctions, dont les paramètres et les valeurs de paramètres peuvent être limités dans JEA.

Les règles sont les suivantes :

1. Si une applet de commande n’est visible que dans un rôle, elle sera visible par l’utilisateur avec n’importe quelles contraintes de paramètres applicables.
2. Si une applet de commande est visible dans plusieurs rôles, et que chaque rôle a les mêmes contraintes sur l’applet de commande, l’applet de commande sera visible par l’utilisateur avec ces contraintes.
3. Si une applet de commande est visible dans plusieurs rôles, et que les rôles autorisent différents ensembles de paramètres, l’applet de commande et tous les paramètres définis sur tous les rôles seront visibles par l’utilisateur. Si un rôle n’a pas de contraintes sur les paramètres, tous les paramètres seront autorisées.
4. Si un rôle définit un ensemble ou un modèle de validation d’un paramètre d’applet de commande, et que l’autre rôle autorise le paramètre mais ne contraint pas les valeurs du paramètre, l’ensemble ou le modèle de validation sera ignoré.
5. Si un ensemble de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs de tous les ensembles de validation seront autorisées.
6. Si un modèle de validation est défini pour le même paramètre d’applet de commande dans plusieurs rôles, toutes les valeurs qui correspondent aux modèles seront autorisées.
7. Si un ensemble de validation est défini dans un ou plusieurs rôles, et qu’un modèle de validation est défini dans un autre rôle pour le même paramètre d’applet de commande, l’ensemble de validation est ignoré et la règle (6) s’applique aux modèles de validation restants.

Vous trouverez ci-dessous un exemple de la façon dont les rôles sont fusionnés en fonction de ces règles :

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Tous les autres champs du fichier de capacités de rôle sont simplement ajoutés à un ensemble cumulatif de commandes externes admissibles, d’alias, de fournisseurs et de scripts de démarrage.
Les commandes, alias, fournisseurs ou scripts disponibles dans une capacité de rôle seront accessibles à l’utilisateur JEA.

Veillez à ce que l’ensemble combiné de fournisseurs d’une capacité de rôle et les applets de commande/fonctions/commandes d’une autre n’autorisent pas les utilisateurs connectés à accéder involontairement aux ressources système.
Par exemple, si un rôle autorise l’applet de commande `Remove-Item` et un autre le fournisseur `FileSystem`, il existe un risque qu’un utilisateur JEA supprime des fichiers arbitraires sur votre ordinateur.
Vous trouverez des informations supplémentaires sur l’identification des autorisations effectives des utilisateurs dans la [rubrique Audit de JEA](audit-and-report.md).

## <a name="next-steps"></a>Étapes suivantes

- [Créer un fichier de configuration de session](session-configurations.md)
