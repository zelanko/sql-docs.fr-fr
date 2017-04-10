---
title: "Colonnes de mise en correspondance de la qualit&#233; des donn&#233;es (Compl&#233;ment MDS pour Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f683fdc6-0d4c-4793-8143-567616cb2094
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Colonnes de mise en correspondance de la qualit&#233; des donn&#233;es (Compl&#233;ment MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], après avoir mis les données en correspondance, dans le groupe **Qualité des données** du ruban, vous pouvez cliquer sur **Afficher les détails** pour afficher les colonnes qui fournissent des détails sur les correspondances.  
  
 Le tableau suivant présente les colonnes affichées lors de la mise en correspondance des données.  
  
|Nom|Description|  
|----------|-----------------|  
|**CLUSTER_ID**|Identificateur unique utilisé pour regrouper les enregistrements similaires. Toutes les lignes similaires ont le même **CLUSTER_ID**. Si aucun **CLUSTER_ID** n’est affiché pour une ligne, aucun enregistrement similaire n’a été trouvé.|  
|**RECORD_ID**|Identificateur unique utilisé pour identifier les enregistrements. Similaire à la valeur Code stockée dans le référentiel MDS, il s'agit d'une valeur utilisée pour identifier un enregistrement. Il est généré automatiquement chaque fois que la mise en correspondance a lieu.|  
|**PIVOT_MARK**|Enregistrement arbitraire auxquels les autres enregistrements sont comparés ; il n'a pas de valeur de score.|  
|**SCORE**|Représente le degré de similitude des enregistrements du groupe par rapport à l'enregistrement pivot. Ce score est déterminé par DQS. Si aucun score n'est affiché, l'enregistrement est le tableau croisé dynamique d'autres enregistrements, ou bien aucune correspondance n'a été trouvée.|  
  
## Voir aussi  
 [Mise en correspondance de la qualité des données dans le complément MDS pour Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Mettre en correspondance les données similaires &#40;Complément MDS pour Excel&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)   
 [Correspondance de données](../../data-quality-services/data-matching.md)  
  
  