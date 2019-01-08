---
title: CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 534df29b5ad3422ed3290ce4037490f69f988832
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535751"
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Interprète la valeur SYS_CHANGE_COLUMNS retournée par la fonction CHANGETABLE(CHANGES...). Cela permet à une application de déterminer si la colonne spécifiée est incluse dans les valeurs retournées pour SYS_CHANGE_COLUMNS.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Arguments  
 *column_id*  
 ID de la colonne en cours de vérification. La colonne ID peut être obtenu à l’aide de la [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) (fonction).  
  
 *change_columns*  
 Les données binaires à partir de la colonne SYS_CHANGE_COLUMNS de la [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) données.  
  
## <a name="return-type"></a>Type de retour  
 **bit**  
  
## <a name="return-values"></a>Valeurs de retour  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK retourne les valeurs suivantes.  
  
|Valeur retournée|Description|  
|------------------|-----------------|  
|0|La colonne spécifiée n’est pas dans le *change_columns* liste.|  
|1|La colonne spécifiée est dans le *change_columns* liste.|  
  
## <a name="remarks"></a>Notes  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK n’effectue aucune vérification pour valider le *column_id* valeur ou qui le *change_columns* paramètre a été obtenu à partir de la table à partir de laquelle le  *column_id* a été obtenu.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant détermine si la colonne `Salary` de la table `Employees` a été mise à jour. Le `COLUMNPROPERTY` fonction retourne l’ID de colonne de la `Salary` colonne. La variable locale `@change_columns` doit être définie en fonction des résultats d'une requête en utilisant CHANGETABLE comme source de données.  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de suivi des modifications &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Suivi des modifications de données &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
