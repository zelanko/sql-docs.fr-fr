---
description: Fichiers journaux des traces par défaut désactivés
title: Fichiers journaux des traces par défaut désactivés
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c27761e6-75ed-4ee4-a236-0cbc42e500a1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0ef696fa684c7a473d06d94d10c1761cb41c8a2c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470327"
---
# <a name="default-trace-log-files-disabled"></a>Fichiers journaux des traces par défaut désactivés
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie la valeur de l'option default trace enabled (trace par défaut activée) de la procédure stockée sp_configure pour déterminer si la trace par défaut est définie sur ON (1) ou sur OFF (0). Lorsque cette option est activée, le traçage par défaut fournit des informations sur les modifications DDL et de configuration du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces informations peuvent être utiles aux clients, mais aussi au service clientèle et au support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] quand il s’agit de résoudre des problèmes liés à [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez la procédure stockée sp_configure pour activer le traçage en définissant la valeur de l'option default trace enabled sur 1.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
