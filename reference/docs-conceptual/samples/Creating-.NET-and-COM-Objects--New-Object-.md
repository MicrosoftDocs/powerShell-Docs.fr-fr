---
ms.date: 06/05/2017
keywords: powershell,applet de commande
title: Création d’objets .NET et COM New Object
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: 1ffd8d4afa419ec0c24321e44aa4a2f41a9bee44
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402077"
---
# <a name="creating-net-and-com-objects-new-object"></a>Création d’objets .NET et COM (New-Object)

Il existe des composants logiciels avec des interfaces COM et .NET Framework, qui vous permettent d’effectuer de nombreuses tâches d’administration système. Windows PowerShell permet d’utiliser ces composants. Vous n’êtes donc pas limité aux tâches exécutables à l’aide d’applets de commande. La plupart des applets de commande dans la version initiale de Windows PowerShell ne fonctionnent pas sur des ordinateurs distants. Nous allons expliquer comment contourner cette limitation lors de la gestion des journaux des événements à l’aide de la classe .NET Framework **System.Diagnostics.EventLog** directement à partir de Windows PowerShell.

### <a name="using-new-object-for-event-log-access"></a>Utilisation de l’applet de commande New-Object pour l’accès au journal des événements

La bibliothèque de classes .NET Framework inclut une classe nommée **System.Diagnostics.EventLog** qui permet de gérer les journaux des événements. Vous pouvez créer une nouvelle instance d’une classe .NET Framework en utilisant l’applet de commande **New-Object** avec le paramètre **TypeName**. Par exemple, la commande suivante crée une référence de journal des événements :

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Même si la commande a créé une instance de la classe EventLog, l’instance n’inclut pas de données. Cela est dû au fait que nous n’avons pas spécifié de journal des événements spécifique. Comment obtenir un journal des événements réel ?

#### <a name="using-constructors-with-new-object"></a>Utilisation de constructeurs avec l’applet de commande New-Object

Pour faire référence à un journal des événements spécifique, vous devez spécifier son nom. L’applet de commande **New-Object** a un paramètre **ArgumentList**. Les arguments que vous passez en tant que valeurs pour ce paramètre sont utilisés par une méthode spéciale de démarrage de l’objet. La méthode est appelée *constructeur*, car elles est utilisée pour construire l’objet. Par exemple, pour obtenir une référence au journal des applications, vous spécifiez la chaîne « Application » en tant qu’argument :

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Étant donné que la plupart des classes de base de .NET Framework sont contenues dans l’espace de noms système, Windows PowerShell tente automatiquement de trouver les classes que vous spécifiez dans l’espace de noms système s’il ne trouve pas de correspondance pour le nom de type que vous spécifiez. Cela signifie que vous pouvez spécifier Diagnostics.EventLog au lieu de System.Diagnostics.EventLog.

#### <a name="storing-objects-in-variables"></a>Stockage d’objets dans des variables

Si vous souhaitez stocker une référence à un objet, vous pouvez l’utiliser dans l’interpréteur de commandes en cours. Bien que Windows PowerShell permette d’effectuer de nombreuses tâches avec des pipelines, en réduisant le besoin de variables, parfois, des références de stockage à des objets dans des variables facilite la manipulation de ces objets.

Windows PowerShell permet de créer des variables qui sont essentiellement des objets nommés. La sortie d’une commande Windows PowerShell valide peut être stockée dans une variable. Les noms de variables commencent toujours par $. Si vous souhaitez stocker la référence de journal des applications dans une variable nommée $AppLog, tapez le nom de la variable, suivi d’un signe égal, puis tapez la commande utilisée pour créer l’objet journal des applications :

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Si vous tapez $AppLog, vous pouvez voir qu’il contient le journal des applications :

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

#### <a name="accessing-a-remote-event-log-with-new-object"></a>Accès à un journal des événements à distance avec New-Object

Les commandes utilisées dans la section précédente ciblent l’ordinateur local. L’applet de commande **Get-EventLog** peut faire cela. Pour accéder au journal des applications sur un ordinateur distant, vous devez fournir le nom du journal et un nom d’ordinateur (ou une adresse IP) en tant qu’arguments.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Maintenant que nous avons une référence à un journal des événements stocké dans la variable $RemoteAppLog, quelles tâches pouvons-nous effectuer sur celui-ci ?

#### <a name="clearing-an-event-log-with-object-methods"></a>Effacement d’un journal des événements avec des méthodes d’objet

