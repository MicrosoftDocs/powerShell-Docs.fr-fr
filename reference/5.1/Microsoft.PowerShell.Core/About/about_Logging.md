---
description: PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.
keywords: powershell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207638"
---
# <a name="about-logging"></a>À propos de la journalisation

## <a name="short-description"></a>Description courte

PowerShell journalise les opérations internes à partir du moteur, des fournisseurs et des applets de commande.

## <a name="long-description"></a>Description longue

PowerShell journalise des détails sur les opérations PowerShell, telles que le démarrage et l’arrêt du moteur et des fournisseurs, et l’exécution de commandes PowerShell.

> [!NOTE]
> Les versions 3,0, 4,0, 5,0 et 5,1 de Windows PowerShell incluent des applets de commande **EventLog** pour les journaux des événements Windows. Dans ces versions, pour afficher la liste des applets de commande **EventLog** , tapez : `Get-Command -Noun EventLog` . Pour plus d’informations, consultez la documentation sur les applets de commande et about_EventLogs pour votre version de Windows PowerShell.

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a>Affichage des entrées du journal des événements PowerShell sur Windows

Les journaux PowerShell peuvent être affichés à l’aide de Windows observateur d’événements. Le journal des événements se trouve dans le groupe journaux des applications et des services et est nommé `Microsoft-Windows-PowerShell` . Le fournisseur ETW associé `GUID` est `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` .

Lorsque la journalisation de blocs de script est activée, PowerShell enregistre les événements suivants dans le `Microsoft-Windows-PowerShell/Operational` Journal :

|Champ| Valeur|
|-|-|
|EventId|`4104` / `0x1008`|
|Channel|`Operational`|
|Level|`Verbose`|
|Opcode|`Create`|
|Tâche|`CommandStart`|
|Mot clé|`Runspace`|

## <a name="enabling-script-block-logging"></a>Activation de la journalisation des blocs de script

Lorsque vous activez la journalisation de blocs de script, PowerShell enregistre le contenu de tous les blocs de script qu’il traite. Une fois activé, toute nouvelle session PowerShell consigne ces informations.

> [!NOTE]
> Il est recommandé d’activer la journalisation des événements protégés, comme décrit ci-dessous, lors de l’utilisation de la journalisation par bloc de script pour tout autre chose que des Diagnostics.

La journalisation des blocs de script peut être activée via stratégie de groupe ou un paramètre du Registre.

### <a name="using-group-policy"></a>Utilisation de la stratégie de groupe

Pour activer la transcription automatique, activez la `Turn on PowerShell Script Block
Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows
Components -> Windows PowerShell` .

### <a name="using-the-registry"></a>Utilisation du Registre

Exécutez la fonction suivante :

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a>Journalisation des événements protégés

L’augmentation du niveau de journalisation sur un système augmente la possibilité que du contenu journalisé puisse contenir des données sensibles. Par exemple, avec la journalisation des scripts activée, les informations d’identification ou d’autres données sensibles utilisées par un script peuvent être écrites dans le journal des événements. Lorsqu’un ordinateur qui a des données sensibles journalisées est compromis, les journaux peuvent fournir une personne malveillante avec les informations nécessaires pour étendre leur portée.

Pour protéger ces informations, Windows 10 introduit la journalisation des événements protégés.
L’enregistrement des événements protégés permet aux applications participantes de chiffrer des données sensibles écrites dans le journal des événements. Plus tard, vous pourrez déchiffrer et traiter ces journaux sur un collecteur de journaux plus sécurisé et centralisé.

Le contenu du journal des événements est protégé à l’aide de la norme CMS (Cryptographic Message Syntax) de l’IETF. CMS utilise le chiffrement à clé publique. Les clés utilisées pour chiffrer le contenu et déchiffrer le contenu sont conservées séparément.

La clé publique peut être partagée à grande échelle et ne constitue pas des données sensibles. Tout contenu chiffré avec cette clé publique peut uniquement être déchiffré par la clé privée. Pour plus d’informations sur le chiffrement à clé publique, consultez [wikipedia-Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).

Pour activer une stratégie d’enregistrement des événements protégée, déployez une clé publique sur tous les ordinateurs qui ont des données du journal des événements à protéger. La clé privée correspondante est utilisée pour effectuer un traitement ultérieur des journaux des événements dans un emplacement plus sécurisé, tel qu’un collecteur de journaux des événements centraux ou un agrégateur [Siem][] . Vous pouvez configurer SIEM dans Azure. Pour plus d’informations, consultez [intégration Siem générique](/cloud-app-security/siem).

### <a name="enabling-protected-event-logging-via-group-policy"></a>Activation de la journalisation des événements protégés via stratégie de groupe

Pour activer la journalisation des événements protégés, activez la `Enable Protected Event Logging` fonctionnalité dans stratégie de groupe via `Administrative Templates -> Windows Components
-> Event Logging` . Ce paramètre requiert un certificat de chiffrement, que vous pouvez fournir de l’une des formes suivantes :

- Contenu d’un certificat X. 509 encodé en base 64 (par exemple, tel qu’il est fourni par l' `Export` option dans le gestionnaire de certificats).
- Empreinte numérique d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).
- Le chemin d’accès complet à un certificat (peut être local ou un partage distant).
- Chemin d’accès à un répertoire contenant un ou des certificats (peut être local ou un partage distant).
- Nom du sujet d’un certificat qui se trouve dans le magasin de certificats de l’ordinateur local (peut être déployé par l’infrastructure PKI).

Le certificat obtenu doit avoir `Document Encryption` une utilisation améliorée de la clé ( `1.3.6.1.4.1.311.80.1` ), et `Data Encipherment` les `Key
Encipherment` utilisations de clés ou sont activées.

> [!WARNING]
> La clé privée ne doit pas être déployée sur les événements de journalisation des machines. Elle doit être conservée dans un emplacement sécurisé où vous déchiffrez les messages.

### <a name="decrypting-protected-event-logging-messages"></a>Déchiffrement des messages d’enregistrement des événements protégés

Le script suivant récupère et déchiffre, en supposant que vous disposiez de la clé privée :

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a>Voir aussi

[PowerShell l’équipe Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[Intégration de SIEM générique](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
