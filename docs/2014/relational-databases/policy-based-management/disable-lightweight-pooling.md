---
title: Désactiver le regroupement léger | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 41735f374b811df4400282cbdde67e914ef7ec67
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068836"
---
# <a name="disable-lightweight-pooling"></a>Désactiver le regroupement léger
  Cette règle vérifie que le regroupement léger est désactivé sur le serveur. Si la valeur 1 est affectée à l'option Regroupement léger, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bascule sur la planification en mode fibre. Le mode fibre est utile dans certaines situations, lorsque le basculement de contexte des travailleurs UMS est le principal goulot d'étranglement au niveau des performances. Dans la mesure où cette situation est inhabituelle, le mode fibre améliore rarement les performances ou l'évolutivité sur le système classique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 L'option Regroupement léger ne doit être activée qu'après un test approfondi, une fois toutes les autres options de réglage des performances évaluées et lorsque le basculement de contexte est un problème connu dans votre environnement.  
  
 Nous vous déconseillons d'utiliser la planification en mode fibre pour les opérations courantes. En effet, elle peut dégrader les performances en ne permettant pas au basculement de contexte d'offrir ses avantages habituels et certains composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilisent le stockage TSL (Thread Stockage Local) ou des objets détenus par des threads, tels que des mutex (un type d'objet noyau Win32), ne peuvent pas fonctionner correctement en mode fibre.  
  
 Pour supprimer le regroupement léger, exécutez l’instruction suivante, puis redémarrez le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
```  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweightpooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [lightweight pooling (option de configuration de serveur)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
