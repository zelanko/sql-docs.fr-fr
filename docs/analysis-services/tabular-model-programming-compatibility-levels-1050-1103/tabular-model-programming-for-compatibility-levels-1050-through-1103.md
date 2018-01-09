---
title: "Programmation de modèle tabulaire pour la compatibilité des niveaux de 1050 via 1103 | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9fa62ae93df8b15ca3ef545dc1ebb0d1b4df644e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>Programmation de modèle tabulaire pour la compatibilité 1050 1103 via des niveaux
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Les modèles tabulaires utilisent des constructions relationnelles pour modéliser les données d’Analysis Services utilisées par les applications analytiques et de rapports. Ces modèles s'exécutent sur une instance Analysis Service qui est configurée pour le mode tabulaire, en utilisant un moteur d'analyse en mémoire pour le stockage et les analyses de table rapides qui agrègent et calculent des données à mesure qu'elles sont demandées.  
  
 Si les besoins de votre solution BI personnalisée sont mieux remplis par une base de données de modèles tabulaires, vous pouvez utiliser l'une des bibliothèques Analysis Services et interfaces de programmation clientes pour intégrer votre application à des modèles tabulaires sur une instance Analysis Services. Pour interroger et calculer des données de modèle tabulaire, vous pouvez utiliser MDX ou DAX incorporé dans votre code.  
  
 Pour les modèles tabulaires créés dans les versions antérieures d’Analysis Services, notamment les modèles à des niveaux de compatibilité 1050 via 1103, les objets que vous utilisez par programme dans AMO, ADOMD.NET, XMLA ou OLE DB sont fondamentalement les mêmes pour les solutions tabulaires et multidimensionnelles. Plus précisément, les métadonnées d’objets définies pour les modèles multidimensionnels sont également utilisée pour les niveaux de compatibilité de modèle tabulaire 1050-1103.  
  
 À partir de SQL Server 2016, les modèles tabulaires peuvent créés ou mis à niveau vers le niveau de compatibilité 1200 ou supérieur, qui utilise des métadonnées tabulaires pour définir le modèle. Métadonnées et programmabilité sont fondamentalement différents à ce niveau. Consultez [tabulaire modèle de programmation pour 1200 de niveau de compatibilité et versions ultérieures](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) et [mettre à niveau Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) pour plus d’informations.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Annotations CSDL pour Business Intelligence &#40;CSDLBI&#41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [Présentation du modèle d’objet tabulaire au niveau de compatibilité 1050 1103 via des niveaux](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  

[IMDEmbeddedData, interface](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
