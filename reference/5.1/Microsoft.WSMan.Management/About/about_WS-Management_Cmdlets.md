---
description: Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.
keywords: powershell,applet de commande
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: afcc8ffe53f686cf77cf26374bbb68659e6883f5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387938"
---
# <a name="about-ws-management-cmdlets"></a>À propos des applets de commande WS-Management

## <a name="short-description"></a>DESCRIPTION COURTE

Fournit une vue d’ensemble de Web Services for Management (WS-Management) comme arrière-plan de l’utilisation des applets de commande WS-Management dans Windows PowerShell.

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Cette rubrique fournit une vue d’ensemble de la gestion des services Web (WS-Management) pour l’utilisation des applets de commande WS-Management dans Windows PowerShell. Cette rubrique fournit également des liens vers des informations supplémentaires sur WS-Management. L’implémentation Microsoft de WS-Management est également appelée Windows Remote Management (WinRM).

## <a name="about-ws-management"></a>À propos de WS-Management

Windows Remote Management est l’implémentation Microsoft du protocole WS-Management, un protocole standard SOAP, compatible avec un pare-feu qui permet l’interopérabilité du matériel et des systèmes d’exploitation de différents fournisseurs. La spécification de protocole WS-Management permet aux systèmes d’accéder et d’échanger des informations de gestion dans une infrastructure informatique de manière courante. WS-Management et Intelligent Platform Management Interface (IPMI), ainsi que le collecteur d’événements, sont des composants des fonctionnalités de gestion matérielle de Windows.

Le protocole WS-Management est basé sur les spécifications de service Web standard suivantes : HTTPs, SOAP sur HTTP (profil WS-I), SOAP 1,2, WS-Addressing, WS-Transfer, WS-Enumeration et WS-Eventing.

## <a name="ws-management-and-wmi"></a>WS-Management et WMI

WS-Management peut être utilisé pour récupérer les données exposées par Windows Management Instrumentation (WMI). Vous pouvez obtenir des données WMI avec des scripts ou des applications qui utilisent l’API de script WS-Management ou via l’outil en ligne de commande WinRM. WS-Management prend en charge la plupart des opérations et classes WMI familières, y compris les objets incorporés. WS-Management pouvez tirer parti de WMI pour collecter des données sur les ressources ou pour gérer des ressources sur des ordinateurs Windows. Cela signifie que vous pouvez obtenir des données sur des objets tels que des disques, des cartes réseau, des services ou des processus de votre entreprise par le biais de l’ensemble existant de classes WMI. Vous pouvez également accéder aux données matérielles disponibles à partir du fournisseur IPMI WMI standard.

## <a name="ws-management-windows-powershell-provider-wsman"></a>WS-Management fournisseur Windows PowerShell (WSMan)

Le fournisseur WSMan fournit une vue hiérarchique des paramètres de configuration WS-Management disponibles. Le fournisseur vous permet d’explorer et de définir les différentes options de configuration de WS-Management.

## <a name="ws-management-configuration"></a>Configuration de WS-Management

Si WS-Management n’est pas installé et configuré, la communication à distance Windows PowerShell n’est pas disponible, les applets de commande WS-Management ne s’exécutent pas, les scripts de WS-Management ne s’exécutent pas et le fournisseur WSMan ne peut pas effectuer d’opérations de données. L’outil en ligne de commande WS-Management, WinRM et le transfert d’événements dépendent également de la configuration WS-Management.

## <a name="ws-management-cmdlets"></a>Applets de commande WS-Management

WS-Management fonctionnalité est implémentée dans Windows PowerShell par le biais d’un module qui contient un ensemble d’applets de commande et le fournisseur WSMan. Vous pouvez utiliser ces applets de commande pour effectuer les tâches de bout en bout nécessaires à la gestion des paramètres de WS-Management sur des ordinateurs locaux et distants.

Les applets de commande WS-Management suivantes sont disponibles.

## <a name="connection-cmdlets"></a>Applets de commande de connexion

- Connect-WSMan : connecte l’ordinateur local au service WS-Management (WinRM) sur un ordinateur distant.

- Disconnect-WSMan : déconnecte l’ordinateur local du service WS-Management (WinRM) sur un ordinateur distant.

## <a name="management-data-cmdlets"></a>Applets de commande Management-Data

- Obtenir-WSManInstance : affiche les informations de gestion d’une instance de ressource spécifiée par un URI de ressource.

- Invoke-WSManAction : appelle une action sur l’objet cible qui est spécifié par l’URI de ressource et par les sélecteurs.

- New-WSManInstance : crée une nouvelle instance de ressource de gestion.

- Remove-WSManInstance : supprime une instance de ressource de gestion.

- Set-WSManInstance : modifie les informations de gestion associées à une ressource.

## <a name="setup-and-configuration-cmdlets"></a>Applets de commande d’installation et de configuration

- Set-WSManQuickConfig : configure l’ordinateur local pour la gestion à distance.
  Vous pouvez utiliser l’applet de commande Set-WSManQuickConfig pour configurer WS-Management afin d’autoriser les connexions à distance au service WS-Management (WinRM). L’applet de commande Set-WSManQuickConfig effectue les opérations suivantes :
  - Il détermine si le service WS-Management (WinRM) est en cours d’exécution. Si le service WinRM n’est pas en cours d’exécution, l’applet de commande Set-WSManQuickConfig démarre le service.
  - Il définit le type de démarrage du service WS-Management (WinRM) sur automatique.
  - Il crée un écouteur qui accepte les demandes émanant de n’importe quelle adresse IP. Le protocole de transport par défaut est HTTP.
  - Il active une exception de pare-feu pour le trafic WS-Management.

  Remarque : pour exécuter cette applet de commande dans Windows Vista, Windows Server 2008 et les versions ultérieures de Windows, vous devez démarrer Windows PowerShell avec l’option « Exécuter en tant qu’administrateur ».

- Test-WSMan : vérifie que WS-Management est installé et configuré. L’applet de commande Test-WSMan teste si le service WS-Management (WinRM) est en cours d’exécution et configuré sur un ordinateur local ou distant.

- Disable-WSManCredSSP : désactive l’authentification CredSSP sur un ordinateur client.

- Enable-WSManCredSSP : active l’authentification CredSSP sur un ordinateur client.

- Obtenir-WSManCredSSP : obtient la configuration liée à CredSSP pour un ordinateur client.

## <a name="ws-management-specific-cmdlets"></a>Applets de commande spécifiques à WS-Management

- New-WSManSessionOption : crée un objet WSManSessionOption à utiliser comme entrée pour un ou plusieurs paramètres d’une applet de commande WS-Management.

## <a name="additional-ws-management-information"></a>Informations supplémentaires sur le WS-Management

Pour plus d’informations sur WS-Management, consultez les rubriques suivantes dans la documentation de Windows.

[Gestion à distance de Windows](/windows/win32/winrm/portal)

[À propos de Windows Remote Management](/windows/win32/winrm/about-windows-remote-management)

[Installation et configuration de Windows Remote Management](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Architecture Windows Remote Management](/windows/win32/winrm/windows-remote-management-architecture)

[Protocole Gestion des services web](/windows/win32/winrm/ws-management-protocol)

[Windows Remote Management et WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[URI de ressource](/windows/win32/winrm/resource-uris)

[Gestion matérielle à distance](/windows/win32/winrm/remote-hardware-management)

[Événements](/windows/win32/winrm/events)

## <a name="see-also"></a>VOIR AUSSI

[Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Disconnect-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Enable-WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Test-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
