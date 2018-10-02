---
title: Autorisations Invité sur les bases de données utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 366ee3f80bacbd1cf17bcec7ed0c4e04ce892277
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787977"
---
# <a name="guest-permissions-on-user-databases"></a>Autorisations Invité sur les bases de données utilisateur
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si l'utilisateur invité a l'autorisation d'accéder à la base de données. Cette règle s'applique uniquement aux bases de données utilisateur.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Révoquez l'autorisation d'accès à la base de données octroyée à l'utilisateur invité si elle n'est pas nécessaire.  
  
 Vous ne pouvez pas supprimer l’utilisateur guest, mais vous pouvez le désactiver en révoquant son autorisation CONNECT. Pour ce faire, vous devez exécuter REVOKE CONNECT FROM GUEST dans toute base de données autre que la base master, tempdb ou msdb.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Sécurisation de SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
