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
manager: craigg
ms.openlocfilehash: f6a30012675c45688e49e8d32524b060de869908
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512594"
---
# <a name="trustworthy-bit"></a>Bit de confiance
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si le rôle dbo d'une base de données est affecté au rôle serveur fixe sysadmin et si le bit de confiance de la base de données a la valeur ON.  
  
 Si ces conditions sont réunies, un utilisateur de base de données doté de privilèges peut élever les privilèges au rôle sysadmin. Dans ce rôle, l'utilisateur peut créer et exécuter des assemblys non sécurisés qui compromettent le système.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Désactivez le bit de confiance ou révoquez les autorisations sysadmin du rôle de base de données dbo.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
