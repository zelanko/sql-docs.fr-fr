---
title: "Limiter l&#39;historique de rapport (Gestionnaire de rapports) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualisation de l'historique de rapport"
  - "historique de rapport [Reporting Services], affichage de l’historique"
  - "historique de rapport [Reporting Services], configuration de l’historique"
  - "données historiques [Reporting Services]"
  - "affichage de l'historique de rapport"
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# Limiter l&#39;historique de rapport (Gestionnaire de rapports)
  L'historique de rapport est un ensemble d'instantanés de rapport que vous créez au fil du temps. Vous pouvez soit créer l'historique de rapport à la demande, soit planifier la fréquence à laquelle un instantané est créée et ajoutée à l'historique de rapport.  
  
 L'historique de rapport est stocké dans la base de données du serveur de rapports. Si les instantanés de rapport contiennent une grande quantité de données, songez à limiter l'historique de rapport afin de réduire l'impact de la rétention des instantanés sur la taille de la base de données.  
  
### Pour configurer un historique de rapport destiné à un serveur de rapports  
  
1.  Dans le Gestionnaire de rapports, dans la barre d’outils globale, cliquez sur **Paramètres du site**.  
  
2.  Sélectionnez l’option **Conserver un nombre illimité d’instantanés dans l’historique de rapport** pour conserver tous les historiques de rapport sur une durée indéterminée. Sinon, choisissez **Limiter les copies de l’historique de rapport** pour spécifier le nombre maximal d’instantanés à conserver pour un rapport donné.  
  
3.  Cliquez sur **Appliquer**.  
  
### Pour configurer un historique de rapport destiné à un rapport spécifique  
  
1.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'au rapport pour lequel configurer l'historique, puis cliquez sur cet élément pour l'ouvrir.  
  
2.  Cliquez sur l’onglet **Propriétés**.  
  
3.  Cliquez sur l’onglet **Historique**.  
  
4.  Sélectionnez les options pour votre rapport, puis cliquez sur **Appliquer**. Pour plus d’informations sur chaque option, consultez [Page de propriétés Options d’instantanés &#40;Gestionnaire de rapports&#41;](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md).  
  
## Voir aussi  
 [Ajout d’un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  