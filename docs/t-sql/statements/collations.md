---
title: Classements | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATE
- COLLATE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- collations [SQL Server], COLLATE clause
- COLLATE clause
ms.assetid: 76763ac8-3e0d-4bbb-aa53-f5e7da021daa
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4192928157e3f6e534b8fb50c34e349dac3f5b8c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="collations"></a>Classements
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Clause pouvant être appliquée à la définition d'une base de données ou d'une colonne pour définir le classement, ou à une expression de chaîne de caractères pour appliquer un changement de classement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
COLLATE { <collation_name> | database_default }  
<collation_name> :: =   
     { Windows_collation_name } | { SQL_collation_name }  
```  
  
## <a name="arguments"></a>Arguments  
 *collation_name*  
 Nom du classement à appliquer à l'expression, à la définition de colonne ou à la définition de base de données. *collation_name* peut être uniquement spécifiée *Windows_collation_name* ou un *SQL_collation_name*. *collation_name* doit être une valeur littérale. *collation_name* ne peut pas être représenté par une variable ou une expression.  
  
 *Windows_collation_name* est le nom de classement pour un [nom de classement Windows](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 *SQL_collation_name* est le nom de classement pour un [nom du classement SQL Server](../../t-sql/statements/sql-server-collation-name-transact-sql.md).  
  
 Lors de l'application d'un classement au niveau de la définition de la base de données, les classements Windows Unicode seulement ne peuvent pas être utilisés avec la clause COLLATE.  
  
 **database_default**  
 Oblige la clause COLLATE à hériter du classement de la base de données active.  
  
## <a name="remarks"></a>Notes  
 La clause COLLATE peut être spécifiée à plusieurs niveaux, Ces options en question sont les suivantes :  
  
1.  la création ou modification d'une base de données ;  
  
     Vous pouvez utiliser la clause COLLATE de l'instruction CREATE DATABASE ou ALTER DATABASE pour spécifier le classement par défaut de la base de données. Vous pouvez également spécifier un classement lorsque vous créez une base de données à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si vous ne spécifiez pas de classement, le classement par défaut de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera appliqué à la base de données.  
  
    > [!NOTE]  
    >  Classements Windows Unicode seulement peuvent uniquement être utilisée avec la clause COLLATE pour appliquer des classements pour les **nchar**, **nvarchar**, et **ntext** des types de données sur les données au niveau des colonnes et de niveau expression ; ils ne peut pas être utilisés avec la clause COLLATE pour modifier le classement d’une instance de serveur ou de base de données.  
  
2.  la création ou modification d'une colonne dans une table ;  
  
     Vous pouvez spécifier des classements pour chaque colonne de chaîne de caractères à l'aide de la clause COLLATE de l'instruction CREATE TABLE ou ALTER TABLE. Vous pouvez également spécifier un classement lorsque vous créez une table à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si vous ne spécifiez pas de classement, le classement par défaut de la base de données sera appliqué à la colonne.  
  
     Vous pouvez également utiliser le `database_default` option dans la clause COLLATE pour spécifier qu’une colonne dans une table temporaire utilise le classement par défaut de la base de données utilisateur actuel pour la connexion à la place de **tempdb**.  
  
3.  la conversion du classement d'une expression.  
  
     Vous pouvez utiliser la clause COLLATE pour appliquer une expression de caractère à un classement particulier. Le classement par défaut de la base de données active est attribué aux constantes et aux variables de caractères. Le classement des définitions de la colonne est affecté aux références de colonnes.  
  
 Le classement d'un identificateur dépend du niveau auquel il est défini. Le classement par défaut de l'instance est assigné aux identificateurs d'objets qui sont au niveau de l'instance, tels que les noms de connexion et de base de données. Le classement par défaut de la base de données est assigné aux identificateurs d'objets qui appartiennent à la base de données, tels que les noms des tables, des vues et des colonnes. Par exemple, deux tables dont les noms diffèrent uniquement au niveau de la casse peuvent être créées dans une base de données dont le classement respecte les majuscules/minuscules, mais pas dans une base de données dont le classement ne distingue pas les majuscules des minuscules. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).  
  
 Les variables, étiquettes GOTO, procédures stockées temporaires et tables temporaires peuvent être créées lorsque le contexte de la connexion est associé à une base de données, puis référencées lorsque le contexte est associé à une autre base de données. Les identificateurs des variables, étiquettes GOTO, procédures stockées temporaires et tables temporaires se trouvent dans le classement par défaut de l'instance du serveur.  
  
 La clause COLLATE peut être appliquée uniquement pour le **char**, **varchar**, **texte**, **nchar**, **nvarchar**, et **ntext** des types de données.  
  
 COLLATE utilise *collate_name* pour faire référence au nom de classement SQL Server ou le classement Windows à appliquer à l’expression, la définition de colonne ou la définition de la base de données. *collation_name* peut être uniquement spécifiée *Windows_collation_name* ou un *SQL_collation_name* et le paramètre doit contenir une valeur littérale. *collation_name* ne peut pas être représenté par une variable ou une expression.  
  
 Les classements sont généralement identifiés par un nom de classement, hormis dans le programme d'installation. Dans le programme d'installation, vous spécifiez à la place l'indicateur du classement de la racine (les paramètres régionaux de classement) pour les classements Windows, puis spécifiez des options de tri qui respectent ou non la casse et les accents.  
  
 Vous pouvez exécuter la fonction système [fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) pour récupérer une liste de tous les noms de classement valide pour les classements Windows et SQL Server :  
  
```  
SELECT name, description  
FROM fn_helpcollations();  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut prendre en charge que les pages de codes qui sont prises en charge par le système d'exploitation sous-jacent. Lorsque vous effectuez une action qui dépend de classements, le classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par l'objet référencé doit utiliser une page de codes prise en charge par le système d'exploitation exécuté sur l'ordinateur. Ces actions sont notamment les suivantes :  
  
