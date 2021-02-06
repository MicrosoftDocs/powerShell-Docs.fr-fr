---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99598990"
---
# <span data-ttu-id="91c2f-102">Write-Error</span><span class="sxs-lookup"><span data-stu-id="91c2f-102">Write-Error</span></span>

## <span data-ttu-id="91c2f-103">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="91c2f-103">SYNOPSIS</span></span>
<span data-ttu-id="91c2f-104">Écrit un objet dans le flux d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="91c2f-104">Writes an object to the error stream.</span></span>

## <span data-ttu-id="91c2f-105">SYNTAXE</span><span class="sxs-lookup"><span data-stu-id="91c2f-105">SYNTAX</span></span>

### <span data-ttu-id="91c2f-106">Noexception (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="91c2f-106">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="91c2f-107">WithException</span><span class="sxs-lookup"><span data-stu-id="91c2f-107">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="91c2f-108">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="91c2f-108">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="91c2f-109">Description</span><span class="sxs-lookup"><span data-stu-id="91c2f-109">DESCRIPTION</span></span>

<span data-ttu-id="91c2f-110">L' `Write-Error` applet de commande déclare une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="91c2f-110">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="91c2f-111">Par défaut, les erreurs sont envoyées dans le flux d'erreurs vers le programme hôte pour être affichées, avec la sortie.</span><span class="sxs-lookup"><span data-stu-id="91c2f-111">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="91c2f-112">Pour écrire une erreur sans fin d'exécution, entrez une chaîne de message d'erreur, un objet **ErrorRecord** ou un objet **Exception**.</span><span class="sxs-lookup"><span data-stu-id="91c2f-112">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="91c2f-113">Utilisez les autres paramètres de `Write-Error` pour remplir l’enregistrement d’erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-113">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="91c2f-114">Les erreurs sans fin d'exécution écrivent une erreur dans le flux d'erreurs, mais elles n'arrêtent pas le traitement des commandes.</span><span class="sxs-lookup"><span data-stu-id="91c2f-114">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="91c2f-115">Si une erreur sans fin d'exécution est déclarée sur un élément dans une collection d'éléments d'entrée, la commande continue de traiter les autres éléments dans la collection.</span><span class="sxs-lookup"><span data-stu-id="91c2f-115">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="91c2f-116">Pour déclarer une erreur d’arrêt, utilisez le `Throw` mot clé.</span><span class="sxs-lookup"><span data-stu-id="91c2f-116">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="91c2f-117">Pour plus d’informations, consultez [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span><span class="sxs-lookup"><span data-stu-id="91c2f-117">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="91c2f-118">EXEMPLES</span><span class="sxs-lookup"><span data-stu-id="91c2f-118">EXAMPLES</span></span>

