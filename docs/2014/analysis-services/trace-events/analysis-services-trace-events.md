---
title: Événements de Trace Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, Analysis Services
- monitoring Analysis Services [SQL Server]
- performance [Analysis Services], SQL Server Profiler
- events [Analysis Services]
- event classes [Analysis Services], about event classes
- Profiler [SQL Server Profiler], Analysis Services
- event classes [Analysis Services]
ms.assetid: 6fb219cc-f37e-437a-a544-01cec0953571
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a4c4631e20227cb1d3aeba34337d7b36c8a84c62
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37163440"
---
# <a name="analysis-services-trace-events"></a>Événements de trace Analysis Services
  Vous pouvez suivre l'activité d'une instance Microsoft SQL Server Analysis Services (SSAS) en capturant, puis en analysant les événements de trace générés par l'instance.  Les événements de trace sont regroupés afin que vous puissiez plus facilement rechercher des événements de trace connexes.  Chaque événement de trace contient un jeu de données concernant l'événement ; toutes les parties de données ne sont pas correctes pour tous les événements.  
  
 Événements de trace peuvent être démarrés et capturés à l’aide **[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]**, consultez [utilisez SQL Server Profiler pour surveiller Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md), ou peut être démarré à partir d’une commande XMLA comme **SQL Server Événements étendus** et analysés ultérieurement, consultez [utilisez SQL Server Extended Events &#40;XEvents&#41; pour surveiller Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md).  
    
 Les tables suivantes décrivent chaque catégorie d'événement et les événements de cette catégorie.  
  
 Chaque table contient les colonnes suivantes :  
  
 ID d'événement  
 Valeur entière qui identifie le type d'événement. Cette valeur est utile lorsque vous lisez les traces converties en tables ou en fichiers XML pour filtrer le type d'événement.  
  
 Nom d'événement  
 Le nom donné à l'événement dans les applications clientes Analysis Services.  
  
 Description de l'événement  
 Brève description de l'événement.  
  
 **[Catégorie d’événement événements commande](command-events-event-category.md)**  
  
 Collection d'événements pour les commandes.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|15|Command Begin|Début de la commande.|  
|16|Command End|Fin de la commande.|  
  
 **[Catégorie d’événement événements de découverte](discover-events-event-category.md)**  
  
 Collection d'événements pour les demandes de découverte.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|36|Discover Begin|Début de la demande de découverte.|  
|38|Discover End|Fin de la demande de découverte.|  
  
 **[Catégorie d’événement état du serveur découverte](discover-server-state-event-category.md)**  
  
 Collection d'événements pour les découvertes de l'état du serveur.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|Début de la découverte de l'état du serveur.|  
|34|Server State Discover Data|Contenu de la réponse de la découverte de l'état du serveur.|  
|35|Server State Discover End|Fin de la découverte de l'état du serveur.|  
  
 **[Erreurs et avertissements catégorie d’événement](errors-and-warnings-event-category.md)**  
  
 Collection d'événements pour les erreurs du serveur.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|17|Error|Erreur serveur.|  
  
 **[Chargement de fichier et enregistrement de catégorie d’événement](file-load-and-save-event-category.md)**  
  
 Collection d'événements pour les rapports d'opérations de chargement et d'enregistrement de fichier.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|90|File Load Begin|Début du chargement du fichier.|  
|91|File Load End|Fin du chargement du fichier.|  
|92|File Save Begin|Début de l'enregistrement du fichier.|  
|93|File Save End|File Save End|  
|94|PageOut Begin|Début PageOut.|  
|95|PageOut End|PageOut End|  
|96|PageIn Begin|Début PageIn.|  
|97|PageIn End|PageIn End|  
  
 **[Catégorie d’événements de verrou](lock-events-category.md)**  
  
 Collection d'événements associés au verrou.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|Blocage de verrous de métadonnées.|  
|51|Lock Timeout|Expiration du verrou de métadonnées.|  
|52|Lock Acquired|Lock Acquired|  
|53|Lock Released|Lock Released|  
|54|Lock Waiting|Lock Waiting|  
  
 **[Catégorie d’événement notification Events](notification-events-event-category.md)**  
  
 Collection d'événements de notification.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|39|Notification|Événement de notification.|  
|40|Définis par l'utilisateur|Événement défini par l'utilisateur.|  
  
 **[Catégorie d’événement de rapports de progression](progress-reports-event-category.md)**  
  
 Collection d'événements pour le rapport de progression.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|Début du rapport de progression.|  
|6|Progress Report End|Fin du rapport de progression.|  
|7|Progress Report Current|Le rapport de progression est en cours.|  
|8|Progress Report Error|Erreur du rapport de progression.|  
  
 **[Catégorie d’événements de requêtes](queries-events-category.md)**  
  
 Collection d'événements pour les requêtes.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|Début de la requête.|  
|10|Query End|Fin de la requête.|  
  
 **[Catégorie d’événements de traitement de requête](query-processing-events-category.md)**  
  
 Collection d'événements clés lors du processus d'exécution de requête.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|70|Query Cube Begin|Interroger le cube Début.|  
|71|Query Cube End|Interroger le cube Fin.|  
|72|Calculate Non Empty Begin|Calculer non vide Début.|  
|73|Calculate Non Empty Current|Calculer non vide En cours.|  
|74|Calculate Non Empty End|Calculer non vide Fin.|  
|75|Serialize Results Begin|Sérialiser résultats Début.|  
|76|Serialize Results Current|Sérialiser résultats En cours.|  
|77|Serialize Results End|Sérialiser résultats Fin.|  
|78|Execute MDX Script Begin|Exécuter script MDX Début.|  
|79|Execute MDX Script Current|Exécuter script MDX En cours. Déconseillé.|  
|80|Execute MDX Script End|Exécuter script MDX Fin.|  
|81|Query Dimension|Dimension de requête.|  
|11|Query Subcube|Requête sur un sous-cube, pour une optimisation basée sur l'utilisation.|  
|12|Query Subcube Verbose|Requête sur un sous-cube avec des informations détaillées. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|60|Get Data From Aggregation|Répondre à la requête en obtenant des données à partir de l'agrégation. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|61|Get Data From Cache|Répondre à la requête en obtenant des données à partir de l'un des caches. Cet événement peut avoir un impact négatif sur la performance en cas d'activation.|  
|82|VertiPaq SE Query Begin|Requête VertiPaq SE|  
|83|VertiPaq SE Query End|Requête VertiPaq SE|  
|84|Utilisation des ressources|Lectures de rapports, écritures, utilisation de l'UC après la fin des commandes et des requêtes.|  
|85 %|VertiPaq SE Query Cache Match|Utilisation du cache de requêtes VertiPaq SE|  
|98|Direct Query Begin|Début de requête directe.|  
|99|Direct Query End|Fin de requête directe.|  
  
 **[Catégorie d’événement de sécurité d’Audit](security-audit-event-category.md)**  
  
 Collection de classes d'événements d'audit de base de données.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
| 1|Audit Login|Collecte tous les événements de connexion depuis le début de la trace, telle qu'une demande de connexion d'un client à un serveur qui exécute une instance de SQL Server.|  
|2|Audit Logout|Collecte tous les nouveaux événements de déconnexion depuis le début de la trace, telle que l'émission par un client d'une commande de déconnexion.|  
|4|Audit Server Starts And Stops|Enregistre l'arrêt du service, le début et la suspension des activités des services.|  
|18|Audit Object Permission Event|Enregistre les modifications d'autorisations sur les objets.|  
|19|Audit Admin Operations Event|Enregistre la sauvegarde/la restauration/la synchronisation/l'attachement/le détachement/le chargement d'image/l'enregistrement d'image.|  
  
 **[Catégorie d’événement événements session](session-events-event-category.md)**  
  
 Collection d'événements de session.  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|41|Connexion existante|Connexion utilisateur existante.|  
|42|Existing Session|Session existante.|  
|43|Session Initialize|Initialisation de session.|  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser SQL Server Profiler pour surveiller Analysis Service](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)
