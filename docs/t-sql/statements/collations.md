---
title: COLLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATE
- COLLATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], COLLATE clause
- COLLATE clause
ms.assetid: 76763ac8-3e0d-4bbb-aa53-f5e7da021daa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fcdc1c5cdc4dcbb7eb81236a1bb907d929aee5e0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63051545"
---
# <a name="collate-transact-sql"></a>COLLATE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Définit un classement pour une colonne de base de données ou de table, ou un cast de classement lors d’une application à une expression de chaîne de caractères. Le nom du classement peut être un nom de classement Windows ou SQL. Si aucun classement n’est spécifié pendant la création de la base de données, le classement par défaut de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est attribué à la base de données. Si aucun classement n’est spécifié pendant la création d’une colonne de table, le classement par défaut de la base de données est attribué à la colonne.

![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntaxe

```
COLLATE { <collation_name> | database_default }
<collation_name> :: =
    { Windows_collation_name } | { SQL_collation_name }
```

## <a name="arguments"></a>Arguments

*collation_name* Nom du classement à appliquer à l’expression, à la définition de colonne ou à la définition de base de données. *collation_name* peut uniquement être un *Windows_collation_name* ou un *SQL_collation_name*. *collation_name* doit être une valeur littérale. *collation_name* ne peut pas être représenté par une variable ou une expression.

*Windows_collation_name* est le nom de classement d’un [Windows Collation Name](../../t-sql/statements/windows-collation-name-transact-sql.md).

*SQL_collation_name* est le nom de classement d’un [SQL Server Collation Name](../../t-sql/statements/sql-server-collation-name-transact-sql.md).

**database_default** Oblige la clause COLLATE à hériter du classement de la base de données active.

## <a name="remarks"></a>Notes

La clause COLLATE peut être spécifiée à plusieurs niveaux, Ces options en question sont les suivantes :

1. la création ou modification d'une base de données ;

    Vous pouvez utiliser la clause COLLATE de l’instruction `CREATE DATABASE` ou `ALTER DATABASE` pour spécifier le classement par défaut de la base de données. Vous pouvez également spécifier un classement lorsque vous créez une base de données à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si vous ne spécifiez pas de classement, le classement par défaut de l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sera appliqué à la base de données.

    > [!NOTE]
    > Les classements Unicode Windows ne peuvent être utilisés qu’avec la clause COLLATE pour appliquer des classements aux types de données **nchar**, **nvarchar** et **ntext** au niveau des colonnes et au niveau des expressions. Ils ne peuvent pas être utilisés avec la clause COLLATE pour définir ou changer le classement d’une instance de base de données ou de serveur.

2. la création ou modification d'une colonne dans une table ;

    Vous pouvez spécifier des classements pour chaque colonne de chaîne de caractères à l’aide de la clause COLLATE de l’instruction `CREATE TABLE` ou `ALTER TABLE`. Vous pouvez également spécifier un classement lorsque vous créez une table à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Si vous ne spécifiez pas de classement, le classement par défaut de la base de données sera appliqué à la colonne.

    Vous pouvez également utiliser l’option `database_default` dans la clause COLLATE pour spécifier qu’une colonne d’une table temporaire utilise le classement par défaut de la base de données utilisateur active pour la connexion au lieu de la base de données **tempdb**.

3. la conversion du classement d'une expression.

    Vous pouvez utiliser la clause COLLATE pour appliquer une expression de caractère à un classement particulier. Le classement par défaut de la base de données active est attribué aux constantes et aux variables de caractères. Le classement des définitions de la colonne est affecté aux références de colonnes.

Le classement d'un identificateur dépend du niveau auquel il est défini. Le classement par défaut de l'instance est assigné aux identificateurs d'objets qui sont au niveau de l'instance, tels que les noms de connexion et de base de données. Le classement par défaut de la base de données est assigné aux identificateurs d'objets qui appartiennent à la base de données, tels que les noms des tables, des vues et des colonnes. Par exemple, deux tables dont les noms diffèrent uniquement au niveau de la casse peuvent être créées dans une base de données dont le classement respecte les majuscules/minuscules, mais pas dans une base de données dont le classement ne distingue pas les majuscules des minuscules. Pour plus d'informations, consultez [Database Identifiers](../../relational-databases/databases/database-identifiers.md).

Les variables, étiquettes GOTO, procédures stockées temporaires et tables temporaires peuvent être créées lorsque le contexte de la connexion est associé à une base de données, puis référencées lorsque le contexte est associé à une autre base de données. Les identificateurs des variables, étiquettes GOTO, procédures stockées temporaires et tables temporaires se trouvent dans le classement par défaut de l'instance du serveur.

La clause COLLATE peut être appliquée uniquement pour les types de données **char**, **varchar**, **text**, **nchar**, **nvarchar** et **ntext**.

COLLATE utilise *collate_name* pour faire référence au nom du classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou du classement Windows à appliquer à l’expression, à la définition de colonne ou à la définition de base de données. *collation_name* peut uniquement être un *Windows_collation_name* ou un *SQL_collation_name*, et le paramètre doit contenir une valeur littérale. *collation_name* ne peut pas être représenté par une variable ou une expression.

Les classements sont généralement identifiés par un nom de classement, hormis dans le programme d'installation. Dans le programme d’installation, vous spécifiez à la place l’indicateur du classement de la racine (les paramètres régionaux de classement) pour les classements Windows, puis vous spécifiez des options de tri qui respectent, ou non, la casse et les accents.

Vous pouvez exécuter la fonction système [fn_helpcollations](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md) pour récupérer la liste de tous les noms de classement valides pour les classements Windows et les classements SQL Server autorisés :

```sql
SELECT name, description
FROM fn_helpcollations();
```

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut prendre en charge que les pages de codes qui sont prises en charge par le système d'exploitation sous-jacent. Lorsque vous effectuez une action qui dépend de classements, le classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisé par l'objet référencé doit utiliser une page de codes prise en charge par le système d'exploitation exécuté sur l'ordinateur. Ces actions sont notamment les suivantes :

- l'indication d'un classement par défaut d'une base de données lorsque vous créez ou modifiez cette dernière ;
- l'indication d'un classement d'une colonne lorsque vous créez ou modifiez une table ;
- Lors de la restauration ou de l’attachement d’une base de données, le classement par défaut de cette dernière et le classement de colonnes ou paramètres **char**, **varchar** et **text** de la base de données doivent être pris en charge par le système d’exploitation.

> [!NOTE]
> Le classement du serveur d’instance managée [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] est **SQL_Latin1_General_CP1_CI_AS** et ne peut pas être modifié.
>
> Les traductions de pages de codes sont prises en charge pour les types de données **char** et **varchar**, mais pas pour **text**. La perte de données lors de la traduction d'une page de codes n'est pas mentionnée.
>
> Si le classement spécifié ou utilisé par l’objet référencé utilise une page de codes qui n’est pas prise en charge par Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche une erreur.

## <a name="examples"></a>Exemples

### <a name="a-specifying-collation-during-a-select"></a>A. Spécification d’un classement pendant une opération SELECT

L'exemple suivant crée une table simple et insère 4 lignes. Il applique ensuite deux classements lors de la sélection de données de la table, montrant comment `Chiapas` est trié différemment.

```sql
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

### <a name="b-additional-examples"></a>B. Autres exemples

Pour voir d’autres exemples d’utilisation de **COLLATE**, consultez l’exemple **G. Créer une base de données et spécifier un nom et des options de classement** de la rubrique [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017#examples) et l’exemple **V. Modifier le classement des colonnes** de la rubrique [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md#alter_column).

## <a name="see-also"></a>Voir aussi

- [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)
- [Prise en charge d'Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md)
- [Priorité de classement](../../t-sql/statements/collation-precedence-transact-sql.md)
- [Constantes](../../t-sql/data-types/constants-transact-sql.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md?view=sql-server-2017)
- [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)
- [DECLARE @local_variable](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
- [Type de données de table](../../t-sql/data-types/table-transact-sql.md)
