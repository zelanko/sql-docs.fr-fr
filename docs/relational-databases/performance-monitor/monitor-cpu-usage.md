---
title: "Surveiller l&#39;utilisation de l&#39;UC | Microsoft Docs"
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
  - "surveillance des performances [SQL Server], utilisation de l’UC"
  - "paramétrage des bases de données [SQL Server], utilisation de l’UC"
  - "processeurs [SQL Server], surveillance de l’utilisation"
  - "performances des base de données [SQL Server], utilisation de l’UC"
  - "surveillance de l'utilisation de l'UC [SQL Server]"
  - "performances du serveur [SQL Server], utilisation de l’UC"
  - "surveillance des bases de données [SQL Server], utilisation de l’UC"
  - "surveillance [SQL Server], utilisation de l’UC"
  - "processeurs [SQL Server]"
  - "UC [SQL Server], surveillance"
  - "surveillance des performances du serveur [SQL Server], utilisation de l’UC"
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Surveiller l&#39;utilisation de l&#39;UC
  Surveillez régulièrement une instance Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin de déterminer si les taux d'utilisation de l'unité centrale restent dans des limites normales. Un taux d'utilisation de l'unité centrale régulièrement élevé peut mettre en évidence le besoin d'une mise à niveau de celle-ci ou d'un ajout de plusieurs processeurs. Sinon, si une application sollicite constamment l'unité centrale, cela implique un paramétrage incorrect ou une conception médiocre de cette dernière. En optimisant l'application vous réduirez l'utilisation de l'unité centrale.  
  
 Une bonne manière de déterminer ce besoin consiste à utiliser le compteur **Processeur : % Temps processeur** du Moniteur système. Ce compteur surveille le temps nécessaire à l'unité centrale pour traiter un thread inactif. Une valeur régulièrement comprise entre 80 et 90 % peut indiquer un besoin de mise à niveau de l'unité centrale ou d'ajout de processeurs. Dans le cas de systèmes multiprocesseurs, surveillez une instance séparée de ce compteur pour chaque processeur. Cette valeur représente la somme du temps processeur pour un processeur spécifique. Pour déterminer la moyenne pour tous les processeurs, utilisez plutôt le compteur **Système : % temps total processeur** .  
  
 Éventuellement, vous pouvez également surveiller les compteurs suivants pour contrôler l'utilisation du processeur :  
  
-   **Processeur : % temps privilégié**  
  
     Indique en pourcentage le temps consacré par le processeur aux commandes du noyau Microsoft Windows, telles que l'exécution des requêtes d'E/S [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si ce compteur est constamment élevé lorsque les compteurs **Disque physique** le sont également, envisagez un sous-système de disque plus rapide ou efficace.  
  
    > [!NOTE]  
    >  Différents contrôleurs de disques et pilotes utilisent des durées variables de temps de traitement des noyaux. Des contrôleurs et pilotes efficaces sollicitent moins de temps de traitement, accordant ainsi davantage de temps de traitement aux applications utilisateur, ce qui permet d'accroître le débit global.  
  
-   **Processeur : % temps utilisateur**  
  
     Indique en pourcentage le temps consacré par le processeur aux processus utilisateur tels que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Système : Longueur de la file d'attente du processeur**  
  
     Indique le nombre de threads en attente de temps processeur. Un encombrement du processeur survient quand les threads d'un processus demandent plus de cycles processeur qu'il n'y en a de disponibles. Si de nombreux processus essaient d'utiliser le temps du processeur, vous devez peut-être installer un processeur plus rapide. Si vous avez un système multiprocesseur, vous pouvez ajouter un processeur.  
  
 Quand vous examinez l'utilisation du processeur, tenez compte du type de travail que l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue beaucoup de calculs (ex. requêtes impliquant des agrégats ou requêtes liées à la mémoire et qui ne nécessitent aucune E/S sur disque), il est alors possible d'utiliser 100 % du temps processeur. Si cela nuit aux performances d'autres applications, essayez de modifier la charge de travail. Par exemple, dédiez l'ordinateur à l'exécution de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Des taux d'utilisation proches de 100 %, quand de nombreuses requêtes client sont en cours de traitement, peuvent indiquer que les processus s'accumulent, en attente de temps processeur, et provoquent un goulet d'étranglement. Vous pouvez résoudre ce problème en ajoutant des processeurs plus puissants.  
  
  