Les objets ont souvent des méthodes associées qui peuvent être appelées pour effectuer des tâches. L’applet de commande **Get-Member** permet d’afficher les méthodes associées à un objet. La commande suivante et la sortie sélectionnée affichent certaines des méthodes de la classe EventLog :

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

La méthode **Clear()** permet d’effacer le journal des événements. Lors de l’appel d’une méthode, vous devez toujours faire suivre le nom de la méthode par des parenthèses, même si la méthode ne requiert pas d’argument. Cela permet à Windows PowerShell de faire la distinction entre la méthode et une propriété éventuelle du même nom. Tapez ce qui suit pour appeler la méthode **clair** :

```
PS> $RemoteAppLog.Clear()
```

Tapez ce qui suit pour afficher le journal. Vous voyez que le journal des événements a été effacé et contient désormais 0 entrée au lieu de 262 :

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

### <a name="creating-com-objects-with-new-object"></a>Création d’objets COM avec New-Object
L’applet de commande **New-Object** permet d’utiliser des composants COM (Component Object Model). Les composants vont des différentes bibliothèques incluses dans l’environnement d’exécution de scripts WSH (Windows Script Host) aux applications ActiveX telles qu’Internet Explorer qui sont installées sur la plupart des systèmes.

L’applet de commande **New-Object** utilise des wrappers RCW (Runtime-Callable Wrappers) .NET Framework pour créer des objets COM. Elle est donc sujette aux mêmes limitations que .NET Framework lors de l’appel d’objets COM. Pour créer un objet COM, vous devez spécifier le paramètre **ComObject** avec l’identificateur programmatique, ou *ProgId*, de la classe COM que vous souhaitez utiliser. Une description complète des limitations de l’utilisation de COM et de la détermination des ProgID disponibles sur un système dépasserait la portée de ce guide, mais la plupart des objets bien connus d’environnements tels que WSH peuvent être utilisés dans Windows PowerShell.

Vous pouvez créer les objets WSH en spécifiant les ProgID : **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, et **Scripting.FileSystemObject**. Les commandes suivantes créent ces objets :

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Si l’essentiel de la fonctionnalité de ces classes est rendu disponible par d’autres moyens dans Windows PowerShell, quelques tâches telles que la création de raccourci sont encore plus faciles à effectuer à l’aide des classes WSH.

### <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Création d’un raccourci sur le Bureau avec WScript.Shell

Une tâche exécutable rapidement avec un objet COM est la création d’un raccourci. Supposons que vous souhaitez créer un raccourci sur votre bureau, qui établit un lien vers le dossier de base de Windows PowerShell. Vous devez commencer par créer une référence à **WScript.Shell**, que nous allons stocker dans une variable nommée **$WshShell** :

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

L’applet de commande Get-Member fonctionnant avec des objets COM, vous pouvez explorer les membres de l’objet en tapant ce qui suit :

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

L’applet de commande **Get-Member** dispose d’un paramètre facultatif, **InputObject**, que vous pouvez utiliser à la place d’un piping pour fournir l’entrée à **Get-Member**. Vous obtiendriez la même sortie que celle indiquée ci-dessus si vous utilisez à la place la commande **Get-Member -InputObject $WshShell**. Si vous utilisez **InputObject**, l’argument est traité comme un seul élément. Cela signifie que, si vous disposez de plusieurs objets dans une variable, l’applet de commande **Get-Member** les traite comme un tableau d’objets. Par exemple :

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

La méthode **WScript.Shell CreateShortcut** accepte un seul argument, le chemin d’accès au fichier de raccourci à créer. Nous pourrions taper le chemin d’accès complet au bureau, mais il existe un moyen plus simple. Le bureau est généralement représenté par un dossier nommé Bureau à l’intérieur du dossier de base de l’utilisateur actuel. Windows PowerShell dispose d’une variable **$Home** qui contient le chemin d’accès à ce dossier. Nous pouvons spécifier le chemin d’accès au dossier de base à l’aide de cette variable, puis ajouter le nom du dossier Bureau et le nom du raccourci à créer en tapant ce qui suit :

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Lorsque vous utilisez quelque chose ressemblant à un nom de variable entre guillemets doubles, Windows PowerShell tente de remplacer cet élément par une valeur correspondante. Si vous utilisez des guillemets simples, Windows PowerShell n’essaie pas de remplacer la variable par une valeur. Par exemple, essayez de taper les commandes suivantes :

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Nous avons désormais une variable nommée **$lnk** qui contient une nouvelle référence au raccourci. Si vous souhaitez voir ses membres, vous pouvez la canaliser vers l’applet de commande **Get-Member**. La sortie ci-dessous montre les membres que nous devons utiliser pour achever la création de notre raccourci :

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

