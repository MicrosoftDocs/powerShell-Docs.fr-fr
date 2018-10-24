---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Valeurs de manifeste d’élément qui impactent l’interface utilisateur de PowerShell Gallery
ms.openlocfilehash: e7e9910504a665e464add0a83454cec64c1a0937
ms.sourcegitcommit: 601609575a3214ea7086a3bcb586ae0d1df3d418
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532968"
---
# <a name="item-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valeurs de manifeste d’élément qui impactent l’interface utilisateur de PowerShell Gallery

Cette rubrique fournit aux éditeurs des informations récapitulatives sur la façon de modifier le manifeste pour leurs publications PowerShell Gallery afin d’impacter les fonctionnalités des applets de commande PowerShellGet et de l’interface utilisateur de PowerShell Gallery. Ce contenu est organisé selon l’endroit où apparaît la modification, en commençant par la section centrale, puis la zone de navigation à gauche. Une sélection présente les balises les plus importantes ainsi que certaines balises couramment utilisées. Deux rubriques fournissent des exemples de manifeste :

- Pour les modules, voir [Mettre à jour le manifeste du module](/powershell/module/powershellget/Update-ModuleManifest)
- Pour les scripts, voir [Créer un fichier de script avec des métadonnées](/powershell/module/powershellget/New-ScriptFileInfo)

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Éléments des fonctionnalités PowerShell Gallery contrôlés par le manifeste

Le tableau ci-dessous présente les éléments de l’interface utilisateur PowerShell Gallery qui sont contrôlés par l’éditeur. Chaque élément précise s’il peut être contrôlé par le manifeste de type module ou script.

