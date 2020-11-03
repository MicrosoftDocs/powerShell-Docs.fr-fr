---
description: Décrit les accélérateurs de type disponibles pour les classes .NET Framework
keywords: powershell,applet de commande
Locale: en-US
ms.date: 05/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_accelerators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Accelerators
ms.openlocfilehash: 21093f3a649212526c3fc3eb5405e2a7ce6e49f3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207518"
---
# <a name="about-type-accelerators"></a>À propos des accélérateurs de type

## <a name="short-desription"></a>SHORT DESCRIPTION COMPLÈTE :
Décrit les accélérateurs de type disponibles pour les classes .NET Framework

## <a name="long-description"></a>DESCRIPTION DÉTAILLÉE

Les accélérateurs de type sont des alias pour les classes .NET Framework. Elles vous permettent d’accéder à des classes .NET Framework spécifiques sans avoir à taper explicitement le nom de la classe entière. Par exemple, vous pouvez raccourcir la classe **AliasAttribute** de `[System.Management.Automation.AliasAttribute]` à `[Alias]` .

> [!NOTE]
> Tous les accélérateurs de type doivent toujours être encapsulés entre crochets ( `[]` ).

## <a name="available-type-accelerators"></a>Accélérateurs de type disponibles

|        Accélérateur          |                           Nom complet de la classe                           |
|---------------------------- | ------------------------------------------------------------------- |
|modification                         | System. DirectoryServices. DirectoryEntry                             |
|adsisearcher                 | System. DirectoryServices. DirectorySearcher                          |
|Alias                        | System. Management. Automation. AliasAttribute                         |
|AllowEmptyCollection         | System. Management. Automation. AllowEmptyCollectionAttribute          |
|AllowEmptyString             | System. Management. Automation. AllowEmptyStringAttribute              |
|AllowNull                    | System. Management. Automation. AllowNullAttribute                     |
|ArgumentCompleter            | System. Management. Automation. ArgumentCompleterAttribute             |
|tableau                        | System.Array                                                        |
|bigint                       | System. Numerics. BigInteger                                          |
|bool                         | System.Boolean                                                      |
|byte                         | System.Byte                                                         |
|char                         | System.Char                                                         |
|cimclass                     | Microsoft. Management. infrastructure. CimClass                        |
|cimconverter                 | Microsoft. Management. infrastructure. CimConverter                    |
|ciminstance                  | Microsoft.Management.Infrastructure.CimInstance                     |
|CimSession                   | Microsoft.Management.Infrastructure.CimSession                      |
|cimtype                      | Microsoft. Management. infrastructure. CimType                         |
|CmdletBinding                | System. Management. Automation. CmdletBindingAttribute                 |
|CultureInfo                  | System. Globalization. CultureInfo                                    |
|DATETIME                     | System.DateTime                                                     |
|Décimal                      | System.Decimal                                                      |
|double                       | System.Double                                                       |
|DscLocalConfigurationManager | System. Management. Automation. DscLocalConfigurationManagerAttribute  |
|DscProperty                  | System. Management. Automation. DscPropertyAttribute                   |
|DscResource                  | System. Management. Automation. DscResourceAttribute                   |
|float                        | System.Single                                                       |
|guid                         | System.Guid                                                         |
|hachage                    | System.Collections.Hashtable                                        |
|initialsessionstate          | System.Management.Automation.Runspaces.InitialSessionState          |
|int                          | System.Int32                                                        |
|int16                        | System.Int16                                                        |
|int32                        | System.Int32                                                        |
|int64                        | System.Int64                                                        |
|IPAddress                    | System .net. IPAddress                                                |
|IPEndpoint                   | System .net. IPEndPoint                                               |
|long                         | System.Int64                                                        |
|MailAddress                  | System .net. mail. MailAddress                                         |
|NullString                   | System. Management. Automation. Language. NullString                    |
|Objet ObjectSecurity               | System. Security. AccessControl. objet ObjectSecurity                        |
|OutputType                   | System. Management. Automation. OutputTypeAttribute                    |
|Paramètre                    | System. Management. Automation. ParameterAttribute                     |
|PhysicalAddress              | System .net. NetworkInformation. PhysicalAddress                       |
|powershell                   | System. Management. Automation. PowerShell                             |
|psaliasproperty              | System. Management. Automation. PSAliasProperty                        |
|pscredential                 | System. Management. Automation. PSCredential                           |
|pscustomobject               | System. Management. Automation. PSObject                               |
|PSDefaultValue               | System.Management.Automation.PSDefaultValueAttribute                |
|pslistmodifier               | System. Management. Automation. PSListModifier                         |
|PSModuleInfo                 | System. Management. Automation. PSModuleInfo                           |
|psnoteproperty               | System. Management. Automation. PSNoteProperty                         |
|PSObject                     | System. Management. Automation. PSObject                               |
|psprimitivedictionary        | System. Management. Automation. PSPrimitiveDictionary                  |
|psscriptmethod               | System. Management. Automation. PSScriptMethod                         |
|psscriptproperty             | System. Management. Automation. PSScriptProperty                       |
|PSTypeNameAttribute          | System. Management. Automation. PSTypeNameAttribute                    |
|PSVariable                   | System. Management. Automation. PSVariable                             |
|psvariableproperty           | System. Management. Automation. PSVariableProperty                     |
|ref                          | System. Management. Automation. PSReference                            |
|regex                        | System.Text.RegularExpressions.Regex                                |
|instance d’exécution                     | System. Management. Automation. instances d’exécution. Runspace                     |
|runspacefactory              | System. Management. Automation. instances d’exécution. RunspaceFactory              |
|sbyte                        | System.SByte                                                        |
|scriptblock                  | System. Management. Automation. ScriptBlock                            |
|securestring                 | System.Security.SecureString                                        |
|unique                       | System.Single                                                       |
|string                       | System.String                                                       |
|SupportsWildcards            | System. Management. Automation. SupportsWildcardsAttribute             |
|switch                       | System.Management.Automation.SwitchParameter                        |
|intervalle de temps                     | System.TimeSpan                                                     |
|type                         | System.Type                                                         |
|uint16                       | System.UInt16                                                       |
|uint32                       | System.UInt32                                                       |
|uint64                       | System.UInt64                                                       |
|URI                          | System.Uri                                                          |
|ValidateCount                | System. Management. Automation. ValidateCountAttribute                 |
|ValidateDrive                | System. Management. Automation. ValidateDriveAttribute                 |
|ValidateLength               | System. Management. Automation. ValidateLengthAttribute                |
|ValidateNotNull              | System. Management. Automation. ValidateNotNullAttribute               |
|ValidateNotNullOrEmpty       | System. Management. Automation. ValidateNotNullOrEmptyAttribute        |
|ValidatePattern              | System. Management. Automation. ValidatePatternAttribute               |
|ValidateRange                | System. Management. Automation. ValidateRangeAttribute                 |
|ValidateScript               | System. Management. Automation. ValidateScriptAttribute                |
|ValidateSet                  | System. Management. Automation. ValidateSetAttribute                   |
|ValidateTrustedData          | System. Management. Automation. ValidateTrustedDataAttribute           |
|ValidateUserDrive            | System. Management. Automation. ValidateUserDriveAttribute             |
|version                      | System.Version                                                      |
|void                         | System.Void                                                         |
|WildcardPattern              | System. Management. Automation. WildcardPattern                        |
|WMIC                          | System. Management. ManagementObject                                  |
|WMIClass                     | System. Management. ManagementClass                                   |
|wmisearcher                  | System. Management. ManagementObjectSearcher                          |
|X500DistinguishedName        | System.Security.Cryptography.X509Certificates.X500DistinguishedName |
|X509Certificate              | System.Security.Cryptography.X509Certificates.X509Certificate       |
|xml                          | System.Xml.XmlDocument                                              |
