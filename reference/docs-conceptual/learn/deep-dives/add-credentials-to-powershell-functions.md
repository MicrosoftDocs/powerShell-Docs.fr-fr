---
title: Ajout de la prise en charge des informations d’identification aux fonctions PowerShell
description: Ajout des paramètres d’informations d’identification à vos scripts, fonctions et applets de commande PowerShell.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354624"
---
# <a name="add-credential-support-to-powershell-functions"></a>Ajout de la prise en charge des informations d’identification aux fonctions PowerShell

> [!NOTE]
> La [Version d’origine][] de cet article est parue sur le blog écrit par [@joshduffney][]. Cet article a été modifié pour être inclus sur ce site. L’équipe PowerShell remercie Josh d’avoir partagé ce contenu. Consultez son blog à l’adresse [duffney.io][].

Cet article explique comment (et pourquoi) ajouter des paramètres d’informations d’identification aux fonctions PowerShell. Un paramètre d’informations d'identification vous permet d’exécuter la fonction ou l’applet de commande en tant qu’autre utilisateur. L’utilisation la plus courante consiste à exécuter la fonction ou l’applet de commande en tant que compte d’utilisateur avec élévation de privilèges.

Par exemple, l’applet de commande `New-ADUser` inclut un paramètre d’ **informations d’identification** , qui fournit des informations d’identification d’administrateur de domaine pour créer un compte dans un domaine. On suppose que votre compte normal exécutant la session PowerShell ne dispose pas déjà de cet accès.

## <a name="creating-credential-object"></a>Création d’un objet d'informations d'identification

L’objet [PSCredential][] représente un ensemble d’informations d’identification de sécurité comme un nom d’utilisateur et un mot de passe. L’objet peut être passé en tant que paramètre à une fonction qui s’exécute en tant que compte d’utilisateur dans cet objet d’informations d’identification. Vous pouvez créer un objet d’informations d’identification de plusieurs façons. La première façon de créer un objet d’informations d’identification consiste à utiliser l’applet de commande PowerShell `Get-Credential`. Lorsque vous exécutez sans paramètres, vous êtes invité à entrer un nom d’utilisateur et un mot de passe. Ou vous pouvez appeler l’applet de commande avec quelques paramètres facultatifs.

Pour spécifier à l’avance le nom de domaine et le nom d’utilisateur, vous pouvez utiliser les paramètres **Credential** ou **UserName**. Quand vous utilisez le paramètre **UserName** , vous devez également fournir une valeur **Message**. Le code ci-dessous montre l’utilisation de l’applet de commande. Vous pouvez également stocker l’objet d’informations d’identification dans une variable afin de pouvoir utiliser les informations d’identification plusieurs fois. Dans l’exemple ci-dessous, l’objet d’informations d’identification est stocké dans la variable `$Cred`.

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

Parfois, vous ne pouvez pas utiliser la méthode interactive de création d’objets d’informations d’identification présentée dans l’exemple précédent. La plupart des outils d’automatisation requièrent une méthode non interactive. Pour créer des informations d’identification sans intervention de l’utilisateur, créez une chaîne sécurisée contenant le mot de passe. Passez ensuite la chaîne sécurisée et le nom d’utilisateur à la méthode `System.Management.Automation.PSCredential()`.

Utilisez la commande suivante pour créer une chaîne sécurisée contenant le mot de passe :

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

Les paramètres **AsPlainText** et **Force** sont requis. Sans ces paramètres, vous recevez un message d’avertissement indiquant que vous ne devez pas passer un texte brut dans une chaîne sécurisée. PowerShell retourne cet avertissement, car le mot de passe en texte brut est enregistré dans différents journaux. Une fois que vous avez créé une chaîne sécurisée, vous devez la passer à la méthode `PSCredential()` pour créer l’objet d’informations d’identification. Dans l’exemple suivant, la variable `$password` contient la chaîne sécurisée `$Cred` contenant l’objet d’informations d’identification.

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

Maintenant que vous savez comment créer des objets d’informations d’identification, vous pouvez ajouter des paramètres d’informations d’identification à vos fonctions PowerShell.

## <a name="adding-a-credential-parameter"></a>Ajout d’un paramètre Credential

