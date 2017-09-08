---
title: "IDENTITY (propriété) (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IDENTITY_TSQL
- IDENTITY
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY property
- columns [SQL Server], creating
- identity columns [SQL Server], IDENTITY property
- autonumbers, identity numbers
ms.assetid: 8429134f-c821-4033-a07c-f782a48d501c
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1eb7f960210ec89a66f1307d8476e6d47494861f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-transact-sql-identity-property"></a>CRÉER la TABLE (Transact-SQL) IDENTITY (propriété)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Crée une colonne d'identité dans une table. Cette propriété est utilisée avec les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE et ALTER TABLE.  
  
> [!NOTE]  
>  La propriété IDENTITY diffère de SQL-DMO **identité** propriété qui expose la propriété d’identité de lignes d’une colonne.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IDENTITY [ (seed , increment) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *valeur initiale*  
 Valeur utilisée pour la toute première ligne chargée dans la table.  
  
 *incrément*  
 Valeur d'incrément ajoutée à la valeur d'identité de la ligne précédemment chargée.  
  
 Vous devez spécifier à la fois la valeur initiale et l'incrément, ou aucun des deux. Si vous n'en spécifiez aucun, la valeur par défaut est (1,1).  
  
## <a name="remarks"></a>Notes  
 Les colonnes d'identité peuvent être utilisées pour générer des valeurs de clé. La propriété d'identité sur une colonne garantit ce qui suit :  
  
-   Chaque nouvelle valeur est générée en fonction de la valeur et de l'incrément actuels.  
  
-   Chaque nouvelle valeur pour une transaction spécifique est différente des autres transactions simultanées sur la table.  
  
 La propriété d'identité sur une colonne ne garantit pas ce qui suit :  
  
-   **L’unicité de la valeur** – l’unicité doit être appliquée à l’aide un **clé primaire** ou **UNIQUE** contrainte ou **UNIQUE** index.  
  
-   **Valeurs consécutives au sein d’une transaction** – une insertion de plusieurs lignes de transaction n’est pas garantie pour obtenir les valeurs consécutives pour les lignes, car les autres insertions simultanées peuvent se produire sur la table. Si les valeurs doivent être consécutives, la transaction doit utiliser un verrou exclusif sur la table ou utiliser le **SERIALIZABLE** niveau d’isolation.  
  
-   **Valeurs consécutives après le redémarrage du serveur ou d’autres défaillances** –[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut mettre en cache les valeurs d’identité pour des raisons de performances et de certaines valeurs affectées peuvent être perdues lors d’un redémarrage du serveur ou d’échec de la base de données. Cela peut entraîner des intervalles de valeur d'identité à l'insertion. Si les intervalles ne sont pas acceptables, alors l'application doit utiliser son propre mécanisme pour générer des valeurs clés. À l’aide d’un générateur de séquence avec le **NOCACHE** option peut limiter les intervalles pour les transactions qui ne sont jamais validées.  
  
-   **Réutilisation des valeurs** – pour une propriété d’identité donnée avec valeur initiale/incrément spécifique, l’identité de valeurs ne sont pas réutilisés par le moteur. Si une instruction d'insertion donnée échoue, ou si l'instruction d'insertion est restaurée, alors les valeurs d'identité consommées sont perdues et ne peuvent plus être générées. Cela peut entraîner des intervalles lorsque les valeurs d'identité ultérieures sont générées.  
  
 Ces restrictions sont dues à la conception et visent à améliorer les performances, car elles sont acceptables dans la plupart des situations. Si vous ne pouvez pas utiliser les valeurs d'identité en raison de ces restrictions, créez une table distincte contenant une valeur actuelle et gérez l'accès à la table et l'affectation de numéro dans votre application.  
  
 Si une table possédant une colonne d'identité est publiée pour la réplication, la colonne doit être gérée de manière à ce qu'elle soit compatible avec le type de réplication utilisée. Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Une seule colonne d'identité peut être créée par table.  
  
 Pour les tables optimisées en mémoire, la valeur initiale et l'incrément doivent être définis à « 1,1 ». Définition de la valeur de départ ou incrément sur une valeur autre que 1 provoque l’erreur suivante : l’utilisation de départ et d’incrément valeurs autres que 1 n’est pas pris en charge avec tables optimisées en mémoire.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-the-identity-property-with-create-table"></a>A. Utilisation de la propriété IDENTITY avec CREATE TABLE  
 L'exemple crée une table avec la propriété `IDENTITY` pour incrémenter automatiquement un numéro d'identification.  
  
```  
USE AdventureWorks2012;  
  
IF OBJECT_ID ('dbo.new_employees', 'U') IS NOT NULL  
   DROP TABLE new_employees;  
GO  
CREATE TABLE new_employees  
(  
 id_num int IDENTITY(1,1),  
 fname varchar (20),  
 minit char(1),  
 lname varchar(30)  
);  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Karin', 'F', 'Josephs');  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Pirkko', 'O', 'Koskitalo');  
```  
  
### <a name="b-using-generic-syntax-for-finding-gaps-in-identity-values"></a>B. Utilisation d'une syntaxe générique afin de trouver des intervalles entre les valeurs d'identité  
 L'exemple suivant illustre une syntaxe générique qui permet de trouver des intervalles entre les valeurs d'identité lorsque des données sont supprimées.  
  
> [!NOTE]  
>  La première partie du script [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant sert uniquement d'illustration. Vous pouvez exécuter le script [!INCLUDE[tsql](../../includes/tsql-md.md)] qui commence par le commentaire : `-- Create the img table`.  
  
```  
-- Here is the generic syntax for finding identity value gaps in data.  
-- The illustrative example starts here.  
SET IDENTITY_INSERT tablename ON;  
DECLARE @minidentval column_type;  
DECLARE @maxidentval column_type;  
DECLARE @nextidentval column_type;  
SELECT @minidentval = MIN($IDENTITY), @maxidentval = MAX($IDENTITY)  
    FROM tablename  
IF @minidentval = IDENT_SEED('tablename')  
   SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('tablename')  
   FROM tablename t1  
   WHERE $IDENTITY BETWEEN IDENT_SEED('tablename') AND   
      @maxidentval AND  
      NOT EXISTS (SELECT * FROM tablename t2  
         WHERE t2.$IDENTITY = t1.$IDENTITY +   
            IDENT_INCR('tablename'))  
ELSE  
   SELECT @nextidentval = IDENT_SEED('tablename');  
SET IDENTITY_INSERT tablename OFF;  
-- Here is an example to find gaps in the actual data.  
-- The table is called img and has two columns: the first column   
-- called id_num, which is an increasing identification number, and the   
-- second column called company_name.  
-- This is the end of the illustration example.  
  
-- Create the img table.  
-- If the img table already exists, drop it.  
-- Create the img table.  
IF OBJECT_ID ('dbo.img', 'U') IS NOT NULL  
   DROP TABLE img;  
GO  
CREATE TABLE img (id_num int IDENTITY(1,1), company_name sysname);  
INSERT img(company_name) VALUES ('New Moon Books');  
INSERT img(company_name) VALUES ('Lucerne Publishing');  
-- SET IDENTITY_INSERT ON and use in img table.  
SET IDENTITY_INSERT img ON;  
  
DECLARE @minidentval smallint;  
DECLARE @nextidentval smallint;  
SELECT @minidentval = MIN($IDENTITY) FROM img  
 IF @minidentval = IDENT_SEED('img')  
    SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('img')  
    FROM img t1  
    WHERE $IDENTITY BETWEEN IDENT_SEED('img') AND 32766 AND  
      NOT    EXISTS (SELECT * FROM img t2  
          WHERE t2.$IDENTITY = t1.$IDENTITY + IDENT_INCR('img'))  
 ELSE  
    SELECT @nextidentval = IDENT_SEED('img');  
SET IDENTITY_INSERT img OFF;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [IDENTITÉ &#40; Fonction &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/identity-function-transact-sql.md)   
 [IDENT_SEED &#40; Transact-SQL &#41;](../../t-sql/functions/ident-seed-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET IDENTITY_INSERT &#40; Transact-SQL &#41;](../../t-sql/statements/set-identity-insert-transact-sql.md)   
 [Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
