---
title: 'Tutoriel : Réplication en continu de données entre serveurs connectés | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 32b97d456c42eab89511d8f5a9d1924914ea81ca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62655390"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>Tutoriel : Réplication de données entre serveurs connectés en permanence
  La réplication constitue une bonne solution au problème de transfert de données entre serveurs connectés en permanence. À l'aide des Assistants de réplication, vous pouvez aisément configurer et administrer une topologie de réplication. Ce didacticiel vous explique comment configurer une topologie de réplication dans le cas de serveurs connectés en permanence.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Ce didacticiel vous explique comment publier des données d'une base de données sur une autre à l'aide de la réplication transactionnelle. La première leçon montre comment utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une publication. Les leçons suivantes expliquent comment créer et valider un abonnement et comment mesurer la latence.  
  
## <a name="requirements"></a>Configuration requise  
 Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations élémentaires de base de données, mais dont l'expérience en matière de réplication est limitée. Pour suivre ce didacticiel, vous devez avoir terminé le didacticiel précédent, [Préparation du serveur pour la réplication](tutorial-preparing-the-server-for-replication.md).  
  
 Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   Sur le serveur de publication (source)  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sauf Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) ou [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Ces éditions ne peuvent pas constituer des serveurs de publication de réplication.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] : exemple de base de données. Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   Toute édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sauf [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] ne peut pas être un abonné dans une réplication transactionnelle.  
  
    > [!NOTE]  
    >  La réplication n'est pas installée par défaut dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l’Abonné à l’aide d’un identifiant de connexion membre du rôle serveur fixe **sysadmin** .  
  
 **Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
  
-   [Leçon 1 : Publication de données à l’aide de la réplication transactionnelle](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [Leçon 2 : Création d’un abonnement à la Publication transactionnelle](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [Leçon 3 : Validation de l’abonnement et mesure de la latence](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [Démarrer le didacticiel](transactional/transactional-replication.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation en matière de réplication](concepts/replication-programming-concepts.md)  
  
  
