---
title: Récupération des données à partir d’une Source de données analytiques | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: 41
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4e5595bd4e001b006cb1dfe62cba40cee3bbb30c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196419"
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Récupération de données à partir d'une source de données analytiques
  Dès lors que vous avez établi une connexion et que vous avez créé la requête, vous pouvez récupérer tout type de données. Dans ADOMD.NET, vous pouvez récupérer des données par le biais de trois objets différents (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader> et <xref:System.Xml.XmlReader>) en appelant l'une des méthodes `Execute` de l'objet <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>.  
  
 Chacun de ces trois objets établit un équilibre entre interactivité et charge :  
  
-   *Interactivité* fait référence à la facilité d’utilisation et la quantité d’informations disponibles via le modèle objet.  
  
-   *Surcharge* fait référence à la quantité de trafic qui génère un modèle objet via la connexion réseau au serveur, la quantité de mémoire nécessaire pour le modèle objet et la vitesse à laquelle le modèle objet récupère les données.  
  
 Pour vous aider à sélectionner l'objet de récupération de données qui répond le mieux aux besoins de votre application, le tableau suivant souligne les différences entre interactivité et charge pour chaque objet.  
  
|Object|Interactivité|Charge|Conserve la dimensionnalité|Informations d'utilisation|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Maximale|Relativement élevée, ce qui se traduit par une vitesse de récupération de données des plus lentes|Oui|[Récupération de données à l’aide de la classe CellSet](retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Modérée|Modérée|non|[Remplissage d’un DataSet à partir d’un DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Modérée|Modérée|non|[Récupération de données à l’aide d’AdomdDataReader](retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Minimale|Minimale, ce qui se traduit par une vitesse de récupération de données des plus rapides|Oui|[Récupération de données à l’aide de XmlReader](retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du client ADOMD.NET](adomd-net-client-programming.md)  
  
  
