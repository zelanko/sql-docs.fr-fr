---
title: CONCAT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONCAT
- CONCAT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT function
ms.assetid: fce5a8d4-283b-4c47-95e5-4946402550d5
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 046278bb3016b39df8039a1450a58b177d2bc180
ms.contentlocale: fr-fr
ms.lasthandoff: 10/17/2017

---
# <a name="concat-transact-sql"></a>CONCAT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Retourne une chaîne qui est le résultat de la concaténation de plusieurs valeurs de chaîne. (Pour ajouter une valeur de séparation lors de la concaténation, consultez [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md).)
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CONCAT ( string_value1, string_value2 [, string_valueN ] )  
```  
  
## <a name="arguments"></a>Arguments  
*valeur_de_la_chaîne*  
Valeur de chaîne à concaténer aux autres valeurs.
  
## <a name="return-types"></a>Types de retour
Chaîne, dont la longueur et le type dépendent de l'entrée.
  
## <a name="remarks"></a>Notes  
**CONCAT** prend un nombre variable d’arguments de chaîne et les concatène en une seule chaîne. Elle nécessite un minimum de deux valeurs d'entrée ; sinon, une erreur est générée. Tous les arguments sont implicitement convertis en types chaîne et ensuite concaténés. Les valeurs NULL sont implicitement converties en chaîne vide. Si tous les arguments sont null, une chaîne vide de type **varchar**(1) est retournée. La conversion implicite en chaînes respecte les règles existantes de conversion de type de données. Pour plus d’informations sur les conversions de type de données, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
Le type de retour dépend du type des arguments. Le tableau ci-dessous illustre le mappage.
  
|Type d'entrée|Type de sortie et longueur|  
|---|---|
|Si un argument est un type système SQL-CLR, un type défini par l'utilisateur SQL-CLR ou `nvarchar(max)`|**nvarchar(max)**|  
|Sinon, si un argument est **varbinary (max)** ou **varchar (max)**|**varchar (max)** , sauf si l’un des paramètres est un **nvarchar** d’une longueur quelconque. Si, par conséquent, le résultat est **nvarchar (max)**.|  
|Sinon, si un argument est **nvarchar**(< = 4000)|**nvarchar**(< = 4000)|  
|Sinon, dans tous les autres cas|**varchar**(< = 8000) sauf si l’un des paramètres est de type nvarchar d’une longueur quelconque. Si, par conséquent, le résultat est **nvarchar (max)**.|  
  
Lorsque les arguments sont < = 4000 pour **nvarchar**, ou < = 8000 pour **varchar**, les conversions implicites peuvent affecter la longueur du résultat. D'autres types de données ont différentes longueurs lorsqu'ils sont implicitement convertis en chaînes. Par exemple, un **int** (14) a une longueur de chaîne de 12, pendant un **float** a une longueur de 32. Par conséquent, le résultat de la concaténation de deux entiers a une longueur non inférieure à 24.
  
Si aucun des arguments d'entrée n'est d'un type d'objet (LOB) pris en charge, le type de retour est tronqué à une longueur de 8000, quel que soit le type de retour. Cette troncation préserve l'espace et prend en charge l'efficacité de la génération du plan.
  
La fonction CONCAT peut être exécutée à distance sur un serveur lié qui est la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures. Pour les anciens serveurs liés, l’opération CONCAT sera exécutée localement après que les valeurs non concaténées sont retournées à partir du serveur lié.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-concat"></a>A. Utilisation de CONCAT  
  
```sql
SELECT CONCAT ( 'Happy ', 'Birthday ', 11, '/', '25' ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
-------------------------  
Happy Birthday 11/25  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-concat-with-null-values"></a>B. Utilisation de CONCAT avec des valeurs NULL  
  
```sql
CREATE TABLE #temp (  
    emp_name nvarchar(200) NOT NULL,  
    emp_middlename nvarchar(200) NULL,  
    emp_lastname nvarchar(200) NOT NULL  
);  
INSERT INTO #temp VALUES( 'Name', NULL, 'Lastname' );  
SELECT CONCAT( emp_name, emp_middlename, emp_lastname ) AS Result  
FROM #temp;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
------------------  
NameLastname  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de chaîne (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)   
  