Comme tout autre paramètre, vous commencez par l’ajouter dans le bloc `param` de votre fonction.
Il est recommandé de nommer le paramètre `$Credential`, car il s’agit du nom que les applets de commande PowerShell existantes utilisent. Le type de paramètre devrait être `[System.Management.Automation.PSCredential]`.

L’exemple suivant montre le bloc de paramètres pour une fonction appelée `Get-Something`. Ce bloc contient deux paramètres : `$Name` et `$Credential`.

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

Le code de cet exemple est suffisant pour avoir un paramètre d’informations d’identification fonctionnel, mais il existe quelques éléments que vous pouvez ajouter pour le rendre plus robuste.

- Ajoutez l’attribut de validation `[ValidateNotNull()]` pour vérifier la valeur passée à **Credential**. Si la valeur du paramètre est null, cet attribut empêche la fonction de s’exécuter avec des informations d’identification non valides.

- Ajoutez `[System.Management.Automation.Credential()]`. Cela vous permet de passer un nom d’utilisateur en tant que chaîne et d’obtenir une invite interactive pour le mot de passe.

- Attribuez au paramètre `$Credential` la valeur par défaut `[System.Management.Automation.PSCredential]::Empty`. Votre fonction vous permet de passer cet objet `$Credential` à des applets de commande PowerShell existantes. Si vous fournissez une valeur null à l’applet de commande appelée à l’intérieur de votre fonction, une erreur se produit. Pour éviter cette erreur, fournissez un objet d’informations d’identification vide.

