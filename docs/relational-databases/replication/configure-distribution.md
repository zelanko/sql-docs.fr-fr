---
title: "Configurer la distribution | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "replication [SQL Server], distribution"
  - "configuration de la distribution [réplication SQL Server]"
  - "serveurs de distribution distants [réplication SQL Server]"
  - "réplication transactionnelle, configuration de la distribution"
  - "bases de données de distribution [réplication SQL Server], dimensionnement"
  - "distributeurs [réplication SQL Server], configuration"
  - "bases de données de distribution [réplication SQL Server], à propos des bases de données de distribution"
  - "bases de données de distribution [réplication SQL Server]"
  - "réplication [réplication SQL Server], configuration de la distribution"
ms.assetid: 94d52169-384e-4885-84eb-2304e967d9f7
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Configurer la distribution
  Le serveur de distribution contient la base de données de distribution, laquelle stocke les métadonnées, les données d'historique pour tous les types de réplication et les transactions pour la réplication transactionnelle. Pour définir la réplication, vous devez configurer un serveur de distribution. Chaque serveur de publication ne peut être affecté qu'à une seule instance de serveur de distribution mais plusieurs serveurs de publication peuvent partager un serveur de distribution. Le serveur de distribution utilise les ressources supplémentaires suivantes sur le serveur sur lequel il se trouve :  
  
-   Espace disque supplémentaire si les fichiers d'instantanés de la publication sont stockés sur le serveur de distribution, ce qui est généralement le cas  
  
-   espace disque supplémentaire pour stocker la base de données de distribution ;  
  
-   augmentation de l'utilisation du processeur par les agents de réplication pour les abonnements par envoi de données (push) exécutés sur le serveur de distribution.  
  
 Le serveur que vous sélectionnez comme serveur de distribution doit avoir un espace disque suffisant et un processeur suffisamment puissant pour prendre en charge la réplication et toutes les autres activités basées sur ce serveur. Lorsque vous configurez le serveur de distribution, spécifiez les éléments suivants :  
  
-   Dossier d'instantanés, utilisé par défaut par tous les serveurs de publication qui utilisent ce serveur de distribution. Assurez-vous que ce dossier est déjà partagé et possède les autorisations adéquates. Pour plus d’informations, consultez [sécuriser le dossier de capture instantanée](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
-   Nom et emplacement des fichiers de la base de données de distribution La base de données de distribution ne peut plus être renommée après sa création. Pour utiliser un autre nom de base de données, vous devez désactiver la distribution et la reconfigurer.  
  
-   Tous les serveurs de publication autorisés à utiliser le serveur de distribution. Si vous spécifiez des serveurs de publication autres que l'instance sur laquelle le serveur de distribution s'exécute, vous devez également indiquer un mot de passe pour les connexions des serveurs de publication au serveur de distribution distant.  
  
 Pour la réplication transactionnelle, après avoir configuré la distribution, il est recommandé d'effectuer les opérations suivantes :  
  
-   Dimensionnez correctement la base de données de distribution. Testez la réplication avec une charge normale pour votre système afin de déterminer l'espace nécessaire au stockage des commandes. Assurez-vous que la base de données est suffisamment volumineuse pour stocker les commandes sans avoir fréquemment recours à l'extension automatique. Pour plus d’informations sur la modification de la taille d’une base de données, consultez la page [ALTER DATABASE & #40 ; Transact-SQL & #41 ;](../../t-sql/statements/alter-database-transact-sql.md).  
  
-   Définir la **la synchronisation avec la sauvegarde** option sur la base de données de distribution. Pour plus d’informations, consultez [stratégies de sauvegarde et restauration de capture instantanée et la réplication transactionnelle](../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md) et [Activer les sauvegardes coordonnées pour la réplication transactionnelle & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../relational-databases/replication/administration/enable coordinated backups for transactional replication.md).  
  
## Serveurs de distribution locaux et distants  
 Si, par défaut, le serveur de distribution est le même que le serveur de publication (un serveur de distribution local), il peut également être différent (un serveur de distribution distant). En règle générale, vous opterez pour un serveur de distribution distant si vous souhaitez :  
  
-   transférer une partie du traitement vers un autre ordinateur pour que la réplication ait une incidence mineure sur le serveur de publication (par exemple, s'il s'agit d'un serveur OLTP) ;  
  
-   configurer un serveur de distribution centralisé pour plusieurs serveurs de publication.  
  
 Les serveurs de distribution distants sont plus utilisés pour la réplication transactionnelle que pour la réplication de fusion et ce, pour deux raisons :  
  
-   Le serveur de distribution joue un rôle plus important dans la réplication transactionnelle car toutes les transactions répliquées sont lues et écrites dans la base de données de distribution.  
  
-   Les topologies de réplication de fusion utilisent généralement des abonnements extraits de sorte que les Agents s'exécutent sur chaque Abonné, plutôt qu'ils s'exécutent tous sur le serveur de distribution.  Pour plus d’informations, consultez la page [s’abonner aux Publications](../../relational-databases/replication/subscribe-to-publications.md). Dans la plupart des cas, vous devez utiliser un serveur de distribution local pour la réplication de fusion.  
  
 Pour configurer la publication et la distribution, consultez [configurer la publication et Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
 Pour modifier les propriétés d’éditeur et de distributeur, voir [Afficher et de modifier le serveur de distribution et de propriétés de l’éditeur](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Protéger le serveur de distribution](../../relational-databases/replication/security/secure-the-distributor.md)  
  
  