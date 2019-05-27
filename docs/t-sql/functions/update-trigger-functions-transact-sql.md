---
title: UPDATE() (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UPDATE()_TSQL
- UPDATE()
dev_langs:
- TSQL
helpviewer_keywords:
- INSERT statement [SQL Server], UPDATE function
- testing column updates
- UPDATE function
- UPDATE() function
- detecting changes
- columns [SQL Server], change detection
- UPDATE statement [SQL Server], UPDATE function
- verifying column updates
- checking column updates
ms.assetid: 8e3be25b-2e3b-4d1f-a610-dcbbd8d72084
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 783eb070efcbafa2b8ec3685d66b080c420cc768
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65946783"
---
# <a name="update---trigger-functions-transact-sql"></a>UPDATE - Fonctions de déclencheurs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne une valeur booléenne qui indique si une tentative d'opération INSERT ou UPDATE a été réalisée sur une colonne spécifiée d'une table ou d'une vue. UPDATE() est utilisé à n'importe quel endroit du corps d'un déclencheur INSERT ou UPDATE [!INCLUDE[tsql](../../includes/tsql-md.md)] pour tester si celui-ci doit exécuter certaines actions.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
  
UPDATE ( column )   
```  
  
## <a name="arguments"></a>Arguments  
 *column*  
 Nom de la colonne à tester pour une action INSERT ou UPDATE. Étant donné que le nom de la table est spécifié dans la clause ON du déclencheur, n'incluez pas ce nom avant le nom de la colonne. La colonne peut correspondre à n’importe quel [type de données](../../t-sql/data-types/data-types-transact-sql.md) pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, les colonnes calculées ne peuvent pas être utilisées dans ce contexte.  
  
## <a name="return-types"></a>Types de retour  
 Booléen  
  
## <a name="remarks"></a>Notes   
 UPDATE() retourne TRUE quelle que soit l'issue d'une tentative d'opération INSERT ou UPDATE.  
  
 Afin de tester une action INSERT ou UPDATE pour plusieurs colonnes, spécifiez une clause séparée UPDATE(*column*) après la première colonne. Plusieurs colonnes peuvent également être testées pour des actions INSERT ou UPDATE à l'aide de COLUMNS_UPDATED. Celui-ci retourne un modèle binaire qui indique quelles colonnes ont été insérées ou mises à jour.  
  
 IF UPDATE retourne la valeur TRUE dans les actions INSERT car des valeurs explicites ou implicites (NULL) sont insérées dans les colonnes.  
  
> [!NOTE]  
>  La clause IF UPDATE(*colonne*n) fonctionne de la même manière qu’une clause IF, IF...ELSE ou WHILE, et elle peut utiliser le bloc BEGIN...END. Pour plus d’informations, consultez [Langage de contrôle de flux &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md).  
  
 UPDATE(*column*) peut être utilisé dans n’importe quel endroit du corps d’un déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)].  
 
Si un déclencheur s’applique à une colonne, la valeur `UPDATED` retourne `true` ou `1`, même si la valeur de colonne reste inchangée. Cela est intentionnel. Le déclencheur doit implémenter une logique métier qui détermine si l’opération d’insertion/de mise à jour/de suppression est autorisée ou non. 
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée un déclencheur qui envoie un message au client lorsqu'une personne essaie de mettre à jour les colonnes `StateProvinceID` ou `PostalCode` de la table `Address`.  
  
```sql  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
      WHERE name = 'reminder' AND type = 'TR')  
   DROP TRIGGER Person.reminder;  
GO  
CREATE TRIGGER reminder  
ON Person.Address  
AFTER UPDATE   
AS   
IF ( UPDATE (StateProvinceID) OR UPDATE (PostalCode) )  
BEGIN  
RAISERROR (50009, 16, 10)  
END;  
GO  
-- Test the trigger.  
UPDATE Person.Address  
SET PostalCode = 99999  
WHERE PostalCode = '12345';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [COLUMNS_UPDATED &#40;Transact-SQL&#41;](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
  
  
