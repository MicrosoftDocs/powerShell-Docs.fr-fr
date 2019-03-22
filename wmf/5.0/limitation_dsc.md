---
ms.date: 06/12/2017
keywords: wmf,powershell,configuration
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795145"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Problèmes connus liés à la Configuration d’état souhaité (DSC)

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Changement cassant : Les certificats utilisés pour chiffrer/déchiffrer les mots de passe dans les configurations DSC peuvent ne pas fonctionner après l’installation de WMF 5.0 RTM

Dans les versions WMF 4.0 et WMF 5.0 Preview, DSC n’autorisait pas les mots de passe de plus de 121 caractères dans la configuration. DSC forçait l’utilisation de mots de passe courts même si des mots de passe forts et longs étaient souhaités. Cette modification avec rupture autorise les mots de passe de longueur arbitraire dans la configuration DSC.

**Résolution :** Recréez le certificat avec l’attribut Data Encipherment ou Key Encipherment Key Usage, et avec l’attribut Document Encryption Enhanced Key Usage (1.3.6.1.4.1.311.80.1). L’article TechNet <https://technet.microsoft.com/library/dn807171.aspx> contient des informations supplémentaires.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>Les applets de commande DSC peuvent échouer après l’installation de WMF 5.0 RTM

Start-DscConfiguration et d’autres applets de commande DSC peuvent échouer après l’installation de WMF 5.0 RTM avec l’erreur suivante :
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Résolution :** Supprimez DSCEngineCache.mof en exécutant la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>Les applets de commande DSC peuvent ne pas fonctionner si WMF 5.0 RTM est installé sur WMF 5.0 Production Preview

**Résolution :** Exécutez la commande suivante dans une session PowerShell avec élévation de privilèges (Exécuter en tant qu’administrateur) :
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>Le gestionnaire de configuration local peut basculer dans un état instable lors de l’utilisation de Get-DscConfiguration en DebugMode

Si le gestionnaire de configuration local est en DebugMode, une pression sur Ctrl+C pour arrêter le traitement de Get-DscConfiguration peut provoquer son basculement dans un état instable où la plupart des applets de commande DSC ne fonctionneront pas.

**Résolution :** N’appuyez pas sur Ctrl+C lors du débogage de l’applet de commande Get-DscConfiguration.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration peut ne pas répondre en DebugMode

Si le Gestionnaire de configuration local est en DebugMode, Stop-DscConfiguration peut ne pas répondre lors d’une tentative d’arrêt d’une opération démarrée par Get-DscConfiguration

