---
title: Informations sur le serveur Web | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b23f0c9439c7d1cc0ee1f4e6d7d9237fea40e6b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="web-server-information"></a>Informations sur le serveur Web
  Les informations sur le serveur Web sont nécessaires pour pouvoir utiliser l'option de synchronisation Web pour la réplication de fusion. Pour obtenir des informations sur la configuration de la synchronisation Web, consultez [Configurer la synchronisation Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="options"></a>Options  
 **Adresse du serveur Web**  
 Si vous avez spécifié une adresse de serveur web dans la page **Capture instantanée FTP et Internet** de la boîte de dialogue **Propriétés de publication**, elle figure dans la zone de texte comme adresse par défaut. Acceptez cette adresse ou entrez une adresse de serveur Web qualifiée complète pour le serveur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) qui synchronise cet abonnement.  
  
 **Procédure de connexion de chaque Abonné au serveur Web**  
 Spécifiez le type d'authentification à utiliser pour la connexion au serveur Web. Il est recommandé d'utiliser l'authentification de base pour les connexions au serveur IIS avec SSL (Secure Sockets Layer). Si vous sélectionnez I'authentification de base, entrez la connexion et le mot de passe à utiliser pour se connecter de l'Abonné au serveur IIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement par extraction](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Afficher et modifier les propriétés d’un abonnement par extraction](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
