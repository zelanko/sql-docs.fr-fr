---
title: SUBSTRING (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUBSTRING
- SUBSTRING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- portion of expression returned [SQL Server]
- part of expression returned [SQL Server]
- SUBSTRING function
- offsets [SQL Server]
- binary [SQL Server], returning part of
- expressions [SQL Server], part returned
- characters [SQL Server], returning part of
ms.assetid: a19c808f-aaf9-4a69-af59-b1a5fc3e5c4c
caps.latest.revision: 65
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f36ec82c65e5d52c2186c67033adddbf1700c4d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="substring-transact-sql"></a>SUBSTRING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne une partie d'une expression de type caractère, binaire, texte ou image dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SUBSTRING ( expression ,start , length )  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Est un **caractère**, **binaire**, **texte**, **ntext**, ou **image**[expression](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 *Démarrer*  
 Est un entier ou **bigint** expression qui spécifie où les caractères renvoyés commencent. (La numérotation est la signification de base, 1 que le premier caractère de l’expression est 1). Si *Démarrer* est inférieur à 1, l’expression retournée commence au premier caractère qui est spécifié dans *expression*. Dans ce cas, le nombre de caractères retournés est la plus grande valeur de la somme de *Démarrer* + *longueur*- 1 ou 0. Si *Démarrer* est supérieur au nombre de caractères dans l’expression de valeur, une expression de longueur nulle est retournée.  
  
 *length*  
 Est un entier positif ou **bigint** expression qui spécifie le nombre de caractères de la *expression* sera retourné. Si *longueur* est négatif, une erreur est générée et l’instruction est terminée. Si la somme des *Démarrer* et *longueur* est supérieur au nombre de caractères dans *expression*, l’expression de valeur d’entier commençant à *Démarrer* est retourné.  
  
## <a name="return-types"></a>Types de retour  
 Données de type caractère si *expression* est un des types de données caractères pris en charge. Retourne des données binaires si *expression* est un des prises en charge **binaire** des types de données. La chaîne retournée est du même type que l'expression spécifiée, sauf pour les exceptions énumérées dans le tableau suivant :  
  
|Expression spécifiée|Type de retour|  
|--------------------------|-----------------|  
|**char**/**varchar**/**texte**|**varchar**|  
|**NCHAR**/**nvarchar**/**ntext**|**nvarchar**|  
|**binaire**/**varbinary**/**image**|**varbinary**|  
  
## <a name="remarks"></a>Notes  
 Les valeurs de *Démarrer* et *longueur* doit être spécifié en nombre de caractères pour **ntext**, **char**, ou **varchar** des types de données et octets pour **texte**, **image**, **binaire**, ou **varbinary** des types de données.  
  
 Le *expression* doit être **varchar (max)** ou **varbinary (max)** lors de la *Démarrer* ou *longueur* contient une valeur supérieure à 2147483647.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Caractères supplémentaires (paires de substitution)  
 Lors de l’utilisation de classements de caractères supplémentaires (SC), les deux *Démarrer* et *longueur* comptent chaque paire de substitution dans *expression* comme un caractère unique. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-substring-with-a-character-string"></a>A. Utilisation de SUBSTRING avec une chaîne de caractères  
 L'exemple suivant illustre la manière de retourner uniquement une partie d'une chaîne de caractères. À partir de la `sys.databases` table, cette requête renvoie le système de noms de base de données dans la première colonne, la première lettre de la base de données dans la deuxième colonne et les troisième et quatrième caractères dans la dernière colonne.  
  
```  
SELECT name, SUBSTRING(name, 1, 1) AS Initial ,
SUBSTRING(name, 3, 2) AS ThirdAndFourthCharacters
FROM sys.databases  
WHERE database_id < 5;   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

|name |Initial |ThirdAndFourthCharacters|
|---|--|--|
|master  |m  |St |
|tempdb  |t  |Pack d’administration |
|model   |m  |de |
|msdb    |m  |base de données |


  
 Voici comment afficher les deuxième, troisième et quatrième caractères de la constante de chaîne `abcdef` :  
  
```  
SELECT x = SUBSTRING('abcdef', 2, 3);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x  
----------  
bcd  
  
(1 row(s) affected)
```  
  
### <a name="b-using-substring-with-text-ntext-and-image-data"></a>B. Utilisation de SUBSTRING avec des données text, ntext et image  
  
> [!NOTE]  
>  Pour exécuter les exemples suivants, vous devez installer le **pubs** base de données.  
  
 L’exemple suivant montre comment retourner les 10 premiers caractères de chaque d’un **texte** et **image** colonne de données dans le `pub_info` table de la `pubs` base de données. **texte** données sont retournées en tant que **varchar**, et **image** données sont retournées en tant que **varbinary**.  
  
```  
USE pubs;  
SELECT pub_id, SUBSTRING(logo, 1, 10) AS logo,   
   SUBSTRING(pr_info, 1, 10) AS pr_info  
FROM pub_info  
WHERE pub_id = '1756';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 pub_id logo    pr_info
------ ---------------------- ----------
1756   0x474946383961E3002500 This is sa

(1 row(s) affected)
```  
  
 L’exemple suivant montre l’effet de SUBSTRING sur les deux **texte** et **ntext** données. D'abord, cet exemple crée, dans la base de données `pubs`, une nouvelle table nommée `npub_info`. Ensuite, l'exemple crée la colonne `pr_info` dans la table `npub_info` à partir des 80 premiers caractères de la colonne `pub_info.pr_info` puis ajoute le caractère `ü` en guise de premier caractère. Enfin, un `INNER JOIN` récupère tous les numéros d’identification de serveur de publication et la `SUBSTRING` des deux le **texte** et **ntext** colonnes d’informations de serveur de publication.  
  
```  
IF EXISTS (SELECT table_name FROM INFORMATION_SCHEMA.TABLES   
      WHERE table_name = 'npub_info')  
   DROP TABLE npub_info;  
GO  
-- Create npub_info table in pubs database. Borrowed from instpubs.sql.  
USE pubs;  
GO  
CREATE TABLE npub_info  
(  
 pub_id char(4) NOT NULL  
    REFERENCES publishers(pub_id)  
    CONSTRAINT UPKCL_npubinfo PRIMARY KEY CLUSTERED,  
pr_info ntext NULL  
);  
  
GO  
  
-- Fill the pr_info column in npub_info with international data.  
RAISERROR('Now at the inserts to pub_info...',0,1);  
  
GO  
  
INSERT npub_info VALUES('0736', N'üThis is sample text data for New Moon Books, publisher 0736 in the pubs database')  
,('0877', N'üThis is sample text data for Binnet & Hardley, publisher 0877 in the pubs databa')  
,('1389', N'üThis is sample text data for Algodata Infosystems, publisher 1389 in the pubs da')  
,('9952', N'üThis is sample text data for Scootney Books, publisher 9952 in the pubs database')  
,('1622', N'üThis is sample text data for Five Lakes Publishing, publisher 1622 in the pubs d')  
,('1756', N'üThis is sample text data for Ramona Publishers, publisher 1756 in the pubs datab')  
,('9901', N'üThis is sample text data for GGG&G, publisher 9901 in the pubs database. GGG&G i')  
,('9999', N'üThis is sample text data for Lucerne Publishing, publisher 9999 in the pubs data');  
GO  
-- Join between npub_info and pub_info on pub_id.  
SELECT pr.pub_id, SUBSTRING(pr.pr_info, 1, 35) AS pr_info,  
   SUBSTRING(npr.pr_info, 1, 35) AS npr_info  
FROM pub_info pr INNER JOIN npub_info npr  
   ON pr.pub_id = npr.pub_id  
ORDER BY pr.pub_id ASC;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-substring-with-a-character-string"></a>C. Utilisation de SUBSTRING avec une chaîne de caractères  
 L'exemple suivant illustre la manière de retourner uniquement une partie d'une chaîne de caractères. À partir de la table `dbo.DimEmployee`, cette requête retourne les noms de famille dans une colonne avec seulement la première initiale des prénoms dans la seconde colonne.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUBSTRING(FirstName, 1, 1) AS Initial  
FROM dbo.DimEmployee  
WHERE LastName LIKE 'Bar%'  
ORDER BY LastName;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
LastName             Initial
-------------------- -------
Barbariol            A
Barber               D
Barreto de Mattos    P
```  
  
 L’exemple suivant montre comment retourner le deuxième, troisième et quatrième caractères de la constante de chaîne `abcdef`.  
  
```  
USE ssawPDW;  
  
SELECT TOP 1 SUBSTRING('abcdef', 2, 3) AS x FROM dbo.DimCustomer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
x
-----
bcd
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  