**Résolution :** Terminez le débogage de l’opération démarrée par Get-DscConfiguration comme décrit dans la section « [Débogage des ressources DSC](https://msdn.microsoft.com/powershell/dsc/debugresource) ».

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Aucun message d’erreur détaillé n’est affiché en DebugMode

Si le gestionnaire de configuration local est en DebugMode, aucun message d’erreur détaillé n’est affiché à partir des ressources DSC.

**Résolution :** Désactivez *DebugMode* pour afficher les messages détaillés à partir de la ressource

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Les opérations Invoke-DscResource ne peuvent pas être récupérées par l’applet de commande Get-DscConfigurationStatus

Après l’utilisation de l’applet de commande Invoke-DscResource pour appeler directement les méthodes d’une ressource quelconque, les enregistrements de cette opération ne peuvent pas être récupérés ultérieurement par Get-DscConfigurationStatus.

**Résolution :** Aucune.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus retourne les opérations de cycle d’extraction en tant que type *Consistency*

Quand un nœud est configuré en mode d’actualisation par extraction, pour chaque opération d’extraction effectuée, l’applet de commande Get-DscConfigurationStatus indique que le type d’opération est *Consistency* au lieu de *Initial*

**Résolution :** Aucune.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>L’applet de commande Invoke-DscResource ne retourne pas les messages dans l’ordre dans lequel ils ont été générés

L’applet de commande Invoke-DscResource ne retourne pas les messages détaillés, d’avertissement et d’erreur dans l’ordre dans lequel ils ont été générés par le gestionnaire de configuration local ou la ressource DSC.

**Résolution :** Aucune.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>Les ressources DSC ne peuvent pas être déboguées facilement en cas d’utilisation avec Invoke-DscResource

Quand le gestionnaire de configuration local s’exécute en mode débogage (pour plus de détails, consultez [Débogage des ressources DSC](https://msdn.microsoft.com/powershell/dsc/debugresource)), l’applet de commande Invoke-DscResource ne donne pas d’informations sur l’instance d’exécution à laquelle se connecter pour le débogage.
**Résolution :** Effectuez la découverte et la jonction à l’instance d’exécution à l’aide des applets de commande **Get-PSHostProcessInfo**, **Enter-PSHostProcess** , **Get-Runspace** et **Debug-Runspace** pour déboguer la ressource DSC.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Différents documents de configuration partielle pour le même nœud ne peuvent pas avoir des noms de ressources identiques

Pour plusieurs configurations partielles déployées sur un même nœud, des noms de ressources identiques provoquent des erreurs au moment de l’exécution.

**Résolution :** Utilisez des noms différents pour les mêmes ressources dans différentes configurations partielles.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration –UseExisting ne fonctionne pas avec -Credential

Quand vous utilisez Start-DscConfiguration avec le paramètre –UseExisting, le paramètre –Credential est ignoré. DSC utilise l’identité de processus par défaut pour continuer l’opération. Cela provoque une erreur quand des informations d’identification différentes sont nécessaires pour continuer sur le nœud distant.

**Résolution :** Utilisez une session CIM pour les opérations DSC à distance :
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>Adresses IPv6 en tant que noms de nœuds dans les configurations DSC

Les adresses IPv6 en tant que noms de nœuds dans les scripts de configuration DSC ne sont pas prises en charge dans cette version.

**Résolution :** Aucune.

## <a name="debugging-of-class-based-dsc-resources"></a>Débogage des ressources DSC basées sur une classe

Le débogage des ressources DSC basées sur une classe n’est pas pris en charge dans cette version.

**Résolution :** Aucune.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Les variables et fonctions définies dans l’étendue $script dans une ressource DSC basée sur une classe ne sont pas conservées entre les appels à une ressource DSC

Plusieurs appels successifs à Start-DSCConfiguration échouent si la configuration utilise une ressource basée sur une classe qui a des variables ou des fonctions définies dans l’étendue $script.

**Résolution :** Définissez toutes les variables et fonctions dans la classe de ressources DSC proprement dite. Aucune variable/fonction d’étendue $script.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Débogage de ressources DSC quand une ressource utilise PSDscRunAsCredential

Le débogage de ressources DSC quand une ressource utilise la propriété *PSDscRunAsCredential* dans la configuration n’est pas pris en charge dans cette version.

**Résolution :** Aucune.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential n’est pas pris en charge pour les ressources DSC composites

**Résolution :** Utilisez si possible une propriété Credential. Exemple de ServiceSet et WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource -Syntax* ne reflète pas correctement PsDscRunAsCredential

Get-DscResource -Syntax ne reflète pas correctement PsDscRunAsCredential quand la ressource la marque comme étant obligatoire ou ne la prend pas en charge.

**Résolution :** Aucune. Cependant, la création de configuration dans ISE reflète les métadonnées correctes concernant la propriété PsDscRunAsCredential lors de l’utilisation d’IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature n’est pas disponible dans Windows 7

La ressource DSC WindowsOptionalFeature n’est pas disponible dans Windows 7. Cette ressource nécessite le module DISM et les applets de commande DISM qui sont disponibles à partir de Windows 8 et des versions plus récentes du système d’exploitation Windows.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Pour les ressources DSC basées sur une classe, Import-DscResource -ModuleVersion peut ne pas fonctionner comme prévu

Si le nœud de compilation a plusieurs versions d’un module de ressource DSC basé sur une classe, `Import-DscResource -ModuleVersion` ne récupère pas la version spécifiée et génère l’erreur de compilation suivante.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Résolution :** Importez la version requise en définissant l’objet *ModuleSpecification* sur `-ModuleName` avec la clé `RequiredVersion` spécifiée comme suit :

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Certaines ressources DSC comme une ressource du Registre peuvent commencer à prendre beaucoup de temps pour traiter la demande.

**Résolution 1 :** Créez une tâche planifiée qui nettoie le dossier suivant régulièrement.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Résolution 2 :** Modifiez la configuration DSC pour nettoyer le dossier *CommandAnalysis* à la fin de la configuration.

``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
