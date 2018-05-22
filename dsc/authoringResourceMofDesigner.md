---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Utilisation du Concepteur de ressources
ms.openlocfilehash: 3dc03adefa71eadc5e80532fdeaaa0e0388e6dce
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="using-the-resource-designer-tool"></a>Utilisation du Concepteur de ressources

> S’applique à : Windows PowerShell 4.0, Windows PowerShell 5.0

L’outil Concepteur de ressources est un ensemble d’applets de commande exposées par le module **xDscResourceDesigner** qui facilite la création de ressources DSC Windows PowerShell. Les applets de commande de cette ressource vous aident à créer le schéma MOF, le module de script et la structure de répertoires de votre nouvelle ressource. Pour plus d’informations sur les ressources DSC, consultez [Création de ressources DSC Windows PowerShell personnalisées](authoringResource.md).
Dans cette rubrique, nous allons créer une ressource DSC qui gère les utilisateurs Active Directory.
Utilisez l’applet de commande [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) pour installer le module **xDscResourceDesigner**.

>**Remarque** : **Install-Module** est inclus dans le module **PowerShellGet** de PowerShell 5.0. Vous pouvez télécharger le module **PowerShellGet** pour PowerShell 3.0 et 4.0 ici : [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Création de propriétés de ressource
La première chose à faire est de décider des propriétés que doit exposer la ressource. Pour cet exemple, nous allons définir un utilisateur Active Directory avec les propriétés suivantes.

Nom du paramètre  Description
* **UserName** : propriété de clé qui identifie de façon unique un utilisateur.
* **Ensure** : spécifie si le compte d’utilisateur doit être Present ou Absent. Ce paramètre a seulement deux valeurs possibles.
* **DomainCredential** : mot de passe de l’utilisateur.
* **Password** : mot de passe souhaité pour que l’utilisateur autorise une configuration à modifier le mot de passe si nécessaire.

Pour créer les propriétés, nous utilisons l’applet de commande **New-xDscResourceProperty**. Les commandes PowerShell suivantes créent les propriétés décrites ci-dessus.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Créer la ressource

Maintenant que les propriétés de la ressource ont été créées, nous pouvons appeler l’applet de commande **New-xDscResource** pour créer la ressource. L’applet de commande **New-xDscResource** prend la liste des propriétés comme paramètres. Elle prend également le chemin de l’emplacement auquel le module doit être créé, le nom de la nouvelle ressource et le nom du module dans lequel elle est contenue. La commande PowerShell suivante crée la ressource.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

L’applet de commande **New-xDscResource** crée le schéma MOF, un script de ressource squelette, la structure de répertoires nécessaire pour votre nouvelle ressource et un manifeste pour le module qui expose la nouvelle ressource.

Le fichier de schéma MOF se trouve à l’emplacement **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, et son contenu est le suivant.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

Le script de la ressource se trouve à l’emplacement **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Il ne comprend pas la logique permettant d’implémenter la ressource. Vous devrez l’ajouter vous-même. Voici le contenu du script squelette.

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a>Mise à jour de la ressource

Si vous avez besoin d’ajouter ou de modifier la liste des paramètres de la ressource, vous pouvez appeler l’applet de commande **Update-xDscResource**. L’applet de commande met à jour la ressource avec une nouvelle liste de paramètres. Si vous avez déjà ajouté une logique au script de votre ressource, celle-ci reste inchangée.

Supposons, par exemple, que vous vouliez inclure le dernier journal en date dans votre ressource pour l’utilisateur. Plutôt que de réécrire complètement la ressource, vous pouvez appeler **New-xDscResourceProperty** pour créer la nouvelle propriété, puis appeler **Update-xDscResource** et ajouter votre nouvelle propriété à la liste des propriétés.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Test d’un schéma de ressource

L’outil Concepteur de ressources expose une applet de commande supplémentaire qui peut être utilisée pour tester la validité d’un schéma MOF que vous avez écrit manuellement. Appelez l’applet de commande **Test-xDscSchema** en passant le chemin d’un schéma de ressource MOF comme paramètre. C’est dans ce schéma que l’applet de commande affiche les éventuelles erreurs.

### <a name="see-also"></a>Voir aussi

#### <a name="concepts"></a>Concepts
[Création de ressources personnalisées de configuration d’état souhaité Windows PowerShell](authoringResource.md)

#### <a name="other-resources"></a>Autres ressources
[Module xDscResourceDesigner](https://powershellgallery.com/packages/xDscResourceDesigner)