| Élément de l'interface utilisateur | Description | Module | Script |
| --- | --- | --- | --- |
| **Titre** | Nom de l’élément publié dans Gallery  | Non | Non |
| **Version** | La version affichée représente la chaîne de version dans les métadonnées, ainsi qu’une préversion si elle est spécifiée. La partie principale de la version dans un manifeste Module est ModuleVersion. Pour un script, elle est identifiée par .VERSION. Si une chaîne de préversion est spécifiée, elle est ajoutée à la partie ModuleVersion pour les modules, ou identifiée par .VERSION pour les scripts. Il existe une documentation pour spécifier les chaînes de préversion dans les [modules](module-prerelease-support.md) et les [scripts](script-prerelease-support.md) | Oui | Oui |
| **Description** | Description dans le manifeste du module. Dans un manifeste de fichier de script, elle est identifiée par .DESCRIPTION | Oui | Oui |
| **Exiger l’acceptation de la licence** | Un module peut obliger l’utilisateur à accepter une licence en modifiant le manifeste du module avec RequireLicenseAcceptance = $true, en fournissant une valeur LicenseURI, et en plaçant un fichier license.txt à la racine du dossier du module. Des informations supplémentaires sont disponibles dans la rubrique [Exiger l’acceptation de la licence](../how-to/working-with-items/items-that-require-license-acceptance.md). | Oui | Non |
| **Notes de publication** | Pour les modules, ces informations sont extraites de la section ReleaseNotes, sous PSData\PrivateData. Dans les manifestes de script, il s’agit de l’élément .RELEASENOTES. | Oui | Oui |
| **Propriétaires** | Les propriétaires représentent la liste des utilisateurs de PowerShell Gallery autorisés à mettre à jour un élément. La liste des propriétaires n’est pas incluse dans le manifeste de l’élément. Une documentation supplémentaire explique comment [gérer les propriétaires de l’élément](../how-to/publishing-items/managing-item-owners.md). | Non | Non |
| **Auteur** | Cette information est incluse dans le manifeste du module sous la forme Auteur et dans un manifeste de script sous la forme .AUTHOR. Le champ Auteur est souvent utilisé pour spécifier une société ou organisation associée à un élément. | Oui | Oui |
| **Copyright** | Il s’agit du champ Copyright dans le manifeste du module, et identifié par .COPYRIGHT dans un manifeste de script. | Oui | Oui |
| **FileList** | La liste des fichiers est extraite du package lors de sa publication dans PowerShell Gallery. Elle n’est pas contrôlable par les informations du manifeste. Remarque : un fichier .nuspec supplémentaire est répertorié avec chaque élément dans PowerShell Gallery, mais n’est pas présent après l’installation de l’élément sur un système. Il s’agit du manifeste du package Nuget pour l’élément, et il peut être ignoré. | Non | Non |
| **Balises** | Pour les modules, les balises sont incluses sous PSData\PrivateData. Pour les scripts, la section est intitulée .TAGS. Notez que les balises ne peuvent pas contenir d’espaces, même si elles sont entourées de guillemets. Les balises comportent des exigences et des significations supplémentaires, décrites plus loin dans cette rubrique, à la section Détails de la balise. | Oui | Oui |
| **Applets de commande** | Ces informations sont spécifiées dans le manifeste du module à l’aide de CmdletsToExport. Notez que la meilleure pratique consiste à répertorier explicitement les éléments plutôt que d’utiliser le caractère générique « * », car cela améliore les performances du module de chargement pour les utilisateurs. | Oui | Non |
| **Functions** | Ces informations sont spécifiées dans le manifeste du module à l’aide de FunctionsToExport. Notez que la meilleure pratique consiste à répertorier explicitement les éléments plutôt que d’utiliser le caractère générique « * », car cela améliore les performances du module de chargement pour les utilisateurs. | Oui | Non |
| **Ressources DSC** | Pour les modules qui seront utilisés dans PowerShell version 5.0 et ultérieures, ces informations sont fournies dans le manifeste à l’aide de DscResourcesToExport. Si le module sera utilisé dans PowerShell 4, DSCResourcesToExport ne doit pas être utilisé car il ne s’agit pas d’une clé de manifeste prise en charge. (DSC n’était pas disponible avant PowerShell 4.) | Oui | Non |
| **Flux de travail** | Les flux de travail sont publiés dans PowerShell Gallery en tant que scripts et identifiés en tant que flux de travail dans le code (voir [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) pour obtenir un exemple). Ces informations ne sont pas contrôlées par le manifeste. | Non | Non |
| **Fonctionnalités de rôle** | Ces informations apparaissent lorsque le module publié dans PowerShell Gallery contient un ou plusieurs fichiers de capacité (.psrc) de rôle, utilisés par JEA. Consultez la documentation de JEA pour plus d’informations sur les [capacités de rôle](/powershell/jea/role-capabilities). | Oui | Non |
| **Éditions de PowerShell** | Ces informations sont spécifiées dans un manifeste de module ou de script. Pour les modules conçus pour être utilisés avec PowerShell 5.0 et versions antérieures, elles sont contrôlées à l’aide de balises. Pour un système de type bureau (Desktop), utilisez la balise PSEdition_Desktop, et pour un système de base (Core), utilisez la balise PSEdition_Core. Pour les modules qui seront utilisés uniquement dans PowerShell 5.1 et versions ultérieures, une clé CompatiblePSEditions est disponible dans le manifeste du principal. Pour plus d’informations, reportez-vous à la fonctionnalité PS Edition dans la [documentation PowerShell Get](module-psedition-support.md). | Oui | Oui |
| **Dépendances** | Les dépendances représentent les modules de PowerShell Gallery qui sont déclarés dans le module en tant que RequiredModules ou dans le manifeste de script en tant que #Requires – Module (nom). | Oui | Oui |
| **Version minimale de PowerShell** | Cette information peut être spécifiée dans un manifeste de module en tant que PowerShellVersion | Oui | Non |
| **Historique des versions** | L’historique des versions reflète les mises à jour apportées à un module dans PowerShell Gallery. Si une version d’un élément est masquée à l’aide de la fonctionnalité de suppression, elle n’apparaît pas dans l’historique des versions, sauf pour les propriétaires de l’élément. | Non | Non |
| **Site du projet** | Le site du projet est indiqué pour les modules dans la section Privatedata\PSData du manifeste du module en spécifiant une valeur ProjectURI. Dans le manifeste de script, cette information est contrôlée en spécifiant une valeur .PROJECTURI. | Oui | Oui |
| **Licence** | Le lien de la licence est indiqué pour les modules dans la section Privatedata\PSData du manifeste du module en spécifiant une valeur LicenseURI. Dans le manifeste de script, cette information est contrôlée en spécifiant une valeur .LICENSEURI. Il est important de noter que si une licence n’est pas fournie via LicenseURI ou dans un module, les conditions d’utilisation de PowerShell Gallery précisent les conditions d’utilisation de l’élément. Pour plus d’informations, consultez les conditions d’utilisation. | Oui | Oui |
| **Icône** | Il est possible de spécifier une icône pour tout élément figurant dans PowerShell Gallery en fournissant l’indicateur IconURI dans le manifeste de script ou dans la section Privatedata-PSData du manifeste de module. IconURI doit pointer vers une image de 32 x 32 avec un arrière-plan transparent. L’URI **doit** être une URL d’image directe et **ne doit pas** accéder à une page web contenant l’image ou à un fichier du package PowerShell Gallery. | Oui | Oui |


