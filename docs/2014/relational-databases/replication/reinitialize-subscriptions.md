---
title: Réinitialiser des abonnements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- initializing subscriptions [SQL Server replication], reinitializing
- subscriptions [SQL Server replication], reinitializing
- reinitializing subscriptions
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 189667ecd2756ebf0026a22d981f9bb0ddd347c9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85056979"
---
# <a name="reinitialize-subscriptions"></a>Réinitialiser des abonnements
  La réinitialisation d'un abonnement nécessite l'application d'un nouvel instantané d'un ou plusieurs articles à un ou plusieurs Abonnés : la réplication transactionnelle et la réplication d'instantané permettent à des articles individuels d'être réinitialisés ; la réplication de fusion nécessite que tous les articles soient réinitialisés. Les nœuds d'une topologie de réplication transactionnelle d'égal à égal ne peuvent pas être réinitialisés. Si vous voulez être certain qu'un nœud dispose d'une nouvelle copie des données, restaurez une sauvegarde sur le nœud. Une réinitialisation se produit pour l'une de ces deux raisons :  
  
-   Vous marquez explicitement un abonnement pour réinitialisation.  
  
-   Vous effectuez une action, par exemple une modification de propriété, qui nécessite une réinitialisation. Pour plus d’informations sur les actions qui nécessitent une réinitialisation, consultez [Modifier les propriétés des publications et des articles](publish/change-publication-and-article-properties.md).  
  
 Dans les deux cas, l'instantané le plus récent est appliqué à l'Abonné lors de l'exécution suivante de l'Agent de distribution ou de l'Agent de fusion. Pour la réplication d'instantané et la réplication transactionnelle, quand une réinitialisation se produit, toutes les modifications effectuées sur l'Abonné qui ne sont pas encore synchronisées avec le serveur de publication sont écrasées par l'application du nouvel instantané.  
  
 Pour la réplication de fusion, vous pouvez choisir de charger à partir de l'Abonné toutes les modifications apportées aux données avant d'appliquer l'instantané. Toutes les modifications de schéma en attente provenant du serveur de publication sont appliquées à l'Abonné, puis toutes les modifications qui ont été effectuées sur l'Abonné depuis la dernière synchronisation sont propagées vers le serveur de publication avant que l'instantané soit réappliqué. Ce fonctionnement est contrôlé par les propriétés **upload_first** et **automatic_reinitialization_policy** ; pour plus d'informations, consultez [Reinitialize a Subscription](reinitialize-a-subscription.md). Si vous marquez un abonnement pour réinitialisation à l'aide de SQL Server Management Studio ou du moniteur de réplication, vous pouvez choisir de charger dans la boîte de dialogue **Réinitialiser les abonnements** de charger d'abord les modifications.  
  
> [!IMPORTANT]  
>  Si vous ajoutez, supprimez ou modifiez un filtre paramétré dans une publication de fusion, les modifications en attente sur l'Abonné ne peuvent pas être chargées sur le serveur de publication au cours de la réinitialisation. Si vous voulez télécharger les modifications en attente, synchronisez tous les abonnements avant de modifier le filtre.  
  
 Si vous avez précisé qu'il ne fallait appliquer aucun instantané initial sur l'Abonné au moment de créer l'abonnement et marquez ensuite ce dernier en vue d'une réinitialisation, aucun instantané n'est appliqué. Pour plus d’informations, consultez [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Pour réinitialiser un abonnement**  
  
 Pour réinitialiser tous les articles d'un abonnement, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], des procédures stockées ou Replication Management Objects. Pour réinitialiser des articles individuels dans des publications d'instantané et transactionnelles, vous devez utiliser des procédures stockées. Pour plus d’informations, voir [Reinitialize a Subscription](reinitialize-a-subscription.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement](initialize-a-subscription.md)   
 [Expiration et désactivation des abonnements](subscription-expiration-and-deactivation.md)  
  
  
