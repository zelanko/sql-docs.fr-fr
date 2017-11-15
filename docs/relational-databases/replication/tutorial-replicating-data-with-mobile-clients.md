---
title: "Didacticiel : Réplication de données avec des clients mobiles | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 642f2fa95b2ff69f11a10f7bbaae6e184928c7b9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>Didacticiel : Réplication de données avec des clients mobiles
La réplication constitue une bonne solution au problème de transfert des données entre un serveur central et des clients mobiles qui ne sont connectés que de façon occasionnelle. À l'aide des Assistants de réplication, vous pouvez aisément configurer et administrer une topologie de réplication. Ce didacticiel vous explique comment configurer une topologie de réplication pour des clients mobiles.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
Dans ce didacticiel, vous allez utiliser la réplication de fusion pour publier des données à partir d'une base de données centrale vers un ou plusieurs utilisateurs mobiles afin que chaque utilisateur obtienne un sous-ensemble des données filtré de façon unique. La première leçon montre comment utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une publication. Les leçons suivantes expliquent comment créer et synchroniser un abonnement.  
  
## <a name="requirements"></a>Spécifications  
Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations essentielles de base de données, mais dont l'expérience en matière de réplication est limitée. Avant de commencer ce didacticiel, vous devez effectuer le [Didacticiel : Préparation du serveur à la réplication](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   Sur le serveur de publication (source)  
  
    -   Toute édition de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sauf Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) ou [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Ces éditions ne peuvent pas constituer un serveur de publication de réplication.  
  
    -   Exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   Toute édition de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], sauf [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] n'est pas pris en charge par la publication créée dans ce didacticiel.  
  
    > [!NOTE]  
    > La réplication n’est pas installée par défaut dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
> [!NOTE]  
> Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l'Abonné à l'aide d'un identifiant de connexion membre du rôle serveur fixe sysadmin.  
  
**Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
  
-   [Leçon 1 : publication de données à l'aide de la réplication de fusion](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Leçon 2 : Création d'un abonnement à la publication de fusion](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
[Démarrer le didacticiel](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
## <a name="see-also"></a>Voir aussi  
[Concepts de programmation en matière de réplication](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  
