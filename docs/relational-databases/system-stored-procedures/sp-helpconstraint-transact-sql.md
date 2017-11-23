---
title: sp_helpconstraint (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbd28705c736817c224762b1535acd34a22dc15e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Renvoie une liste de tous les types de contraintes, en précisant leur nom (défini par l'utilisateur ou fourni par le système), les colonnes auxquelles elles s'appliquent et l'expression qui les définit (contraintes DEFAULT et CHECK uniquement).  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@objname=** ] **'***table***'**  
 Table sur laquelle sont renvoyées les informations concernant les contraintes. La table spécifiée doit être locale par rapport à la base de données active. *table* est **nvarchar(776)**, sans valeur par défaut.  
  
 [  **@nomsg=**] **'***pas_de_message***'**  
 Paramètre facultatif qui permet l'impression du nom de la table. *pas_de_message* est **varchar (5)**, avec une valeur par défaut **msg**. **nomsg** supprime l’impression.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 **sp_helpconstraint** affiche une colonne indexée décroissante si elle est impliquée dans les clés primaires. Une colonne indexée descendante sera listée dans le jeu de résultats avec un signe moins (-) derrière son nom. Une colonne indexée ascendante (valeur par défaut) sera listée sous son seul nom.  
  
## <a name="remarks"></a>Notes  
 L’exécution de **sp_help***table* toutes les informations sur la table spécifiée. Pour afficher uniquement les informations de contrainte, utilisez **sp_helpconstraint**.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant affiche toutes les contraintes de la table `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sys.key_constraints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [Sys.CHECK_CONSTRAINTS &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [Sys.default_constraints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  
