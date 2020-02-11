---
title: Émulation des enregistrements et des collections via l’UDT du CLR
description: Explique comment le Assistant Migration SQL Server (SSMA) pour Oracle utilise les types de données définis par l’utilisateur SQL Server CLR (Common Language Runtime) pour émuler les collections et les enregistrements Oracle.
authors: nahk-ivanov
ms.service: ssma
ms.devlang: sql
ms.topic: article
ms.date: 1/22/2020
ms.author: alexiva
ms.openlocfilehash: 39a7e8d59425db7ce2d7e81083012321caac35ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "76762813"
---
# <a name="emulating-records-and-collections-via-clr-udt"></a>Émulation des enregistrements et des collections via l’UDT du CLR

Cet article explique comment l’Assistant Migration SQL Server (SSMA) pour Oracle utilise les types de données définis par l’utilisateur (UDT) SQL Server CLR (Common Language Runtime) pour émuler les collections et les enregistrements Oracle.

## <a name="declaring-record-or-collection-types-and-variables"></a>Déclaration des variables et des types d’enregistrement ou de collection

SSMA crée trois UDT basés sur CLR :

* `CollectionIndexInt`
* `CollectionIndexString`
* `Record`

Le `CollectionIndexInt` type est destiné à émuler des collections indexées par un entier, `VARRAY`telles que des, des tables imbriquées et des tableaux associatifs basés sur des clés entières. Le `CollectionIndexString` type est utilisé pour les tableaux associatifs indexés par clés de caractères. La fonctionnalité d’enregistrement Oracle est émulée par `Record` le type.

Toutes les déclarations des types d’enregistrement ou de collection sont converties en cette déclaration Transact-SQL :

```sql
declare @Collection$TYPE varchar(max) = '<type definition>'
```

Voici `<type definition>` un texte descriptif qui identifie de façon unique le type PL/SQL source.

Prenons l’exemple suivant :

```sql
DECLARE
    TYPE Manager IS RECORD
    (
        mgrid integer,
        mgrname varchar2(40),
        hiredate date
    );

    TYPE Manager_table is TABLE OF Manager INDEX BY PLS_INTEGER;

    Mgr_rec Manager;
    Mgr_table_rec Manager_table;
BEGIN
    mgr_rec.mgrid := 1;
    mgr_rec.mgrname := 'Mike';
    mgr_rec.hiredate := sysdate;

    select
        empno,
        ename,
        hiredate
    BULK COLLECT INTO
        mgr_table_rec
    FROM
        emp;
END;
```

En cas de conversion à l’aide de SSMA, il deviendra le code Transact-SQL suivant :

```sql
BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) =
            ' TABLE INDEX BY INT OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'

    DECLARE
        @Mgr_rec$mgrid int,
        @Mgr_rec$mgrname varchar(40),
        @Mgr_rec$hiredate datetime2(0),
        @Mgr_table_rec dbo.CollectionIndexInt =
            dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

    SET @mgr_rec$mgrid = 1
    SET @mgr_rec$mgrname = 'Mike'
    SET @mgr_rec$hiredate = sysdatetime()

    SET @mgr_table_rec = @mgr_table_rec.RemoveAll()
    SET @mgr_table_rec =
        @mgr_table_rec.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionComplex((
                SELECT
                    CAST(EMP.EMPNO AS int) AS mgrid,
                    EMP.ENAME AS mgrname,
                    EMP.HIREDATE AS hiredate
                FROM dbo.EMP
                FOR XML PATH
            ))
        )
END
```

Ici, étant donné `Manager` que la table est associée à un index`INDEX BY PLS_INTEGER`numérique (), la déclaration T-SQL correspondante utilisée est `@CollectionIndexInt$TYPE`de type. Si la table était associée à un index de jeu de caractères `VARCHAR2`, par exemple, la déclaration T-SQL correspondante serait `@CollectionIndexString$TYPE`de type :

```sql
-- Oracle
TYPE Manager_table is TABLE OF Manager INDEX BY VARCHAR2(40);

-- SQL Server
@CollectionIndexString$TYPE varchar(max) =
    ' TABLE INDEX BY STRING OF ( RECORD ( MGRID INT , MGRNAME STRING , HIREDATE DATETIME ) )'
```

La fonctionnalité d’enregistrement Oracle est émulée par `Record` le type uniquement.

Chacun des types `CollectionIndexInt`,, `CollectionIndexString`et a une `Record`propriété `[Null]` statique qui retourne une instance vide. La `SetType` méthode est appelée pour recevoir un objet vide d’un type spécifique (comme indiqué dans l’exemple ci-dessus).

## <a name="constructor-call-conversions"></a>Conversions d’appel de constructeur

