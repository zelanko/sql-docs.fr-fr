---
title: "mettre en cache un rapport (Gestionnaire de rapports) | Microsoft Docs"
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
  - "propriétés relatives à l'exécution des rapports [Reporting Services]"
  - "cache [Reporting Services]"
  - "rapports mis en cache [Reporting Services]"
  - "planifications [Reporting Services], expiration des rapports"
  - "expiration [Reporting Services]"
ms.assetid: 723d1cb0-c2e7-4763-8690-a6a7a8bbbb90
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# mettre en cache un rapport (Gestionnaire de rapports)
  L'un des moyens d'améliorer les performances est de configurer les propriétés de mise en cache d'un rapport. Lorsqu'un rapport est mis en cache, une copie du rapport rendu est enregistrée pour une courte durée. Le premier utilisateur qui demande le rapport doit attendre que son traitement soit entièrement terminé avant de pouvoir l'afficher. Les utilisateurs ultérieurs qui demandent le rapport pendant la période de mise en cache peuvent le consulter immédiatement, car son traitement a déjà eu lieu.  
  
 Il existe des restrictions concernant les types de rapports que vous pouvez mettre en cache. Par exemple, un rapport ne peut pas être mis en cache si sa sortie varie selon l'identité de l'utilisateur, ou si les données sont récupérées à l'aide du jeton de sécurité de l'utilisateur qui demande le rapport. Pour plus d’informations, consultez [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md).  
  
### Pour planifier l'expiration d'un rapport mis en cache  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** . Accédez au rapport pour lequel vous souhaitez définir des propriétés de mise en cache, pointez sur l'élément et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**.  
  
4.  Dans le cadre de gauche, cliquez sur **Options de traitement**.  
  
5.  Dans la page qui s’affiche, sélectionnez **Toujours exécuter ce rapport avec les données les plus récentes**.  
  
6.  Sélectionnez l’une des deux options de cache suivantes et configurez l’expiration comme suit :  
  
    -   Pour configurer l'expiration d'une copie mise en cache après l'écoulement d'une durée particulière, cliquez sur **Mettre en cache une copie temporaire du rapport. Faire expirer la copie du rapport après un certain nombre de minutes**. Tapez le nombre de minutes pour l'expiration du rapport.  
  
    -   Pour configurer l’expiration d’une copie mise en cache selon une planification, cliquez sur **Mettre en cache une copie temporaire du rapport. Faire expirer la copie du rapport selon la planification suivante.** Cliquez sur **Configurer** ou sélectionnez une planification partagée pour contrôler l’expiration du rapport.  
  
7.  Cliquez sur **Appliquer**.  
  
## Voir aussi  
 [Définir les propriétés de traitement d'un rapport](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)  
  
  