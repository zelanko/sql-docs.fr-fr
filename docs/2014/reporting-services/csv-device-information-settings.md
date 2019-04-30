---
title: Paramètres d’informations de périphérique CSV | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 123afc28db147118d10a66199364ca8b73afb34c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63265409"
---
# <a name="csv-device-information-settings"></a>Paramètres d'informations de périphérique CSV
  Les paramètres d'informations de périphérique de l'extension de rendu CSV permettent de modifier les séparateurs et les qualificateurs et de spécifier la manière de gérer les sauts de ligne. L'extension du fichier peut également être envoyée, ainsi que l'encodage et l'inclusion des lignes d'en-tête dans la sortie. Étant donné que les séparateurs sont probablement des caractères spéciaux, vous devez les encoder dans une section CDATA, si les paramètres sont écrits au format XML.  
  
 Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu du rapport au format Texte.  
  
|Paramètre|Value|  
|-------------|-----------|  
|`Encoding`|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
|`ExcelMode`|Indique que la sortie cible est destinée à Excel. La valeur par défaut est `true`.|  
|`FieldDelimiter`|Chaîne de séparateur à placer dans le résultat. La valeur par défaut est une virgule (,). Vous devez encoder la valeur de cette information de périphérique pour la transmettre à une URL. Par exemple, un caractère de tabulation utilisé en tant que séparateur doit être codé par « %09 ».<br /><br /> Vous pouvez changer de séparateur de champs par défaut et utiliser le caractère de votre choix, y compris TAB, en modifiant les paramètres d'informations de périphérique dans le fichier de configuration. Par exemple, pour utiliser TAB, remplacez le paramètre FieldDelimiter par \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter><br /><br /> Dans l'exemple, [TAB] est une vraie tabulation, ce qui signifie que l'espace blanc apparaît dans le fichier de configuration. L'attribut « xml:space » indique aux analyseurs de conserver l'espace blanc.|  
|`FileExtension`|Extension de fichier à placer dans le résultat. La valeur par défaut est `.CSV`. Si les paramètres `FileExtension` et `Extension` sont spécifiés, alors le paramètre `FileExtension` est prioritaire.|  
|**NoHeader**|Indique si la ligne d'en-tête est exclue de la sortie. La valeur par défaut est `false`.|  
|`Qualifier`|Chaîne de qualificateur à placer dans les résultats qui contiennent le séparateur de champs ou le séparateur d'enregistrements. Si les résultats contiennent le qualificateur, celui-ci est répété. Le paramètre `Qualifier` doit être différent des paramètres `FieldDelimiter` et `RecordDelimiter`. La valeur par défaut est un guillemet (").|  
|`RecordDelimiter`|Séparateur d'enregistrements à placer à la fin de chaque d'enregistrement. La valeur par défaut est \<cr>\<lf>.|  
|**SuppressLineBreaks**|Indique si les sauts de ligne sont supprimés des données incluses dans la sortie. La valeur par défaut est `false`. Si la valeur est `true`, les paramètres `FieldDelimiter`, `RecordDelimiter` et `Qualifier` ne peuvent pas être un espace.|  
|`UseFormattedValues`|Indique si les chaînes mises en forme sont placées dans la sortie CSV. La valeur par défaut est `true` lorsque le `ExcelMode` a pour valeur `true` ; sinon, la valeur par défaut est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d'informations de périphérique aux extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d'extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
