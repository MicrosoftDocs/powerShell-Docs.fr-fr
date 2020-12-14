---
description: Décrit comment PowerShell utilise l’encodage de caractères pour l’entrée et la sortie de données de type chaîne.
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 27a5d818c1ed8e114e15d8a121626fc79101a59f
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349770"
---
# <a name="about_character_encoding"></a>about_Character_Encoding

## <a name="short-description"></a>Description courte
Décrit comment PowerShell utilise l’encodage de caractères pour l’entrée et la sortie de données de type chaîne.

## <a name="long-description"></a>Description longue

Unicode est une norme internationale d’encodage de caractères. Le système utilise uniquement Unicode pour la manipulation de caractères et de chaînes. Pour obtenir une description détaillée de tous les aspects d’Unicode, reportez-vous à [la norme Unicode](https://www.unicode.org/standard/standard.html).

Windows prend en charge les jeux de caractères Unicode et traditionnels. Les jeux de caractères traditionnels, tels que les pages de codes Windows, utilisent des valeurs 8 bits ou des combinaisons de valeurs 8 bits pour représenter les caractères utilisés dans une langue spécifique ou des paramètres de région géographique.

PowerShell utilise un jeu de caractères Unicode par défaut. Toutefois, plusieurs applets de commande ont un paramètre d' **encodage** qui peut spécifier l’encodage d’un jeu de caractères différent. Ce paramètre vous permet de choisir l’encodage de caractères spécifique dont vous avez besoin pour l’interopérabilité avec d’autres systèmes et applications.

Les applets de commande suivantes ont le paramètre **Encoding** :

- Microsoft.PowerShell.Management
  - Add-Content
  - Get-Content
  - Set-Content
- Microsoft.PowerShell.Utility
  - Export-Clixml
  - Export-Csv
  - Export-PSSession
  - Format-Hex
  - Import-Csv
  - Out-File
  - Select-String
  - Send-MailMessage

## <a name="the-byte-order-mark"></a>Marque d’ordre d’octet

La marque d’ordre d’octet (BOM) est une _signature Unicode_ dans les premiers octets d’un fichier ou d’un flux de texte qui indique l’encodage Unicode utilisé pour les données. Pour plus d’informations, consultez la documentation relative à la [marque d’ordre d’octet](/globalization/encoding/byte-order-mark) .

Dans Windows PowerShell, tout encodage Unicode, à l’exception de `UTF7` , crée toujours une nomenclature. PowerShell Core a pour valeur par défaut `utf8NoBOM` pour toute la sortie de texte.

Pour une compatibilité générale optimale, évitez d’utiliser des nomenclatures dans des fichiers UTF-8. Les plateformes UNIX et les utilitaires Unix-Heritage utilisés sur les plates-formes Windows ne prennent pas en charge les nomenclatures.

De même, l' `UTF7` encodage doit être évité. UTF-7 n’est pas un encodage Unicode standard et il est écrit sans une nomenclature dans toutes les versions de PowerShell.

La création de scripts PowerShell sur une plateforme de type UNIX ou l’utilisation d’un éditeur multiplateforme sur Windows, par exemple Visual Studio Code, entraîne l’encodage d’un fichier à l’aide de `UTF8NoBOM` . Ces fichiers fonctionnent correctement sur PowerShell Core, mais peuvent s’arrêter dans Windows PowerShell si le fichier contient des caractères non-ASCII.

Si vous devez utiliser des caractères non-ASCII dans vos scripts, enregistrez-les au format UTF-8 avec BOM. Sans la nomenclature, Windows PowerShell interprète votre script comme étant encodé dans la page de codes « ANSI » héritée. À l’inverse, les fichiers qui ont la nomenclature UTF-8 peuvent être problématiques sur les plateformes de type UNIX. De nombreux outils Unix, tels que `cat` ,, `sed` `awk` , et certains éditeurs, tels que, `gedit` ne savent pas comment traiter la nomenclature.

## <a name="character-encoding-in-windows-powershell"></a>Encodage de caractères dans Windows PowerShell

Dans PowerShell 5,1, le paramètre **Encoding** prend en charge les valeurs suivantes :

- `Ascii` Utilise le jeu de caractères ASCII (7 bits).
- `BigEndianUnicode` Utilise UTF-16 avec l’ordre des octets de poids fort (Big-endian).
- `BigEndianUTF32` Utilise UTF-32 avec l’ordre des octets de poids fort (Big-endian).
- `Byte` Encode un jeu de caractères en une séquence d’octets.
- `Default` Utilise l’encodage qui correspond à la page de codes active du système (généralement ANSI).
- `Oem` Utilise l’encodage qui correspond à la page de codes OEM actuelle du système.
- `String` Identique à `Unicode`.
- `Unicode` Utilise UTF-16 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `Unknown` Identique à `Unicode`.
- `UTF32` Utilise UTF-32 avec l’ordre de primauté des octets de poids faible (Little-endian).
- `UTF7` Utilise UTF-7.
- `UTF8` Utilise UTF-8 (avec BOM).

En général, Windows PowerShell utilise l’encodage Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) par défaut. Toutefois, l’encodage par défaut utilisé par les applets de commande dans Windows PowerShell n’est pas cohérent.