-   l'indication d'un classement par défaut d'une base de données lorsque vous créez ou modifiez cette dernière ;  
  
-   l'indication d'un classement d'une colonne lorsque vous créez ou modifiez une table ;  
  
-   Lors de la restauration ou attachement d’une base de données, le classement par défaut de la base de données et le classement de n’importe quel **char**, **varchar**, et **texte** colonnes ou des paramètres dans la base de données doivent être pris en charge par le système d’exploitation.  
  
     Traductions de page de codes sont prises en charge pour **char** et **varchar** des types de données, mais pas pour **texte** type de données. La perte de données lors de la traduction d'une page de codes n'est pas mentionnée.  
  
 Si le classement spécifié ou le classement utilisé par l’objet référencé utilise une page de codes non prise en charge par Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche une erreur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-specifying-collation-during-a-select"></a>A. Spécification d'un classement pendant une sélection  
 L'exemple suivant crée une table simple et insère 4 lignes. Il applique ensuite deux classements lors de la sélection de données de la table, montrant comment `Chiapas` est trié différemment.  
  
```tsql  
CREATE TABLE Locations  
(Place varchar(15) NOT NULL);  
GO  
INSERT Locations(Place) VALUES ('Chiapas'),('Colima')  
                             , ('Cinco Rios'), ('California');  
GO  
--Apply an typical collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Latin1_General_CS_AS_KS_WS ASC;  
GO  
-- Apply a Spanish collation  
SELECT Place FROM Locations  
ORDER BY Place  
COLLATE Traditional_Spanish_ci_ai ASC;  
GO  
```  

 Voici les résultats de la première requête.  
  
 ```
 Place 
 ------------- 
 California 
 Chiapas 
 Cinco Rios 
 Colima
 ```  
  
 Voici les résultats de la seconde requête.  
  
 ```
 Place 
 ------------- 
 California 
 Cinco Rios 
 Colima 
 Chiapas
 ```  
  
### <a name="b-additional-examples"></a>B. Exemples supplémentaires  
 Pour obtenir des exemples supplémentaires qui utilisent **COLLATE**, consultez [CREATE DATABASE &#40; SQL Server Transact-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md) exemple **g. création d’une base de données et en spécifiant un nom de classement et les options**, et [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md) exemple **V. modification de classement de colonne**.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Priorité de classement &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [Constantes &#40; Transact-SQL &#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [table &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)  
  
  
