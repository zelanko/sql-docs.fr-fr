---
title: Objets créés sur le serveur de publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], objects created
ms.assetid: c58a124b-4da7-46e2-9292-af8ce9e6664b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5331597181f8d04ae74dd5d3bc4b8781bd4eb04e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124819"
---
# <a name="objects-created-on-the-oracle-publisher"></a>Objets créés sur le serveur de publication Oracle
  La réplication[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installe des objets de base de données sur le serveur de publication Oracle pour permettre le suivi et la transmission des modifications ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] n'installe aucun fichier binaire sur le serveur de publication Oracle). Le tableau suivant donne la liste des objets qui sont créés sur le serveur de publication Oracle quand il est identifié en tant que serveur de publication sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Les descriptions des objets sont données seulement à titre d'information. Il est recommandé de ne pas modifier ces objets.  
  
|Nom de l’objet|Type d'objet|Description|  
|-----------------|-----------------|-----------------|  
|HREPL_ArticleNlog_V|Table de charge de travail|Table de suivi des modifications utilisée pour stocker les informations quand des modifications sont apportées à la table publiée. Une table de suivi des modifications est créée pour chaque table publiée.|  
|HREPL_Changes|Table de charge de travail|Table utilisée en interne par le travail Xactset pour déterminer le nombre de modifications en attente d'affectation à un ensemble de transactions. Pour plus d’informations sur ce travail, consultez [Réglage des performances pour les serveurs de publication Oracle](performance-tuning-for-oracle-publishers.md).|  
|HREPL_Distributor|Table de charge de travail|Table d'état du serveur de distribution utilisée pour gérer les informations sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] associé au serveur de publication Oracle.|  
|HREPL_Event|Table de charge de travail|Table d'événements utilisée pour la synchronisation entre les instantanés et les demandes de comptage de lignes.|  
|HREPL_Mutex|Table de charge de travail|Table utilisée pour garantir que la procédure du package Oracle PopulatePollTable n'est pas exécutée simultanément par l'Agent de lecture du journal et le travail de la base de données.|  
|HREPL_Poll|Table de charge de travail|Table utilisée pour identifier les entrées de table de journal associées avec des ensembles de modifications apportées aux tables publiées.|  
|HREPL_PublishedTables|Table de charge de travail|Table contenant une entrée pour chaque article d'une publication transactionnelle.|  
|HREPL_Publisher|Table de charge de travail|Table d'état du serveur de publication utilisée pour la gestion d'informations spécifiques au serveur de publication.|  
|HREPL_SchemaFilter|Table de charge de travail|Table contenant des schémas qui ne sont pas affichés lors de la publication via l'Assistant Nouvelle Publication.|  
|HREPL_XactsetCreateTimes|Table de charge de travail|Table identifiant la date/heure de création associée avec chaque ensemble de transactions.|  
|HREPL_XactsetJob|Table de charge de travail|Table avec les valeurs des paramètres en cours pour le travail Xactset.|  
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
 [Configurer un serveur de publication Oracle](configure-an-oracle-publisher.md)   
 [Glossaire des termes de la publication Oracle](glossary-of-terms-for-oracle-publishing.md)   
 [Vue d’ensemble de la publication Oracle](oracle-publishing-overview.md)  
  
  
