---
description: Décrit les paramètres qui peuvent être utilisés avec n’importe quelle applet de commande.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 0b303590aab756aaa7dd55683e114a20c2b2a12c
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860808"
---
# <a name="about-commonparameters"></a>À propos de Paramètres_courants

## <a name="short-description"></a>DESCRIPTION COURTE

Décrit les paramètres qui peuvent être utilisés avec n’importe quelle applet de commande.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les paramètres communs sont un ensemble de paramètres d’applet de commande que vous pouvez utiliser avec n’importe quelle applet de commande. Elles sont implémentées par PowerShell, et non par le développeur d’applets de commande, et sont automatiquement disponibles pour n’importe quelle applet de commande.

Vous pouvez utiliser les paramètres communs avec n’importe quelle applet de commande, mais ils peuvent ne pas avoir d’effet sur toutes les applets de commande. Par exemple, si une applet de commande ne génère pas de sortie détaillée, l’utilisation du paramètre commun **Verbose** n’a aucun effet.

Les paramètres communs sont également disponibles sur les fonctions avancées qui utilisent l’attribut **CmdletBinding** ou l’attribut **Parameter** .

Plusieurs paramètres communs remplacent les valeurs par défaut ou les préférences système que vous définissez à l’aide des variables de préférence PowerShell. Contrairement aux variables de préférence, les paramètres communs affectent uniquement les commandes dans lesquelles ils sont utilisés.

Pour plus d’informations, consultez [about_Preference_Variables](./about_Preference_Variables.md).

La liste suivante affiche les paramètres communs. Leurs alias sont répertoriés entre parenthèses.

- **Debug** (db)
- **ErrorAction** (EA)
- **ErrorVariable** (EV)
- **InformationAction** (INFA)
- **InformationVariable** (IV)
- En- **variable** (OV)
- **Mémoire tampon** (OB)
- **PipelineVariable** (PV)
- **Verbose** (VB)
- **WarningAction** (WA)
- **WarningVariable** (WV)

Les paramètres d' **action** sont des valeurs de type **PréférenceAction** .
**PréférenceAction** est une énumération avec les valeurs suivantes :

| Nom             | Value |
|------------------|-------|
| Interrompre          | 5     |
| Ignorer           | 4     |
| Inquire          | 3     |
| Continuer         | 2     |
| Arrêter             | 1     |
| SilentlyContinue | 0     |

Vous pouvez utiliser le nom ou la valeur avec le paramètre.

En plus des paramètres communs, de nombreuses applets de commande offrent des paramètres d’atténuation des risques. Les applets de commande qui impliquent un risque pour le système ou pour des données utilisateur proposent généralement ces paramètres.

Les paramètres d’atténuation des risques sont les suivants :

- **WhatIf** (Wi)
- **Confirmer** (CF)

### <a name="common-parameter-descriptions"></a>DESCRIPTIONS DES PARAMÈTRES COMMUNS

#### <a name="debug"></a>Débogage

