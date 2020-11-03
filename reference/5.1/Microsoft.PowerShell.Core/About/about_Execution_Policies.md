---
description: Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Execution_Policies
ms.openlocfilehash: 3332adb76c76fa644d23060abe2af43bd45a15a6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208042"
---
# <a name="about-execution-policies"></a>À propos des stratégies d’exécution

## <a name="short-description"></a>Description courte

Décrit les stratégies d’exécution de PowerShell et explique comment les gérer.

## <a name="long-description"></a>Description longue

La stratégie d’exécution de PowerShell est une fonctionnalité de sécurité qui contrôle les conditions dans lesquelles PowerShell charge les fichiers de configuration et exécute des scripts. Cette fonctionnalité permet d’éviter l’exécution de scripts malveillants.

Sur un ordinateur Windows, vous pouvez définir une stratégie d’exécution pour l’ordinateur local, pour l’utilisateur actuel ou pour une session particulière. Vous pouvez également utiliser un paramètre de stratégie de groupe pour définir des stratégies d’exécution pour les ordinateurs et les utilisateurs.

Les stratégies d’exécution de l’ordinateur local et de l’utilisateur actuel sont stockées dans le registre. Vous n’avez pas besoin de définir des stratégies d’exécution dans votre profil PowerShell.
La stratégie d’exécution pour une session particulière est stockée uniquement en mémoire et est perdue lorsque la session est fermée.

La stratégie d’exécution n’est pas un système de sécurité qui restreint les actions des utilisateurs. Par exemple, les utilisateurs peuvent facilement contourner une stratégie en tapant le contenu du script sur la ligne de commande lorsqu’ils ne peuvent pas exécuter un script. Au lieu de cela, la stratégie d’exécution aide les utilisateurs à définir des règles de base et les empêche de les violer involontairement.

## <a name="powershell-execution-policies"></a>Stratégies d’exécution de PowerShell

Les stratégies d’exécution de PowerShell sont les suivantes :

### <a name="allsigned"></a>AllSigned

- Les scripts peuvent s’exécuter.
- nécessite que tous les scripts et fichiers de configuration soient signés par un éditeur approuvé, y compris les scripts que vous écrivez sur l'ordinateur local.
- Vous invite à confirmer l’exécution des scripts des serveurs de publication que vous n’avez pas encore classés comme approuvés ou non approuvés.
- Risques liés à l’exécution de scripts signés, mais malveillants.

### <a name="bypass"></a>Contournement

- rien n'est bloqué, et aucun avertissement, ni aucune invite ne s'affiche.
- Cette stratégie d’exécution est conçue pour les configurations dans lesquelles un script PowerShell est intégré à une application plus volumineuse ou pour les configurations dans lesquelles PowerShell est la base d’un programme qui possède son propre modèle de sécurité.

### <a name="default"></a>Default

- Définit la stratégie d’exécution par défaut.
- **Limité** pour les clients Windows.
- **RemoteSigned** pour les serveurs Windows.

### <a name="remotesigned"></a>RemoteSigned

- Stratégie d’exécution par défaut pour les ordinateurs Windows Server.
- Les scripts peuvent s’exécuter.
- Requiert une signature numérique d’un éditeur approuvé sur les scripts et les fichiers de configuration téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.
- Ne requiert pas de signatures numériques sur les scripts écrits sur l’ordinateur local et non téléchargés à partir d’Internet.
- Exécute les scripts qui sont téléchargés à partir d’Internet et non signés, si les scripts sont débloqués, par exemple à l’aide de l’applet de commande `Unblock-File` .
- Risques liés à l’exécution de scripts non signés provenant de sources autres que l’Internet et scripts signés pouvant être malveillants.

### <a name="restricted"></a>Limitées

- Stratégie d’exécution par défaut pour les ordinateurs clients Windows.
- Autorise des commandes individuelles, mais n’autorise pas les scripts.
- Empêche l’exécution de tous les fichiers de script, y compris les fichiers de mise en forme et de configuration ( `.ps1xml` ), les fichiers de script de module ( `.psm1` ) et les profils PowerShell ( `.ps1` ).

### <a name="undefined"></a>Indéfini

- Aucune stratégie d’exécution n’est définie dans l’étendue actuelle.
- Si la stratégie d’exécution dans toutes les portées n’est **pas définie** , la stratégie d’exécution effective est **limitée** pour les clients Windows et **RemoteSigned** pour Windows Server.

