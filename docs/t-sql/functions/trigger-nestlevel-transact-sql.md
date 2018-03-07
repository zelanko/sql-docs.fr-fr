---
title: TRIGGER_NESTLEVEL (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRIGGER_NESTLEVEL
- TRIGGER_NESTLEVEL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- triggers [SQL Server], number executed
- number of triggers
- TRIGGER_NESTLEVEL function
ms.assetid: 6a33e74a-0cf9-4ae1-a1e4-4a137a3ea39d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0416b80079ac4c1dfb6dc10b507fd85800dd3a27
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="triggernestlevel-transact-sql"></a>TRIGGER_NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie le nombre de déclencheurs exécutés pour l'instruction qui a activé le déclencheur. TRIGGER_NESTLEVEL est utilisé dans les déclencheurs DML et DDL pour déterminer le niveau d'imbrication actuel.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
TRIGGER_NESTLEVEL ( [ object_id ] , [ 'trigger_type' ] , [ 'trigger_event_category' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *object_id*  
 Identificateur d'objet d'un déclencheur. Si *object_id* est spécifié, le nombre d’exécutions du déclencheur spécifié pour l’instruction est retournée. Si *object_id* n’est pas spécifié, le nombre de fois que tous les déclencheurs exécutés pour l’instruction est retournée.  
  
 **'** *trigger_type* **'**  
 Spécifie si TRIGGER_NESTLEVEL doit s'appliquer aux déclencheurs AFTER ou aux déclencheurs INSTEAD OF. Spécifiez **AFTER** pour les déclencheurs AFTER. Spécifiez **IOT** pour des déclencheurs INSTEAD OF. Si *trigger_type* est spécifié, *trigger_event_category* doit également être spécifié.  
  
 **'** *trigger_event_category* **'**  
 Spécifie si TRIGGER_NESTLEVEL doit s'appliquer aux déclencheurs DML ou DDL. Spécifiez **DML** pour les déclencheurs DML. Spécifiez **DDL** pour les déclencheurs DDL. Si *trigger_event_category* est spécifié, *trigger_type* doit également être spécifié. Notez que seul **AFTER** peut être spécifié avec **DDL**, car les déclencheurs DDL peuvent uniquement être déclencheurs AFTER.  
  
## <a name="remarks"></a>Notes  
 Si aucun paramètre n'est spécifié, TRIGGER_NESTLEVEL renvoie le nombre total de déclencheurs sur la pile des appels. Elle est comprise elle-même dans ce décompte. Les paramètres peuvent être omis lorsqu'un déclencheur exécute des commandes entraînant l'activation d'un autre déclencheur ou provoque l'activation d'une succession de déclencheurs.  
  
 Pour retourner le nombre total de déclencheurs sur la pile des appels pour une catégorie de type et événement déclencheur particulier, spécifiez *object_id* = 0.  
  
 TRIGGER_NESTLEVEL renvoie la valeur 0 si son exécution se produit à l'extérieur d'un déclencheur et si aucun paramètre n'a la valeur NULL.  
  
 Si des paramètres sont explicitement spécifiés avec la valeur NULL, une valeur NULL est renvoyée, que TRIGGER_NESTLEVEL ait été utilisé à l'intérieur ou à l'extérieur d'un déclencheur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-testing-the-nesting-level-of-a-specific-dml-trigger"></a>A. Test du niveau d'imbrication d'un déclencheur DML spécifique  
  
```  
IF ( (SELECT TRIGGER_NESTLEVEL( OBJECT_ID('xyz') , 'AFTER' , 'DML' ) ) > 5 )  
   RAISERROR('Trigger xyz nested more than 5 levels.',16,-1)  
```  
  
### <a name="b-testing-the-nesting-level-of-a-specific-ddl-trigger"></a>B. Test du niveau d'imbrication d'un déclencheur DDL spécifique  
  
```  
IF ( ( SELECT TRIGGER_NESTLEVEL ( ( SELECT object_id FROM sys.triggers  
WHERE name = 'abc' ), 'AFTER' , 'DDL' ) ) > 5 )  
   RAISERROR ('Trigger abc nested more than 5 levels.',16,-1)  
```  
  
### <a name="c-testing-the-nesting-level-of-all-triggers-executed"></a>C. Test du niveau d'imbrication de tous les déclencheurs exécutés  
  
```  
IF ( (SELECT trigger_nestlevel() ) > 5 )  
   RAISERROR  
      ('This statement nested over 5 levels of triggers.',16,-1)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
