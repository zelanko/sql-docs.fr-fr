---
title: Colonnes de mise en correspondance de la qualité des données (Complément MDS pour Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 9a7303d6791c8320bc2c45fc624c396eaee52e98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488203"
---
# <a name="data-quality-matching-columns-mds-add-in-for-excel"></a>Colonnes de mise en correspondance de la qualité des données (Complément MDS pour Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], après avoir mis les données en correspondance, dans le groupe **Qualité des données** du ruban, vous pouvez cliquer sur **Afficher les détails** pour afficher les colonnes qui fournissent des détails sur les correspondances.  
  
 Le tableau suivant présente les colonnes affichées lors de la mise en correspondance des données.  
  
|Créer une vue d’abonnement|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Identificateur unique utilisé pour regrouper les enregistrements similaires. Toutes les lignes similaires ont le même **CLUSTER_ID**. Si aucun **CLUSTER_ID** n’est affiché pour une ligne, aucun enregistrement similaire n’a été trouvé.|  
|**RECORD_ID**|Identificateur unique utilisé pour identifier les enregistrements. Similaire à la valeur Code stockée dans le référentiel MDS, il s'agit d'une valeur utilisée pour identifier un enregistrement. Il est généré automatiquement chaque fois que la mise en correspondance a lieu.|  
|**PIVOT_MARK**|Enregistrement arbitraire auxquels les autres enregistrements sont comparés ; il n'a pas de valeur de score.|  
|**SCORE**|Représente le degré de similitude des enregistrements du groupe par rapport à l'enregistrement pivot. Ce score est déterminé par DQS. Si aucun score n'est affiché, l'enregistrement est le tableau croisé dynamique d'autres enregistrements, ou bien aucune correspondance n'a été trouvée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Correspondance de données](../../data-quality-services/data-matching.md)  
  
  
