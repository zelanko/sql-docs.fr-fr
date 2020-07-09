---
title: Réinitialiser les abonnements - Un abonnement | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.reinit.single.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c7992f3b9b27c219c2a28d226136442bddb2646f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767708"
---
# <a name="reinitialize-subscriptions---one-subscription"></a>Réinitialiser les abonnements - Un abonnement
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  La boîte de dialogue **Réinitialiser les abonnements** vous permet de marquer un abonnement en vue de sa réinitialisation. La réinitialisation sous-entend l'application d'un instantané à un Abonné. Cette tâche revient à l'agent de distribution dans le cas d'abonnements à des publications transactionnelles et à l'agent de fusion dans le cas d'abonnements à des publications de fusion.  
  
## <a name="options"></a>Options  
 **Utiliser l'instantané actuel**  
 Permet d'appliquer l'instantané à l'Abonné lors de l'exécution suivante de l'agent de distribution ou de l'agent de fusion. Si aucun instantané valide n'est disponible, vous ne pouvez pas sélectionner cette option.  
  
 **Utiliser un nouvel instantané**  
 Permet de réinitialiser l'abonnement par un nouvel instantané. L'instantané ne peut être appliqué à l'Abonné qu'après sa génération par l'Agent d'instantané. Si l'exécution de ce dernier est planifiée, l'abonnement n'est alors réinitialisé qu'après la prochaine exécution planifiée de l'Agent d'instantané.  
  
 Sélectionnez **Générer le nouvel instantané maintenant** pour lancer immédiatement l'Agent d'instantané.  
  
 **Télécharger les modifications non synchronisées avant la réinitialisation**  
 Réplication de fusion uniquement. Permet de télécharger vers le serveur toute modification en attente et apportée à la base de données d'abonnement avant que les données au niveau de l'Abonné ne soient écrasées par un instantané.  
  
 Si vous ajoutez, supprimez ou modifiez un filtre paramétré, les modifications en attente chez l'abonné ne peuvent pas être chargées sur le serveur de publication pendant la réinitialisation. Si vous voulez télécharger les modifications en attente, synchronisez tous les abonnements avant de modifier le filtre.  
  
 **Marquer pour réinitialisation**  
 Permet de marquer l'abonnement en vue de sa réinitialisation. Lorsqu'un instantané est disponible, lors de la prochaine exécution de l'Agent de distribution ou de fusion, l'instantané est appliqué à l'Abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