### <a name="unrestricted"></a>Non restreint

- Les scripts non signés peuvent s’exécuter. L’exécution de scripts malveillants présente un risque.
- Avertit l’utilisateur avant d’exécuter des scripts et des fichiers de configuration qui ne proviennent pas de la zone Intranet local.

> [!NOTE]
> Sur les systèmes qui ne distinguent pas les chemins d’accès UNC (Universal Naming Convention) des chemins Internet, les scripts identifiés par un chemin d’accès UNC peuvent ne pas être autorisés à s’exécuter avec la stratégie d’exécution **RemoteSigned** .

## <a name="execution-policy-scope"></a>Étendue de la stratégie d’exécution

Vous pouvez définir une stratégie d’exécution qui est effective uniquement dans une étendue particulière.

Les valeurs valides pour **scope** sont **MachinePolicy** , **UserPolicy** , **Process** , **CurrentUser** et **LocalMachine** . **LocalMachine** est la valeur par défaut lors de la définition d’une stratégie d’exécution.

Les valeurs d' **étendue** sont répertoriées par ordre de priorité. La stratégie qui est prioritaire est effective dans la session active, même si une stratégie plus restrictive a été définie à un niveau de priorité inférieur.

Pour plus d’informations, consultez [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy).

### <a name="machinepolicy"></a>MachinePolicy

Défini par un stratégie de groupe pour tous les utilisateurs de l’ordinateur.

### <a name="userpolicy"></a>UserPolicy

Défini par un stratégie de groupe pour l’utilisateur actuel de l’ordinateur.

### <a name="process"></a>Process

L’étendue du **processus** affecte uniquement la session PowerShell active. La stratégie d’exécution est enregistrée dans la variable d’environnement `$env:PSExecutionPolicyPreference` , plutôt que dans le registre. Une fois la session PowerShell fermée, la variable et la valeur sont supprimées.

### <a name="currentuser"></a>Utilisateur en cours

la stratégie d'exécution affecte uniquement l'utilisateur actuel. Elle est stockée dans la sous-clé de Registre **HKEY_CURRENT_USER** .

### <a name="localmachine"></a>LocalMachine

La stratégie d’exécution affecte tous les utilisateurs sur l’ordinateur actuel. Elle est stockée dans la sous-clé de Registre **HKEY_LOCAL_MACHINE** .

## <a name="managing-the-execution-policy-with-powershell"></a>Gestion de la stratégie d’exécution avec PowerShell

Pour obtenir la stratégie d’exécution effective pour la session PowerShell actuelle, utilisez l’applet de commande `Get-ExecutionPolicy` .

La commande suivante obtient la stratégie d’exécution effective :

```powershell
Get-ExecutionPolicy
```

Pour obtenir toutes les stratégies d’exécution qui affectent la session active et les afficher dans l’ordre de priorité :

```powershell
Get-ExecutionPolicy -List
```

Le résultat ressemble à l’exemple de sortie suivant :

```Output
        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser    RemoteSigned
 LocalMachine       AllSigned
```

Dans ce cas, la stratégie d’exécution effective est **RemoteSigned** car la stratégie d’exécution de l’utilisateur actuel est prioritaire sur la stratégie d’exécution définie pour l’ordinateur local.

Pour obtenir la stratégie d’exécution définie pour une étendue particulière, utilisez le paramètre **scope** de `Get-ExecutionPolicy` .

Par exemple, la commande suivante obtient la stratégie d’exécution pour l’étendue **CurrentUser** :

```powershell
Get-ExecutionPolicy -Scope CurrentUser
```

### <a name="change-the-execution-policy"></a>Modifier la stratégie d’exécution

Pour modifier la stratégie d’exécution de PowerShell sur votre ordinateur Windows, utilisez l’applet de commande `Set-ExecutionPolicy` . La modification prend effet immédiatement. Vous n’avez pas besoin de redémarrer PowerShell.

Si vous définissez la stratégie d’exécution pour les étendues **LocalMachine** ou **CurrentUser** , la modification est enregistrée dans le registre et reste effective jusqu’à ce que vous la modifiiez de nouveau.

Si vous définissez la stratégie d’exécution pour l’étendue du **processus** , celle-ci n’est pas enregistrée dans le registre. La stratégie d’exécution est conservée jusqu’à la fermeture du processus en cours et de tous les processus enfants.

