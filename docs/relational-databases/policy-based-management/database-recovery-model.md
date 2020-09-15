---
title: Modèle de récupération de base de données
description: Découvrez comment activer une stratégie pour vérifier le mode de récupération de sauvegarde pour des bases de données utilisateur afin de réduire la perte de données.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 048fa8d28e32ad73aa9e2a85e217f268fa865a3c
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285071"
---
# <a name="database-recovery-model"></a>Mode de récupération de base de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Pour SQL Server Entreprise et Standard, cette règle recherche les bases de données utilisateur qui ne sont pas en lecture et pour lesquelles la récupération simple est définie. Pour les bases de données de production, nous vous recommandons d'utiliser le mode de récupération complète plutôt que le mode de récupération simple. Le mode de récupération complète permet la récupération jusqu'à une date et heure. Cela permet de réduire la perte de données en cas récupération d'urgence.
  
## <a name="best-practices-recommendations"></a>Bonnes pratiques recommandées  
 Les bases de données de production doivent utiliser le mode de récupération complète et le journal des transactions doit être fréquemment sauvegardé pour garantir la récupération avec une perte de données minimum.
  
## <a name="see-also"></a>Voir aussi 
  
 [Vue d’ensemble de la restauration et de la récupération](../backup-restore/restore-and-recovery-overview-sql-server.md)   
  
 [Restaurations complètes de bases de données (mode de récupération complète)](../backup-restore/complete-database-restores-full-recovery-model.md)  

 [Sauvegardes du journal des transactions](../backup-restore/transaction-log-backups-sql-server.md)   
  
