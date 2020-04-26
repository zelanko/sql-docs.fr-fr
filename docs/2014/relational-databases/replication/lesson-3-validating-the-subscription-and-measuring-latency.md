---
title: 'Leçon 3 : Validation de l’abonnement et mesure de la latence | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 6968331bc7699334f61997ec6a16e521c158078a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62721049"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>Leçon 3 : Validation de l'abonnement et mesure de la latence
  Dans cette leçon, vous allez utiliser des jetons de suivi pour vérifier que les modifications sont en cours de réplication vers l'Abonné et pour déterminer la latence, à savoir le temps qu'il faut pour qu'une modification apportée sur le serveur de publication apparaisse sur l'Abonné. Cette leçon suppose que vous avez terminé la leçon précédente, [Leçon 2 : Création d’un abonnement à la publication transactionnelle](lesson-2-creating-a-subscription-to-the-transactional-publication.md).  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>Pour insérer un jeton de suivi et afficher des informations sur le jeton  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud du serveur, cliquez avec le bouton droit sur le dossier **Réplication** , puis cliquez sur **Lancer le moniteur de réplication**.  
  
     Le moniteur de réplication démarre.  
  
2.  Développez un groupe de serveurs de publication dans le volet gauche, développez une instance du serveur de publication, puis cliquez sur la publication **AdvWorksProductTrans** .  
  
3.  Cliquez sur l'onglet **Jetons de suivi** .  
  
4.  Cliquez sur **Insérer un suivi**.  
  
5.  Affichez le temps écoulé pour le jeton de suivi dans les colonnes suivantes : **Du serveur de publication vers le serveur de distribution**, **Du serveur de distribution vers l'Abonné**et **Latence totale**. La valeur **en attente** indique que le jeton n’a pas atteint un point donné.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans cette leçon, vous avez utilisé avec succès les jetons de suivi pour valider que les modifications de données sont bien en cours de réplication du serveur de publication vers l'Abonné. Vous pouvez aussi insérer, modifier ou supprimer des données dans la table **Product** du serveur de publication et interroger la table **Product** de l'Abonné pour afficher les modifications après qu'elles ont été répliquées.  
  
 Ainsi s'achève le didacticiel sur la réplication de données entre serveurs connectés en permanence. Pour obtenir un didacticiel similaire utilisant la réplication de fusion, consultez [Tutorial: Replicating Data with Mobile Clients](tutorial-replicating-data-with-mobile-clients.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer la latence et valider les connexions pour la réplication transactionnelle](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
