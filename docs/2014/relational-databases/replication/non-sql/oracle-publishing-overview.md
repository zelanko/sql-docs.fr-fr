---
title: Présentation de la publication Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 595547640aa5fb2647208cf092448d691ea92027
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152096"
---
# <a name="oracle-publishing-overview"></a>Présentation de la publication Oracle
  À partir de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], vous pouvez inclure des serveurs de publication Oracle dans votre topologie de réplication, en partant d'Oracle version 9i. Les serveurs de publication peuvent être déployés sur tout matériel et système d'exploitation prenant en charge Oracle. La fonctionnalité s'appuie sur les solides fondations de la réplication d'instantané et de la réplication transactionnelle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en fournissant des performances et une exploitabilité similaires.  
  
 La publication Oracle est déconseillée. La réplication hétérogène sur les abonnés non SQL Server est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a>Réplication d'instantané pour Oracle  
 Les publications d'instantanés Oracle sont implémentées de manière similaire à celle des publications d'instantanés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Lorsque l'Agent d'instantané s'exécute pour une publication Oracle, il se connecte au serveur de publication Oracle et traite chaque table de la publication. Lorsqu'il traite la table, l'agent en extrait les lignes et crée des scripts de schéma qui sont ensuite stockés sur le partage des instantanés de la publication. Comme l'ensemble de données complet est créé à chaque exécution de l'Agent d'instantané, les déclencheurs de suivi des modifications ne sont pas ajoutés aux tables Oracle comme dans le cas de la réplication transactionnelle. La réplication d'instantané est un moyen pratique de migrer des données avec un impact minimal sur le système de publication.  
  
## <a name="transactional-replication-for-oracle"></a>Réplication transactionnelle pour Oracle  
 Les publications transactionnelles Oracle sont implémentées selon l'architecture de publication transactionnelle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; cependant, les modifications sont suivies à l'aide d'une combinaison de déclencheurs de base de données sur la base de données Oracle et de l'Agent de lecture du journal. Les Abonnés à une publication transactionnelle Oracle sont automatiquement initialisés à l'aide de la réplication d'instantané ; les modifications ultérieures sont suivies et remises aux Abonnés par l'Agent de lecture de journal.  
  
 Lorsqu'une publication Oracle est créée, des déclencheurs et des tables de suivi sont créés pour chaque table publiée dans la base de données Oracle. Lorsque des modifications de données sont apportées aux tables publiées, les déclencheurs de base de données sont activés sur les tables et insèrent des informations dans les tables de suivi de réplication pour chaque ligne modifiée. L'Agent de lecture du journal sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] déplace alors les informations de modification des données à partir des tables de suivi vers la base de données de distribution sur le serveur de distribution. Enfin, comme dans la réplication transactionnelle standard, l'Agent de distribution déplace les modifications du serveur de distribution vers les Abonnés.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de publication Oracle](configure-an-oracle-publisher.md)   
 [Glossaire des termes de la publication Oracle](glossary-of-terms-for-oracle-publishing.md)   
 [Réplication de base de données hétérogène](heterogeneous-database-replication.md)  
  
  