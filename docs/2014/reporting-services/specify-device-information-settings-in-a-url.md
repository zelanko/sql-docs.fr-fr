---
title: Spécifier les paramètres d’informations des périphériques dans une URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a77fe212fc4637c384a8328aa1094db91b9a8d11
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255571"
---
# <a name="specify-device-information-settings-in-a-url"></a>Spécifier les paramètres d'informations de périphérique dans une URL
  Les paramètres d'informations de périphérique sont des paramètres qui sont transmis à une extension de rendu. Si vous utilisez les méthodes du service Web Report Server [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour effectuer le rendu d'un rapport, un élément XML `DeviceInfo` est transmis en tant que paramètre d'entrée. Éléments enfants de le `DeviceInfo` élément sont spécifiques aux paramètres d’informations de périphérique de différentes extensions de rendu. Vous pouvez inclure des paramètres d’informations de périphérique dans une URL en utilisant la chaîne de paramètre *rc:tag=value* , où *tag* est le nom de l’élément des paramètres d’informations de périphérique en cours d’accès. Pour plus d’informations sur les paramètres d’informations de périphérique dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consultez [en passant des paramètres d’informations de périphérique aux Extensions de rendu](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit le format du rapport spécifié sur JPEG en utilisant le paramètre d’informations de périphérique *OutputFormat* de l’extension de rendu d’image (les sauts de ligne ont été ajoutés pour la lisibilité) :  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Accès URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Référence de paramètres d'accès URL](url-access-parameter-reference.md)  
  
  
