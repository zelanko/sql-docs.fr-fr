---
title: Abonnés de réplication et groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover subscribers with AlwaysOn
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 0995f269-0580-43ed-b8bf-02b9ad2d7ee6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8968754a797c3f3b1a7e66886f7874c9bc13c5d3
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52390663"
---
# <a name="replication-subscribers-and-alwayson-availability-groups-sql-server"></a>Abonnés de réplication et groupes de disponibilité AlwaysOn (SQL Server)
  Lorsqu'un groupe de disponibilité AlwaysOn contenant une base de données est un abonné de réplication et bascule, l'abonnement de réplication peut échouer. Pour les abonnés transactionnels, l'agent de distribution continue la réplication automatiquement si l'abonnement utilise le nom de l'écouteur de groupe de disponibilité de l'abonné. Pour les abonnés de fusion, un administrateur de réplication doit reconfigurer l'abonné manuellement, en recréant l'abonnement.  
  
## <a name="what-is-supported"></a>Ce qui est pris en charge  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le basculement automatique du serveur de publication, le basculement automatique des abonnés transactionnels et le basculement manuel des abonnés de fusion. Le basculement d'un serveur de distribution dans une base de données de disponibilité n'est pas pris en charge. AlwaysOn ne peut pas être combiné avec Websync et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Compact.  
  
 **Basculement d'un abonnement de fusion par extraction de données (pull)**  
  
 Un abonnement par extraction échoue lors d'un basculement de groupe de disponibilité, car l'agent d'extraction de données ne trouve pas les travaux stockés dans la base de données **msdb** de l'instance de serveur qui héberge le réplica principal, qui n'est pas disponible parce que l'instance de serveur a échoué.  
  
 **Basculement d'un abonnement de fusion par émission de données (push)**  
  
 Un abonnement par émission de données échoue lors du basculement d'un groupe de disponibilité, car l'agent de transmission de type push ne peut plus se connecter à la base de données d'abonnement d'origine sur l'abonné d'origine.  
  
## <a name="how-to-create-transactional-subscription-in-an-alwayson-environment"></a>Procédure de création d'un abonnement transactionnel dans un environnement AlwaysOn  
 Pour la réplication transactionnelle, utilisez la procédure suivante pour configurer et basculer un groupe de disponibilité d'abonné :  
  
1.  Avant de créer l'abonnement, ajoutez la base de données de l'abonné au groupe de disponibilité AlwaysOn approprié.  
  
2.  Ajoutez l'écouteur de groupe de disponibilité de l'abonné en tant que serveur lié à tous les nœuds du groupe de disponibilité. Cette étape garantit que tous les partenaires de basculement potentiels ont connaissance de l'écouteur et peuvent s'y connecter.  
  
3.  À l'aide du script de la section **Création d'un abonnement de réplication transactionnelle par émission de données** ci-dessous, créez l'abonnement avec le nom de l'écouteur du groupe de disponibilité de l'abonné. Après un basculement, le nom de l'écouteur demeure valide, alors que le nom du serveur réel de l'abonné dépend du nœud réel qui est devenu le nouveau nœud principal.  
  
    > [!NOTE]  
    >  L'abonnement doit être créé à l'aide d'un script [!INCLUDE[tsql](../../../includes/tsql-md.md)] ; il ne peut pas être créé à l'aide de [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)].  
  
4.  Pour la création d'un abonnement par extraction de données :  
  
    1.  Dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], sur le nœud principal de l'abonné, ouvrez l'arborescence de l'Agent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    2.  Identifiez le travail de l' **Agent de distribution par extraction de données** et modifiez le travail.  
  
    3.  À l'étape de travail **Exécution de l'Agent** , vérifiez les paramètres `-Publisher` et `-Distributor` . Assurez-vous que ces paramètres contiennent les noms corrects du serveur direct et de l'instance du serveur de publication et du serveur de distribution.  
  
    4.  Remplacez le paramètre `-Subscriber` par le nom de l'écouteur de groupe de disponibilité de l'abonné.  
  
 Si vous créez votre abonnement en suivant ces étapes, vous n’aurez aucune action à accomplir après un basculement.  
  
## <a name="creating-a-transactional-replication-push-subscription"></a>Création d'un abonnement de réplication transactionnelle par émission de données  
  
```  
-- commands to execute at the publisher, in the publisher database:  
use [<publisher database name>]  
EXEC sp_addsubscription @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @destination_db = N'<subscriber database name>',   
       @subscription_type = N'Push',   
       @sync_type = N'automatic', @article = N'all', @update_mode = N'read only', @subscriber_type = 0;  
GO  
  
EXEC sp_addpushsubscription_agent @publication = N'<publication name>',   
       @subscriber = N'<availability group listener name>',   
       @subscriber_db = N'<subscriber database name>',   
       @job_login = null, @job_password = null, @subscriber_security_mode = 1;  
GO  
```  
  
## <a name="to-resume-the-merge-agents-after-the-availability-group-of-the-subscriber-fails-over"></a>Pour récupérer les agents de fusion après le basculement du groupe de disponibilité de l'abonné  
 Pour une réplication de fusion, un administrateur de réplication doit reconfigurer l'abonné manuellement en procédant comme suit :  
  
1.  Exécutez `sp_subscription_cleanup` pour supprimer l'ancien abonnement de l'abonné. Effectuez cette action sur le nouveau réplica principal (qui était auparavant le réplica secondaire).  
  
2.  Recréez l'abonnement en en créant un nouveau, en commençant par un nouvel instantané.  
  
> [!NOTE]  
>  Le processus actuel n'est pas pratique pour les abonnés de réplication de fusion ; toutefois, le scénario principal de la réplication de fusion implique des utilisateurs déconnectés (bureaux, ordinateurs portables, appareils combinés téléphoniques) qui n'utilisent pas les groupes de disponibilité AlwaysOn sur l'abonné.  
  
  
