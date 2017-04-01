---
title: "Pr&#233;sentation de l’architecture (SQL Server R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# Pr&#233;sentation de l’architecture (SQL Server R Services)
Cette section fournit une vue d’ensemble de l’architecture de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], y compris la sécurité, les nouveaux composants ajoutés dans le moteur de base de données SQL Server aux composants de prise en charge R et l’interopérabilité des scripts open source de R en cours d’exécution dans SQL Server.


## Objectifs


L’architecture de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] est conçu pour prendre en charge le langage open source de R. Les utilisateurs actuels de R doivent être en mesure de leur code R du port et de l’exécuter avec des modifications relativement mineures dans T-SQL.

Toutefois, SQL Server R Services fournit également des innovations qui offrent des performances accrues et une intégration plus étroite de base de données pour le langage R, pour activer le débit de données plus rapide et le traitement et pour réduire les obstacles pour le développement de l’entreprise de solutions de R. Il s’agit notamment des composants propriétaires développés par Microsoft et open source.


Les principaux objectifs de l’intégration avec SQL Server sont pour fournir des performances et évolutivité pour R, tandis que la gestion des données en toute sécurité. Dans cette optique, SQL Server R Services fournit une infrastructure à plusieurs PROCEDE qui prend en charge l’authentification intégrée Windows et mot de passe des connexions SQL. 

+ [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] Fournit une distribution base r, ainsi que les packages ScaleR et la possibilité d’exécuter des tâches de R en parallèle.
+ De nouveaux composants de SQL Server fournissent une infrastructure sécurisée et hautes performances pour l’exécution de scripts externes.
+ Tâches de R s’exécutent en dehors du processus SQL Server, à la sécurité et la facilité de gestion accrue.
+ [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] gère la sécurité de tous les processus de R. 

Pour vous aider à optimiser le code R existant et de tirer parti de ces améliorations, les rubriques de cette section décrivent en détail l’architecture de nouveau. En comprenant comment analyse et traitement des données est gérée par [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], vous pouvez faire les choix appropriés sur la réception de données, comment effectuer plus efficacement l’ingénierie de caractéristiques et comment utiliser les résultats.
 

## Dans cette section
+ [Interopérabilité de R](../../advanced-analytics/r-services/r-interoperability-in-sql-server-r-services.md)
+ [De nouveaux composants de SQL Server pour les Services de R](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md)
+ [Vue d'ensemble de la sécurité](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md)

## Voir aussi
[R didacticiels des Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)
