---
description: Explique les modes de langue et leur effet sur les sessions PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: 91e3021c854945d86822c5d8219542eff7118aa7
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625650"
---
# <a name="about-language-modes"></a>À propos des modes de langage

## <a name="short-description"></a>DESCRIPTION COURTE
Explique les modes de langue et leur effet sur les sessions PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Le mode de langage d’une session PowerShell détermine, en partie, les éléments du langage PowerShell qui peuvent être utilisés dans la session.

PowerShell prend en charge les modes de langue suivants :

- FullLanguage
- ConstrainedLanguage (introduit dans PowerShell 3,0)
- RestrictedLanguage
- NoLanguage

### <a name="what-is-a-language-mode"></a>QU’EST-CE QU’UN MODE DE LANGAGE ?

Le mode de langage détermine les éléments de langage qui sont autorisés dans la session.

Le mode de langage est en fait une propriété de la configuration de session (ou « point de terminaison ») qui est utilisée pour créer la session. Toutes les sessions qui utilisent une configuration de session particulière ont le mode de langue de la configuration de session.

Toutes les sessions PowerShell ont un mode de langage, y compris les sessions PSSession que vous créez à l’aide de l’applet de commande `New-PSSession` , des sessions temporaires qui utilisent le paramètre ComputerName et des sessions par défaut qui s’affichent lorsque vous démarrez PowerShell.

Les sessions à distance sont créées à l’aide des configurations de session sur l’ordinateur distant. Le mode de langage défini dans la configuration de session détermine le mode de langue de la session. Pour spécifier la configuration de session d’une session PSSession, utilisez le paramètre ConfigurationName des applets de commande qui créent une session.

### <a name="language-modes"></a>MODES DE LANGUE

Cette section décrit les modes de langue dans les sessions PowerShell.

#### <a name="full-language-fulllanguage"></a>FULL LANGUAGE (FullLanguage)

Le mode FullLanguage autorise tous les éléments de langage de la session.
FullLanguage est le mode de langue par défaut pour les sessions par défaut sur toutes les versions de Windows, à l’exception de Windows RT.

#### <a name="restricted-language-restrictedlanguage"></a>LANGUE RESTREINTe (RestrictedLanguage)

En mode RestrictedLanguage, les utilisateurs peuvent exécuter des commandes (applets de commande, fonctions, commandes CIM et flux de travail), mais ils ne sont pas autorisés à utiliser des blocs de script.

Par défaut, seules les variables suivantes sont autorisées en mode RestrictedLanguage :

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

Seuls les opérateurs de comparaison suivants sont autorisés :

- `-eq` valeur
- `-gt` (supérieur à)
- `-lt` (inférieur à)

Les instructions d'assignation, les références de propriété et les appels de méthode ne sont pas autorisés.

#### <a name="no-language-nolanguage"></a>AUCUNE langue (nolanguage)

Le mode nolanguage ne peut être utilisé que par le biais de l’API. Le mode nolanguage signifie qu’aucun texte de script n’est autorisé. Cela exclut l’utilisation de la méthode **AddScript ()** qui envoie des fragments de script PowerShell à analyser et à exécuter. Vous ne pouvez utiliser que **AddCommand ()** et **AddParameter ()** qui ne passent pas par l’analyseur.

#### <a name="constrained-language-constrained-language"></a>LANGUE restreinte (langage restreint)

Le mode ConstrainedLanguage autorise toutes les applets de commande et tous les éléments de langage PowerShell, mais il limite les types autorisés.

Le mode ConstrainedLanguage est conçu pour prendre en charge l’intégrité du code en mode utilisateur (UMCI) sur Windows RT. Il s’agit du seul mode de langage pris en charge sur Windows RT, mais il est disponible sur tous les systèmes pris en charge.

UMCI protège les appareils ARM en autorisant uniquement l’installation d’applications signées par Microsoft et certifiées par Microsoft sur des appareils basés sur Windows RT.
Le mode ConstrainedLanguage empêche les utilisateurs d’utiliser PowerShell pour contourner ou enfreindre UMCI.

Les fonctionnalités du mode ConstrainedLanguage sont les suivantes :

- Toutes les applets de commande dans les modules Windows et les autres applets de commande approuvées par UMCI sont entièrement opérationnelles et disposent d’un accès complet aux ressources système, sauf indication contraire.

