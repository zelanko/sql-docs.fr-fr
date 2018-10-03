---
title: Bit de confiance | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 524c1c330288579649fd7744366cf8f3866fe8a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072109"
---
# <a name="trustworthy-bit"></a>Bit de confiance
  Cette règle détermine si le rôle dbo d'une base de données est affecté au rôle serveur fixe sysadmin et si le bit de confiance de la base de données a la valeur ON.  
  
 Si ces conditions sont réunies, un utilisateur de base de données doté de privilèges peut élever les privilèges au rôle sysadmin. Dans ce rôle, l'utilisateur peut créer et exécuter des assemblys non sécurisés qui compromettent le système.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Désactivez le bit de confiance ou révoquez les autorisations sysadmin du rôle de base de données dbo.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
