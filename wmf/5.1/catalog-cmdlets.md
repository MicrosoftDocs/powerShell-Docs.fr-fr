---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,configuration
title: Applets de commande de catalogue
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2018
---
# <a name="catalog-cmdlets"></a>Applets de commande de catalogue

Nous avons ajouté deux nouvelles applets de commande au module [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) pour générer et valider des fichiers catalogue Windows.

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` crée un fichier catalogue Windows pour un ensemble de dossiers et de fichiers. Un fichier catalogue contient des hachages pour tous les fichiers dans les chemins spécifiés. Les utilisateurs peuvent distribuer l’ensemble des dossiers ainsi que le fichier catalogue correspondant qui représente ces dossiers. Un fichier catalogue peut être utilisé par le destinataire du contenu pour valider si des modifications ont été apportées aux dossiers après la création du catalogue.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Nous prenons en charge la création des versions de catalogues 1 et 2. La version 1 utilise l’algorithme de hachage SHA1 pour créer des fichiers à hacher et la version 2 utilise SHA256. La version de catalogue 2 n’est pas prise en charge sur *Windows Server 2008 R2* ni *Windows 7*. Il est recommandé d’utiliser la version de catalogue 2 si vous utilisez les plateformes *Windows 8*, *Windows Server 2012* et versions ultérieures.

Pour utiliser cette commande sur un module existant, spécifiez les variables CatalogFilePath et Path de façon à ce qu’elles correspondent à l’emplacement du manifeste du module. Dans l’exemple ci-dessous, le manifeste du module se trouve dans C:\Program Files\Windows PowerShell\Modules\Pester.

![](../images/NewFileCatalog.jpg)

Le fichier catalogue est ainsi créé.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Pour vérifier l’intégrité d’un fichier catalogue (Pester.cat dans l’exemple ci-dessus), il doit être signé à l’aide de l’applet de commande [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` valide le catalogue représentant un ensemble de dossiers.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Cette applet de commande compare les hachages de tous les fichiers et leurs chemins relatifs qui figurent dans le fichier catalogue à ceux enregistrés sur le disque. Si elle détecte une incompatibilité entre les hachages de fichier et les chemins, elle retourne le statut `ValidationFailed`.
Les utilisateurs peuvent récupérer toutes ces informations à l’aide de l’indicateur `Detailed`. Le statut de signature du catalogue est affiché dans le champ `Signature`, ce qui revient à appeler l’applet de commande [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) sur le fichier catalogue.
Les utilisateurs peuvent également ignorer des fichiers pendant la validation à l’aide du paramètre `FilesToSkip`.
