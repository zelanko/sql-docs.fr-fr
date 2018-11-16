---
title: Désactiver le regroupement léger | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d5bc9651433cc0940732d4818f5d9b8c0f011ad1
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51511974"
---
# <a name="disable-lightweight-pooling"></a>Désactiver le regroupement léger
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie que le regroupement léger est désactivé sur le serveur. Si la valeur 1 est affectée à l'option Regroupement léger, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bascule sur la planification en mode fibre. Le mode fibre est utile dans certaines situations, lorsque le basculement de contexte des travailleurs UMS est le principal goulot d'étranglement au niveau des performances. Dans la mesure où cette situation est inhabituelle, le mode fibre améliore rarement les performances ou l'évolutivité sur le système classique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 L'option Regroupement léger ne doit être activée qu'après un test approfondi, une fois toutes les autres options de réglage des performances évaluées et lorsque le basculement de contexte est un problème connu dans votre environnement.  
  
 Nous vous déconseillons d'utiliser la planification en mode fibre pour les opérations courantes. En effet, elle peut dégrader les performances en ne permettant pas au basculement de contexte d'offrir ses avantages habituels et certains composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui utilisent le stockage TSL (Thread Stockage Local) ou des objets détenus par des threads, tels que des mutex (un type d'objet noyau Win32), ne peuvent pas fonctionner correctement en mode fibre.  
  
 Pour supprimer le regroupement léger, exécutez l’instruction suivante, puis redémarrez le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
```sql  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweight pooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Regroupement léger (option de configuration de serveur)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
