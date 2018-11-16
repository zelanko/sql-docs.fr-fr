---
title: Rechercher un rapport à l’aide de l’accès URL | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- searching reports
- text searches [Reporting Services]
- URL access [Reporting Services], report searches
ms.assetid: 6f3410c4-7944-448f-bae8-bab3e8152d46
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a63f4c1c1ad925ee57def853c76f71ec52f9cb58
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813192"
---
# <a name="search-a-report-using-url-access"></a>Rechercher un rapport à l'aide de l'accès URL
  L'accès URL vous permet de lancer des recherches sur des rapports ou sur du texte spécifique. Pour effectuer une recherche dans un rapport, affectez au paramètre *rc:FindString* de l’URL le texte à rechercher. Vous povuez aussi utilisez les paramètres *rc:StartFind* et *rc:EndFind* pour limiter votre recherche à certaines pages du rapport.  
  
## <a name="example"></a> Exemple  
 Dans l'exemple suivant, qui illustre une recherche effectuée à l'aide d'un accès URL, la recherche porte sur la première occurrence du texte « Mountain-400 » entre les pages un et cinq de l'exemple de rapport intitulé Product Catalog :  
  
```  
https://server/Reportserver?/SampleReports/Product Catalog&rs:Command=Render&rc:StartFind=1&rc:EndFind=5&rc:FindString=Mountain-400  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Accès URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
  
  
