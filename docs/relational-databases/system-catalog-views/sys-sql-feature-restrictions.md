---
title: sys.sql_feature_restrictions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_sql_feature_restrictions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_feature_restrictions catalog view
author: vainolo
ms.author: arib
manager: tomerw
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b583afef9f52da7801384d4a7a9c76deaf8d4ee4
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822676"
---
# <a name="syssqlfeaturerestrictions-transact-sql"></a>sys.sql_feature_restrictions (Transact-SQL)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Retourne une ligne pour chaque restriction dans la base de données.
  
| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| class       | nvarchar(128) | Classe d’objet auquel s’applique la restriction |
| objet      | nvarchar (256) | Nom de l’objet auquel s’applique la restriction |
| Fonctionnalité     | nvarchar(128) | Fonctionnalité limitée |
  
## <a name="remarks"></a>Notes

Actuellement il est possible de limiter les fonctionnalités suivantes :

| Fonctionnalité          | Description |
|------------------|-------------|
| N'ErrorMessages' | Lorsque la limitée, toutes les données utilisateur dans le message d’erreur seront masquées. |
| N'Waitfor'       | Lors de la restriction, la commande retournera immédiatement sans délai. |
  
## <a name="permissions"></a>Autorisations

Le principal en cours d’exécution doit avoir le `CONTROL` autorisation sur la base de données.
  
## <a name="see-also"></a>Voir aussi

 [Restrictions liées aux fonctionnalités](../../relational-databases/security/feature-restrictions.md)
