---
title: "La récupération des données à partir d’une Source de données analytiques | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f8d2c400fc82852333b64d9bd89b2e7c74190061
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Récupération de données à partir d'une source de données analytiques
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Une fois qu’une connexion et la création de la requête, vous pouvez extraire des données. Dans ADOMD.NET, vous pouvez récupérer des données à l’aide de trois objets différents (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, et <xref:System.Xml.XmlReader>) en appelant une de le **Execute** méthodes de la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> objet.  
  
 Chacun de ces trois objets établit un équilibre entre interactivité et charge :  
  
-   *L’interactivité* fait référence à la facilité d’utilisation et la quantité d’informations disponibles via le modèle objet.  
  
-   *Surcharge* fait référence à la quantité de trafic qui génère un modèle objet via la connexion réseau au serveur, la quantité de mémoire nécessaire pour le modèle d’objet et la vitesse à laquelle le modèle objet récupère les données.  
  
 Pour vous aider à sélectionner l'objet de récupération de données qui répond le mieux aux besoins de votre application, le tableau suivant souligne les différences entre interactivité et charge pour chaque objet.  
  
|Objet|Interactivité|Charge|Conserve la dimensionnalité|Informations d'utilisation|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Maximale|Relativement élevée, ce qui se traduit par une vitesse de récupération de données des plus lentes|Oui|[Récupération de données à l’aide de la classe CellSet](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Modérée|Modérée|Non|[Remplissage d’un DataSet à partir d’un DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Modérée|Modérée|Non|[Récupération de données à l’aide d’AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minimale|Minimale, ce qui se traduit par une vitesse de récupération de données des plus rapides|Oui|[Récupération de données à l’aide de XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
