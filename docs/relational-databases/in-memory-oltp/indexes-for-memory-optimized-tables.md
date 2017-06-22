---
title: "Index pour les tables optimisées en mémoire | Microsoft Docs"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eecc5821-152b-4ed5-888f-7c0e6beffed9
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b468f44444a9c6cc031ea892f44849db401e0ab7
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="indexes-for-memory-optimized-tables"></a>Index pour les tables optimisées en mémoire
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  
Cet article décrit les types d’index qui sont disponibles pour une table optimisée en mémoire. L’article :  
  
- fournit de courts exemples de code pour illustrer la syntaxe Transact-SQL ;  
- décrit comment les index optimisés en mémoire diffèrent des index sur disque classiques ;  
- décrit les conditions optimales pour chaque type d’index optimisé en mémoire.  
  
  
Les index de*hachage* sont abordés plus en détail dans un [article spécifique](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md).  
  
  
Les index*columnstore* sont abordés dans un [autre article](~/relational-databases/indexes/columnstore-indexes-overview.md).  
  
  
## <a name="a-syntax-for-memory-optimized-indexes"></a>A. Syntaxe des index optimisés en mémoire  
  
Chaque instruction CREATE TABLE pour une table optimisée en mémoire doit inclure entre 1 et 8 clauses pour déclarer des index. Le type d’index doit être l’un des suivants :  
  
- Index de hachage.  
- Index non cluster, ce qui désigne la structure interne par défaut d’un arbre B (B-tree).  
  
  
Pour être déclarée avec DURABILITY = SCHEMA_AND_DATA (paramètre par défaut), la table optimisée en mémoire doit avoir une clé primaire. La clause PRIMARY KEY NONCLUSTERED dans l’instruction CREATE TABLE suivante répond à deux conditions :  
  
- Elle fournit un index pour satisfaire à la condition minimale d’un index dans l’instruction CREATE TABLE.  
- Elle fournit la clé primaire qui est requise pour la clause SCHEMA_AND_DATA.  
  
  
  
    CREATE TABLE SupportEvent  
    (  
        SupportEventId   int NOT NULL  
            PRIMARY KEY NONCLUSTERED,  
        ...  
    )  
        WITH (  
            MEMORY_OPTIMIZED = ON,  
            DURABILITY = SCHEMA_AND_DATA);  
  
  
  
### <a name="a1-code-sample-for-syntax"></a>A.1 Exemple de code pour la syntaxe  
  
Cette sous-section contient un bloc de code Transact-SQL qui illustre la syntaxe pour créer plusieurs index sur une table optimisée en mémoire. Le code illustre les opérations suivantes :  
  
  
1. Créer une table optimisée en mémoire.  
2. Utiliser des instructions ALTER TABLE pour ajouter deux index.  
3. Ajouter quelques lignes de données avec INSERT.  
  
  
  
    DROP TABLE IF EXISTS SupportEvent;  
    go  
  
    CREATE TABLE SupportEvent  
    (  
      SupportEventId   int               not null   identity(1,1)  
        PRIMARY KEY NONCLUSTERED,  
  
      StartDateTime        datetime2     not null,  
      CustomerName         nvarchar(16)  not null,  
      SupportEngineerName  nvarchar(16)      null,  
      Priority             int               null,  
      Description          nvarchar(64)      null  
    )  
      WITH (  
        MEMORY_OPTIMIZED = ON,  
        DURABILITY = SCHEMA_AND_DATA);  
    go  
      
        --------------------  
      
    ALTER TABLE SupportEvent  
      ADD CONSTRAINT constraintUnique_SDT_CN  
        UNIQUE NONCLUSTERED (StartDateTime DESC, CustomerName);  
    go  
  
    ALTER TABLE SupportEvent  
      ADD INDEX idx_hash_SupportEngineerName  
        HASH (SupportEngineerName) WITH (BUCKET_COUNT = 64);  -- Nonunique.  
    go  
      
        --------------------  
      
    INSERT INTO SupportEvent  
        (StartDateTime, CustomerName, SupportEngineerName, Priority, Description)  
      VALUES  
        ('2016-02-25 13:40:41:123', 'Abby', 'Zeke', 2, 'Display problem.'     ),  
        ('2016-02-25 13:40:41:323', 'Ben' , null  , 1, 'Cannot find help.'    ),  
        ('2016-02-25 13:40:41:523', 'Carl', 'Liz' , 2, 'Button is gray.'      ),  
        ('2016-02-25 13:40:41:723', 'Dave', 'Zeke', 2, 'Cannot unhide column.');  
    go  
  
  
  
