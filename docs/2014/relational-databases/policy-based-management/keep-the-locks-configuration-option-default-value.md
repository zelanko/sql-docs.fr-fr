---
title: Conserver la valeur par défaut de l’option de configuration locks | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b64bb0d734d9b8674b3b4edabf35c9dd8fd30386
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152794"
---
# <a name="keep-the-locks-configuration-option-default-value"></a>Conserver la valeur par défaut de l'option de configuration locks
  Cette règle vérifie la valeur de l'option de configuration locks (verrous). Cette option détermine le nombre maximal de verrous disponibles et limite ainsi la quantité de mémoire utilisée par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pour les verrous. La valeur par défaut 0 permet à [!INCLUDE[ssDE](../../includes/ssde-md.md)] d’allouer et de libérer des structures de verrous de manière dynamique en fonction des modifications de la configuration requise.  
  
 Si la valeur de l'option locks est différente de zéro, les programmes de traitement par lots s'arrêtent et un message d'erreur indiquant un nombre de verrous insuffisant est généré lorsque la valeur spécifiée est dépassée.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Utilisez la procédure stockée système sp_configure pour rétablir la valeur par défaut de l'option locks à l'aide de l'instruction suivante :  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Configurer l'option de configuration du serveur locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [Article 271509 de la Base de connaissances Microsoft](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