### <span data-ttu-id="91c2f-119">Exemple 1 : écrire une erreur pour l’objet RegistryKey</span><span class="sxs-lookup"><span data-stu-id="91c2f-119">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="91c2f-120">Cette commande déclare une erreur sans fin d’achèvement lorsque l' `Get-ChildItem` applet de commande retourne un `Microsoft.Win32.RegistryKey` objet, tel que les objets dans `HKLM:` les `HKCU:` lecteurs ou du fournisseur de Registre PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91c2f-120">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="91c2f-121">Exemple 2 : écrire un message d’erreur dans la console</span><span class="sxs-lookup"><span data-stu-id="91c2f-121">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="91c2f-122">Cette commande déclare une erreur sans fin d'exécution et écrit une erreur « Accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="91c2f-122">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="91c2f-123">La commande utilise le paramètre **Message** pour spécifier le message, mais omet le nom du paramètre **Message** facultatif.</span><span class="sxs-lookup"><span data-stu-id="91c2f-123">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="91c2f-124">Exemple 3 : écrire une erreur dans la console et spécifier la catégorie</span><span class="sxs-lookup"><span data-stu-id="91c2f-124">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="91c2f-125">Cette commande déclare une erreur sans fin d'exécution et spécifie une catégorie d'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-125">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="91c2f-126">Exemple 4 : écrire une erreur à l’aide d’un objet exception</span><span class="sxs-lookup"><span data-stu-id="91c2f-126">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="91c2f-127">Cette commande utilise un objet **Exception** pour déclarer une erreur sans fin d'exécution.</span><span class="sxs-lookup"><span data-stu-id="91c2f-127">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="91c2f-128">La première commande utilise une table de hachage pour créer l'objet **System.Exception**.</span><span class="sxs-lookup"><span data-stu-id="91c2f-128">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="91c2f-129">Elle enregistre l’objet exception dans la `$E` variable.</span><span class="sxs-lookup"><span data-stu-id="91c2f-129">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="91c2f-130">Vous pouvez utiliser une table de hachage pour créer n'importe quel objet d'un type qui a un constructeur de valeur null.</span><span class="sxs-lookup"><span data-stu-id="91c2f-130">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="91c2f-131">La deuxième commande utilise l' `Write-Error` applet de commande pour déclarer une erreur sans fin d’achèvement.</span><span class="sxs-lookup"><span data-stu-id="91c2f-131">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="91c2f-132">La valeur du paramètre **exception** est l’objet **exception** dans la `$E` variable.</span><span class="sxs-lookup"><span data-stu-id="91c2f-132">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="91c2f-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="91c2f-133">PARAMETERS</span></span>

### <span data-ttu-id="91c2f-134">-Catégorie</span><span class="sxs-lookup"><span data-stu-id="91c2f-134">-Category</span></span>

<span data-ttu-id="91c2f-135">Spécifie la catégorie de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-135">Specifies the category of the error.</span></span> <span data-ttu-id="91c2f-136">La valeur par défaut est **NotSpecified**.</span><span class="sxs-lookup"><span data-stu-id="91c2f-136">The default value is **NotSpecified**.</span></span> <span data-ttu-id="91c2f-137">Les valeurs valides pour ce paramètre sont :</span><span class="sxs-lookup"><span data-stu-id="91c2f-137">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="91c2f-138">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="91c2f-138">NotSpecified</span></span>
- <span data-ttu-id="91c2f-139">OpenError</span><span class="sxs-lookup"><span data-stu-id="91c2f-139">OpenError</span></span>
- <span data-ttu-id="91c2f-140">CloseError</span><span class="sxs-lookup"><span data-stu-id="91c2f-140">CloseError</span></span>
- <span data-ttu-id="91c2f-141">DeviceError</span><span class="sxs-lookup"><span data-stu-id="91c2f-141">DeviceError</span></span>
- <span data-ttu-id="91c2f-142">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="91c2f-142">DeadlockDetected</span></span>
- <span data-ttu-id="91c2f-143">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="91c2f-143">InvalidArgument</span></span>
- <span data-ttu-id="91c2f-144">InvalidData</span><span class="sxs-lookup"><span data-stu-id="91c2f-144">InvalidData</span></span>
- <span data-ttu-id="91c2f-145">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="91c2f-145">InvalidOperation</span></span>
- <span data-ttu-id="91c2f-146">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="91c2f-146">InvalidResult</span></span>
- <span data-ttu-id="91c2f-147">InvalidType</span><span class="sxs-lookup"><span data-stu-id="91c2f-147">InvalidType</span></span>
- <span data-ttu-id="91c2f-148">MetadataError</span><span class="sxs-lookup"><span data-stu-id="91c2f-148">MetadataError</span></span>
- <span data-ttu-id="91c2f-149">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="91c2f-149">NotImplemented</span></span>
- <span data-ttu-id="91c2f-150">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="91c2f-150">NotInstalled</span></span>
- <span data-ttu-id="91c2f-151">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="91c2f-151">ObjectNotFound</span></span>
- <span data-ttu-id="91c2f-152">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="91c2f-152">OperationStopped</span></span>
- <span data-ttu-id="91c2f-153">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="91c2f-153">OperationTimeout</span></span>
- <span data-ttu-id="91c2f-154">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="91c2f-154">SyntaxError</span></span>
- <span data-ttu-id="91c2f-155">ParserError</span><span class="sxs-lookup"><span data-stu-id="91c2f-155">ParserError</span></span>
- <span data-ttu-id="91c2f-156">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="91c2f-156">PermissionDenied</span></span>
- <span data-ttu-id="91c2f-157">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="91c2f-157">ResourceBusy</span></span>
- <span data-ttu-id="91c2f-158">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="91c2f-158">ResourceExists</span></span>
- <span data-ttu-id="91c2f-159">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="91c2f-159">ResourceUnavailable</span></span>
- <span data-ttu-id="91c2f-160">ReadError</span><span class="sxs-lookup"><span data-stu-id="91c2f-160">ReadError</span></span>
- <span data-ttu-id="91c2f-161">WriteError</span><span class="sxs-lookup"><span data-stu-id="91c2f-161">WriteError</span></span>
- <span data-ttu-id="91c2f-162">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="91c2f-162">FromStdErr</span></span>
- <span data-ttu-id="91c2f-163">SecurityError</span><span class="sxs-lookup"><span data-stu-id="91c2f-163">SecurityError</span></span>
- <span data-ttu-id="91c2f-164">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="91c2f-164">ProtocolError</span></span>
- <span data-ttu-id="91c2f-165">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="91c2f-165">ConnectionError</span></span>
- <span data-ttu-id="91c2f-166">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="91c2f-166">AuthenticationError</span></span>
- <span data-ttu-id="91c2f-167">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="91c2f-167">LimitsExceeded</span></span>
- <span data-ttu-id="91c2f-168">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="91c2f-168">QuotaExceeded</span></span>
- <span data-ttu-id="91c2f-169">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="91c2f-169">NotEnabled</span></span>