## <a name="b-nature-of-memory-optimized-indexes"></a>B. Nature des index optimisés en mémoire  
  
Sur une table optimisée en mémoire, chaque index est également optimisé en mémoire. Il existe plusieurs différences entre un index sur un index optimisé en mémoire et un index classique sur une table sur disque.  
  
Chaque index optimisé en mémoire existe uniquement dans la mémoire active. L’index n’a aucune représentation sur le disque.  
  
- Les index optimisés en mémoire sont reconstruits quand la base de données est remise en ligne.  
  
  
Quand une instruction SQL UPDATE modifie des données dans une table optimisée en mémoire, les modifications correspondantes apportées à ses index ne sont pas écrites dans le journal.  
  
  
Les entrées dans un index optimisé en mémoire contiennent une adresse mémoire directe vers la ligne dans la table.  
  
- En revanche, les entrées dans un index d’arbre B classique sur disque contiennent une valeur de clé que le système doit d’abord utiliser pour rechercher l’adresse mémoire vers la ligne de table associée.  
  
  
Les index optimisés en mémoire n’ont aucune page fixe contrairement aux index sur disque.  
  
- Ne contribuant pas au type traditionnel de fragmentation dans une page, ils ne présentent aucun facteur de remplissage.  
  
## <a name="c-duplicate-index-key-values"></a>C. Valeurs de clé d’index dupliquées

Les valeurs de clés d’index dupliquées peuvent affecter les performances des opérations sur les tables optimisées en mémoire. Un nombre élevé de doublons (par exemple, 100 et au-delà) rend inefficace la tâche de maintenance des index, car les chaînes en double doivent être parcourues pour la plupart des opérations d’index. L’impact peut être observé dans les opérations INSERT, UPDATE et DELETE sur les tables optimisées en mémoire. Ce problème est plus visible dans le cas des index de hachage, en raison du coût par opération inférieur pour les index de hachage et de l’interférence des chaînes en double volumineuses avec la chaîne de collision de hachage. Pour réduire la duplication dans un index, utilisez un index non cluster et ajoutez des colonnes (par exemple à partir de la clé primaire) à la fin de la clé d’index pour réduire le nombre de doublons.

Considérons, par exemple, une table Clients avec une clé primaire sur le CustomerId et un index sur la colonne CustomerCategoryID. Une catégorie donnée comprend généralement de nombreux clients et, donc, de nombreuses valeurs en double pour une clé donnée dans le CustomerCategoryID. Dans ce scénario, une bonne pratique consiste à utiliser un index non cluster (CustomerCategoryID, CustomerId). Cet index peut être utilisé pour les requêtes qui utilisent un prédicat impliquant le CustomerCategoryID. Il ne contient pas de doublons et n’altère donc pas la maintenance d’index.

