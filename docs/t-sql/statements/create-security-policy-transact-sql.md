---
title: "CRÉER une stratégie de sécurité (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/10/2017
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
- SECURITY_POLICY_TSQL
- CREATE SECURITY
- SECURITY
- CREATE_SECURITY_POLICY_TSQL
- CREATE_SECURITY_TSQL
- SECURITY POLICY
- SECURITY_TSQL
- CREATE SECURITY POLICY
dev_langs: TSQL
helpviewer_keywords:
- RLS
- CREATE SECURITY POLICY statement
- Row-Level Security
ms.assetid: d6ab70ee-0fa2-469c-96f6-a3c16d673bc8
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 205a09efdef9e59736fa20238455b4327dced330
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="create-security-policy-transact-sql"></a>CRÉER une stratégie de sécurité (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crée une stratégie de sécurité pour la sécurité au niveau des lignes.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```     
CREATE SECURITY POLICY [schema_name. ] security_policy_name    
    { ADD [ FILTER | BLOCK ] } PREDICATE tvf_schema_name.security_predicate_function_name   
      ( { column_name | arguments } [ , …n] ) ON table_schema_name. table_name    
      [ <block_dml_operation> ] , [ , …n] 
    [ WITH ( STATE = { ON | OFF }  [,] [ SCHEMABINDING = { ON | OFF } ] ) ]  
    [ NOT FOR REPLICATION ] 
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Arguments  
 *security_policy_name*  
 Nom de la stratégie de sécurité. Les noms de stratégie de sécurité doivent respecter les règles applicables aux identificateurs et doivent être uniques dans la base de données et pour son schéma.  
  
 *schema_name*  
 Nom du schéma auquel appartient la stratégie de sécurité. *schema_name* est nécessaire en raison de la liaison de schéma.  
  
 [FILTRE | BLOC]  
 Le type de prédicat de sécurité pour la fonction liée à la table cible. Les prédicats de filtre filtrent en mode silencieux les lignes qui sont disponibles pour les opérations de lecture. BLOC de prédicats explicitement des opérations d’écriture de blocs qui violent la fonction de prédicat.  
  
 *tvf_schema_name.security_predicate_function_name*  
 Fonction de valeur de table inline à utiliser comme prédicat et à appliquer dans les requêtes portant sur une table cible. Au plus un prédicat de sécurité peut être défini pour une opération DML particulière sur une table donnée. La fonction de valeur de table inline doit avoir été créée à l'aide de l'option SCHEMABINDING.  
  
 { *column_name* | *arguments* }  
 Le nom de la colonne ou l'expression utilisé en tant que paramètres de la fonction de prédicat de sécurité. Toutes les colonnes de la table cible peuvent être utilisées comme arguments pour la fonction de prédicat. Les expressions qui incluent des littéraux, les données prédéfinies et les expressions qui utilisent des opérateurs arithmétiques peuvent être utilisées.  
  
 *table_schema_name.TABLE_NAME*  
 Table cible à laquelle sera appliqué le prédicat de sécurité. Plusieurs stratégies de sécurité désactivées peuvent cibler une table unique pour une opération DML particulière, mais une seule peut être activée à un moment donné.  
  
 *\<block_dml_operation >* l’opération DML particulière pour laquelle le prédicat de bloc est appliqué. Spécifie une fois que le prédicat est évalué sur les valeurs des lignes après que l’opération DML a été effectuée (INSERT ou UPDATE). Spécifie avant que le prédicat est évalué sur les valeurs des lignes avant l’opération DML est effectuée (mise à jour ou suppression). Si aucune opération n’est spécifiée, le prédicat s’appliquera à toutes les opérations.  
  
 [ÉTAT = {ON | **OFF** }]  
 Permet à la stratégie de sécurité d'appliquer ses prédicats de sécurité sur les tables cibles, ou l'empêche d'effectuer cette opération. Sauf indication contraire, la stratégie de sécurité en cours de création est activée.  
  
 [SCHEMABINDING = {ON | {OFF}]  
 Indique si toutes les fonctions de prédicat dans la stratégie doivent être créées avec l’option SCHEMABINDING. Par défaut, toutes les fonctions doivent être créées avec SCHEMABINDING.  
  
 NOT FOR REPLICATION  
 Indique que la stratégie de sécurité ne doit pas être exécutée quand un agent de réplication modifie l'objet cible. Pour plus d’informations, consultez [Contrôler le comportement de déclencheurs et de contraintes au cours de la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 [*table_schema_name*.] *nom_table*  
 Table cible à laquelle sera appliqué le prédicat de sécurité. Plusieurs stratégies de sécurité désactivées peuvent cibler une même table, mais une seule peut être activée à un moment donné.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez des fonctions de prédicat avec tables optimisées en mémoire, vous devez inclure **SCHEMABINDING** et utiliser le **WITH NATIVE_COMPILATION** indicateur de compilation.  
  
 Les prédicats Block sont évaluées après l’exécution de l’opération DML correspondante. Par conséquent, une requête READ UNCOMMITTED permettre voir les valeurs temporaires qui seront restaurées.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY SECURITY POLICY et l'autorisation ALTER sur le schéma.  
  
 En outre, les autorisations suivantes sont requises pour chaque prédicat ajouté :  
  
-   Les autorisations SELECT et REFERENCES sur la fonction utilisée en tant que prédicat  
  
-   L'autorisation REFERENCES sur la table cible liée à la stratégie  
  
-   L'autorisation REFERENCES sur chaque colonne de la table cible utilisée comme arguments  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent l'utilisation de la syntaxe **CREATE SECURITY POLICY** . Pour obtenir un exemple d’un scénario de stratégie de sécurité complète, consultez [sécurité de niveau ligne](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-creating-a-security-policy"></a>A. Création d'une stratégie de sécurité  
 La syntaxe suivante crée une stratégie de sécurité avec un prédicat de filtre pour la table Customer et laisse la stratégie de sécurité désactivée.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate]([CustomerId])   
ON [dbo].[Customer];  
```  
  
### <a name="b-creating-a-policy-that-affects-multiple-tables"></a>B. Création d'une stratégie qui affecte plusieurs tables  
 La syntaxe suivante crée une stratégie de sécurité avec trois prédicats de filtre sur trois tables différentes et active la stratégie de sécurité.  
  
```  
CREATE SECURITY POLICY [FederatedSecurityPolicy]   
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([CustomerId])   
    ON [dbo].[Customer],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate1]([VendorId])   
    ON [dbo].[ Vendor],  
ADD FILTER PREDICATE [rls].[fn_securitypredicate2]([WingId])   
    ON [dbo].[Patient]  
WITH (STATE = ON);  
```  
  
### <a name="c-creating-a-policy-with-multiple-types-of-security-predicates"></a>C. Création d’une stratégie avec plusieurs types de prédicats de sécurité  
 Ajout d’un prédicat de filtre et un prédicat de bloc pour la table Sales.  
  
```  
CREATE SECURITY POLICY rls.SecPol  
    ADD FILTER PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales,  
    ADD BLOCK PREDICATE rls.tenantAccessPredicate(TenantId) ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [ALTER SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Sys.security_predicates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  

