---
title: "SÉQUENCE de ALTER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/08/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SEQUENCE_TSQL
- ALTER SEQUENCE
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, altering
- ALTER SEQUENCE statement
ms.assetid: decc0760-029e-4baf-96c9-4a64073df1c2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 66960ed0ae27cb7ecbe2d39d0e30d1ec12dcc3cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="alter-sequence-transact-sql"></a>ALTER SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Modifie les arguments d'un objet séquence existant. Si la séquence a été créée avec la **CACHE** option, la modification de la séquence recréera le cache.  
  
 Objets séquences sont créés à l’aide de la [CREATE SEQUENCE](../../t-sql/statements/create-sequence-transact-sql.md) instruction. Les séquences sont des valeurs entières et peuvent être de tout type de données qui retourne un entier. Le type de données ne peut pas être modifié à l'aide de l'instruction ALTER SEQUENCE. Pour modifier le type de données, supprimez et créez l'objet séquence.  
  
 Une séquence est un objet lié au schéma défini par l'utilisateur qui génère une séquence de valeurs numériques d'après une spécification. De nouvelles valeurs sont générées à partir d'une séquence par appel de la fonction NEXT VALUE FOR. Utilisez **sp_sequence_get_range** pour obtenir plusieurs numéros séquentiels à la fois. Pour plus d’informations et des scénarios qui utilisent à la fois CREATE SEQUENCE, **sp_sequence_get_range**et la fonction NEXT VALUE FOR, consultez [numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER SEQUENCE [schema_name. ] sequence_name  
    [ RESTART [ WITH <constant> ] ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE <constant> } | { NO MINVALUE } ]  
    [ { MAXVALUE <constant> } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *sequence_name*  
 Spécifie le nom unique sous lequel la séquence est connue dans la base de données. Est de type **sysname**.  
  
 Redémarrez [WITH \<constante >]  
 Valeur suivante qui sera retournée par l'objet séquence. Si elle est fournie, la valeur RESTART WITH doit être un entier inférieur ou égal à la valeur maximale et supérieur ou égal à la valeur minimale de l'objet séquence. Si la valeur WITH est omise, la numérotation de séquence redémarre selon les options CREATE SEQUENCE d'origine.  
  
 INCREMENT BY \<constante >  
 Valeur utilisée pour incrémenter (ou décrémenter en cas de valeurs négatives) la valeur de base de l'objet séquence pour chaque appel à la fonction NEXT VALUE FOR. Si l'incrément est une valeur négative, l'objet séquence décroît ; sinon, il augmente. L'incrément ne peut pas être égal à 0.  
  
 [MINVALUE \<constante > | AUCUN MINVALUE]  
 Spécifie les limites de l'objet séquence. Si NO MINVALUE est spécifié, la valeur minimale possible du type de données de séquence est utilisée.  
  
 [MAXVALUE \<constante > | AUCUN MAXVALUE  
 Spécifie les limites de l'objet séquence. Si NO MAXVALUE est spécifié, la valeur maximale possible du type de données de séquence est utilisée.  
  
 [ CYCLE | NO CYCLE ]  
 Cette propriété spécifie si l'objet séquence doit redémarrer à partir de la valeur minimale (ou de la valeur maximale pour les objets séquences décroissants) ou lever une exception lorsque sa valeur minimale ou maximale est dépassée.  
  
> [!NOTE]  
>  À l'issue du cycle, la valeur suivante correspond à la valeur minimale ou à la valeur maximale, et non à la valeur START VALUE de la séquence.  
  
 [CACHE [\<constante >] | AUCUN CACHE]  
 Augmente les performances pour les applications qui utilisent des objets séquences en réduisant le nombre d'entrées/sorties requises pour rendre des valeurs générées persistantes dans les tables système.  
  
 Pour plus d’informations sur le comportement du cache, consultez [CREATE SEQUENCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-sequence-transact-sql.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la création de séquences et comment le cache de séquence est géré, consultez [CREATE SEQUENCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-sequence-transact-sql.md).  
  
 La valeur MINVALUE pour les séquences croissantes et la valeur MAXVALUE pour les séquences décroissantes ne peuvent pas être modifiées par une valeur qui n'autorise pas la valeur START WITH de la séquence. Pour modifier la valeur MINVALUE d'une séquence croissante par un nombre plus grand que la valeur START WITH ou pour modifier la valeur MAXVALUE d'une séquence décroissante par un nombre plus petit que la valeur START WITH, incluez l'argument RESTART WITH pour redémarrer la séquence à un point de votre choix compris dans la plage minimale et maximale.  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur les séquences, interrogez [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Requiert **ALTER** autorisation sur la séquence ou **ALTER** autorisation sur le schéma. Pour accorder **ALTER** autorisation sur la séquence, utilisez **ALTER ON OBJECT** au format suivant :  
  
```  
GRANT ALTER ON OBJECT::Test.TinySeq TO [AdventureWorks\Larry]  
```  
  
 La propriété d’un objet séquence peut être transférée à l’aide de la **ALTER AUTHORIZATION** instruction.  
  
### <a name="audit"></a>Audit  
 Pour auditer **ALTER SEQUENCE**, analyse le **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Exemples  
 Pour obtenir des exemples de création de séquences et à l’aide de la **NEXT VALUE FOR** afin de générer des numéros de séquence, consultez [numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
### <a name="a-altering-a-sequence"></a>A. Modification d'une séquence  
 L’exemple suivant crée un schéma nommé Test et une séquence nommée à l’aide de TestSeq les **int** type de données, avec une plage comprise entre 0 et 255. La séquence démarre à 125 et est incrémentée de 25 chaque fois qu'un nombre est généré. Étant donné que la séquence est configurée pour se répéter, lorsque la valeur dépasse la valeur maximale de 200, la séquence redémarre à la valeur minimale de 100.  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.TestSeq  
    AS int   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
GO  
```  
  
 L’exemple suivant modifie la séquence TestSeq pour avoir une plage comprise entre 0 et 255. La séquence redémarre la série de numérotation à 100 et est incrémentée de 50 chaque fois qu'un nombre est généré.  
  
```  
ALTER SEQUENCE Test. TestSeq  
    RESTART WITH 100  
    INCREMENT BY 50  
    MINVALUE 50  
    MAXVALUE 200  
    NO CYCLE  
    NO CACHE  
;  
GO  
```  
  
 Étant donné que la séquence se répète pas, le **NEXT VALUE FOR** fonction entraîne une erreur lors de la séquence dépasse 200.  
  
### <a name="b-restarting-a-sequence"></a>B. Redémarrage d'une séquence  
 L’exemple suivant crée une séquence nommée CountBy1. La séquence utilise les valeurs par défaut.  
  
```  
CREATE SEQUENCE Test.CountBy1 ;  
```  
  
 Pour générer une valeur de séquence, le propriétaire exécute ensuite l'instruction suivante :  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1  
```  
  
 La valeur retournée de -9,223,372,036,854,775,808 est la plus petite valeur possible pour le **bigint** type de données. Le propriétaire se rend compte qu’il souhaitait que la séquence démarre à 1, mais qui n’indiquait pas le **START WITH** clause lorsqu’il a créé la séquence. Pour corriger cette erreur, le propriétaire exécute l'instruction suivante.  
  
```  
ALTER SEQUENCE Test.CountBy1 RESTART WITH 1 ;  
```  
  
 Puis le propriétaire exécute une nouvelle fois l'instruction suivante pour générer un numéro séquentiel.  
  
```  
SELECT NEXT VALUE FOR Test.CountBy1;  
```  
  
 Le nombre correspond maintenant à 1, comme attendu.  
  
 La séquence de CountBy1 a été créée à l’aide de la valeur par défaut de NO CYCLE ; elle cessera de fonctionner après avoir généré le nombre 9,223,372,036,854,775,807. Les appels suivants à l'objet séquence retourneront l'erreur 11728. L'instruction suivante modifie l'objet séquence en vue d'une répétition et définit un cache de 20.  
  
```  
ALTER SEQUENCE Test.CountBy1  
    CYCLE  
    CACHE 20 ;  
  
```  
  
 Maintenant lorsque l'objet séquence atteint 9 223 372 036 854 775 807, il entame un cycle de répétition et le nombre suivant à l'issue du cycle correspond à la valeur minimale du type de données, à savoir -9 223 372 036 854 775 808.  
  
 Le propriétaire de réaliser que le **bigint** type de données utilise 8 octets chaque fois qu’il est utilisé. Le **int** type de données qui utilise 4 octets est suffisant. Toutefois, le type de données d'un objet séquence ne peut pas être modifié. Pour convertir un **int** type de données, le propriétaire doit supprimer l’objet séquence et recréer l’objet avec le type de données correct.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une séquence de &#40; Transact-SQL &#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [VALEUR suivante de &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [sp_sequence_get_range &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