La notation de constructeur ne peut être utilisée que pour les `VARRAY`tables imbriquées et les s, donc tous les appels de `CollectionIndexInt` constructeur explicites sont convertis à l’aide du type. Les appels de constructeur vides sont `SetType` convertis via un appel appelé sur une `CollectionIndexInt`instance null de. La `[Null]` propriété retourne l’instance null. Si le constructeur contient une liste d’éléments, les appels de méthode spéciaux sont appliqués de manière séquentielle pour ajouter la valeur à la collection.

Par exemple :

```sql
-- Oracle

DECLARE
    TYPE nested_type IS TABLE OF VARCHAR2(20);
    TYPE varray_type IS VARRAY(5) OF INTEGER;

    v1 nested_type;
    v2 varray_type;
BEGIN
   v1 := nested_type('Arbitrary','number','of','strings');
   v2 := varray_type(10, 20, 40, 80, 160);
END;

-- SQL Server

BEGIN
    DECLARE
        @CollectionIndexInt$TYPE varchar(max) = ' VARRAY OF INT',
        @CollectionIndexInt$TYPE$2 varchar(max) = ' TABLE OF STRING',
        @v1 dbo.CollectionIndexInt,
        @v2 dbo.CollectionIndexInt

    SET @v1 =
        dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE$2)
            .AddString('Arbitrary')
            .AddString('number')
            .AddString('of')
            .AddString('strings')

   SET @v2 =
       dbo.CollectionIndexInt::[Null]
            .SetType(@CollectionIndexInt$TYPE)
            .AddInt(10)
            .AddInt(20)
            .AddInt(40)
            .AddInt(80)
            .AddInt(160)
END
```

## <a name="referencing-and-assigning-record-and-collection-elements"></a>Référencer et assigner des éléments d’enregistrement et de collection

Chacun des UDT possède un ensemble de méthodes qui utilisent des éléments des différents types de données. Par exemple, la `SetDouble` méthode assigne une `float(53)` valeur à l’enregistrement ou à la `GetDouble` collection et peut lire cette valeur. Voici la liste complète des méthodes :

```sql
GetCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
SetCollectionIndexInt(@key <KeyType>, @value CollectionIndexInt) returns <UDT_type>;
GetCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
SetCollectionIndexString(@key <KeyType>, @value CollectionIndexString) returns <UDT_type>;
Record GetRecord(@key <KeyType>) returns Record;
SetRecord(@key <KeyType>, @value Record) returns <UDT_type>;
GetString(@key <KeyType>) returns nvarchar(max);
SetString(@key <KeyType>, @value nvarchar(max)) returns nvarchar(max);
GetDouble(@key <KeyType>) returns float(53);
SetDouble(@key <KeyType>, @value float(53)) returns <UDT_type>;
GetDatetime(@key <KeyType>) returns datetime;
SetDatetime(@key <KeyType>, @value datetime) returns <UDT_type>;
GetVarbinary(@key <KeyType>) returns varbinary(max);
SetVarbinary(@key <KeyType>, @value varbinary(max)) returns <UDT_type>;
SqlDecimal GetDecimal(@key <KeyType>);
SetDecimal(@key <KeyType>, @value numeric) returns <UDT_type>;
GetXml(@key <KeyType>) returns xml;
SetXml(@key <KeyType>, @value xml) returns <UDT_type>;
GetInt(@key <KeyType>) returns bigint;
SetInt(@key <KeyType>, @value bigint) returns <UDT_type>;
```

Ces méthodes sont utilisées lors du référencement ou de l’assignation d’une valeur à un élément d’une collection ou d’un enregistrement.

```sql
-- Oracle
a_collection(i) := 'VALUE';

-- SQL Server
SET @a_collection = @a_collection.SetString(@i, 'VALUE');
```

Lors de la conversion d’instructions d’assignation pour des collections ou des collections multidimensionnelles avec des éléments d’enregistrement, SSMA ajoute les méthodes suivantes pour faire référence à un élément parent à l’intérieur de la méthode Set :

```sql
GetOrCreateCollectionIndexInt(@key <KeyType>) returns CollectionIndexInt;
GetOrCreateCollectionIndexString(@key <KeyType>) returns CollectionIndexString;
GetOrCreateRecord(@key <KeyType>) returns Record;
```

Par exemple, une collection d’éléments d’enregistrement est créée de la façon suivante :

```sql
-- Oracle
DECLARE
    TYPE rec_details IS RECORD (id int, name varchar2(20));
    TYPE ntb1 IS TABLE of rec_details index BY binary_integer;
    c ntb1;
BEGIN
    c(1).id := 1;
END;

-- SQL Server
DECLARE
   @CollectionIndexInt$TYPE varchar(max) =
       ' TABLE INDEX BY INT OF ( RECORD ( ID INT , NAME STRING ) )',
   @c dbo.CollectionIndexInt =
       dbo.CollectionIndexInt::[Null].SetType(@CollectionIndexInt$TYPE)

SET @c = @c.SetRecord(1, @c.GetOrCreateRecord(1).SetInt(N'ID', 1))
```

