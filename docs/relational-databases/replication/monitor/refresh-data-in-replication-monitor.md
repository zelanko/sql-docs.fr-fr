---
title: "Actualiser des donn&#233;es dans le Moniteur de r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "actualisation des données"
ms.assetid: e9582244-7d00-45f4-be16-020a65c76a5e
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Actualiser des donn&#233;es dans le Moniteur de r&#233;plication
  Dans le moniteur de réplication, la fenêtre principale et les fenêtres de détails (ces fenêtres lancées à partir de la fenêtre principale) peuvent être actualisées automatiquement ou manuellement. Pour actualiser une fenêtre manuellement, appuyez sur la touche F5. Par défaut, la fenêtre principale est actualisée automatiquement toutes les cinq secondes ; la fréquence peut être personnalisée pour chaque serveur de publication.  
  
 Les données affichées dans le moniteur de réplication sont interrogées à partir d’un cache. Pour plus d’informations sur la relation entre le cache et l’actualisation le moniteur de réplication, consultez [mise en cache, l’actualisation et performances du moniteur de réplication](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md). Pour plus d’informations sur le démarrage du moniteur de réplication, consultez [Démarrer le moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Pour définir les options d'actualisation pour le moniteur de réplication  
  
1.  Cliquez sur un serveur de publication dans le volet gauche du moniteur de réplication, puis cliquez sur **les paramètres de serveur de publication**.  
  
2.  Dans le **paramètres Publisher** boîte de dialogue, définissez la **actualisation automatique** et **d’actualisation** options. Le **actualisation automatique** paramètre a une incidence sur la fenêtre principale dans le moniteur de réplication. Le **d’actualisation** paramètre affecte également toutes les fenêtres de détails qui sont définies pour actualiser automatiquement (modifications du paramètre affectent uniquement les fenêtres de détails ouvertes après la modification).  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour spécifier qu'une fenêtre de détails doit s'actualiser automatiquement  
  
1.  Ouvrez une fenêtre de détails dans le moniteur de réplication. Exemple :  
  
    1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
    2.  Cliquez sur l'onglet **Tous les abonnements** .  
  
    3.  Avec le bouton droit à un abonnement, puis cliquez sur **Afficher les détails**.  
  
2.  Dans la **abonnement \< SubscriptionName>** fenêtre de détails, cliquez sur **Action**, puis cliquez sur **actualisation automatique**. La fréquence d’actualisation est déterminée par la **d’actualisation** dans le **paramètres Publisher** boîte de dialogue.  
  
## Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  