> [!NOTE]
> Dans Windows Vista et les versions ultérieures de Windows, pour exécuter des commandes qui modifient la stratégie d’exécution pour l’ordinateur local, l’étendue **LocalMachine** , démarrez PowerShell avec l’option **exécuter en tant qu’administrateur** .

Pour modifier votre stratégie d’exécution :

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName>
```

Par exemple :

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

Pour définir la stratégie d’exécution dans une étendue particulière :

```powershell
Set-ExecutionPolicy -ExecutionPolicy <PolicyName> -Scope <scope>
```

Par exemple :

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Une commande pour modifier une stratégie d’exécution peut être exécutée, mais ne modifie toujours pas la stratégie d’exécution en vigueur.

Par exemple, une commande qui définit la stratégie d’exécution de l’ordinateur local peut être exécutée, mais être remplacée par la stratégie d’exécution de l’utilisateur actuel.

### <a name="remove-the-execution-policy"></a>Supprimer la stratégie d’exécution

Pour supprimer la stratégie d’exécution d’une étendue particulière, définissez la stratégie d’exécution sur **non définie** .

Par exemple, pour supprimer la stratégie d’exécution pour tous les utilisateurs de l’ordinateur local :

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope LocalMachine
```

Pour supprimer la stratégie d’exécution d’une **étendue** :

```powershell
Set-ExecutionPolicy -ExecutionPolicy Undefined -Scope CurrentUser
```

Si aucune stratégie d’exécution n’est définie dans une étendue, la stratégie d’exécution en vigueur est **Restricted** , ce qui correspond à la valeur par défaut pour les clients Windows.

### <a name="set-a-different-policy-for-one-session"></a>Définir une stratégie différente pour une session

Vous pouvez utiliser le paramètre **ExecutionPolicy** de **powershell.exe** pour définir une stratégie d’exécution pour une nouvelle session PowerShell. La stratégie affecte uniquement la session active et les sessions enfants.

Pour définir la stratégie d’exécution d’une nouvelle session, démarrez PowerShell sur la ligne de commande, par exemple **cmd.exe** ou à partir de PowerShell, puis utilisez le paramètre **ExecutionPolicy** de **powershell.exe** pour définir la stratégie d’exécution.

Par exemple :

```powershell
powershell.exe -ExecutionPolicy AllSigned
```

La stratégie d’exécution que vous définissez n’est pas stockée dans le registre. Au lieu de cela, il est stocké dans la `$env:PSExecutionPolicyPreference` variable d’environnement. La variable est supprimée lorsque vous fermez la session dans laquelle la stratégie est définie. Vous ne pouvez pas modifier la stratégie en modifiant la valeur de la variable.

Pendant la session, la stratégie d’exécution définie pour la session est prioritaire sur une stratégie d’exécution qui est définie dans le registre de l’ordinateur local ou de l’utilisateur actuel. Toutefois, il n’est pas prioritaire sur la stratégie d’exécution définie à l’aide d’un stratégie de groupe.

## <a name="use-group-policy-to-manage-execution-policy"></a>Utiliser stratégie de groupe pour gérer la stratégie d’exécution

Vous pouvez utiliser le paramètre **activer l’exécution du Script** stratégie de groupe pour gérer la stratégie d’exécution des ordinateurs de votre entreprise. Le paramètre stratégie de groupe remplace les stratégies d’exécution définies dans PowerShell dans toutes les étendues.

Les paramètres **de stratégie d’exécution de script** sont les suivants :

- Si vous désactivez **l’exécution des** scripts, les scripts ne s’exécutent pas. Cela équivaut à la stratégie d’exécution **restreinte** .
- Si vous activez **activer l’exécution des scripts** , vous pouvez sélectionner une stratégie d’exécution. Les paramètres de stratégie de groupe sont équivalents aux paramètres de stratégie d’exécution suivants :

  | Stratégie de groupe                                  | Stratégie d’exécution |
  | --------------------------------------------- | ---------------- |
  | Autoriser tous les scripts                             | Non restreint     |
  | Autoriser les scripts locaux et les scripts signés distants | RemoteSigned     |
  | Autoriser uniquement les scripts signés                     | AllSigned        |

- Si **l’exécution du script** n’est pas configurée, elle n’a aucun effet. La stratégie d’exécution définie dans PowerShell est effective.

