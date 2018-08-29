---
title: CHANGE_TRACKING_CURRENT_VERSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_CURRENT_VERSION_TSQL
- CHANGE_TRACKING_CURRENT_VERSION
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_CURRENT_VERSION
- CHANGE_TRACKING_CURRENT_VERSION
ms.assetid: 3027c4f7-6b4d-4089-a369-5926e8a8da1c
caps.latest.revision: 16
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fb799aa3d13536396781b583ef320a908cca45e0
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43077581"
---
# <a name="changetrackingcurrentversion-transact-sql"></a>CHANGE_TRACKING_CURRENT_VERSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une version associée à la dernière transaction validée. Cette version peut être utilisée lorsque vous énumérez des modifications à l’aide de [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CHANGE_TRACKING_CURRENT_VERSION ( )  
```  
  
## <a name="return-type"></a>Type de retour  
 **bigint**  
  
## <a name="remarks"></a>Notes  
 Retourne la valeur NULL lorsque le suivi des modifications n'est pas activé pour la base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant déclare la variable locale `@next_baseline` pour stocker la version actuelle du suivi des modifications, puis utilise la fonction `CHANGE_TRACKING_CURRENT_VERSION()` pour obtenir la valeur de la variable.  
  
```sql  
DECLARE @next_baseline bigint;  
SET @next_baseline = CHANGE_TRACKING_CURRENT_VERSION();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de suivi des modifications &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
