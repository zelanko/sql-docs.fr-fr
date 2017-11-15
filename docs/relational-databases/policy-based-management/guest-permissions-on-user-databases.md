---
title: "Autorisations Invité sur les bases de données utilisateur | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49a29bf175c9ad048a1243bc4d495bf4be6f0e92
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="guest-permissions-on-user-databases"></a>Autorisations Invité sur les bases de données utilisateur
  Cette règle détermine si l'utilisateur invité a l'autorisation d'accéder à la base de données. Cette règle s'applique uniquement aux bases de données utilisateur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Révoquez l'autorisation d'accès à la base de données octroyée à l'utilisateur invité si elle n'est pas nécessaire.  
  
 Vous ne pouvez pas supprimer l’utilisateur guest, mais vous pouvez le désactiver en révoquant son autorisation CONNECT. Pour ce faire, vous devez exécuter REVOKE CONNECT FROM GUEST dans toute base de données autre que la base master, tempdb ou msdb.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
