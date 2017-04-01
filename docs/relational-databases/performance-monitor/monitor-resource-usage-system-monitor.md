---
title: "Analyser l&#39;utilisation des ressources (Moniteur syst&#232;me) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "surveillance des performances [SQL Server], utilisation des ressources"
  - "Moniteur système [SQL Server], à propos du Moniteur système Windows"
  - "utilisation des ressources, surveillance [SQL Server]"
  - "Moniteur système [SQL Server]"
  - "compteurs [SQL Server], sujets d’utilisation des ressources"
  - "compteurs de performances [SQL Server], sujets d’utilisation des ressources"
  - "Moniteur système Windows [SQL Server], à propos du Moniteur système Windows"
  - "surveillance [SQL Server], utilisation des ressources de serveur"
  - "surveillance de l'utilisation des ressources [SQL Server]"
  - "Moniteur système Windows [SQL Server]"
  - "surveillance des bases de données [SQL Server], utilisation des ressources"
  - "performances des bases de données [SQL Server], utilisation des ressources"
  - "paramétrage des bases de données [SQL Server], utilisation des ressources"
  - "performances de serveur [SQL Server], utilisation des ressources"
ms.assetid: f2993a28-0b81-46f2-aec0-6877fe990387
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Analyser l&#39;utilisation des ressources (Moniteur syst&#232;me)
  Si vous utilisez le système d'exploitation Microsoft Windows Server, faites appel à l'outil graphique Moniteur système pour mesurer les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez afficher les objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les compteurs de performance ainsi que le comportement d’autres objets, tels que les processeurs, la mémoire, le cache, les threads et les processus. Chacun de ces objets dispose d'un jeu de compteurs qui mesurent l'utilisation du dispositif, la longueur des files d'attente, les temporisations et d'autres indicateurs de débit et de congestion interne.  
  
> [!NOTE]  
>  Le Moniteur système a remplacé l'Analyseur de performances après Windows NT 4.0.  
  
## Avantages du Moniteur système  
 Le Moniteur système peut s'avérer utile pour surveiller les compteurs du système d'exploitation Windows et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] simultanément afin déterminer toute corrélation entre les performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et celles de Windows. Par exemple, la surveillance des compteurs d'E/S de disque de Windows et des compteurs de gestionnaire de tampons [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en même temps peut révéler le comportement de l'ensemble du système.  
  
 Le Moniteur système vous permet d'obtenir des statistiques sur l'activité et sur les performances actuelles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le Moniteur système vous permet :  
  
-   d'afficher simultanément des données provenant d'un nombre illimité d'ordinateurs ;  
  
-   d'afficher et de modifier les graphiques pour refléter l'activité en cours, et d'afficher les valeurs des compteurs actualisés selon une fréquence choisie par l'utilisateur ;  
  
-   d'exporter les données provenant de graphiques, des journaux, des journaux d'alertes et des rapports vers un tableur ou des applications de base de données afin de les traiter ou de les imprimer ultérieurement ;  
  
-   d'ajouter des alertes système qui répertorient un événement dans le journal d'alerte et peuvent vous en avertir par l'émission d'une alerte réseau ;  
  
-   d'exécuter un programme prédéfini la première fois ou chaque fois que la valeur d'un compteur est supérieure ou inférieure à une valeur définie par l'utilisateur ;  
  
-   de créer des fichiers journaux contenant des données relatives à différents objets provenant de différents ordinateurs ;  
  
-   d'ajouter à un fichier sélectionné des sections d'autres fichiers journaux afin de créer un fichier d'archive à long terme ;  
  
-   d'afficher les rapports d'activité en cours ou de créer des rapports à partir de fichiers journaux existants ;  
  
-   de sauvegarder les paramètres individuels de graphiques, d'alertes, de journaux ou de rapports, ou la totalité de la structure de l'espace de travail afin de pouvoir les réutiliser.  
  
    > [!NOTE]  
    >  Le Moniteur système a remplacé l'Analyseur de performances après Windows NT 4.0. Vous pouvez utiliser soit le Moniteur système, soit l'Analyseur de performances pour effectuer ces tâches.  
  
## Performances du Moniteur système  
 Quand vous surveillez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le système d'exploitation Microsoft Windows pour étudier leurs performances, trois grands domaines doivent avant tout retenir votre attention :  
  
-   Activité du disque  
  
-   Utilisation du processeur  
  
-   Utilisation de la mémoire  
  
 La surveillance d'un ordinateur sur lequel est exécuté le Moniteur système peut affecter légèrement les performances de l'ordinateur. Par conséquent, enregistrez les données générées par le Moniteur système sur un autre disque (ou ordinateur) afin de réduire l'impact résultant sur l'ordinateur surveillé, ou exécutez le Moniteur système depuis un ordinateur distant. Surveillez seulement les compteurs qui vous intéressent. Si vous surveillez un nombre trop élevé de compteurs, le processus de surveillance consomme davantage de ressources au détriment des performances de l'ordinateur surveillé.  
  
## Tâches du Moniteur système  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit quand utiliser le Moniteur système et présente la surcharge de performances lorsque vous utilisez le Moniteur système.|[Exécuter le Moniteur système](../../relational-databases/performance-monitor/run-system-monitor.md)|  
|Décrit comment surveiller les compteurs de disque afin de déterminer l'activité des disque et la quantité d'E/S générées par leurs composants SQL Server.|[Surveiller l'utilisation du disque](../../relational-databases/performance-monitor/monitor-disk-usage.md)|  
|Décrit comment surveiller une instance de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de déterminer si les taux d'utilisation de l'unité centrale restent dans des limites normales.|[Surveiller l'utilisation de l'UC](../../relational-databases/performance-monitor/monitor-cpu-usage.md)|  
|Décrit comment surveiller une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vous assurer que l'utilisation de la mémoire reste dans des limites normales.|[Surveiller l'utilisation de la mémoire](../../relational-databases/performance-monitor/monitor-memory-usage.md)|  
|Décrit comment créer une alerte qui est émise lorsque la valeur seuil d'un compteur du Moniteur système est atteinte.|[Créer une alerte de base de données SQL Server](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md)|  
|Décrit comment créer des graphiques, des alertes, des journaux et des rapports pour surveiller une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Créer des graphiques, des alertes, des journaux et des rapports](../../relational-databases/performance-monitor/create-charts-alerts-logs-and-reports.md)|  
|Répertorie les objets et compteurs utilisés pour analyser l'activité des ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Utiliser des objets SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md)|  
|Répertorie les objets et les compteurs que le Moniteur système utilise pour analyser l'activité de l'OLTP en mémoire.|[SQL Server XTP &#40;OLTP en mémoire&#41;, compteurs de performances](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)|  
  
  