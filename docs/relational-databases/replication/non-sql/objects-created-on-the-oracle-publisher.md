---
title: "Objets créés sur le serveur de publication Oracle | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle publishing [SQL Server replication], objects created
ms.assetid: c58a124b-4da7-46e2-9292-af8ce9e6664b
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 97a45c8f524f81d01dceda7a616932b18e799d82
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="objects-created-on-the-oracle-publisher"></a>Objets créés sur le serveur de publication Oracle
  La réplication[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe des objets de base de données sur le serveur de publication Oracle pour permettre le suivi et la transmission des modifications ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'installe aucun fichier binaire sur le serveur de publication Oracle). Le tableau suivant donne la liste des objets qui sont créés sur le serveur de publication Oracle quand il est identifié en tant que serveur de publication sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Les descriptions des objets sont données seulement à titre d'information. Il est recommandé de ne pas modifier ces objets.  
  
|Nom de l'objet|Type d'objet|Description|  
|-----------------|-----------------|-----------------|  
|HREPL_ArticleNlog_V|Table|Table de suivi des modifications utilisée pour stocker les informations quand des modifications sont apportées à la table publiée. Une table de suivi des modifications est créée pour chaque table publiée.|  
|HREPL_Changes|Table|Table utilisée en interne par le travail Xactset pour déterminer le nombre de modifications en attente d'affectation à un ensemble de transactions. Pour plus d’informations sur ce travail, consultez [Réglage des performances pour les serveurs de publication Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).|  
|HREPL_Distributor|Table|Table d'état du serveur de distribution utilisée pour gérer les informations sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] associé au serveur de publication Oracle.|  
|HREPL_Event|Table|Table d'événements utilisée pour la synchronisation entre les instantanés et les demandes de comptage de lignes.|  
|HREPL_Mutex|Table|Table utilisée pour garantir que la procédure du package Oracle PopulatePollTable n'est pas exécutée simultanément par l'Agent de lecture du journal et le travail de la base de données.|  
|HREPL_Poll|Table|Table utilisée pour identifier les entrées de table de journal associées avec des ensembles de modifications apportées aux tables publiées.|  
|HREPL_PublishedTables|Table|Table contenant une entrée pour chaque article d'une publication transactionnelle.|  
|HREPL_Publisher|Table|Table d'état du serveur de publication utilisée pour la gestion d'informations spécifiques au serveur de publication.|  
|HREPL_SchemaFilter|Table|Table contenant des schémas qui ne sont pas affichés lors de la publication via l'Assistant Nouvelle Publication.|  
|HREPL_XactsetCreateTimes|Table|Table identifiant la date/heure de création associée avec chaque ensemble de transactions.|  
|HREPL_XactsetJob|Table|Table avec les valeurs des paramètres en cours pour le travail Xactset.|  
|HREPL_Pollid|Séquence|Séquence utilisée pour générer des ID d'interrogation.|  
|HREPL_Seq|Séquence|Séquence utilisée pour trier des commandes de modification.|  
|HREPL_Stmt|Séquence|Séquence utilisée pour générer des ID d'instruction.|  
|HREPL|Package et corps du package|Package de code de prise en charge du serveur de publication, qui est créé sur le serveur de publication.|  
|MSSQLSERVERDISTRIBUTOR|Synonyme public|Synonyme public pour la table HREPL_Distributor. Si vous configurez un serveur de distribution à utiliser avec un serveur de publication Oracle, et que ce synonyme existe déjà dans la base de données, il est supprimé et recréé.<br /><br /> La suppression du synonyme public et de l'utilisateur de réplication Oracle avec l'option CASCADE entraîne la suppression de tous les objets de réplication sur le serveur de publication Oracle.|  
|HREPL_Len_I_J_K|Fonction|Fonction définie en dehors du code du package de publication Oracle, utilisée pour rechercher la longueur d'une colonne de type LONG (utilisée lors de la génération de commandes paramétrables pour les tables avec des colonnes LONG publiées). Une fonction est créée pour chaque table publiée avec une colonne LONG.|  
|HREPL_DropPublisher|Procédure|Procédure définie en dehors du code du package de publication Oracle, utilisée pour supprimer le serveur de publication Oracle.|  
|HREPL_ExecuteCommand|Procédure|Procédure définie en dehors du code du package de publication Oracle, utilisée pour exécuter une commande sur le serveur de publication.|  
|HREPL_ArticleN_Trigger_Row|Déclencheur|Déclencheur généré pour chaque table publiée, utilisé pour le suivi des modifications de lignes.|  
|HREPL_ArticleN_Trigger_Stmt|Déclencheur|Déclencheur généré pour chaque table publiée, utilisé pour le suivi des modifications au niveau des instructions.|  
|HREPL_Article_I_J|Affichage|Vue créée pour chaque table publiée, utilisée pour des requêtes sur la table publiée.|  
|HREPL_Log_I_J_K|Affichage|Vue créée pour chaque table publiée, utilisée pour des requêtes sur la table de suivi des modifications.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Glossaire des termes de la publication Oracle](../../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Oracle Publishing Overview](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
