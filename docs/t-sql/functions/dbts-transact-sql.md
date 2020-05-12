---
title: '@@DBTS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 9d06a019d162c6c8455efd1c85e49ec109763d0a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82804661"
---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction retourne la valeur du type de données actuel **timestamp** pour la base de données active. La base de données actuelle a une valeur timestamp unique garantie.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>Types de retour
**varbinary**
  
## <a name="remarks"></a>Notes  
@@DBTS renvoie la dernière valeur timestamp utilisée de la base de données active. L’insertion ou la mise à jour d’une ligne comprenant une colonne **timestamp** génère une nouvelle valeur timestamp.
  
Les changements apportés aux niveaux d’isolation des transactions n’affectent pas la fonction @@DBTS.
  
## <a name="examples"></a>Exemples  
Cet exemple retourne la valeur **timestamp** actuelle de la base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de configuration &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)  
[Accès concurrentiel au curseur &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  
