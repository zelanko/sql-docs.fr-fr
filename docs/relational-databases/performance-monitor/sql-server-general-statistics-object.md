---
title: SQL Server, objet General Statistics | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:General Statistics
- General Statistics object
ms.assetid: c738e549-d7e7-4211-9ec3-064ac140af7c
caps.latest.revision: "26"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cd44f59d6fe693dbf8695830240ba1a16453d123
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-general-statistics-object"></a>SQL Server, objet General Statistics
  L’objet **SQLServer:General Statistics** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs pour surveiller l’activité générale du serveur, comme le nombre de connexions actives et le nombre d’utilisateurs se connectant et se déconnectant à la seconde d’ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cela s'avère utile lorsque vous travaillez sur des systèmes OLTP importants sur lesquels de nombreux clients se connectent et se déconnectent d'ordinateurs exécutant une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Statistiques générales** .  
  
|Compteurs statistiques générales de SQL Server|Description|  
|--------------------------------------------|-----------------|  
|**Tables temporaires actives**|Nombre de tables temporaires/variables de table en cours d'utilisation.|  
|**Réinitialisation de la connexion/s**|Nombre total de connexions établies à partir du groupement de connexions.|  
|**Suppression différée des notifications d'événements**|Nombre de notifications d'événements en attente de suppression par un thread système|  
|**Requêtes HTTP authentifiées**|Nombre de requêtes HTTP authentifiées démarrées par seconde.|  
|**Connexions logiques**|Nombre de connexions logiques au système.<br /><br /> La finalité principale des connexions logiques est de traiter les requêtes MARS (multiple active result sets). Dans le cas des requêtes MARS, chaque fois qu'une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il peut y avoir plusieurs connexions logiques associées à une connexion physique.<br /><br /> Lorsque vous n'utilisez pas MARS, le ratio entre les connexions physiques et logiques et de 1:1. Chaque fois qu'une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les connexions logiques augmentent donc de 1.|  
|**Connexions/s**|Nombre total de connexions démarrées par seconde. N'inclut pas les connexions regroupées.|  
|**Déconnexions/s**|Nombre total de déconnexions effectuées par seconde.|  
|**Blocages MARS**|Nombre de blocages MARS détectés.|  
|**Taux de rendement non atomique**|Nombre de rendements non atomiques par seconde.|  
|**Processus bloqués**|Nombre de processus actuellement bloqués.|  
|**Requêtes SOAP vides**|Nombre de requêtes SOAP vides démarrées par seconde.|  
|**Appels de méthode SOAP**|Nombre d'appels de méthode SOAP démarrés par seconde.|  
|**Requêtes d'ouverture de session SOAP**|Nombre de requêtes d'ouverture de session SOAP démarrées par seconde.|  
|**Requêtes de fermeture de session SOAP**|Nombre de requêtes de fermeture de session SOAP démarrées par seconde.|  
|**Requêtes SQL SOAP**|Nombre de requêtes SQL SOAP démarrées par seconde.|  
|**Requêtes WSDL SOAP**|Nombre de requêtes WSDL SOAP démarrées par seconde.|  
|**Attentes de verrouillage du fournisseur d’E/S de la trace SQL**|Nombre d’attentes pour le verrouillage du fournisseur d’E/S de fichier par seconde.| 
|**Taux de création de tables temporaires**|Nombre de tables temporaires/variables de table créées par seconde.|  
|**Tables temporaires en attente de destruction**|Nombre de tables temporaires/variables de table qui attendent d'être détruites par le thread système de nettoyage|  
|**ID d’unité de récupération tempdb**|Nombre d’ID d’unité de récupération Tempdb en double générés.|
|**Id d’ensemble de lignes tempdb**|Nombre d’ID d’ensemble de lignes tempdb en double générés.| 
|**File d'attente des notifications d'événements de trace**|Nombre d'instances de notifications d'événements de trace qui attendent dans la file d'attente interne d'être envoyées via Service Broker|  
|**Transactions**|Nombre d'inscriptions de transactions (locales, du DTC et lie´es).|  
|**Connexions utilisateur**|Compte le nombre d'utilisateurs actuellement connectés à SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
