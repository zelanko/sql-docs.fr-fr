---
title: Paramètres d’informations de périphérique ATOM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c4d0f85da3c3762d32b8a59a34e073e9f14736a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321879"
---
# <a name="atom-device-information-settings"></a>Paramètres d'informations de périphérique ATOM
  Les paramètres d'informations de périphériques pour l'extension de rendu Atom prennent en charge la soumission du nom d'un flux Atom et de l'encodage de caractères à utiliser.  
  
 Le tableau suivant répertorie les paramètres des informations de périphériques pour le rendu dans un document de service de données.  
  
|Paramètre|Valeur|  
|-------------|-----------|  
|`DataFeed`|Si spécifié, restitue le flux Atom correspondant au nom de flux fourni dans ce paramètre. Dans le cas contraire, restitue le document de service Atom pour le rapport. Identificateur unique de la source de données générée automatiquement. Cette valeur est utilisée en interne et vous ne devez pas le modifier.|  
|**Encodage**|Nom IANA (Internet Assigned Numbers Authority) d'un encodage de caractères pris en charge par le .NET Framework. La valeur par défaut est `UTF-8`. Les exemples d'autres valeurs incluent ASCII, UTF-7 et UTF-16.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Transmission de paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  