Affiche des détails au niveau du programmeur sur l’opération effectuée par la commande. Ce paramètre fonctionne uniquement lorsque la commande génère un message de débogage. Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Debug` applet de commande.

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Par défaut, les messages de débogage ne s’affichent pas, car la valeur de la `$DebugPreference` variable est **SilentlyContinue**.

En mode interactif, le paramètre de **débogage** remplace la valeur de la `$DebugPreference` variable pour la commande actuelle, en affectant à la valeur `$DebugPreference` **inquire**.

En mode non interactif, le paramètre de **débogage** remplace la valeur de la `$DebugPreference` variable pour la commande actuelle, en affectant la valeur `$DebugPreference` à **continue**.

`-Debug:$true` a le même effet que `-Debug` . Utilisez `-Debug:$false` pour supprimer l’affichage des messages de débogage lorsque `$DebugPreference` n’est pas **SilentlyContinue**, qui est la valeur par défaut.

#### <a name="erroraction"></a>ErrorAction

Détermine la façon dont l’applet de commande répond à une erreur sans fin d’achèvement de la commande.
Ce paramètre fonctionne uniquement lorsque la commande génère une erreur sans fin d’achèvement, telle que celles de l' `Write-Error` applet de commande.

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Le paramètre **ErrorAction** remplace la valeur de la `$ErrorActionPreference` variable pour la commande actuelle. Étant donné que la valeur par défaut de la `$ErrorActionPreference` variable est **continue**, les messages d’erreur s’affichent et l’exécution se poursuit, sauf si vous utilisez le paramètre **ErrorAction** .

Le paramètre **ErrorAction** n’a aucun effet sur les erreurs de fin (telles que les données manquantes, les paramètres qui ne sont pas valides ou les autorisations insuffisantes) qui empêchent une commande de se terminer correctement.

`-ErrorAction:Continue` Affichez le message d’erreur et poursuivez l’exécution de la commande. `Continue` est la valeur par défaut.

`-ErrorAction:Ignore` supprime le message d’erreur et poursuit l’exécution de la commande. Contrairement à **SilentlyContinue**, **ignore** n’ajoute pas le message d’erreur à la `$Error` variable automatique. La valeur **ignorée** est introduite dans PowerShell 3,0.

`-ErrorAction:Inquire` affiche le message d’erreur et vous invite à confirmer avant de poursuivre l’exécution. Cette valeur est rarement utilisée.

`-ErrorAction:SilentlyContinue` supprime le message d’erreur et poursuit l’exécution de la commande.

`-ErrorAction:Stop` affiche le message d’erreur et arrête l’exécution de la commande.

`-ErrorAction:Suspend` est uniquement disponible pour les flux de travail qui ne sont pas pris en charge dans PowerShell 6 et les versions ultérieures.

> [!NOTE]
> Le paramètre **ErrorAction** substitue, mais ne remplace pas la valeur de la `$ErrorAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.

#### <a name="errorvariable"></a>ErrorVariable

**ErrorVariable** stocke les messages d’erreur relatifs à la commande dans la variable spécifiée et dans la `$Error` variable automatique. Pour plus d’informations, consultez [about_Automatic_Variables](about_Automatic_Variables.md)

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Par défaut, les nouveaux messages d’erreur remplacent les messages d’erreur qui sont déjà stockés dans la variable. Pour ajouter le message d’erreur au contenu de la variable, tapez un signe plus ( `+` ) avant le nom de la variable.

Par exemple, la commande suivante crée la `$a` variable et y stocke les erreurs :

```powershell
Get-Process -Id 6 -ErrorVariable a
```

La commande suivante ajoute tous les messages d’erreur à la `$a` variable :

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

La commande suivante affiche le contenu de `$a` :

```powershell
$a
```

Vous pouvez utiliser ce paramètre pour créer une variable qui contient uniquement des messages d’erreur de commandes spécifiques et n’affecte pas le comportement de la `$Error` variable automatique. La `$Error` variable automatique contient des messages d’erreur de toutes les commandes de la session. Vous pouvez utiliser la notation de tableau, telle que `$a[0]` ou, `$error[1,2]` pour faire référence à des erreurs spécifiques stockées dans les variables.

> [!NOTE]
> La variable d’erreur personnalisée contient toutes les erreurs générées par la commande, y compris les erreurs des appels à des fonctions ou des scripts imbriqués.

#### <a name="informationaction"></a>InformationAction

Introduit dans PowerShell 5,0. Dans la commande ou le script dans lequel elle est utilisée, le paramètre commun **InformationAction** remplace la valeur de la `$InformationPreference` variable de préférence, qui est définie par défaut sur **SilentlyContinue**. Lorsque vous utilisez `Write-Information` dans un script avec **InformationAction**, les `Write-Information` valeurs sont affichées en fonction de la valeur du paramètre **InformationAction** . Pour plus d’informations sur `$InformationPreference` , consultez [about_Preference_Variables](./about_Preference_Variables.md).

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

`-InformationAction:Stop` arrête une commande ou un script à une occurrence de la `Write-Information` commande.

