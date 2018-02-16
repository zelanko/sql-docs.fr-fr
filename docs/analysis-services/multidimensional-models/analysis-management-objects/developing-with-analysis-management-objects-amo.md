---
title: "Développement avec Analysis Management Objects (AMO) | Documents Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, programming
- AMO, programming
ms.assetid: 91354fc9-22da-4724-b97f-3b1e7b0e69d3
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4a44da0b795bcb7e8ed05510d8caf0178bb789e5
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="developing-with-analysis-management-objects-amo"></a>Développement avec AMO (Analysis Management Objects)
Objets AMO (Analysis Management) est la bibliothèque d’objets accessibles par programme complète qui permet à une application gérer une instance en cours d’exécution de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].

Cette section explique les concepts AMO en mettant l'accent sur les objets principaux. Elle explique comment et quand les utiliser et la façon dont ils sont liés les uns aux autres. Pour plus d’informations sur les classes ou des objets spécifiques, consultez :

- [Microsoft.AnalysisServices Namespace](http://msdn.microsoft.com/library/microsoft.analysisservices.aspx), pour la documentation de référence
- [Analysis Services Management Objects (AMO)](http://www.bing.com/search?q=Analysis+Services+Management+Objects+%28AMO%29), comme une recherche générale Bing.com.


 **Nouveautés de SQL Server 2016**

Dans SQL Server 2016, AMO est refactorisé en plusieurs assemblys. Classes génériques, telles que Server, base de données et des rôles sont dans le **Microsoft.AnalysisServices.Core** Namespace. API spécifiques multidimensionnel restent dans [Microsoft.AnalysisServices Namespace](https://msdn.microsoft.com/library/ms146720.aspx).

Des scripts personnalisés et les applications écrites sur des versions antérieures de AMO continue de fonctionner sans modification. Toutefois, si vous avez script ou des applications qui ciblent SQL Server 2016 en particulier, ou si vous avez besoin de reconstruire une solution personnalisée, veillez à ajouter le nouvel assembly et l’espace de noms à votre projet.

## <a name="see-also"></a>Voir aussi
[Développement avec Analysis Services Scripting Language &#40; ASSL &#41; ](../../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md) 
 [Développement avec XMLA dans Analysis Services](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)
