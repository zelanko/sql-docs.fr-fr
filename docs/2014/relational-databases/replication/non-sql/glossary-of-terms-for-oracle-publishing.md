---
title: Glossaire des termes de la publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2bd38adbac216fbfa150c90ccd9a1ef60b9746ab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049139"
---
# <a name="glossary-of-terms-for-oracle-publishing"></a>Glossaire des termes de la publication Oracle
  Vous devez connaître et comprendre les termes Oracle suivants pour configurer et administrer la publication Oracle. Pour une liste complète des termes Oracle, consultez la documentation en ligne d'Oracle.  
  
 Table organisée en index (IOT)  
 Table dont les données sont physiquement triées sur le disque dans l’ordre de l’index ; elle est comparable à une table [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec un index cluster. Une IOT est répliquée vers un Abonné sous forme de table avec un index cluster.  
  
 Instance  
 Une base de données Oracle est associée à une instance. L'instance comprend les processus mémoire et d'arrière-plan qui prennent en charge la base de données. Une instance Oracle est toujours mappée vers une seule base de données, alors qu'une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut contenir plusieurs bases de données. Il y a des circonstances où une base de données Oracle peut avoir plusieurs instances.  
  
 Écouteur Oracle  
 Gère le trafic réseau entrant pour une instance de base de données Oracle. Quand vous configurez la connectivité réseau pour une base de données Oracle, vous spécifiez le protocole via lequel le trafic est envoyé et le port sur lequel l'écouteur écoute le trafic. L'écouteur est généralement configuré pour s'exécuter sur le même ordinateur que l'instance de base de données Oracle et peut être configuré pour servir une ou plusieurs instances.  
  
 ROWID  
 Un pointeur vers l'emplacement d'une ligne spécifique dans une base de données. L'extraction de lignes à l'aide du ROWID étant plus rapide que l'utilisation d'une analyse ou d'un index de table, la réplication utilise le ROWID temporairement pendant le traitement des modifications de la table publiée.  
  
 Séquence  
 Un objet de base de données qui est utilisé pour générer des nombres uniques. La réplication utilise des séquences pour classer les modifications apportées à des tables publiées.  
  
 SQL\*Plus  
 Une application utilisée pour accéder à et faire des requêtes sur des bases de données Oracle. Elle est comparable à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.  
  
 Synonyme  
 Un alias pour un objet. Le synonyme public spécial **MSSQLSERVERDISTRIBUTOR** est automatiquement créé quand un serveur de publication Oracle est configuré. Le synonyme référence la table **HREPL_Distributor** et fournit un pointeur logique vers le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui sert le serveur de publication.  
  
 Après qu'une base de données Oracle ait été publiée, les tentatives ultérieures de configuration de ce serveur de publication pour qu'il utilise un serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vont échouer, car ce synonyme public identifie le serveur de distribution particulier déjà configuré pour servir le serveur de publication.  
  
 Espace disque logique  
 Une unité de stockage de base de données qui est à peu près équivalente à un groupe de fichiers dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Nom du service TNS  
 TNS (Transparent Network Substrate) est une couche de communication utilisée par les bases de données Oracle. Le nom du service TNS est le nom sous lequel une instance de base de données Oracle est connue sur un réseau. Vous attribuez un nom du service TNS quand vous configurez la connectivité pour une base de données Oracle. La réplication utilise le nom du service TNS pour identifier le serveur de publication et pour établir des connexions.  
  
 Schéma utilisateur  
 Un schéma utilisateur peut être vu comme un utilisateur de base de données qui détient un ensemble donné d'objets de base de données. Le schéma utilisateur d'administration de réplication détient tous les objets créés par le processus de réplication de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la base de données Oracle, à l'exception du synonyme public **MSSQLSERVERDISTRIBUTOR** .  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](configure-an-oracle-publisher.md)   
 [Objets créés sur le serveur de publication Oracle](objects-created-on-the-oracle-publisher.md)   
 [Serveurs de publication non SQL Server](non-sql-server-publishers.md)   
 [Vue d’ensemble de la publication Oracle](oracle-publishing-overview.md)  
  
  
