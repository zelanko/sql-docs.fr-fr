---
title: Définir l’option de base de données AUTO_CLOSE sur OFF | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1ea25d2198206595048e70501ddc14e1dbedc4b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="set-the-autoclose-database-option-to-off"></a>Définir l'option de base de données AUTO_CLOSE sur OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie si l'option AUTO_ CLOSE est désactivée (OFF). Lorsqu'elle est définie sur ON, cette option peut entraîner une dégradation des performances sur les bases de données fréquemment sollicitées en raison de la surcharge causée par l'ouverture et la fermeture de la base de données après chaque connexion. AUTO_CLOSE vide également le cache de procédure après chaque connexion.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 En cas d'accès fréquent à une base de données, définissez l'option AUTO_CLOSE sur OFF pour la base de données.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
