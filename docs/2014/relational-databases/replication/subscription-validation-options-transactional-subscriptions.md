---
title: Options de validation d’abonnement (abonnements transactionnels) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 37fdbafa1f6dbdbc593277e4e5d4df37ad054d82
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230659"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Options de validation d'abonnement (abonnements transactionnels)
  Utilisez la boîte de dialogue **Options de validation d'abonnement** pour spécifier si la validation doit utiliser uniquement un nombre de lignes ou un nombre de lignes et une somme de contrôle binaire.  
  
## <a name="options"></a>Options  
 **Vérifiez si l'abonné possède le même nombre de lignes de données répliquées que le serveur de publication**  
 Sélectionnez le type de validation du nombre de lignes à effectuer. Pour les publications Oracle, la seule option proposée est **Calculer le nombre réel de lignes en interrogeant directement les tables**.  
  
 **Comparer les sommes de contrôle pour vérifier les données de ligne**  
 Outre le comptage des lignes sur le serveur de publication et sur l'Abonné, une somme de contrôle de toutes les données est calculée à l'aide de l'algorithme de somme de contrôle binaire. Si le nombre de lignes est erroné, la somme de contrôle n'est pas effectuée.  
  
 **Arrêter l'Agent de distribution une fois la validation terminée**  
 Par défaut, l'Agent de distribution s'exécute en permanence. Sélectionnez cette option pour arrêter l'agent lorsque la validation est terminée. Cela permet de vérifier que la validation a réussi avant de continuer à répliquer des données vers l'Abonné.  
  
## <a name="see-also"></a>Voir aussi  
 [Valider des données sur l’abonné](validate-data-at-the-subscriber.md)   
 [Valider des données répliquées](validate-replicated-data.md)  
  
  
