---
title: Fichiers journaux des traces par défaut désactivés
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2ab57498c9b188818663cfe326287ee3f45a409f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62705355"
---
# <a name="default-trace-log-files-disabled"></a>Fichiers journaux des traces par défaut désactivés
  Cette règle vérifie la valeur de l'option default trace enabled (trace par défaut activée) de la procédure stockée sp_configure pour déterminer si la trace par défaut est définie sur ON (1) ou sur OFF (0). Lorsque cette option est activée, le traçage par défaut fournit des informations sur les modifications DDL et de configuration du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces informations peuvent être utiles aux clients, mais aussi au service clientèle et au support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] quand il s’agit de résoudre des problèmes liés à [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez la procédure stockée sp_configure pour activer le traçage en définissant la valeur de l'option default trace enabled sur 1.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Options de configuration de serveur &#40;SQLServer&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