Nous devons spécifier **TargetPath**, qui est le dossier d’application pour Windows PowerShell, puis enregistrer le raccourci **$lnk** en appelant la méthode **Save**. Le chemin d’accès au dossier d’application de Windows PowerShell étant stocké dans la variable **$PSHome**, nous pouvons faire cela en tapant ce qui suit :

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

### <a name="using-internet-explorer-from-windows-powershell"></a>Utilisation d’Internet Explorer à partir de Windows PowerShell

De nombreuses applications (dont la famille d’applications Microsoft Office et Internet Explorer) peuvent être automatisées à l’aide de COM. Internet Explorer illustre certains problèmes et techniques classiques impliqués dans l’utilisation d’applications basées sur COM.

Vous créez une instance Internet Explorer en spécifiant le ProgId d’Internet Explorer, **InternetExplorer.Application** :

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Cette commande démarre Internet Explorer, mais ne le rend pas visible. Si vous tapez Get-Process, vous pouvez voir qu’un processus nommé iexplore est en cours d’exécution. En fait, si vous quittez Windows PowerShell, le processus continue à s’exécuter. Pour arrêter le processus iexplore, vous devez redémarrer l’ordinateur ou utiliser un outil tel que le Gestionnaire des tâches.

> [!NOTE]
> Les objets COM qui démarrent en tant que processus séparés, généralement appelés *exécutables ActiveX*, peuvent ou non afficher une fenêtre d’interface utilisateur au démarrage. S’ils créent une fenêtre, comme Internet Explorer, mais ne la rendent pas visible, le focus se positionne généralement sur le Bureau Windows, et vous devez rendre la fenêtre visible pour pouvoir interagir avec elle.

Pour afficher les propriétés et méthodes pour Internet Explorer, tapez **$ie | Get-Member**. Pour afficher la fenêtre Internet Explorer, définissez la propriété Visible sur $true en tapant ce qui suit :

```powershell
$ie.Visible = $true
```

Vous pouvez ensuite accéder à une adresse web spécifique à l’aide de la méthode Navigate :

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

En utilisant d’autres membres du modèle d’objet Internet Explorer, vous pouvez récupérer le contenu de texte de la page web. La commande suivante affiche le texte HTML dans le corps de la page web active :

```powershell
$ie.Document.Body.InnerText
```

Pour fermer Internet Explorer à partir de PowerShell, appelez sa méthode Quit() :

```powershell
$ie.Quit()
```

Cette opération force la fermeture. La variable $ie ne contient plus de référence valide, même si elle apparaît toujours comme un objet COM. Si vous tentez de l’utiliser, vous obtenez une erreur Automation :

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

Vous pouvez soit supprimer la référence restante avec une commande telle que $ie = $null, ou supprimer complètement la variable en tapant ce qui suit :

```powershell
Remove-Variable ie
```

> [!NOTE]
> Il n’existe aucune norme commune déterminant si les exécutables ActiveX s’arrêtent ou continuent à s’exécuter lorsque vous supprimez une référence à ceux-ci. En fonction des circonstances, selon que l’application est visible, qu’un document modifié est en cours d’exécution dans celle-ci, et même que Windows PowerShell est toujours en cours d’exécution, l’application peut se fermer ou non. C’est pourquoi, vous devez tester le comportement d’arrêt de chaque exécutable ActiveX à utiliser dans Windows PowerShell.

### <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Obtention d’alertes sur les objets COM encapsulés .NET Framework

Dans certains cas, un objet COM peut avoir un *wrapper RCW* (Runtime-Callable Wrapper) .NET Framework associé, qui sera utilisé par l’applet de commande **New-Object**. Étant donné que le comportement du wrapper RCW peut différer du comportement de l’objet COM normal, l’applet de commande **New-Object** dispose d’un paramètre **Strict** pour vous avertir de l’accès au wrapper RCW. Si vous spécifiez le paramètre **Strict**, puis créez un objet COM qui utilise un wrapper RCW, vous recevez un message d’avertissement :

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Bien que l’objet soit toujours créé, vous êtes averti qu’il ne s’agit pas d’un objet COM standard.