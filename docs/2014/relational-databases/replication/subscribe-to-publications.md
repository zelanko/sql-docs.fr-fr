---
title: S’abonner à des publications | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.conc.subtopubs.f1
helpviewer_keywords:
- subscriptions [SQL Server replication], about subscriptions
- pull subscriptions [SQL Server replication]
- subscriptions [SQL Server replication]
- push subscriptions [SQL Server replication], about push subscriptions
- merge replication subscribing [SQL Server replication]
- merge replication subscribing [SQL Server replication], about subscribing
- publications [SQL Server replication], subscribing
- push subscriptions [SQL Server replication]
- pull subscriptions [SQL Server replication], about pull subscriptions
- snapshot replication [SQL Server], subscribing
- transactional replication, subscribing
ms.assetid: 088ee30a-05ab-47c4-92ed-316b93e12445
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3aa122e19d890b0b994e4403dcc59b3131571d7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62629692"
---
# <a name="subscribe-to-publications"></a>S'abonner à des publications
  Un abonnement est une demande de copie de données et d'objets de base de données d'une publication. Il définit la publication qui sera reçue, où et quand elle sera reçue. Lorsque vous planifiez des abonnements, pensez à l'endroit où vous voulez qu'ait lieu le traitement de l'agent. Le type d'abonnement choisi détermine l'emplacement d'exécution de l'agent. Avec un abonnement par envoi de données (push), l'Agent de fusion ou l'Agent de distribution s'exécute sur le serveur de distribution tandis qu'avec un abonnement par extraction de données (pull), les agents s'exécutent sur les Abonnés. Il n'est plus possible de modifier le type d'un abonnement une fois celui-ci créé.  
  
|Subscription|Caractéristiques|Cas d'utilisation|  
|------------------|---------------------|--------------|  
|Abonnement envoyé|Avec un abonnement par envoi de données, le serveur de publication propage les modifications à un Abonné sans que ce dernier en ait fait la demande. Les modifications peuvent être envoyées à des Abonnés à la demande, en continu ou selon un horaire planifié. L'Agent de distribution ou l'Agent de fusion s'exécute sur le serveur de distribution.|Les données sont censées être synchronisées de façon permanente ou à intervalles fréquents et périodiques.<br /><br /> La publication nécessite un transfert en temps réel (ou presque) des données.<br /><br /> L'augmentation de la charge imposée au processeur d'un serveur de distribution n'affecte pas les performances.<br /><br /> Le plus souvent utilisé avec la réplication d'instantané et la réplication transactionnelle.|  
|Abonnement extrait|Dans le cas d'un abonnement par extraction, l'Abonné demande à recevoir les modifications apportées sur le serveur de publication. Ce type d'abonnement permet à l'utilisateur sur l'Abonné de déterminer le moment où les modifications sont synchronisées. L'Agent de distribution ou l'Agent de fusion s'exécute sur l'Abonné.|Avec ce type d'abonnement, les données sont en général synchronisées à la demande ou selon un horaire planifié plutôt qu'en continu.<br /><br /> La publication compte un grand nombre d'Abonnés et l'exécution de tous les agents sur un seul site ou sur le serveur de distribution entraînerait une consommation excessive des ressources.<br /><br /> Les abonnés sont autonomes, non connectés et/ou mobiles. Ils déterminent à quel moment ils se connectent et synchronisent les modifications.<br /><br /> Le plus souvent utilisé avec la réplication de fusion.|  
  
## <a name="merge-replication-subscription-types"></a>Types d'abonnements de réplication de fusion  
 Tous les types de réplication permettent des abonnements par envoi ou extraction de données. La réplication de fusion fait la distinction entre deux types d'abonnement : les abonnements client et les abonnements serveur. Ces deux types d'abonnement sont utilisables avec les abonnements par envoi ou extraction de données. Les abonnements client sont adaptés à la plupart des Abonnés, tandis que les abonnements serveur sont généralement utilisés pour les Abonnés qui republient des données vers d'autres Abonnés. Le choix de l'abonnement a également une incidence sur la résolution des conflits.  
  
## <a name="non-sql-server-subscribers"></a>Non-SQL Server Subscribers  
 Oracle et IBM DB2 peuvent s'abonner à des publications transactionnelles et des publications d'instantané à l'aide des abonnements par envoi de données. Pour plus d’informations, consultez [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md).  
  
## <a name="creating-subscriptions"></a>Création d'abonnements  
 Pour créer un abonnement, fournissez les informations suivantes :  
  
-   Nom de la publication.  
  
-   le nom de l'Abonné et de la base de données d'abonnement ;  
  
-   si l'Agent de distribution ou l'Agent de fusion s'exécute sur le serveur de distribution ou sur l'Abonné ;  
  
-   si l'Agent de distribution ou l'Agent de fusion s'exécute en continu, selon un horaire planifié ou à la demande seulement ;  
  
-   si l'Agent d'instantané doit créer un instantané initial pour l'abonnement et si l'Agent de distribution ou l'Agent de fusion doit appliquer cet instantané sur l'abonné ;  
  
-   les comptes sous lesquels l'Agent de distribution ou l'Agent de fusion s'exécute ;  
  
-   Pour la réplication de fusion, le type d'abonnement : serveur ou client.  
  
 **Pour créer un abonnement envoyé**  
  
 [Créer un abonnement par émission de données](create-a-push-subscription.md)  
  
 **Pour afficher ou modifier les propriétés d'un abonnement par envoi de données**  
  
 [Afficher et modifier les propriétés d’un abonnement par émission (push)](view-and-modify-push-subscription-properties.md)  
  
 **Pour supprimer un abonnement par envoi de données**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] : [Supprimer un abonnement par émission de données](delete-a-push-subscription.md)  
  
> [!NOTE]  
>  La suppression d'un abonnement n'entraîne pas la suppression des objets publiés sur l'Abonné.  
  
 **Pour créer un abonnement par extraction de données**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] : [Créer un abonnement par extraction (pull)](create-a-pull-subscription.md)  
  
 **Pour afficher ou modifier les propriétés d'un abonnement extrait**  
  
 [Afficher et modifier les propriétés d’un abonnement par extraction (pull)](view-and-modify-pull-subscription-properties.md)  
  
 **Pour supprimer un abonnement extrait**  
  
 [Supprimer un abonnement par extraction (pull)](delete-a-pull-subscription.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser l’abonné](security/secure-the-subscriber.md)   
 [Expiration et désactivation des abonnements](subscription-expiration-and-deactivation.md)  
  
  
