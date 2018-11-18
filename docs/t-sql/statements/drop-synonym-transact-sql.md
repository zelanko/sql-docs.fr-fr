---
title: DROP SYNONYM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b4704b1fdb9181e8abd9f800da7c57a7973d2090
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701237"
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime un synonyme d'un schéma spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
**S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu’à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Supprime, de manière conditionnelle, le synonyme uniquement s’il existe déjà.  
  
 *schema*  
 Spécifie le schéma dans lequel le synonyme existe. Si le schéma n'est pas spécifié, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise le schéma par défaut de l'utilisateur actuel.  
  
 *synonym_name*  
 Nom du synonyme à supprimer.  
  
## <a name="remarks"></a>Notes   
 Les références aux synonymes ne sont pas liées aux schémas ; vous pouvez supprimer un synonyme à n'importe quel moment. Les références aux synonymes supprimés ne se rencontrent que lors de l'exécution.  
  
 Vous pouvez créer, supprimer et référencer des synonymes dans des instructions SQL dynamiques.  
  
## <a name="permissions"></a>Permissions  
 Pour supprimer un synonyme, un utilisateur doit satisfaire au moins l'une des conditions suivantes. L'utilisateur doit être :  
  
-   Le propriétaire actuel d'un synonyme.  
  
-   Un bénéficiaire possédant une autorisation CONTROL sur un synonyme.  
  
-   Un bénéficiaire possédant une autorisation ALTER SCHEMA sur le schéma conteneur.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée d'abord un synonyme, `MyProduct`, puis le supprime.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
