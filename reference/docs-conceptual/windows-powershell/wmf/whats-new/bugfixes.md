---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Résolutions de bogues dans WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809305"
---
# <a name="bug-fixes-in-wmf-51"></a>Résolutions de bogues dans WMF 5.1

## <a name="bug-fixes"></a>Résolution des bogues

Les bogues importants suivants sont résolus dans WMF 5.1 :

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>La détection automatique de module respecte entièrement PSModulePath

La détection automatique de module (chargement automatique des modules sans Import-Module explicite lors de l’appel d’une commande) a été introduite dans WMF 3. Lors de l’introduction, PowerShell vérifiait la présence des commandes dans `$PSHome\Modules` avant d’utiliser `$env:PSModulePath`.

WMF 5.1 modifie ce comportement pour honorer `$env:PSModulePath` complètement. Ainsi, un module créé par l’utilisateur qui définit des commandes fournies par PowerShell (par exemple, `Get-ChildItem`) peut être chargé automatiquement et remplacer correctement la commande intégrée.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>La redirection de fichiers ne code plus en dur -Encoding Unicode

Dans toutes les versions précédentes de PowerShell, il était impossible de contrôler l’encodage de fichier utilisé par l’opérateur de redirection de fichier.

À compter de WMF 5.1, vous pouvez modifier l’encodage de fichier de la redirection en définissant `$PSDefaultParameterValues` :

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Correction d’une régression dans l’accès aux membres de System.Reflection.TypeInfo

Une régression introduite dans WMF 5.0 interdisait l’accès aux membres de `System.Reflection.RuntimeType`, par exemple `[int].ImplementedInterfaces`. Ce bogue a été résolu dans WMF 5.1.

### <a name="fixed-some-issues-with-com-objects"></a>Résolution de certains problèmes liés aux objets COM

WMF 5.0 a introduit un nouveau binder COM pour appeler des méthodes sur des objets COM et accéder aux propriétés des objets COM. Ce nouveau binder a amélioré les performances de manière significative, mais il a également introduit des bogues qui ont été résolus dans WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Les conversions d’arguments n’étaient pas toujours effectuées correctement

Dans l’exemple suivant :

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

La méthode **SendKeys** attend une chaîne, mais PowerShell n’a pas converti le caractère en chaîne, ce qui diffère la conversion en **IDispatch::Invoke**, qui utilise **VariantChangeType**. Dans cet exemple, les clés « 1 », « 7 » et « 3 » ont donc été envoyées au lieu de la clé **Volume.Mute** attendue.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Les objets COM énumérables ne sont pas toujours gérés correctement

PowerShell énumère normalement la plupart des objets énumérables, mais une régression introduite dans WMF 5.0 empêchait l’énumération des objets COM qui implémentent IEnumerable. Par exemple :

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Dans l’exemple ci-dessus, WMF 5.0 écrivait le **Scripting.Dictionary** dans le pipeline au lieu d’énumérer les paires clé/valeur.

### <a name="ordered-was-not-allowed-inside-classes"></a>[ordered] n’était pas autorisé à l’intérieur des classes

WMF 5.0 a introduit des classes avec la validation des littéraux de type utilisée dans les classes. `[ordered]` ressemble à un littéral de type, mais n’est pas un vrai type .NET. WMF 5.0 signalait de façon erronée une erreur sur `[ordered]` à l’intérieur d’une classe :

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>L’aide sur les rubriques de procédures avec plusieurs versions ne fonctionne pas

Avant WMF 5.1, si plusieurs versions d’un module étaient installées et que toutes partageaient une rubrique d’aide, par exemple about_PSReadline, `help about_PSReadline` retournait plusieurs rubriques sans aucun moyen évident d’afficher l’aide réelle.

WMF 5.1 résout ce problème en retournant l’aide de la version la plus récente de la rubrique.

`Get-Help` n’offre aucun moyen de spécifier la version pour laquelle vous souhaitez obtenir de l’aide. Pour contourner ce problème, accédez au répertoire de modules et affichez l’aide directement avec un outil tel que votre éditeur favori.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>Impossible de lire powershell.exe à partir de STDIN

Les clients utilisent `powershell -command -` à partir d’applications natives pour passer des commandes PowerShell dans le script par le biais de STDIN. Malheureusement, d’autres modifications apportées à l’hôte de la console avaient cassé cette fonctionnalité.

Ce problème est résolu pour la version 5.1 dans la Mise à jour anniversaire Windows 10.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>powershell.exe crée un pic d’utilisation du processeur au démarrage

PowerShell utilise une requête WMI pour vérifier s’il a été démarré par le biais d’une stratégie de groupe afin de ne pas causer de retard au niveau de la connexion. La requête WMI finit par injecter tzres.mui.dll dans chaque processus du système, car la classe WMI **Win32_Process** tente de récupérer des informations sur le fuseau horaire local. Il en résulte un pic d’utilisation du processeur dans **wmiprvse** (hôte du fournisseur WMI). Pour y remédier tout en obtenant les mêmes informations, utilisez des appels d’API Win32 à la place de WMI.