`-InformationAction:Ignore` supprime le message d’information et poursuit l’exécution de la commande. Contrairement à **SilentlyContinue**, **ignore** complètement le message d’information ; elle n’ajoute pas le message d’information au flux d’informations.

`-InformationAction:Inquire` affiche le message d’information que vous spécifiez dans une `Write-Information` commande, puis vous demande si vous souhaitez continuer.

`-InformationAction:Continue` affiche le message d’information et poursuit son exécution.

`-InformationAction:Suspend` n’est pas pris en charge sur PowerShell Core, car il n’est disponible que pour les flux de travail.

`-InformationAction:SilentlyContinue` aucun effet, car le message d’information n’est pas (valeur par défaut) s’affiche et le script se poursuit sans interruption.

> [!NOTE]
> Le paramètre **InformationAction** substitue, mais ne remplace pas la valeur de la `$InformationAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.

#### <a name="informationvariable"></a>InformationVariable

Introduit dans PowerShell 5,0. Dans la commande ou le script dans lequel elle est utilisée, le paramètre commun **InformationVariable** stocke dans une variable une chaîne que vous spécifiez en ajoutant la `Write-Information` commande. `Write-Information` les valeurs sont affichées en fonction de la valeur du paramètre commun **InformationAction** ; Si vous n’ajoutez pas le paramètre commun **InformationAction** , les `Write-Information` chaînes sont affichées en fonction de la valeur de la `$InformationPreference` variable de préférence. Pour plus d’informations sur `$InformationPreference` , consultez [about_Preference_Variables](./about_Preference_Variables.md).

> [!NOTE]
> La variable d’informations contient tous les messages d’information générés par la commande, y compris les messages d’informations provenant d’appels à des fonctions ou des scripts imbriqués.

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a>OutBuffer

Détermine le nombre d’objets à accumuler dans une mémoire tampon avant l’envoi des objets via le pipeline. Si vous omettez ce paramètre, les objets sont envoyés lorsqu’ils sont générés.

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Ce paramètre de gestion des ressources est conçu pour les utilisateurs expérimentés. Lorsque vous utilisez ce paramètre, PowerShell envoie des données à l’applet de commande suivante dans des lots de `OutBuffer + 1` .

L’exemple suivant montre comment afficher entre `ForEach-Object` les blocs pour traiter les blocs qui utilisent l’applet de commande `Write-Host` . L’affichage alterne dans les lots de 2 ou `OutBuffer + 1` .

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a>OutVariable

Stocke les objets de sortie de la commande dans la variable spécifiée, en plus de l’envoi de la sortie le long du pipeline.

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Pour ajouter la sortie à la variable, au lieu de remplacer une sortie qui peut déjà y être stockée, tapez un signe plus ( `+` ) avant le nom de la variable.

Par exemple, la commande suivante crée la `$out` variable et y stocke l’objet processus :

```powershell
Get-Process PowerShell -OutVariable out
```

La commande suivante ajoute l’objet processus à la `$out` variable :

```powershell
Get-Process iexplore -OutVariable +out
```

La commande suivante affiche le contenu de la `$out` variable :

```powershell
$out
```

> [!NOTE]
> La variable créée par le paramètre de la variable de la **variable** est un `[System.Collections.ArrayList]` .

#### <a name="pipelinevariable"></a>PipelineVariable

**PipelineVariable** stocke la valeur de l’élément de pipeline actuel sous la forme d’une variable, pour toute commande nommée à travers le pipeline.

>[!NOTE]
> Les fonctions avancées peuvent comporter jusqu’à trois blocs de script : `begin` , `process` et `end` . Lors de l’utilisation du paramètre **PipelineVariable** avec des fonctions avancées, seules les valeurs du premier bloc de script défini sont affectées à la variable lors de l’exécution de la fonction. Pour plus d’informations, consultez [fonctions avancées](./about_functions_advanced.md).
> PowerShell 7,2 corrige ce comportement.

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Les valeurs valides sont les chaînes, les mêmes que pour les noms de variable.

Voici un exemple de fonctionnement de **PipelineVariable** . Dans cet exemple, le paramètre **PipelineVariable** est ajouté à une `Foreach-Object` commande pour stocker les résultats de la commande dans les variables. Une plage de nombres, de 1 à 10, est dirigée vers la première `Foreach-Object` commande, dont les résultats sont stockés dans une variable nommée **Left**.

Les résultats de la première `Foreach-Object` commande sont dirigés vers une deuxième `Foreach-Object` commande, qui filtre les objets retournés par la première `Foreach-Object` commande. Les résultats de la deuxième commande sont stockés dans une variable nommée **Right**.

Dans la troisième `Foreach-Object` commande, les résultats des deux premières `Foreach-Object` commandes dirigées, représentées par les variables **Left** et **Right**, sont traités à l’aide d’un opérateur de multiplication. La commande indique que les objets stockés dans les variables de **gauche** et de **droite** doivent être multipliés, et spécifie que les résultats doivent être affichés sous la forme « membre de la plage de gauche * membre de la plage droite = produit ».

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a>Commentaires

Affiche des informations détaillées sur l’opération effectuée par la commande. Ces informations sont semblables aux informations contenues dans une trace ou dans un journal des transactions. Ce paramètre fonctionne uniquement lorsque la commande génère un message détaillé. Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Verbose` applet de commande.

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Le paramètre **Verbose** remplace la valeur de la `$VerbosePreference` variable pour la commande actuelle. Étant donné que la valeur par défaut de la `$VerbosePreference` variable est **SilentlyContinue**, les messages détaillés ne sont pas affichés par défaut.