La requête suivante affiche le nombre moyen d’index de doublons de valeurs de clé d’index sur `CustomerCategoryID` dans la table `Sales.Customers`, dans l’exemple de base de données [WideWorldImporters](https://msdn.microsoft.com/library/mt734199(v=sql.1).aspx).

```Transact-SQL
    SELECT AVG(row_count) FROM
       (SELECT COUNT(*) AS row_count 
        FROM Sales.Customers
        GROUP BY CustomerCategoryID) a
```

Pour évaluer le nombre moyen de doublons de clé d’index de votre propre table et de votre propre index, remplacez `Sales.Customers` par votre nom de table et remplacez `CustomerCategoryID` par la liste de colonnes de clé d’index.

## <a name="d-comparing-when-to-use-each-index-type"></a>D. Comparaison des utilisations de chaque type d’index  
  
  
La nature de vos requêtes particulières détermine le type d’index le mieux approprié.  

Quand vous implémentez des tables optimisées en mémoire dans une application existante, la recommandation générale consiste à commencer avec des index non cluster, dont les fonctionnalités rappellent celles des index cluster et non cluster traditionnels sur les tables sur disque. 
  
  
### <a name="d1-strengths-of-nonclustered-indexes"></a>D.1 Avantages des index non cluster  
  
  
Un index non cluster est préférable à un index de hachage dans les cas suivants :  
  
- Les requêtes ont une clause ORDER BY sur la colonne indexée.  
- Requêtes où seule(s) la (les) colonne(s) de début d’un index sur plusieurs colonnes est (sont) testée(s).  
- Les requêtes testent la colonne indexée à l’aide d’une clause WHERE avec :  
  - Une inégalité : *WHERE StatusCode != 'Done'*  
  - Une plage de valeurs : *WHERE Quantity >= 100*  
  
  
Dans toutes les instructions SELECT suivantes, un index non cluster est préférable à un index de hachage :  
  
  
  
    SELECT col2 FROM TableA  
        WHERE StartDate > DateAdd(day, -7, GetUtcDate());  
      
    SELECT col3 FROM TableB  
        WHERE ActivityCode != 5;  
      
    SELECT StartDate, LastName  
        FROM TableC  
        ORDER BY StartDate;  
      
    SELECT IndexKeyColumn2  
        FROM TableD  
        WHERE IndexKeyColumn1 = 42;  
  
  
  
### <a name="d2-strengths-of-hash-indexes"></a>D.2 Avantages des index de hachage  
  
  
Un [index de hachage](../../relational-databases/in-memory-oltp/hash-indexes-for-memory-optimized-tables.md) est préférable à un index non cluster dans les cas suivants :  
  
- Les requêtes testent les colonnes indexées à l’aide d’une clause WHERE avec une égalité exacte sur toutes les colonnes de clés d’index, comme dans le code suivant :  
  
  
  
    SELECT col9 FROM TableZ  
        WHERE Z_Id = 2174;  
  
  
  
### <a name="d3-summary-table-to-compare-index-strengths"></a>D.3 Tableau de synthèse pour comparer les avantages des différents index  
  
  
Le tableau suivant répertorie toutes les opérations qui sont prises en charge par les différents types d’index.  
  
  
| Opération | Index optimisé en mémoire, <br/> hachage | Index optimisé en mémoire, <br/> non-cluster | Index sur disque, <br/> (non) cluster |  
| :-------- | :--------------------------- | :----------------------------------- | :------------------------------------ |  
| Analyse d'index, récupère toutes les lignes de la table. | Oui | Oui | Oui |  
| Recherche d’index sur les prédicats d’égalité (=). | Oui <br/> (Une clé complète est requise.) | Oui  | Oui |  
| Recherche d’index sur les prédicats d’inégalité et de plage <br/> (>, <, <=, >=, BETWEEN). | Non <br/> (Résultats dans une analyse d’index) | Oui | Oui |  
| Récupérer les lignes selon un ordre de tri qui correspond à la définition d’index. | Non | Oui | Oui |  
| Récupérer les lignes selon un ordre de tri inverse par rapport à la définition d’index. | Non | Non | Oui |  
  
  
Dans le tableau, Oui signifie que l’index peut traiter efficacement la demande et Non signifie que l’index ne peut pas traiter efficacement la demande.  