> [!NOTE]
> À l’aide de n’importe quel encodage Unicode, à l’exception de `UTF7` , crée toujours une nomenclature.

Pour les applets de commande qui écrivent la sortie dans des fichiers :

- `Out-File` et les opérateurs de redirection `>` et `>>` créent UTF-16LE, qui diffèrent notamment de `Set-Content` et `Add-Content` .

- `New-ModuleManifest` et `Export-CliXml` créent également des fichiers UTF-16LE.

- Lorsque le fichier cible est vide ou n’existe pas, `Set-Content` et `Add-Content` Utilisez l' `Default` encodage. `Default` est l’encodage spécifié par la page de codes ANSI héritée des paramètres régionaux du système.

- `Export-Csv` crée des `Ascii` fichiers, mais utilise un encodage différent lors de l’utilisation du paramètre **Append** (voir ci-dessous).

- `Export-PSSession` crée des fichiers UTF-8 avec BOM par défaut.

- `New-Item -Type File -Value` crée un fichier UTF-8 sans marque de nomenclature.

- `Send-MailMessage` utilise `Default` l’encodage par défaut.

- `Start-Transcript` crée `Utf8` des fichiers avec une nomenclature. Lorsque le paramètre **Append** est utilisé, l’encodage peut être différent (voir ci-dessous).

Pour les commandes qui ajoutent à un fichier existant :

- `Out-File -Append` et l' `>>` opérateur de redirection n’essaient pas de mettre en correspondance l’encodage du contenu du fichier cible existant. Au lieu de cela, ils utilisent l’encodage par défaut, sauf si le paramètre d' **encodage** est utilisé. Vous devez utiliser l’encodage d’origine des fichiers lors de l’ajout de contenu.

- En l’absence d’un paramètre d' **encodage** explicite, `Add-Content` détecte l’encodage existant et l’applique automatiquement au nouveau contenu. Si le contenu existant n’a pas de nomenclature, l' `Default` encodage ANSI est utilisé. Le comportement de `Add-Content` est le même dans PowerShell Core (V6 et versions ultérieures), sauf que l’encodage par défaut est `Utf8` .

- `Export-Csv -Append` correspond à l’encodage existant lorsque le fichier cible contient une nomenclature. En l’absence de nomenclature, il utilise l' `Utf8` encodage.

- `Start-Transcript -Append` correspond à l’encodage existant des fichiers qui incluent une nomenclature. En l’absence de nomenclature, l’encodage est utilisé par défaut `Ascii` . Cet encodage peut entraîner une perte de données ou une altération des caractères lorsque les données de la transcription contiennent des caractères multioctets.

Pour les applets de commande qui lisent les données de chaîne en l’absence d’une nomenclature :