## <a name="collection-built-in-methods"></a>Méthodes intégrées de collection

SSMA utilise les méthodes UDT suivantes pour émuler les méthodes intégrées des collections PL/SQL.

Méthodes de collecte Oracle | `CollectionIndexInt`et `CollectionIndexString` équivalent
--- | ---
COUNT | `Count returns int`
Suppression | `RemoveAll() returns <UDT_type>`
SUPPRIMER (n) | `Remove(@index int) returns <UDT_type>`
SUPPRIMER (m, n) | `RemoveRange(@indexFrom int, @indexTo int) returns <UDT_type>`
EXISTS | `ContainsElement(@index int) returns bit`
ÉTENDRE | `Extend() returns <UDT_type>`
ÉTENDRE (n) | `Extend() returns <UDT_type>`
ÉTENDRE (n, i) | `ExtendDefault(@count int, @def int) returns <UDT_type>`
FIRST | `First() returns int`
LAST | `Last() returns int`
LIMIT | N/A
PRIOR | `Prior(@current int) returns int`
NEXT | `Next(@current int) returns int`
TRIM | `Trim() returns <UDT_type>`
TRIM (n) | `TrimN(@count int) returns <UDT_type>`

## <a name="bulk-collect-operation"></a>Opération de collecte en bloc

SSMA convertit les `BULK COLLECT INTO` instructions `SELECT ... FOR XML PATH` en SQL Server instruction, dont le résultat est encapsulé dans l’une des fonctions suivantes :

* `ssma_oracle.fn_bulk_collect2CollectionSimple`
* `ssma_oracle.fn_bulk_collect2CollectionComplex`

Le choix dépend du type de l’objet cible. Ces fonctions retournent des valeurs XML qui peuvent être `CollectionIndexInt`analysées par `CollectionIndexString` les types et `Record` . Une fonction `AssignData` spéciale affecte la collection XML au type défini par l’utilisateur.

SSMA reconnaît trois types d' `BULK COLLECT INTO` instructions.

### <a name="the-collection-contains-elements-with-scalar-types-and-the-select-list-contains-one-column"></a>La collection contient des éléments avec des types scalaires `SELECT` , et la liste contient une colonne

```sql
-- Oracle
SELECT column_name_1
BULK COLLECT INTO <collection_name_1>
FROM <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionSimple(
            (SELECT column_name_1 FROM <data_source> FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-record-types-and-the-select-list-contains-one-column"></a>La collection contient des éléments avec des types d’enregistrements `SELECT` , et la liste contient une colonne

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2...]
BULK COLLECT INTO
    <collection_name_1>
FROM
    <data_source>

-- SQL Server
SET @<collection_name_1> =
    @<collection_name_1>.AssignData(
        ssma_oracle.fn_bulk_collect2CollectionComplex(
            (SELECT
                column_name_1 as [collection_name_1_element_field_name_1],
                column_name_2 as [collection_name_1_element_field_name_2]
            FROM <data_source>
            FOR XML PATH)))
```

### <a name="the-collection-contains-elements-with-scalar-type-and-the-select-list-contains-multiple-columns"></a>La collection contient des éléments avec le type scalaire et `SELECT` la liste contient plusieurs colonnes

```sql
-- Oracle
SELECT
    column_name_1[, column_name_2 ...]
BULK COLLECT INTO
    <collection_name_1>[, <collection_name_2> ...]
FROM
    <data_source>

-- SQL Server
;WITH bulkC AS (
    SELECT
        column_name_1 [collection_name_1_element_field_name_1],
        column_name_2 [collection_name_1_element_field_name_2]
    FROM
        <data_source>
)
SELECT
    @<collection_name_1> =
        @<collection_name_1>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_1]
                FROM
                    bulkC
                FOR XML PATH))),
    @<collection_name_2> =
        @<collection_name_2>.AssignData(
            ssma_oracle.fn_bulk_collect2CollectionSimple(
                (SELECT
                    [collection_name_1_element_field_name_2]
                FROM bulkC
                FOR XML PATH)))
```

## <a name="select-into-record"></a>SÉLECTIONNER dans l’enregistrement

Lorsque le résultat de la requête Oracle est enregistré dans une variable d’enregistrement PL/SQL, vous avez le choix entre deux options en fonction du paramètre SSMA pour **convertir l’enregistrement en tant que liste de variables séparées** (disponibles dans le menu **Outils** , **paramètres du projet**, puis sur**conversion** **générale** -> ). Si la valeur de ce paramètre est **Oui** (valeur par défaut), SSMA ne crée pas d’instance du type d’enregistrement. Au lieu de cela, il fractionne l’enregistrement en champs constituant en créant une variable Transact-SQL distincte pour chaque champ d’enregistrement. Si le paramètre est **non**, l’enregistrement est instancié et une valeur est assignée à chaque `Set` champ à l’aide de méthodes.
