---
title: uniqueidentifier (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- uniqueidentifier
- uniqueidentifier_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- uniqueidentifier data type
- globally unique identifiers [SQL Server]
- GUIDs [SQL Server]
ms.assetid: b026035b-f3d2-4d70-989d-3884b4ca0233
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 1450aa86e3f47ef27be5acd5b5410fe40dd5983e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="uniqueidentifier-transact-sql"></a>uniqueidentifier (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

GUID sur 16 octets.
  
## <a name="remarks"></a>Notes  
Une colonne ou une variable locale de **uniqueidentifier** type de données peut être initialisé à une valeur comme suit :
-   en utilisant la fonction NEWID ;  
-   En convertissant à partir d’une constante de chaîne sous la forme *xxxxxxxx*-*xxxx*-*xxxx*-*xxxx*-*xxxxxxxxxxxx*, dans lequel chaque *x* est un chiffre hexadécimal dans la plage 0-9 ou a-f. Par exemple, 6F9619FF-8B86-D011-B42D-00C04FC964FF est valide **uniqueidentifier** valeur.  
  
Opérateurs de comparaison peuvent être utilisés avec **uniqueidentifier** valeurs. Toutefois, le classement n'est pas effectué par la comparaison des configurations binaires des deux valeurs. Les seules opérations qui peuvent être effectuées par rapport à un **uniqueidentifier** valeur sont les comparaisons (=, <>, \<, >, \<=, > =) et la vérification de la valeur NULL (IS NULL et IS NOT NULL). Aucun autre opérateur arithmétique n'est admis. Toutes les contraintes de colonne et les propriétés, à l’exception d’identité, peuvent être utilisées sur le **uniqueidentifier** type de données.
  
Réplication de fusion et la réplication transactionnelle avec mise à jour des abonnements utilisation **uniqueidentifier** colonnes afin de garantir que les lignes sont identifiées unique entre plusieurs copies de la table.
  
## <a name="converting-uniqueidentifier-data"></a>Conversion de données uniqueidentifier  
Le **uniqueidentifier** type est considéré comme un type de caractère dans le cadre de la conversion à partir d’une expression de caractères et est donc soumis aux règles de troncation pour la conversion en un type de caractère. Autrement dit, lorsque des expressions de caractères sont converties en type caractère de taille différente, les valeurs trop longues pour le nouveau type de données sont tronquées. Consultez la section exemples.
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions

Ces outils et fonctionnalités ne prennent pas en charge la `uniqueidentifier` type de données :
- PolyBase
- [outil de chargement de dwloader](https://msdn.microsoft.com/sql/analytics-platform-system/dwloader) pour Parallel Data Warehouse

## <a name="examples"></a>Exemples  
L'exemple suivant convertit une valeur `uniqueidentifier` en type de données `char`.
  
```sql
DECLARE @myid uniqueidentifier = NEWID();  
SELECT CONVERT(char(255), @myid) AS 'char';  
```  
  
L'exemple suivant illustre la troncation des données lorsque la valeur est trop longue pour le type de données vers lequel la conversion est effectuée. Étant donné que la **uniqueidentifier** type est limité à 36 caractères, les caractères qui dépassent cette longueur sont tronqués.
  
```sql
DECLARE @ID nvarchar(max) = N'0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong';  
SELECT @ID, CONVERT(uniqueidentifier, @ID) AS TruncatedValue;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
String                                       TruncatedValue  
-------------------------------------------- ------------------------------------  
0E984725-C51C-4BF4-9960-E1C80E27ABA0wrong    0E984725-C51C-4BF4-9960-E1C80E27ABA0  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[NEWID &#40; Transact-SQL &#41;](../../t-sql/functions/newid-transact-sql.md)  
[NEWSEQUENTIALID &#40; Transact-SQL &#41; ](../../t-sql/functions/newsequentialid-transact-sql.md) 
 [Définir @local_variable &#40; Transact-SQL &#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)  
[Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)
  
  

