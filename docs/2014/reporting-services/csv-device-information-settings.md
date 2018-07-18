---
title: Paramètres d’informations de périphérique CSV | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 5e2183790fcc7af3f173d7f674173f3dd49857fb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307499"
---
# <a name="csv-device-information-settings"></a>Paramètres d'informations de périphérique CSV
  Les paramètres d'informations de périphérique de l'extension de rendu CSV permettent de modifier les séparateurs et les qualificateurs et de spécifier la manière de gérer les sauts de ligne. L'extension du fichier peut également être envoyée, ainsi que l'encodage et l'inclusion des lignes d'en-tête dans la sortie. Étant donné que les séparateurs sont probablement des caractères spéciaux, vous devez les encoder dans une section CDATA, si les paramètres sont écrits au format XML.  
  
 Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu du rapport au format Texte.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|`Encoding`|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
|`ExcelMode`|Indique que la sortie cible est destinée à Excel. La valeur par défaut est `true`.|  
|`FieldDelimiter`|Chaîne de séparateur à placer dans le résultat. La valeur par défaut est une virgule (,). Vous devez encoder la valeur de cette information de périphérique pour la transmettre à une URL. Par exemple, un caractère de tabulation utilisé en tant que séparateur doit être codé par « %09 ».<br /><br /> Vous pouvez changer de séparateur de champs par défaut et utiliser le caractère de votre choix, y compris TAB, en modifiant les paramètres d'informations de périphérique dans le fichier de configuration. Par exemple, pour utiliser TAB, remplacez le paramètre FieldDelimiter par \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter><br /><br /> Dans l'exemple, [TAB] est une vraie tabulation, ce qui signifie que l'espace blanc apparaît dans le fichier de configuration. L'attribut « xml:space » indique aux analyseurs de conserver l'espace blanc.|  
|`FileExtension`|Extension de fichier à placer dans le résultat. La valeur par défaut est `.CSV`. Si les paramètres `FileExtension` et `Extension` sont spécifiés, alors le paramètre `FileExtension` est prioritaire.|  
|**NoHeader**|Indique si la ligne d'en-tête est exclue de la sortie. La valeur par défaut est `false`.|  
|`Qualifier`|Chaîne de qualificateur à placer dans les résultats qui contiennent le séparateur de champs ou le séparateur d'enregistrements. Si les résultats contiennent le qualificateur, celui-ci est répété. Le paramètre `Qualifier` doit être différent des paramètres `FieldDelimiter` et `RecordDelimiter`. La valeur par défaut est un guillemet (").|  
|`RecordDelimiter`|Séparateur d'enregistrements à placer à la fin de chaque d'enregistrement. La valeur par défaut est \<cr>\<lf>.|  
|**SuppressLineBreaks**|Indique si les sauts de ligne sont supprimés des données incluses dans la sortie. La valeur par défaut est `false`. Si la valeur est `true`, le `FieldDelimiter`, `RecordDelimiter`, et `Qualifier` paramètres ne peut pas être un caractère d’espacement.|  
|`UseFormattedValues`|Indique si les chaînes mises en forme sont placées dans la sortie CSV. La valeur par défaut est `true` lorsque `ExcelMode` est `true`; sinon, il est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
