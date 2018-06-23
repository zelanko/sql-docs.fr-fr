---
title: Paramètres d’informations de périphérique XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
caps.latest.revision: 44
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b60e0abfbd6a0487fbc264a824c80ae8a5db60b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044891"
---
# <a name="xml-device-information-settings"></a>Paramètres d'informations de périphérique XML
  Le tableau suivant répertorie les paramètres d'informations de périphérique qui permettent un rendu au format XML.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|`XSLT`|Chemin d'accès dans l'espace de noms du serveur de rapports d'un XSLT et destiné au fichier XML, par exemple `/Transforms/myxslt`. Le fichier xsl doit être une ressource publiée sur le serveur de rapports et vous devez y accéder par le biais d'un chemin d'accès de l'élément du serveur de rapports. La valeur de ce paramètre est appliquée après tout XSLT spécifié dans le rapport. Si le paramètre `XSLT` est appliqué, le paramètre `OmitSchema` est ignoré.|  
|**MIMEType**|Type MIME (Multipurpose Internet Mail Extensions) du fichier XML.|  
|**UseFormattedValues**|Indique s'il faut restituer la valeur mise en forme d'une zone de texte lors de la génération des données XML. Une valeur false indique que la valeur sous-jacente de la zone de texte est utilisée.|  
|**Indented**|Indique s'il faut générer du code XML mis en retrait. La valeur par défaut `false` génère le code XML compressé sans mise en retrait.|  
|`OmitNamespace`|Indique s'il faut omettre l'espace de noms XML par défaut.<br /><br /> Si la valeur est True, le XML ne spécifie aucun espace de noms par défaut.<br /><br /> Si la valeur est False, le XML spécifie un espace de noms par défaut avec la valeur de la propriété DataSchema du rapport. La propriété DataSchema utilise par défaut le nom du rapport.<br /><br /> La valeur par défaut est `false`.|  
|`OmitSchema`|Indique s'il faut omettre l'emplacement du schéma XML par défaut. L'emplacement est l'attribut SchemaLocation. La valeur par défaut d'OmitSchema dépend de la valeur d'OmitNamespace :<br /><br /> Si OmitNamespace = False, OmitSchema = `False` par défaut. L'utilisateur peut remplacer la valeur par défaut en attribuant la valeur True à OmitSchema.<br /><br /> If OmitNamespace = True, then OmitSchema fonctionne comme `True` indépendamment de la valeur explicitement configurée pour OmitShema.|  
|**Encoding**|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
|**FileExtension**|Extension de fichier à utiliser pour le fichier généré.|  
|**Schéma**|Indique si la définition de schéma XML (XSD) est restituée ou si les données XML réelles sont restituées. La valeur `true` indique qu’un schéma XML est restitué. La valeur par défaut est `false`.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passage de paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  