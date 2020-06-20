---
title: 'Didacticiel : Réplication de données avec des clients mobiles | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b8c9e2d0f20a91bb11c0d5e08aff00c27785818e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047593"
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>Didacticiel : Réplication de données avec des clients mobiles
  La réplication constitue une bonne solution au problème de transfert des données entre un serveur central et des clients mobiles qui ne sont connectés que de façon occasionnelle. À l'aide des Assistants de réplication, vous pouvez aisément configurer et administrer une topologie de réplication. Ce didacticiel vous explique comment configurer une topologie de réplication pour des clients mobiles.  
  
## <a name="what-you-will-learn"></a>Contenu du didacticiel  
 Dans ce didacticiel, vous allez utiliser la réplication de fusion pour publier des données à partir d'une base de données centrale vers un ou plusieurs utilisateurs mobiles afin que chaque utilisateur obtienne un sous-ensemble des données filtré de façon unique. La première leçon montre comment utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une publication. Les leçons suivantes expliquent comment créer et synchroniser un abonnement.  
  
## <a name="requirements"></a>Spécifications  
 Ce didacticiel est destiné aux utilisateurs qui sont familiers des opérations essentielles de base de données, mais dont l'expérience en matière de réplication est limitée. Avant de commencer ce didacticiel, vous devez effectuer le [Didacticiel : Préparation du serveur à la réplication](tutorial-preparing-the-server-for-replication.md).  
  
 Pour utiliser ce didacticiel, les composants suivants doivent être installés sur votre système :  
  
-   Sur le serveur de publication (source)  
  
    -   Toute édition de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]sauf Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) ou [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Ces éditions ne peuvent pas constituer un serveur de publication de réplication.  
  
    -   Exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Pour des raisons de sécurité, les exemples de bases de données ne sont pas installés par défaut.  
  
-   Serveur de l'Abonné (destination) :  
  
    -   Toute édition de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], sauf [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] n'est pas pris en charge par la publication créée dans ce didacticiel.  
  
    > [!NOTE]  
    >  La réplication n’est pas installée par défaut dans [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], vous devez vous connecter au serveur de publication et à l'Abonné à l'aide d'un identifiant de connexion membre du rôle serveur fixe sysadmin.  
  
 **Durée estimée pour effectuer ce didacticiel : 30 minutes.**  
  
## <a name="lessons-in-this-tutorial"></a>Leçons du didacticiel  
  
-   [Leçon 1 : Publication de données à l’aide de la réplication de fusion](lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Leçon 2 : Création d’un abonnement à la publication de fusion](lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
 [Démarrer le didacticiel](merge/merge-replication.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de programmation en matière de réplication](concepts/replication-programming-concepts.md)  
  
  