`-Verbose:$true` a le même effet que `-Verbose`

`-Verbose:$false` supprime l’affichage des messages détaillés. Utilisez ce paramètre lorsque la valeur de `$VerbosePreference` n’est pas **SilentlyContinue** (valeur par défaut).

#### <a name="warningaction"></a>WarningAction

Détermine la façon dont l’applet de commande répond à un avertissement de la commande. **Continue** est la valeur par défaut. Ce paramètre fonctionne uniquement lorsque la commande génère un message d’avertissement. Par exemple, ce paramètre fonctionne quand une commande contient l' `Write-Warning` applet de commande.

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Le paramètre **WarningAction** remplace la valeur de la `$WarningPreference` variable pour la commande actuelle. Étant donné que la valeur par défaut de la `$WarningPreference` variable est **continue**, les avertissements sont affichés et l’exécution se poursuit, sauf si vous utilisez le paramètre **WarningAction** .

`-WarningAction:Continue` affiche les messages d’avertissement et poursuit l’exécution de la commande. `Continue` est la valeur par défaut.

`-WarningAction:Inquire` affiche le message d’avertissement et vous invite à confirmer l’exécution. Cette valeur est rarement utilisée.

`-WarningAction:SilentlyContinue` supprime le message d’avertissement et poursuit l’exécution de la commande.

`-WarningAction:Stop` affiche le message d’avertissement et arrête l’exécution de la commande.

> [!NOTE]
> Le paramètre **WarningAction** substitue, mais ne remplace pas la valeur de la `$WarningAction` variable de préférence lorsque le paramètre est utilisé dans une commande pour exécuter un script ou une fonction.

#### <a name="warningvariable"></a>WarningVariable

Stocke les avertissements relatifs à la commande dans la variable spécifiée.

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

Tous les avertissements générés sont enregistrés dans la variable même si les avertissements ne sont pas affichés à l’utilisateur.

Pour ajouter les avertissements au contenu de la variable, au lieu de remplacer les avertissements qui peuvent déjà y être stockés, tapez un signe plus ( `+` ) avant le nom de la variable.

Par exemple, la commande suivante crée la `$a` variable et y stocke tous les avertissements :

```powershell
Get-Process -Id 6 -WarningVariable a
```

La commande suivante ajoute tous les avertissements à la `$a` variable :

```powershell
Get-Process -Id 2 -WarningVariable +a
```

La commande suivante affiche le contenu de `$a` :

```powershell
$a
```

