---
title: Constantes (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- bit data type
- constants [SQL Server]
- scalar values
- money data type, constants
- binary [SQL Server], constants
- float data type
- Unicode [SQL Server], constants
- constants [Transact-SQL]
- integer constants
- decimal data type, constants
- character strings [SQL Server], constants
- positive values [SQL Server]
- formats [SQL Server], constants
- datetime data type [SQL Server]
- literals [SQL Server], constants
- real data type
- negative values
ms.assetid: 58ae3ff3-b1d5-41b2-9a2f-fc7ab8c83e0e
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d9b212354492b96ca69ebf29afbc39c8ed1de6e3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="constants-transact-sql"></a>Constantes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Une constante, également appelée valeur littérale ou scalaire, est un symbole représentant une valeur de donnée spécifique. Le format d'une constante dépend du type de données dont elle représente la valeur.
  
## <a name="character-string-constants"></a>Constantes de type chaîne de caractères
Une constante de type chaîne de caractères est placée entre des guillemets simples. Elle se compose de caractères alphanumériques (a-z, A-Z et 0-9) ainsi que de caractères spéciaux tels que le point d'exclamation (!), l'arobase (@) et le dièse (#). Les constantes de type chaîne de caractères reçoivent le classement par défaut de la base de données active, sauf si la clause COLLATE est utilisée pour spécifier un classement. Les chaînes de caractères tapées par l'utilisateur sont analysées au moyen de la page de codes de l'ordinateur et sont converties, le cas échéant, dans la page de codes par défaut de la base de données.
  
Si l'option QUOTED_IDENTIFIER a été désactivée (OFF) pour une connexion, les chaînes de caractères peuvent également être placées entre des guillemets doubles. Notez que le fournisseur Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC utilisent automatiquement SET QUOTED_IDENTIFIER ON. Il est recommandé d'utiliser des guillemets simples.
  
Si un guillemet simple est inséré dans une chaîne de caractères placée entre des guillemets simples, celui-ci doit être représenté par deux guillemets simples. Ceci n'est pas nécessaire dans une chaîne insérée entre des guillemets doubles.
  
Voici des exemples de chaînes de caractères :
  
```sql
'Cincinnati'  
'O''Brien'  
'Process X is 50% complete.'  
'The level for job_id: %d should be between %d and %d.'  
"O'Brien"  
```  
  
Les chaînes vides sont représentées par deux guillemets simples, sans aucun caractère ou espace entre eux. En mode de compatibilité 6.x, une chaîne vide est traitée comme un espace simple.
  
Les constantes de chaînes de caractères prennent en charge les classements évolués.
  
> [!NOTE]  
>  Constantes supérieures à 8 000 octets sont de type de caractère **varchar (max)** données.  
  
## <a name="unicode-strings"></a>Chaînes Unicode
Une chaîne Unicode a le même format qu'une chaîne de caractères, mais celle-ci est précédée de l'identificateur N (N correspond à National Language dans la norme SQL-92). Le préfixe N doit être en majuscule. Par exemple, 'Michel' est une constante de type caractère tandis que N'Michel' est une constante Unicode. Les constantes Unicode sont interprétées comme des données Unicode et ne sont pas évaluées à l'aide d'une page de codes. Les constantes Unicode présentent un classement, qui contrôle essentiellement les comparaisons et le respect de la casse. Les constantes Unicode reçoivent le classement par défaut de la base de données active, sauf si la clause COLLATE est utilisée pour spécifier un classement. Les données Unicode sont stockées en utilisant 2 octets par caractère, alors que les données de type caractère utilisent 1 octet par caractère. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md).
  
Les constantes de chaînes Unicode prennent en charge les classements évolués.
  
> [!NOTE]  
>  Les constantes Unicode supérieures à 8 000 octets sont de type **nvarchar (max)** données.  
  
## <a name="binary-constants"></a>Constantes binaires
Une constante binaire a le préfixe `0x` et se compose d'une chaîne de nombres hexadécimaux. La chaîne n'est pas entourée de guillemets.
  
Voici des exemples de chaînes binaires :
  
```sql
0xAE  
0x12Ef  
0x69048AEFDD010E  
0x  (empty binary string)  
```  
  
> [!NOTE]  
>  Les constantes binaires supérieures à 8 000 octets sont de type **varbinary (max)** données.  
  
## <a name="bit-constants"></a>constantes de bits
**bit** constantes sont représentés par les nombres 0 ou 1 et n’est pas entourées de guillemets. Si un nombre supérieur à 1 est utilisé, il est converti en 1.
  
## <a name="datetime-constants"></a>constantes de DateTime
**DateTime** constantes sont représentées à l’aide des valeurs de date de caractère dans un format spécifique, placé entre guillemets simples.
  
Voici des exemples de **datetime** constantes :
  
```sql
'December 5, 1985'  
'5 December, 1985'  
'851205'  
'12/5/98'  
```  
  
Exemples de constantes de date/heure sont :
  
```sql
'14:30:24'  
'04:24 PM'  
```  
  
## <a name="integer-constants"></a>constantes entières
**entier** constantes sont représentées par une chaîne de nombres qui n’est pas entourée de guillemets et qui ne contient pas de décimales. **entier** les constantes doivent être des nombres entiers ; ils ne peuvent pas contenir de décimales.
  
Voici des exemples de **entier** constantes :
  
```sql
1894  
2  
```  
  
## <a name="decimal-constants"></a>constantes décimales
**décimal** constantes sont représentées par une chaîne de nombres qui n’est pas entourée de guillemets et qui contiennent une virgule décimale.
  
Voici des exemples de **décimal** constantes :
  
```sql
1894.1204  
2.0  
```  
  
## <a name="float-and-real-constants"></a>constantes de type float et real
**float** et **réel** constantes sont représentées à l’aide de la notation scientifique.
  
Voici des exemples de **float** ou **réel** valeurs :
  
```sql
101.5E5  
0.5E-2  
```  
  
## <a name="money-constants"></a>constantes monétaires
**Money** constantes sont représentés en tant que chaîne de chiffres avec un séparateur décimal facultatif et un symbole monétaire en tant que préfixe. **Money** constante ne pas entourée de guillemets.
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'impose aucune règle de regroupement, telle que l'insertion d'une virgule (,) tous les trois chiffres dans les chaînes qui représentent une valeur monétaire.
  
> [!NOTE]  
>  Virgules sont ignorées dans spécifié **money** littéral.  
  
Voici des exemples de **money** constantes :
  
```sql
$12  
$542023.14  
```  
  
## <a name="uniqueidentifier-constants"></a>constantes de type
**uniqueidentifier** constantes sont une chaîne représentant un GUID. Elles peuvent être spécifiées dans un format de chaîne de caractères ou binaire.
  
Les deux exemples ci-après spécifient le même identificateur globalement unique (GUID) :
  
```sql
'6F9619FF-8B86-D011-B42D-00C04FC964FF'  
0xff19966f868b11d0b42d00c04fc964ff  
```  
  
## <a name="specifying-negative-and-positive-numbers"></a>Définition d'un nombre négatif ou positif  
Pour indiquer si un nombre est positif ou négatif, appliquez le  **+**  ou  **-**  opérateurs unaires à une constante numérique. Ceci crée une expression numérique représentant la valeur numérique signée. Constantes numériques utilisent positif quand la  **+**  ou  **-**  opérateurs unaires ne sont pas appliquées.
  
Signé **entier** expressions :  
  
```sql
+145345234
-2147483648
```
Signé **décimal** expressions :  
  
```sql
+145345234.2234
-2147483648.10
```
  
Signé **float** expressions :  
  
```sql
+123E-3
-12E5
```
  
Signé **money** expressions :  
  
```sql
-$45.56
+$423456.99
```
  
## <a name="enhanced-collations"></a>Classements évolués  
SQL Server gère les constantes de chaînes de caractères et Unicode qui prennent en charge les classements évolués. Pour plus d’informations, consultez le [COLLATE &#40; Transact-SQL &#41; ](http://msdn.microsoft.com/library/4ba6b7d8-114a-4f4e-bb38-fe5697add4e9) clause.
  
## <a name="see-also"></a>Voir aussi
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Expressions &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[Opérateurs &#40; Transact-SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)
  
  

