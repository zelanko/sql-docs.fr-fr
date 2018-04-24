---
title: Force du mot de passe de connexion SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
ms.assetid: b0862c3a-926b-490c-a37f-382e50146a3e
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b06638d8f47bc6eda827f6f85b38a96fb85a5851
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-login-password-strength"></a>Force du mot de passe de connexion SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie si l'option Conserver la stratégie de mot de passe est activée pour chaque connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est activée et si la version du système d'exploitation est antérieure à [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)], un pirate peut régulièrement exploiter un mot de passe de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connu.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Nous vous recommandons de mettre à niveau le système d'exploitation vers [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)].  
  
 Si l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas requise dans votre environnement, utilisez l'authentification Windows.  
  
 Activez l'option Conserver la stratégie de mot de passe pour toutes les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md) pour configurer la stratégie de mot de passe pour la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
