---
title: Autorisations Invité sur les bases de données utilisateur | Microsoft Docs
description: Déterminez si l’utilisateur invité est autorisé à accéder aux bases de données utilisateur dans SQL Server. Révoquez l’autorisation utilisateur invité si elle n’est pas requise.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b6a911c84574c0b064c1c71bf9ff68aa725fc9c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749368"
---
# <a name="guest-permissions-on-user-databases"></a>Autorisations Invité sur les bases de données utilisateur
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle détermine si l'utilisateur invité a l'autorisation d'accéder à la base de données. Cette règle s'applique uniquement aux bases de données utilisateur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Révoquez l'autorisation d'accès à la base de données octroyée à l'utilisateur invité si elle n'est pas nécessaire.  
  
 Vous ne pouvez pas supprimer l’utilisateur guest, mais vous pouvez le désactiver en révoquant son autorisation CONNECT. Pour ce faire, vous devez exécuter REVOKE CONNECT FROM GUEST dans toute base de données autre que la base master, tempdb ou msdb.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
