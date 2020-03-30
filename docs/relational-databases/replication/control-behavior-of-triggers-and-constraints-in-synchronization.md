---
title: Contrôler le comportement des déclencheurs et des contraintes de la synchronisation
description: Découvrez comment empêcher l’exécution de déclencheurs ou de contraintes pendant la synchronisation d’une publication de réplication SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- identities [SQL Server replication]
- constraints [SQL Server], replication
- triggers [SQL Server], replication
- triggers [SQL Server replication]
- constraints [SQL Server replication]
- NOT FOR REPLICATION option
- NFR option
ms.assetid: 7c4e0f0e-cadc-4c99-98f4-69799b9b356b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 2b0e768712d1987755f100f4db555a5e09f6db7c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "76284794"
---
# <a name="control-behavior-of-triggers-and-constraints-in-synchronization"></a>Contrôler le comportement des déclencheurs et des contraintes de la synchronisation
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Au cours de la synchronisation, les agents de réplication exécutent des instructions [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md), [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) et [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) sur les tables répliquées, ce qui peut entraîner l’exécution de déclencheurs de langage de manipulation de données (DML) sur ces tables. Dans certains cas, vous pouvez avoir besoin d'empêcher l'exécution de ces déclencheurs ou l'application de contraintes au cours de la synchronisation. Ce comportement dépend de la manière dont le déclencheur ou la contrainte sont créés.  
  
### <a name="to-prevent-triggers-from-executing-during-synchronization"></a>Pour empêcher l'exécution de déclencheurs pendant la synchronisation  
  
1.  Quand vous créez un déclencheur, spécifiez l’option NOT FOR REPLICATION de [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md).  
  
2.  Pour un déclencheur existant, spécifiez l’option NOT FOR REPLICATION d’[ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md).  
  
### <a name="to-prevent-constraints-from-being-enforced-during-synchronization"></a>Pour empêcher l'application de contraintes pendant la synchronisation  
  
1.  Quand vous créez une contrainte CHECK ou FOREIGN KEY, spécifiez l’option CHECK NOT FOR REPLICATION dans la définition de contrainte de [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des tables &#40;moteur de base de données&#41;](../../relational-databases/tables/create-tables-database-engine.md)  
  
  