- Tous les éléments du langage de script PowerShell sont autorisés.

- Tous les modules inclus dans Windows peuvent être importés et toutes les commandes que les modules exportent s’exécutent dans la session.

- Dans PowerShell workflow, vous pouvez écrire et exécuter des workflows de script (workflows écrits dans le langage PowerShell). Les workflows XAML ne sont pas pris en charge et vous ne pouvez pas exécuter XAML dans un flux de travail de script, par exemple à l’aide de `Invoke-Expression -Language XAML` . En outre, les flux de travail ne peuvent pas appeler d’autres workflows, bien que les workflows imbriqués soient autorisés.

- L' `Add-Type` applet de commande peut charger des assemblys signés, mais elle ne peut pas charger du code C# arbitraire ou des API Win32.

- L' `New-Object` applet de commande peut être utilisée uniquement sur les types autorisés (listés ci-dessous).

- Seuls les types autorisés (listés ci-dessous) peuvent être utilisés dans PowerShell. Les autres types ne sont pas autorisés.

- La conversion de type est autorisée, mais uniquement lorsque le résultat est un type autorisé.

- Les paramètres d’applet de commande qui convertissent une entrée de chaîne en types fonctionnent uniquement lorsque le type résultant est un type autorisé.

- La méthode **ToString ()** et les méthodes .net des types autorisés (listés ci-dessous) peuvent être appelées. D’autres méthodes ne peuvent pas être appelées.

- Les utilisateurs peuvent accéder à toutes les propriétés des types autorisés. Les utilisateurs peuvent définir les valeurs des propriétés uniquement sur les types de base. Seuls les objets COM suivants sont autorisés :

  - **Script. dictionary**
  - **Scripting.FileSystemObject**
  - **VBScript. RegExp**

Les types suivants sont autorisés en mode ConstrainedLanguage. Les utilisateurs peuvent accéder aux propriétés, appeler des méthodes et convertir des objets en ces types.

Types autorisés :

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- Array
- Bool
- byte
- char
- CmdletBindingAttribute
- DateTime
- Décimal
- DirectoryEntry
- DirectorySearcher
- double
- float
- Guid
- Hashtable
- int
- Int16
- long
- ManagementClass
- ManagementObject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- Expression régulière
- SByte
- string
- SupportsWildcardsAttribute
- SwitchParameter
- System. Globalization. CultureInfo
- System .net. IPAddress
- System .net. mail. MailAddress
- System. Numerics. BigInteger
- System.Security.SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>RECHERCHE DU MODE DE LANGUE D’UNE CONFIGURATION DE SESSION

Quand une configuration de session est créée à l’aide d’un fichier de configuration de session, la configuration de session a une propriété LanguageMode. Vous pouvez trouver le mode de langage en obtenant la valeur de la propriété LanguageMode.

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

Sur d’autres configurations de session, vous pouvez trouver le mode de langage indirectement en recherchant le mode de langue d’une session créée à l’aide de la configuration de session.

### <a name="finding-the-language-mode-of-a-session"></a>RECHERCHE DU MODE DE LANGUE D’UNE SESSION

Vous pouvez trouver le mode de langage d’une session FullLanguage ou ConstrainedLanguage en obtenant la valeur de la propriété LanguageMode de l’état de session.

Par exemple :

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

Toutefois, dans les sessions avec des modes RestrictedLanguage et nolanguage, vous ne pouvez pas utiliser la méthode dot pour récupérer des valeurs de propriété. Au lieu de cela, le message d’erreur révèle le mode de langage.

Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session RestrictedLanguage, PowerShell retourne les messages d’erreur PropertyReferenceNotSupportedInDataSection et VariableReferenceNotSupportedInDataSection.

- PropertyReferenceNotSupportedInDataSection : les références de propriété ne sont pas autorisées en mode de langage restreint ou dans une section de données.
- VariableReferenceNotSupportedInDataSection : une variable qui ne peut pas être référencée en mode de langage restreint ou une section de données est référencée.

Quand vous exécutez la `$ExecutionContext.SessionState.LanguageMode` commande dans une session nolanguage, PowerShell retourne le message d’erreur ScriptsNotAllowed.

- ScriptsNotAllowed : la syntaxe n’est pas prise en charge par cette instance d’exécution. Cela peut être dû au fait qu’il n’est pas en mode sans langage.

## <a name="see-also"></a>VOIR AUSSI

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)