Les fichiers PowerShellExecutionPolicy. adm et PowerShellExecutionPolicy. admx ajoutent la stratégie d' **exécution de script activer** aux nœuds Configuration ordinateur et configuration utilisateur dans stratégie de groupe éditeur dans les chemins d’accès suivants.

Pour Windows XP et Windows Server 2003 :

Modèles d’administration\Composants Windows\windows PowerShell

Pour Windows Vista et les versions ultérieures de Windows :

Modèles d’administration d’administration Templates\Classic \
Windows Windows\windows PowerShell

Les stratégies définies dans le nœud Configuration de l’ordinateur sont prioritaires sur les stratégies définies dans le nœud Configuration utilisateur.

Pour plus d’informations, consultez [about_Group_Policy_Settings](about_Group_Policy_Settings.md).

### <a name="execution-policy-precedence"></a>Priorité de la stratégie d’exécution

Lors de la détermination de la stratégie d’exécution effective pour une session, PowerShell évalue les stratégies d’exécution dans l’ordre de priorité suivant :

- Stratégie de groupe : MachinePolicy
- Stratégie de groupe : UserPolicy
- Stratégie d’exécution : processus (ou `powershell.exe -ExecutionPolicy` )
- Stratégie d’exécution : CurrentUser
- Stratégie d’exécution : LocalMachine

## <a name="manage-signed-and-unsigned-scripts"></a>Gérer les scripts signés et non signés

Dans Windows, les programmes comme Internet Explorer et Microsoft Edge ajoutent un flux de données de remplacement aux fichiers téléchargés. Cela marque le fichier comme « provenant d’Internet ». Si votre stratégie d’exécution de PowerShell est **RemoteSigned** , PowerShell n’exécutera pas les scripts non signés téléchargés à partir d’Internet, y compris les programmes de messagerie et de messagerie instantanée.

Vous pouvez signer le script ou choisir d’exécuter un script non signé sans modifier la stratégie d’exécution.

À compter de PowerShell 3,0, vous pouvez utiliser le paramètre **Stream** de l' `Get-Item` applet de commande pour détecter les fichiers qui sont bloqués, car ils ont été téléchargés à partir d’Internet. Utilisez l' `Unblock-File` applet de commande pour débloquer les scripts afin de pouvoir les exécuter dans PowerShell.

Pour plus d’informations, consultez [about_Signing](about_Signing.md), [obtenir un élément](xref:Microsoft.PowerShell.Management.Get-Item)et [Unblock-file](xref:Microsoft.PowerShell.Utility.Unblock-File).

> [!NOTE]
> D’autres méthodes de téléchargement de fichiers peuvent ne pas marquer les fichiers comme provenant de la zone Internet. Voici quelques exemples :
>
> - `curl.exe`
> - `Invoke-RestMethod`
> - `Invoke-WebRequest`

## <a name="execution-policy-on-windows-server-core-and-window-nano-server"></a>Stratégie d’exécution sur Windows Server Core et Windows nano Server

Quand PowerShell 5,1 est exécuté sur Windows Server Core ou Windows nano Server sous certaines conditions, les stratégies d’exécution peuvent échouer avec l’erreur suivante :

```Output
AuthorizationManager check failed.
At line:1 char:1
+ C:\scriptpath\scriptname.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

PowerShell utilise des API dans Windows Desktop Shell ( `explorer.exe` ) pour valider la zone d’un fichier de script. L’interpréteur de commandes Windows n’est pas disponible sur Windows Server Core et sur Windows nano Server.

Vous pouvez également recevoir cette erreur sur n’importe quel système Windows si Windows Desktop Shell n’est pas disponible ou ne répond pas. Par exemple, lors de l’ouverture de session, un script d’ouverture de session PowerShell peut démarrer l’exécution avant que le bureau Windows soit prêt, provoquant ainsi un échec.

L’utilisation d’une stratégie d’exécution **Bypass** ou **AllSigned** ne nécessite pas de vérification de zone qui évite le problème.

## <a name="see-also"></a>Voir aussi

[about_Environment_Variables](about_Environment_Variables.md)

[about_Group_Policy_Settings](about_Group_Policy_Settings.md)

[about_Signing](about_Signing.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)

[ Aide Command-LinePowerShell.exe](about_PowerShell_exe.md)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Unblock-File](xref:Microsoft.PowerShell.Utility.Unblock-File)