Vous pouvez utiliser ce paramètre pour créer une variable qui contient uniquement les avertissements de commandes spécifiques. Vous pouvez utiliser la notation de tableau, telle que `$a[0]` ou, `$warning[1,2]` pour faire référence à des avertissements spécifiques stockés dans la variable.

> [!NOTE]
> La variable d’avertissement contient tous les avertissements générés par la commande, y compris les avertissements liés aux appels à des fonctions ou des scripts imbriqués.

### <a name="risk-management-parameter-descriptions"></a>Descriptions des paramètres de gestion des risques

#### <a name="whatif"></a>WhatIf

Affiche un message qui décrit l’effet de la commande, au lieu d’exécuter la commande.

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

Le paramètre **WhatIf** remplace la valeur de la `$WhatIfPreference` variable pour la commande actuelle. Étant donné que la valeur par défaut de la `$WhatIfPreference` variable est 0 (désactivé), le comportement **WhatIf** n’est pas effectué sans le paramètre **WhatIf** . Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md)

`-WhatIf:$true` a le même effet que `-WhatIf` .

`-WhatIf:$false` supprime le comportement WhatIf automatique qui se produit lorsque la valeur de la `$WhatIfPreference` variable est 1.

Par exemple, la commande suivante utilise le `-WhatIf` paramètre dans une `Remove-Item` commande :

```powershell
Remove-Item Date.csv -WhatIf
```

Au lieu de supprimer l’élément, PowerShell répertorie les opérations qu’il ferait et les éléments qui seraient affectés. Cette commande génère la sortie suivante :

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a>Confirmer

Demande une confirmation avant d'exécuter la commande.

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

Le paramètre **Confirm** remplace la valeur de la `$ConfirmPreference` variable pour la commande actuelle. La valeur par défaut est true. Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md)

`-Confirm:$true` a le même effet que `-Confirm` .

`-Confirm:$false` supprime la confirmation automatique, qui se produit lorsque la valeur de `$ConfirmPreference` est inférieure ou égale au risque estimé de l’applet de commande.

Par exemple, la commande suivante utilise le paramètre **Confirm** avec une `Remove-Item` commande. Avant de supprimer l’élément, PowerShell répertorie les opérations qu’il ferait et les éléments qui seraient affectés et demande l’approbation.

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

Les options de confirmation de la réponse sont les suivantes :

|response       |Résultats                                                     |
|---------------|-----------------------------------------------------------|
|Oui (Y)        |Effectuez l’action.                                        |
|Oui pour tout (A) |Effectuer toutes les actions et supprimer les requêtes Confirm suivantes|
|               |pour cette commande.                                          |
|Non (N) :        |N’effectuez pas l’action.                                 |
|Non pour tout (L) : |Ne pas effectuer d’actions et supprimer la confirmation suivante |
|               |requêtes pour cette commande.                                  |
|Interruption (S) :   |Suspendez la commande et créez une session temporaire.          |
|Aide ( ?)       |Affichez l’aide pour ces options.                            |

L’option **suspend** place la commande en attente et crée une session imbriquée temporaire dans laquelle vous pouvez travailler jusqu’à ce que vous soyez prêt à choisir une option de **confirmation** . L’invite de commandes pour la session imbriquée comporte deux signes (>>) supplémentaires pour indiquer qu’il s’agit d’une opération enfant de la commande parent d’origine. Vous pouvez exécuter des commandes et des scripts dans la session imbriquée. Pour mettre fin à la session imbriquée et revenir aux options Confirm pour la commande d’origine, tapez « exit ».

Dans l’exemple suivant, l’option **suspend** (S) est utilisée pour arrêter temporairement une commande pendant que l’utilisateur vérifie l’aide d’un paramètre de commande. Une fois les informations nécessaires recueillies, l’utilisateur tape « Exit » pour terminer l’invite imbriquée, puis sélectionne la réponse oui (y) à la requête Confirm.

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a>MOT

about_Common_Parameters

## <a name="see-also"></a>VOIR AUSSI

[about_Preference_Variables](about_Preference_Variables.md)

[Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)

[Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)

[Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)

[Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