## <a name="editing-item-details"></a>Modification des détails de l'élément

La page de modification de l’élément dans PowerShell Gallery permet aux éditeurs de modifier certains des champs affichés pour un élément, en particulier :

- Titre
- Description
- Table des matières
- URL de l'icône
- URL de la page d’accueil du projet
- Auteurs
- Copyright
- Balises
- Notes de publication
- Exiger une licence

Cette approche est généralement déconseillée, sauf si elle est nécessaire pour corriger les informations affichées pour une version antérieure d’un module. Les utilisateurs qui acquièrent le module constateront que les métadonnées ne correspondent pas à ce qui est affiché dans PowerShell Gallery, ce qui soulève quelques interrogations concernant l’élément. Dans cette situation, les propriétaires de l’élément sont souvent invités à confirmer la modification. Chaque fois que cette approche est utilisée, il est fortement recommandé de publier une nouvelle version de l’élément avec les mêmes modifications.

## <a name="tag-details"></a>Détails de la balise

Les balises sont de simples chaînes permettant aux utilisateurs de rechercher des éléments. Les balises sont particulièrement utiles lorsqu’elles sont utilisées de manière cohérente entre plusieurs éléments liés à la même rubrique. L’utilisation de plusieurs formes d’un mot (par exemple, database et databases, ou test et testing) n’offre que peu d’avantages. Les balises sont des chaînes constituées d’un mot unique sensible à la casse, et ne peuvent pas inclure d’espaces. Si vous pensez qu’une expression fera l’objet de nombreuses recherches, ajoutez-la à la description de l’objet afin qu’elle apparaisse dans les résultats de la recherche. Utilisez la casse Pascal, le trait d’union, le trait de soulignement ou le point pour améliorer la lisibilité.
Évitez les balises longues, complexes et inhabituelles, car elles sont souvent mal orthographiées.

Certaines balises sont particulièrement importantes car elles sont traitées de façon unique par PowerShell Gallery et les applets de commande PowerShellGet. C’est le cas des balises PSEdition_Desktop et PSEdition_Core, décrites précédemment.

Comme indiqué ci-dessus, les balises sont particulièrement utiles lorsqu’elles sont spécifiques et utilisées de manière cohérente entre plusieurs éléments. Quand un éditeur recherche les meilleures balises à utiliser, l’approche la plus simple consiste à rechercher ces balises dans PowerShell Gallery. Idéalement, beaucoup d’éléments sont retournés et leurs descriptions correspondent à l’utilisation que vous faites de ce mot clé.

Pour référence, voici quelques-unes des balises les plus couramment utilisées en date 14/12/2017. Dans certains cas, d’autres options similaires mais moins recommandées sont proposées en regard de la balise. Il est conseillé d’utiliser la balise préférée car elle génère moins de bruit et offre aux consommateurs de meilleurs résultats.

| Balise préférée | Alternatives et remarques |
| --- | --- |
| Azure |  |
| DSC | La balise DesiredStateConfiguration est déconseillée car trop longue |
| ResourceManager | La balise ARM sert à décrire un groupe de processeurs et ne doit pas être utilisée pour Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatisation |  |
| REST |  |
| ActiveDirectory | AD n’est pas actuellement utilisé  |
| SQLServer |  |
| DBA |  |
| Sécurité | La balise Defense est moins précise |
| Base de données | La balise Databases (pluriel) est moins précise |
| DevOps |  |
| Windows |  |
| Build |  |
| Déploiement | La balise Deploy est moins utilisée |
| Cloud |  |
| GIT |  |
| Test | La balise Testing est moins précise |
| VersionControl | La balise Version est moins précise, bien que plus utilisée  |
| Journalisation | Il est recommandé d’utiliser l’action de journalisation |
| Log | Il est recommandé d’utiliser le document Journal |
| Secours |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Stockage |  |
| GitHub |  |
| Json |  |
| Exchange |  |
| Réseau | La balise Networking est similaire, mais moins souvent utilisée |
| SharePoint |  |
| Création de rapports | La création de rapports est une action, le rapport est un document |
| Rapport | Le rapport est un document |
| WinRM |  |
| Analyse |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Couleur |  |
| DNS |  |
| Office365 | La graphie Office est préférable. O365 est moins couramment utilisé, bien que plus court |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV est moins utilisé en tant que balise |
| Configuration |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Pare-feu |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Utilisé principalement pour les modules AzureRM |
| Zip |  |
| MSI |  |
| Mac |  |
| PoshBot |  |