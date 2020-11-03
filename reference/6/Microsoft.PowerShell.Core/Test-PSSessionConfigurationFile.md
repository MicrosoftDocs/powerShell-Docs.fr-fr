---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,applet de commande
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: ea57ae0b3affcbe060b74c6cc21e6df6d50e50ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204862"
---
# <span data-ttu-id="4d4f0-103">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="4d4f0-103">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="4d4f0-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="4d4f0-104">SYNOPSIS</span></span>
<span data-ttu-id="4d4f0-105">Vérifie les clés et les valeurs d'un fichier de configuration de session.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-105">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="4d4f0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d4f0-106">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="4d4f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="4d4f0-107">DESCRIPTION</span></span>

<span data-ttu-id="4d4f0-108">Cette applet de commande vérifie qu’un fichier de configuration de session contient des clés valides et que les valeurs sont de type correct.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-108">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="4d4f0-109">Pour les valeurs énumérées, l'applet de commande vérifie que les valeurs spécifiées sont valides.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-109">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="4d4f0-110">L’applet de commande retourne `$True` si le fichier réussit tous les tests et `$False` si ce n’est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-110">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="4d4f0-111">Pour rechercher des erreurs, utilisez le paramètre **Verbose** .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-111">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="4d4f0-112">`Test-PSSessionConfigurationFile` vérifie les fichiers de configuration de session, tels que ceux créés par l’applet de commande `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-112">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="4d4f0-113">Pour plus d’informations sur les configurations de session, consultez [about_session_configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4d4f0-113">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="4d4f0-114">Pour plus d’informations sur les fichiers de configuration de session, consultez [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="4d4f0-114">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="4d4f0-115">Cette applet de commande a été introduite dans PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-115">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="4d4f0-116">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="4d4f0-116">EXAMPLES</span></span>

### <span data-ttu-id="4d4f0-117">Exemple 1 : tester un fichier de configuration de session</span><span class="sxs-lookup"><span data-stu-id="4d4f0-117">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="4d4f0-118">Exemple 2 : tester le fichier de configuration de session d’une configuration de session</span><span class="sxs-lookup"><span data-stu-id="4d4f0-118">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="4d4f0-119">Dans cet exemple, nous testons le fichier de configuration utilisé dans la configuration de session **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-119">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="4d4f0-120">La valeur du paramètre **path** est le résultat de la `Get-PSSessionConfiguration` commande qui obtient la configuration de session **restreinte** .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-120">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="4d4f0-121">Le chemin d’accès du fichier de configuration de session est stocké dans la valeur de la propriété **ConfigFilePath** de la configuration de session.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-121">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="4d4f0-122">Exemple 3 : tester tous les fichiers de configuration de session</span><span class="sxs-lookup"><span data-stu-id="4d4f0-122">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="4d4f0-123">Dans cet exemple, la fonction teste tous les fichiers de configuration de session sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-123">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="4d4f0-124">La fonction utilise l' `Get-PSSessionConfiguration` applet de commande pour récupérer toutes les configurations de session.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-124">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="4d4f0-125">Le code à l’intérieur de la `ForEach-Object` boucle affiche le chemin d’accès du fichier et teste chacune des configurations de session.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-125">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="4d4f0-126">La propriété **ConfigFilePath** d’une configuration de session contient le chemin d’accès du fichier de configuration de session utilisé dans la configuration de session, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-126">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="4d4f0-127">Si la valeur de la propriété **ConfigFilePath** est remplie (vraie), la commande obtient (affiche) la valeur de la propriété **ConfigFilePath** .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-127">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="4d4f0-128">Elle utilise ensuite l' `Test-PSSessionConfigurationFile` applet de commande pour tester le fichier dans la valeur **ConfigFilePath** .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-128">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="4d4f0-129">Le paramètre **Verbose** retourne l'erreur de fichier en cas d'échec du test du fichier.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-129">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="4d4f0-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4d4f0-130">PARAMETERS</span></span>

### <span data-ttu-id="4d4f0-131">-Path</span><span class="sxs-lookup"><span data-stu-id="4d4f0-131">-Path</span></span>

<span data-ttu-id="4d4f0-132">Spécifie le chemin d’accès et le nom de fichier d’un fichier de configuration de session (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="4d4f0-132">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="4d4f0-133">Si vous omettez le chemin d’accès, la valeur par défaut est le dossier actif.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-133">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="4d4f0-134">Les caractères génériques sont pris en charge, mais ils doivent être résolus en un seul fichier.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-134">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="4d4f0-135">Vous pouvez également diriger un chemin d’accès de fichier de configuration de session vers `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-135">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="4d4f0-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d4f0-136">CommonParameters</span></span>

<span data-ttu-id="4d4f0-137">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4d4f0-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4d4f0-138">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4d4f0-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4d4f0-139">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="4d4f0-139">INPUTS</span></span>

### <span data-ttu-id="4d4f0-140">System.String</span><span class="sxs-lookup"><span data-stu-id="4d4f0-140">System.String</span></span>

<span data-ttu-id="4d4f0-141">Vous pouvez diriger un chemin d’accès de fichier de configuration de session vers `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="4d4f0-141">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="4d4f0-142">SORTIES</span><span class="sxs-lookup"><span data-stu-id="4d4f0-142">OUTPUTS</span></span>

### <span data-ttu-id="4d4f0-143">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="4d4f0-143">System.Boolean</span></span>

## <span data-ttu-id="4d4f0-144">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="4d4f0-144">NOTES</span></span>

## <span data-ttu-id="4d4f0-145">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="4d4f0-145">RELATED LINKS</span></span>

[<span data-ttu-id="4d4f0-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-147">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="4d4f0-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="4d4f0-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="4d4f0-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="4d4f0-151">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="4d4f0-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="4d4f0-154">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4d4f0-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="4d4f0-155">Fournisseur WSMan</span><span class="sxs-lookup"><span data-stu-id="4d4f0-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="4d4f0-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="4d4f0-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="4d4f0-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="4d4f0-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