- `Get-Content` et `Import-PowerShellDataFile` utilise l' `Default` encodage ANSI. ANSI est également ce que le moteur PowerShell utilise lorsqu’il lit le code source à partir de fichiers.

- `Import-Csv`, `Import-CliXml` et `Select-String` supposent `Utf8` en l’absence d’une nomenclature.

## <a name="character-encoding-in-powershell-core"></a>Encodage de caractères dans PowerShell Core

Dans PowerShell Core (V6 et versions ultérieures), le paramètre **Encoding** prend en charge les valeurs suivantes :

- `ascii`: Utilise l’encodage pour le jeu de caractères ASCII (7 bits).
- `bigendianunicode`: Encode au format UTF-16 à l’aide de l’ordre des octets de poids fort (Big-endian).
- `oem`: Utilise l’encodage par défaut pour les programmes MS-DOS et console.
- `unicode`: Encode au format UTF-16 à l’aide de l’ordre de primauté des octets de poids faible (Little-endian).
- `utf7`: Encode au format UTF-7.
- `utf8`: Encode au format UTF-8 (sans BOM).
- `utf8BOM`: Encode au format UTF-8 avec marque d’ordre d’octet (BOM)
- `utf8NoBOM`: Encode au format UTF-8 sans marque d’ordre d’octet (BOM)
- `utf32`: Encode au format UTF-32.

PowerShell Core a pour valeur par défaut `utf8NoBOM` pour toutes les sorties.

À partir de PowerShell 6,2, le paramètre **Encoding** autorise également les ID numériques des pages de codes inscrites (comme `-Encoding 1251` ) ou les noms de chaîne des pages de codes inscrites (comme `-Encoding "windows-1251"` ). Pour plus d’informations, consultez la documentation .NET pour [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage).

## <a name="changing-the-default-encoding"></a>Modification de l’encodage par défaut

PowerShell a deux variables par défaut qui peuvent être utilisées pour modifier le comportement d’encodage par défaut.

- `$PSDefaultParameterValues`
- `$OutputEncoding`

Pour plus d’informations, consultez [about_Preference_Variables](about_Preference_Variables.md).

À compter de PowerShell 5,1, les opérateurs de redirection ( `>` et `>>` ) appellent l’applet de commande `Out-File` . Par conséquent, vous pouvez définir l’encodage par défaut à l’aide de la `$PSDefaultParameterValues` variable de préférence, comme indiqué dans cet exemple :

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

Utilisez l’instruction suivante pour modifier l’encodage par défaut pour toutes les applets de commande qui ont le paramètre **Encoding** .

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> Le fait de placer cette commande dans votre profil PowerShell fait de la préférence un paramètre de session global qui affecte l’ensemble des commandes et des scripts qui ne spécifient pas explicitement un encodage.
>
> De même, vous devez inclure de telles commandes dans vos scripts ou modules que vous souhaitez adopter de la même façon. L’utilisation de ces commandes garantit que les applets de commande se comportent de la même façon, même lorsqu’elles sont exécutées par un autre utilisateur, sur un autre ordinateur ou dans une version différente de PowerShell.

La variable automatique `$OutputEncoding` affecte l’encodage utilisé par PowerShell pour communiquer avec les programmes externes. Elle n’a aucun effet sur l’encodage utilisé par les opérateurs de redirection de sortie et les applets de commande PowerShell pour enregistrer dans des fichiers.

## <a name="see-also"></a>Voir aussi

- [Présentation de l’encodage de caractères dans .NET](/dotnet/standard/base-types/character-encoding-introduction)
- [Pages de codes-applications Win32](/windows/win32/intl/code-pages)
- [La norme Unicode](https://www.unicode.org/standard/standard.html)
- [Encoding. CodePage](/dotnet/api/system.text.encoding.codepage)
- [UTF-16LE](https://wikipedia.org/wiki/UTF-16)
- [Marque d’ordre d’octet](https://wikipedia.org/wiki/Byte_order_mark)
- [about_Preference_Variables](about_Preference_Variables.md)
