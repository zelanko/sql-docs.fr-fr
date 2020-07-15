---
title: Définir l’option de base de données AUTO_CLOSE sur OFF | Microsoft Docs
description: Vérifiez si l’option AUTO_ CLOSE est désactivée. L’option AUTO_ CLOSE a des implications pour les performances de SQL Server.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0dbcc137a97af6d447dafd44c71bdb8181c69577
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774200"
---
# <a name="set-the-auto_close-database-option-to-off"></a>Définir l'option de base de données AUTO_CLOSE sur OFF
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie si l'option AUTO_ CLOSE est désactivée (OFF). Lorsqu'elle est définie sur ON, cette option peut entraîner une dégradation des performances sur les bases de données fréquemment sollicitées en raison de la surcharge causée par l'ouverture et la fermeture de la base de données après chaque connexion. AUTO_CLOSE vide également le cache de procédure après chaque connexion.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 En cas d'accès fréquent à une base de données, définissez l'option AUTO_CLOSE sur OFF pour la base de données.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