<span data-ttu-id="91c2f-170">Pour plus d’informations sur les catégories d’erreur, consultez [énumération ErrorCategory](https://go.microsoft.com/fwlink/?LinkId=143600).</span><span class="sxs-lookup"><span data-stu-id="91c2f-170">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-171">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="91c2f-171">-CategoryActivity</span></span>

<span data-ttu-id="91c2f-172">Spécifie l’action à l’origine de l’erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-172">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-173">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="91c2f-173">-CategoryReason</span></span>

<span data-ttu-id="91c2f-174">Spécifie comment ou pourquoi l’activité a provoqué l’erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-174">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-175">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="91c2f-175">-CategoryTargetName</span></span>

<span data-ttu-id="91c2f-176">Spécifie le nom de l'objet en cours de traitement quand l'erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="91c2f-176">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-177">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="91c2f-177">-CategoryTargetType</span></span>

<span data-ttu-id="91c2f-178">Spécifie le type de l'objet en cours de traitement quand l'erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="91c2f-178">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-179">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="91c2f-179">-ErrorId</span></span>

<span data-ttu-id="91c2f-180">Spécifie une chaîne d'identification pour identifier l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-180">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="91c2f-181">La chaîne doit être propre à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-181">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-182">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="91c2f-182">-ErrorRecord</span></span>

<span data-ttu-id="91c2f-183">Spécifie un objet d'enregistrement d'erreur qui représente l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-183">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="91c2f-184">Utilisez les propriétés de l'objet pour décrire l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-184">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="91c2f-185">Pour créer un objet enregistrement d’erreur, utilisez l’applet de commande `New-Object` ou récupérez un objet enregistrement d’erreur à partir du tableau dans la `$Error` variable automatique.</span><span class="sxs-lookup"><span data-stu-id="91c2f-185">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-186">-Exception</span><span class="sxs-lookup"><span data-stu-id="91c2f-186">-Exception</span></span>

<span data-ttu-id="91c2f-187">Spécifie un objet d'exception qui représente l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-187">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="91c2f-188">Utilisez les propriétés de l'objet pour décrire l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-188">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="91c2f-189">Pour créer un objet exception, utilisez une table de hachage ou utilisez l’applet de commande `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="91c2f-189">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-190">-Message</span><span class="sxs-lookup"><span data-stu-id="91c2f-190">-Message</span></span>

<span data-ttu-id="91c2f-191">Spécifie le texte du message de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-191">Specifies the message text of the error.</span></span> <span data-ttu-id="91c2f-192">Si le texte comprend des espaces ou des caractères spéciaux, placez-le entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="91c2f-192">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="91c2f-193">Vous pouvez également diriger une chaîne de message vers `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="91c2f-193">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-194">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="91c2f-194">-RecommendedAction</span></span>

<span data-ttu-id="91c2f-195">Spécifie l’action que l’utilisateur doit entreprendre pour résoudre ou éviter l’erreur.</span><span class="sxs-lookup"><span data-stu-id="91c2f-195">Specifies the action that the user should take to resolve or prevent the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-196">-TargetObject</span><span class="sxs-lookup"><span data-stu-id="91c2f-196">-TargetObject</span></span>

<span data-ttu-id="91c2f-197">Spécifie l'objet en cours de traitement quand l'erreur s'est produite.</span><span class="sxs-lookup"><span data-stu-id="91c2f-197">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="91c2f-198">Entrez l’objet, une variable qui contient l’objet ou une commande qui obtient l’objet.</span><span class="sxs-lookup"><span data-stu-id="91c2f-198">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="91c2f-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="91c2f-199">CommonParameters</span></span>

<span data-ttu-id="91c2f-200">Cette applet de commande prend en charge les paramètres courants : -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction et -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="91c2f-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="91c2f-201">Pour plus d’informations, consultez [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="91c2f-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="91c2f-202">ENTRÉES</span><span class="sxs-lookup"><span data-stu-id="91c2f-202">INPUTS</span></span>

### <span data-ttu-id="91c2f-203">System.String</span><span class="sxs-lookup"><span data-stu-id="91c2f-203">System.String</span></span>

<span data-ttu-id="91c2f-204">Vous pouvez diriger une chaîne qui contient un message d’erreur vers `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="91c2f-204">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="91c2f-205">SORTIES</span><span class="sxs-lookup"><span data-stu-id="91c2f-205">OUTPUTS</span></span>

### <span data-ttu-id="91c2f-206">Objet d’erreur</span><span class="sxs-lookup"><span data-stu-id="91c2f-206">Error object</span></span>

<span data-ttu-id="91c2f-207">`Write-Error` écrit uniquement dans le flux d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="91c2f-207">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="91c2f-208">Aucun objet n'est retourné.</span><span class="sxs-lookup"><span data-stu-id="91c2f-208">It does not return any objects.</span></span>

## <span data-ttu-id="91c2f-209">REMARQUES</span><span class="sxs-lookup"><span data-stu-id="91c2f-209">NOTES</span></span>

<span data-ttu-id="91c2f-210">`Write-Error` ne modifie pas la valeur de la `$?` variable automatique. par conséquent, elle ne signale pas une condition d’erreur de fin.</span><span class="sxs-lookup"><span data-stu-id="91c2f-210">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="91c2f-211">Pour signaler une erreur de fin, utilisez la méthode [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .</span><span class="sxs-lookup"><span data-stu-id="91c2f-211">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="91c2f-212">LIENS CONNEXES</span><span class="sxs-lookup"><span data-stu-id="91c2f-212">RELATED LINKS</span></span>

[<span data-ttu-id="91c2f-213">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="91c2f-213">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="91c2f-214">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="91c2f-214">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="91c2f-215">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="91c2f-215">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="91c2f-216">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="91c2f-216">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="91c2f-217">Write-Host</span><span class="sxs-lookup"><span data-stu-id="91c2f-217">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="91c2f-218">Write-Output</span><span class="sxs-lookup"><span data-stu-id="91c2f-218">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="91c2f-219">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="91c2f-219">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="91c2f-220">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="91c2f-220">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="91c2f-221">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="91c2f-221">Write-Warning</span></span>](Write-Warning.md)
