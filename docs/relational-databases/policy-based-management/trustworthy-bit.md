---
title: Bit de confiance | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 7c0fe0b7b8890b3ef9ee2671b4926c8be99cc679
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727290"
---
# <a name="trustworthy-bit"></a>Bit de confiance
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle détermine si le rôle dbo d'une base de données est affecté au rôle serveur fixe sysadmin et si le bit de confiance de la base de données a la valeur ON.  
  
 Si ces conditions sont réunies, un utilisateur de base de données doté de privilèges peut élever les privilèges au rôle sysadmin. Dans ce rôle, l'utilisateur peut créer et exécuter des assemblys non sécurisés qui compromettent le système.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Désactivez le bit de confiance ou révoquez les autorisations sysadmin du rôle de base de données dbo.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
