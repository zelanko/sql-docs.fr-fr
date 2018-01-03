---
title: "MODIFIER la stratégie de sécurité (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 05/01/2017
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
- ALTER_SECURITY_POLICY_TSQL
- ALTER SECURITY POLICY
- ALTER_SECURITY_TSQL
- ALTER SECURITY
dev_langs: TSQL
helpviewer_keywords: ALTER SECURITY POLICY statement
ms.assetid: a8efc37e-113d-489c-babc-b914fea2c316
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f5ce90660a43e5285735a74a01b560ec210ba3f0
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="alter-security-policy-transact-sql"></a>MODIFIER la stratégie de sécurité (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Modifie une stratégie de sécurité.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
ALTER SECURITY POLICY schema_name.security_policy_name   
    (  
        { ADD { FILTER | BLOCK } PREDICATE tvf_schema_name.security_predicate_function_name   
           ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ]  }   
        | { ALTER { FILTER | BLOCK } PREDICATE tvf_schema_name.new_security_predicate_function_name   
             ( { column_name | arguments } [ , …n ] ) ON table_schema_name.table_name   
           [ <block_dml_operation> ] }  
        | { DROP { FILTER | BLOCK } PREDICATE ON table_schema_name.table_name }   
        | [ <additional_add_alter_drop_predicate_statements> [ , ...n ] ]  
    )    [ WITH ( STATE = { ON | OFF } ]  
    [ NOT FOR REPLICATION ]  
[;]  
  
<block_dml_operation>  
    [ { AFTER { INSERT | UPDATE } }   
    | { BEFORE { UPDATE | DELETE } } ]  
```  
  
## <a name="arguments"></a>Arguments  
 security_policy_name  
 Nom de la stratégie de sécurité. Les noms de stratégie de sécurité doivent respecter les règles applicables aux identificateurs et doivent être uniques dans la base de données et pour son schéma.  
  
 schema_name  
 Nom du schéma auquel appartient la stratégie de sécurité. *schema_name* est nécessaire en raison de la liaison de schéma.  
  
 [FILTRE | BLOC]  
 Le type de prédicat de sécurité pour la fonction liée à la table cible. Les prédicats de filtre filtrent en mode silencieux les lignes qui sont disponibles pour les opérations de lecture. BLOC de prédicats explicitement des opérations d’écriture de blocs qui violent la fonction de prédicat.  
  
 tvf_schema_name.security_predicate_function_name  
 Fonction de valeur de table inline à utiliser comme prédicat et à appliquer dans les requêtes portant sur une table cible. Au plus un prédicat de sécurité peut être défini pour une opération DML particulière sur une table donnée. La fonction de valeur de table inline doit avoir été créée à l'aide de l'option SCHEMABINDING.  
  
 { nom_colonne | arguments }  
 Le nom de la colonne ou l'expression utilisé en tant que paramètres de la fonction de prédicat de sécurité. Toutes les colonnes de la table cible peuvent être utilisées comme arguments pour la fonction de prédicat. Les expressions qui incluent des littéraux, les données prédéfinies et les expressions qui utilisent des opérateurs arithmétiques peuvent être utilisées.  
  
 *table_schema_name.TABLE_NAME*  
 Table cible à laquelle sera appliqué le prédicat de sécurité. Plusieurs stratégies de sécurité désactivées peuvent cibler une table unique pour une opération DML particulière, mais une seule peut être activée à un moment donné.  
  
 *\<block_dml_operation >*  
 L’opération DML particulière pour laquelle le prédicat de bloc est appliqué. Spécifie une fois que le prédicat est évalué sur les valeurs des lignes après que l’opération DML a été effectuée (INSERT ou UPDATE). Spécifie avant que le prédicat est évalué sur les valeurs des lignes avant l’opération DML est effectuée (mise à jour ou suppression). Si aucune opération n’est spécifiée, le prédicat s’appliquera à toutes les opérations.  
  
 Vous ne pouvez pas modifier l’opération pour laquelle un prédicat block sera appliqué, car l’opération est utilisée pour identifier de façon unique le prédicat. Au lieu de cela, vous devez supprimer le prédicat et ajouter un nouveau pour la nouvelle opération.  
  
 WITH ( STATE = { ON | OFF } )  
 Permet à la stratégie de sécurité d'appliquer ses prédicats de sécurité sur les tables cibles, ou l'empêche d'effectuer cette opération. Sauf indication contraire, la stratégie de sécurité en cours de création est désactivée.  
  
 NOT FOR REPLICATION  
 Indique que la stratégie de sécurité ne doit pas être exécutée quand un agent de réplication modifie l'objet cible. Pour plus d’informations, consultez [Contrôler le comportement de déclencheurs et de contraintes au cours de la synchronisation &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/control-behavior-of-triggers-and-constraints-in-synchronization.md).  
  
 table_schema_name.table_name  
 Table cible à laquelle sera appliqué le prédicat de sécurité. Plusieurs stratégies de sécurité désactivées peuvent cibler une même table, mais une seule peut être activée à un moment donné.  
  
## <a name="remarks"></a>Notes   
 L'instruction ALTER SECURITY POLICY fait partie de l'étendue d'une transaction. Si la transaction est restaurée, l'instruction l'est également.  
  
 Lorsque vous utilisez des fonctions de prédicat avec tables optimisées en mémoire, les stratégies de sécurité doivent inclure **SCHEMABINDING** et utiliser le **WITH NATIVE_COMPILATION** indicateur de compilation. L’argument SCHEMABINDING ne peut pas être modifié avec l’instruction ALTER car elle s’applique à tous les prédicats. Pour modifier la liaison de schéma, vous devez supprimer et recréer la stratégie de sécurité.  
  
 Les prédicats Block sont évaluées après l’exécution de l’opération DML correspondante. Par conséquent, une requête READ UNCOMMITTED permettre voir les valeurs temporaires qui seront restaurées.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation ALTER ANY SECURITY POLICY.  
  
 En outre, les autorisations suivantes sont requises pour chaque prédicat ajouté :  
  
-   Les autorisations SELECT et REFERENCES sur la fonction utilisée en tant que prédicat  
-   L'autorisation REFERENCES sur la table cible liée à la stratégie  
-   L'autorisation REFERENCES sur chaque colonne de la table cible utilisée comme arguments  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants illustrent l’utilisation de la **ALTER SECURITY POLICY** syntaxe. Pour obtenir un exemple d’un scénario de stratégie de sécurité complète, consultez [sécurité de niveau ligne](../../relational-databases/security/row-level-security.md).  
  
### <a name="a-adding-an-additional-predicate-to-a-policy"></a>A. Ajout d'un prédicat à une stratégie  
 La syntaxe suivante modifie une stratégie de sécurité, en ajoutant un prédicat de filtre sur la table `mytable`.  
  
```  
ALTER SECURITY POLICY pol1   
    ADD FILTER PREDICATE schema_preds.SecPredicate(column1)   
    ON myschema.mytable;  
```  
  
### <a name="b-enabling-an-existing-policy"></a>B. Activation d'une stratégie existante  
 L'exemple suivant utilise la syntaxe ALTER pour activer une stratégie de sécurité.  
  
```  
ALTER SECURITY POLICY pol1 WITH ( STATE = ON );  
```  
  
### <a name="c-adding-and-dropping-multiple-predicates"></a>C. Ajout et suppression de plusieurs prédicats  
 La syntaxe suivante modifie une stratégie de sécurité, en ajoutant des prédicats de filtre sur les tables `mytable1` et `mytable3` et en supprimant le prédicat de filtre sur la table `mytable2`.  
  
```  
ALTER SECURITY POLICY pol1  
ADD FILTER PREDICATE schema_preds.SecPredicate1(column1)   
    ON myschema.mytable1,  
DROP FILTER PREDICATE   
    ON myschema.mytable2,  
ADD FILTER PREDICATE schema_preds.SecPredicate2(column2, 1)   
    ON myschema.mytable3;  
```  
  
### <a name="d-changing-the-predicate-on-a-table"></a>D. Modification du prédicat sur une table  
 La syntaxe suivante change le prédicat de filtre existant sur la table mytable en fonction SecPredicate2.  
  
```  
ALTER SECURITY POLICY pol1  
    ALTER FILTER PREDICATE schema_preds.SecPredicate2(column1)  
        ON myschema.mytable;  
```  
  
### <a name="e-changing-a-block-predicate"></a>E. La modification d’un prédicat de bloc  
 Modification de la fonction de prédicat de bloc pour une opération sur une table.  
  
```  
ALTER SECURITY POLICY rls.SecPol  
    ALTER BLOCK PREDICATE rls.tenantAccessPredicate_v2(TenantId) 
    ON dbo.Sales AFTER INSERT;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [DROP SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-security-policy-transact-sql.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [Sys.security_predicates &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
