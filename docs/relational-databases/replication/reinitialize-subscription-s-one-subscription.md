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
ms.openlocfilehash: 91d5c40e288f35687b1ae34397ad6bcdf51f2159
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287400"
---
# <a name="reinitialize-subscriptions---one-subscription"></a>Réinitialiser les abonnements - Un abonnement
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
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
  
  
