---
title: DROP SYNONYM (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs: TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 25af262ddc5655bc42e4893daecefe0cd8fb85d9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
 *S’IL EXISTE*  
**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Conditionnellement supprime le synonyme uniquement s’il existe déjà.  
  
 *schéma*  
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
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un SYNONYME &#40; Transact-SQL &#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