> [!TIP]
> Certaines applets de commande qui acceptent un paramètre Credential ne prennent pas en charge `[System.Management.Automation.PSCredential]::Empty` comme elles le devraient. Pour obtenir une solution de contournement, consultez la section [Utilisation d’applets de commande héritées](#dealing-with-legacy-cmdlets).

## <a name="using-credential-parameters"></a>Utilisation des paramètres d’informations d’identification

L’exemple suivant illustre l’utilisation des paramètres d’informations d'identification. Cet exemple montre une fonction appelée `Set-RemoteRegistryValue`, tirée de [The Pester Book][]. Cette fonction définit le paramètre d’informations d’identification à l’aide des techniques décrites dans la section précédente. La fonction appelle `Invoke-Command` à l’aide de la variable `$Credential` créée par la fonction. Cela vous permet de modifier l’utilisateur qui exécute `Invoke-Command`. Étant donné que la valeur par défaut de `$Credential` est une information d’identification vide, la fonction peut s’exécuter sans fournir d’informations d’identification.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

Les sections suivantes présentent différentes méthodes permettant de fournir des informations d’identification à `Set-RemoteRegistryValue`.

### <a name="prompting-for-credentials"></a>Demande d’informations d’identification

L’utilisation de `Get-Credential` entre parenthèses `()` au moment de l’exécution lance en premier l’exécution de `Get-credential`. Vous êtes invité à entrer un nom d’utilisateur et un mot de passe. Vous pouvez utiliser les paramètres **Credential** ou **UserName** de `Get-credential` pour préremplir le nom d’utilisateur et le domaine. L’exemple suivant utilise une technique appelée « projection » pour passer des paramètres à la fonction `Set-RemoteRegistryValue`. Pour plus d’informations sur la projection, consultez l’article [about_Splatting][].

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Obtenir des informations d’identification au moment de l’exécution](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

L’utilisation de `(Get-Credential)` semble laborieuse. En règle générale, lorsque vous utilisez le paramètre **Credential** avec un nom d’utilisateur uniquement, l’applet de commande vous invite automatiquement à entrer le mot de passe. L’attribut `[System.Management.Automation.Credential()]` active ce comportement.

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Demander les informations d’identification](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> Pour définir la valeur de Registre indiquée, ces exemples supposent que vous avez installé les fonctionnalités **Serveur Web** de Windows. Exécutez `Install-WindowsFeature Web-Server` et `Install-WindowsFeature web-mgmt-tools` si nécessaire.

### <a name="provide-credentials-in-a-variable"></a>Fournir les informations d’identification dans une variable

Vous pouvez également remplir une variable d’informations d’identification à l’avance et la passer au paramètre **Credential** de la fonction `Set-RemoteRegistryValue`. Utilisez cette méthode avec les outils d’intégration continue / de déploiement continu (CI/CD) tels que Jenkins, TeamCity et Octopus Deploy. Pour obtenir un exemple d’utilisation de Jenkins, consultez le billet de blog de Hodge [Automating with Jenkins and PowerShell on Windows - Part 2][].

Cet exemple utilise la méthode .NET pour créer l’objet d’informations d’identification et une chaîne sécurisée pour passer le mot de passe.

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

Pour cet exemple, la chaîne sécurisée est créée à l’aide d’un mot de passe en texte clair. Tous les outils CI/CD mentionnés précédemment ont une méthode sécurisée pour fournir ce mot de passe au moment de l’exécution. Lorsque vous utilisez ces outils, remplacez le mot de passe en texte brut par la variable définie dans l’outil CI/CD que vous utilisez.

### <a name="run-without-credentials"></a>Exécuter sans informations d’identification

Comme `$Credential` est défini par défaut sur un objet d’informations d’identification vide, vous pouvez exécuter la commande sans informations d’identification, comme illustré dans cet exemple :

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a>Utilisation d’applets de commande héritées

Toutes les applets de commande ne prennent pas en charge les objets d’informations d’identification, ou n’autorisent pas les informations d’identification vides. Au lieu de cela, l’applet de commande exige que les paramètres de nom d'utilisateur et de mot de passe soient des chaînes. Il existe plusieurs façons de contourner cette limitation.

### <a name="using-if-else-to-handle-empty-credentials"></a>Utilisation de if-else pour gérer les informations d’identification vides

Dans ce scénario, l’applet de commande que vous souhaitez exécuter n’accepte pas d’objet d’informations d’identification vide. Cet exemple ajoute le paramètre **Credential** à `Invoke-Command` uniquement s’il n’est pas vide. Sinon, il exécute `Invoke-Command` sans le paramètre **Credential**.

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a>Utilisation de la projection pour gérer les informations d’identification vides

Cet exemple utilise la projection de paramètres pour appeler l’applet de commande héritée. L’objet `$Credential` est ajouté de manière conditionnelle à la table de hachage pour la projection, ce qui évite d’avoir à répéter le bloc de script `Invoke-Command`. Pour en savoir plus sur la projection à l’intérieur de fonctions, consultez le billet de blog [Splatting Parameters Inside Advanced Functions][].

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a>Utilisation de mots de passe de chaînes

L’applet de commande `Invoke-Sqlcmd` est un exemple d’applet de commande qui accepte une chaîne en tant que mot de passe.
`Invoke-Sqlcmd` vous permet d’exécuter les instructions SQL simples insert, update et delete. `Invoke-Sqlcmd` requiert un nom d’utilisateur et un mot de passe en texte clair plutôt qu’un objet d’informations d’identification plus sécurisé. Cet exemple montre comment extraire le nom d’utilisateur et le mot de passe d’un objet d’informations d’identification.

La fonction `Get-AllSQLDatabases` dans cet exemple appelle l’applet de commande `Invoke-Sqlcmd` pour interroger un serveur SQL Server afin d’obtenir toutes ses bases de données. La fonction définit un paramètre **Credential** avec le même attribut utilisé dans les exemples précédents. Étant donné que le nom d’utilisateur et le mot de passe existent dans la variable `$Credential`, vous pouvez extraire ces valeurs afin de les utiliser avec `Invoke-Sqlcmd`.

Le nom d’utilisateur est disponible dans la propriété **UserName** de la variable `$Credential`. Pour obtenir le mot de passe, vous devez utiliser la méthode `GetNetworkCredential()` de l’objet `$Credential`. Les valeurs sont extraites dans des variables ajoutées à une table de hachage utilisée pour les paramètres de projection vers `Invoke-Sqlcmd`.

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a>Apprentissage continu pour la gestion des informations d’identification

La création et le stockage d’objets d’informations d’identification de façon sécurisée peuvent être difficiles. Les ressources suivantes peuvent vous aider à gérer les informations d’identification PowerShell.

- [BetterCredentials][]
- [Azure Key Vault][]
- [Vault Project][]
- [Module SecretManagement][]

<!-- link references -->
[Version d’origine]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Vault Project]: https://www.vaultproject.io/
[Splatting Parameters Inside Advanced Functions]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[Module SecretManagement]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
