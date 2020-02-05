---
title: DROP SEQUENCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SEQUENCE
- DROP_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SEQUENCE statement
- sequence number object, dropping
ms.assetid: c25772d3-61af-4aa7-b58b-a6f67a793e3d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 740c8bff60f56b94304b789e901ec3b1d945fd17
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68077725"
---
# <a name="drop-sequence-transact-sql"></a>DROP SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Permet de supprimer un objet séquence de la base de données actuelle.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP SEQUENCE [ IF EXISTS ] { database_name.schema_name.sequence_name | schema_name.sequence_name | sequence_name } [ ,...n ]  
 [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Supprime, de manière conditionnelle, la séquence uniquement si elle existe déjà.  
  
 *database_name*  
 Nom de la base de données dans laquelle l'objet séquence a été créé.  
  
 *schema_name*  
 Nom du schéma auquel appartient l'objet séquence.  
  
 *sequence_name*  
 Nom de la séquence à supprimer. Le type est **sysname**.  
  
## <a name="remarks"></a>Notes  
 Après avoir généré un nombre, un objet séquence n'a aucune relation continue au nombre qu'il a généré ; par conséquent, l'objet séquence peut être supprimé, bien que le nombre généré soit encore en cours d'utilisation.  
  
 Un objet séquence peut être supprimé alors qu'il est référencé par une procédure stockée ou un déclencheur, car il n'est pas lié au schéma. Un objet séquence ne peut pas être supprimé s'il est référencé en tant que valeur par défaut dans une table. Le message d'erreur indiquera l'objet qui référence la séquence.  
  
 Pour répertorier tous les objets séquences dans la base de données, exécutez l'instruction suivante.  
  
```  
SELECT sch.name + '.' + seq.name AS [Sequence schema and name]   
    FROM sys.sequences AS seq  
    JOIN sys.schemas AS sch  
        ON seq.schema_id = sch.schema_id ;  
GO  
```  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert l'autorisation ALTER ou CONTROL sur le schéma.  
  
### <a name="audit"></a>Audit  
 Pour auditer **DROP SEQUENCE**, surveillez **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Exemples  
 L'exemple ci-dessous supprime un objet séquence nommé `CountBy1` dans la base de données actuelle.  
  
```  
DROP SEQUENCE CountBy1 ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [CREATE SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [NEXT VALUE FOR &#40;Transact-SQL&#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
