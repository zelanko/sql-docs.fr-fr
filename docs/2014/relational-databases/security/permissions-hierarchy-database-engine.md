---
title: Hiérarchie des autorisations (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 150892098f15adc6601b7cfeec3b4afc2cb5b0ec
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176749"
---
# <a name="permissions-hierarchy-database-engine"></a>Hiérarchie des autorisations (moteur de base de données)
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] gère une collection hiérarchisée d’entités qui peuvent être sécurisées à l’aide d’autorisations. Ces entités sont appelées *éléments sécurisables*. Les éléments sécurisables les plus proéminents sont les serveurs et les bases de données, mais les autorisations discrètes peuvent être définies à un niveau beaucoup plus fin. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règle les actions des principaux sur des éléments sécurisables en vérifiant que les autorisations appropriées leur ont été octroyées.

 L'illustration suivante montre les relations entre les hiérarchies des autorisations du [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .

 ![Diagramme de hiérarchies d'autorisations de moteur de base de données](../../database-engine/media/wj-security-layers.gif "Diagramme de hiérarchies d'autorisations de moteur de base de données")

## <a name="chart-of-sql-server-permissions"></a>Graphique des autorisations SQL Server
 Pour obtenir un graphique de la taille [!INCLUDE[ssDE](../../../includes/ssde-md.md)] d’une affiche de toutes les [https://go.microsoft.com/fwlink/?LinkId=229142](https://go.microsoft.com/fwlink/?LinkId=229142)autorisations au format PDF, consultez.

## <a name="working-with-permissions"></a>Utilisation des autorisations
 Les autorisations peuvent être gérées avec les requêtes GRANT, DENY et REVOKE [!INCLUDE[tsql](../../includes/tsql-md.md)] habituelles. Les informations sur les autorisations sont visibles dans les affichages catalogue [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) et [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Il existe également une assistance permettant d'obtenir des informations sur les autorisations à l'aide de fonctions intégrées.

## <a name="see-also"></a>Voir aussi
 [Sécurisation](securing-sql-server.md) des [autorisations SQL Server &#40;moteur de base de données&#41;](permissions-database-engine.md) éléments [sécurisables](securables.md) [&#40;moteur de base de données](authentication-access/principals-database-engine.md) [&#41;&#40;&#41;](/sql/t-sql/statements/grant-transact-sql) [Transact-](/sql/t-sql/functions/has-perms-by-name-transact-sql) sql &#40;[sys.&#41;&#40;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) transact [-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) [sys. HAS_PERMS_BY_NAME &#40;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) Transact [-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) [sys. fn_builtin_permissions &#40;de](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) Transact-SQL&#41;sys. server_permissions &#40;.&#41;s Transact-SQL database_permissions


