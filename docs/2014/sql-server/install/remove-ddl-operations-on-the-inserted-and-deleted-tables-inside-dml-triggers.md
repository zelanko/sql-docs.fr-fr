---
title: Supprimer les opérations DDL sur les tables insérées et supprimées à l’intérieur des déclencheurs DML | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- data definition language [SQL Server]
- DDL statements [SQL Server]
- DML triggers, removing DDL operations
ms.assetid: e49ba7d5-787f-4052-b985-b699195d982b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 61f7ab78b5ab6251b7f27401d36423ec27141c4e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041843"
---
# <a name="remove-ddl-operations-on-the-inserted-and-deleted-tables-inside-dml-triggers"></a>Supprimer les opérations DDL sur les tables insérées et supprimées à l'intérieur des déclencheurs DML
  Les instructions DDL (Data Definition Language), telles que CREATe INDEX, ne peuvent pas être exécutées sur les tables inserted et Deleted dans les déclencheurs DML. Certaines instructions DDL sur les tables insérées et supprimées sont autorisées dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez « Utilisation des tables insérées et supprimées » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Supprimez toutes les opérations DDL effectuées sur les tables insérées et supprimées à l'intérieur des déclencheurs DML.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
