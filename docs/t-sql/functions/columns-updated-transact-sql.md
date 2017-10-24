---
title: COLUMNS_UPDATED (Transact-SQL) | Documents Microsoft
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
- COLUMNS_UPDATED_TSQL
- COLUMNS_UPDATED
dev_langs:
- TSQL
helpviewer_keywords:
- COLUMNS_UPDATED function
- testing columns
- column testing [SQL Server]
- updated columns
ms.assetid: 765fde44-1f95-4015-80a4-45388f18a42c
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8ddb7462ee985ee62efa70455d27c91a51193124
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="columnsupdated-transact-sql"></a>COLUMNS_UPDATED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne un **varbinary** modèle binaire qui indique les colonnes d’une table ou une vue qui ont été insérées ou mises à jour. COLUMNS_UPDATED est utilisé à n'importe quel endroit du corps d'un déclencheur INSERT ou UPDATE [!INCLUDE[tsql](../../includes/tsql-md.md)] pour tester si celui-ci doit exécuter certaines actions.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
COLUMNS_UPDATED ( )   
```  
  
## <a name="return-types"></a>Types de retour
**varbinary**
  
## <a name="remarks"></a>Notes  
COLUMNS_UPDATED effectue un test pour déterminer si des actions UPDATE ou INSERT sont réalisées sur plusieurs colonnes. Pour tester des tentatives UPDATE ou INSERT sur une colonne, utilisez [UPDATE()](../../t-sql/functions/update-trigger-functions-transact-sql.md).
  
COLUMNS_UPDATED retourne un ou plusieurs octets classés de la gauche vers la droite, dans chacun desquels le bit le moins significatif est le bit le plus à droite. Le bit le plus à droite de l'octet le plus à gauche représente la première colonne de la table, le suivant à gauche la deuxième colonne, et ainsi de suite. COLUMNS_UPDATED retourne plusieurs octets si la table sur laquelle le déclencheur est créé contient plus de huit colonnes, l'octet le moins significatif étant celui le plus à gauche. COLUMNS_UPDATED retourne TRUE pour toutes les colonnes des actions INSERT car les valeurs insérées dans ces colonnes sont explicites ou implicites (NULL).
  
Pour tester l'existence de mises à jour ou d'insertions dans des colonnes spécifiques, indiquez, dans la syntaxe, un opérateur au niveau du bit et un masque de bits d'entier couvrant ces colonnes. Par exemple, la table **t1** contient les colonnes **C1**, **C2**, **C3**, **C4**, et **C5**. Pour vérifier que les colonnes **C2**, **C3**, et **C4** sont tous mis à jour (avec la table **t1** possède un déclencheur UPDATE), suivent la syntaxe avec **& 14**. Pour tester si la seule colonne **C2** est mis à jour, spécifiez **& 2**.
  
COLUMNS_UPDATED peut être utilisé à n'importe quel endroit d'un déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT ou UPDATE.
  
La colonne ORDINAL_POSITION de la vue INFORMATION_SCHEMA.COLUMNS n'est pas compatible avec le modèle binaire des colonnes retournées par COLUMNS_UPDATED. Pour obtenir un modèle binaire compatible avec COLUMNS_UPDATED, référencez la propriété `ColumnID` de la fonction système `COLUMNPROPERTY` lorsque vous interrogez la vue `INFORMATION_SCHEMA.COLUMNS`, comme illustré dans l’exemple suivant :
  
```sql
SELECT TABLE_NAME, COLUMN_NAME,  
    COLUMNPROPERTY(OBJECT_ID(TABLE_SCHEMA + '.' + TABLE_NAME),  
    COLUMN_NAME, 'ColumnID') AS COLUMN_ID  
FROM AdventureWorks2012.INFORMATION_SCHEMA.COLUMNS  
WHERE TABLE_NAME = 'Person';  
```  
  
## <a name="column-sets"></a>Jeux de colonnes
Lorsqu'un jeu de colonnes est défini sur une table, la fonction COLUMNS_UPDATED présente les comportements suivants :
-   Lorsqu'une colonne membre du jeu de colonnes est mise à jour de manière explicite, le bit correspondant pour cette colonne est défini sur 1 et le bit pour le jeu de colonnes est défini sur 1.  
-   Lorsqu'un jeu de colonnes est mis à jour de manière explicite, le bit pour le jeu de colonnes est défini sur 1 et les bits pour toutes les colonnes éparses de cette table sont définis sur 1.  
-   Pour les opérations d'insertion, tous les bits sont définis sur 1.  
  
     Étant donné que les modifications apportées à un jeu de colonnes entraînent l'affectation de la valeur 1 à toutes les colonnes du jeu de colonnes, les colonnes d'un jeu de colonnes qui n'ont pas été modifiées semblent l'avoir été. Pour plus d’informations sur les jeux de colonnes, consultez [Utiliser des jeux de colonnes](../../relational-databases/tables/use-column-sets.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-columnsupdated-to-test-the-first-eight-columns-of-a-table"></a>A. Utilisation de COLUMNS_UPDATED pour tester les huit premières colonnes d'une table  
L'exemple suivant crée deux tables, `employeeData` et `auditEmployeeData`. La table `employeeData` contient les informations sensibles relatives aux salaires des employés et peut être modifiée par les membres du service des ressources humaines. Si le numéro de sécurité sociale, le salaire annuel ou le numéro de compte en banque d'un employé sont modifiés, un enregistrement d'audit est généré et inséré dans la table `auditEmployeeData`.
  
En utilisant la fonction `COLUMNS_UPDATED()`, il est possible de tester rapidement les modifications apportées aux colonnes qui contiennent les informations sensibles relatives aux employés. Vous ne pouvez utiliser `COLUMNS_UPDATED()` de cette façon que pour détecter les modifications apportées aux huit premières colonnes de la table.
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'employeeData')  
   DROP TABLE employeeData;  
IF EXISTS(SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_NAME = 'auditEmployeeData')  
   DROP TABLE auditEmployeeData;  
GO  
CREATE TABLE dbo.employeeData (  
   emp_id int NOT NULL PRIMARY KEY,  
   emp_bankAccountNumber char (10) NOT NULL,  
   emp_salary int NOT NULL,  
   emp_SSN char (11) NOT NULL,  
   emp_lname nchar (32) NOT NULL,  
   emp_fname nchar (32) NOT NULL,  
   emp_manager int NOT NULL  
   );  
GO  
CREATE TABLE dbo.auditEmployeeData (  
   audit_log_id uniqueidentifier DEFAULT NEWID() PRIMARY KEY,  
   audit_log_type char (3) NOT NULL,  
   audit_emp_id int NOT NULL,  
   audit_emp_bankAccountNumber char (10) NULL,  
   audit_emp_salary int NULL,  
   audit_emp_SSN char (11) NULL,  
   audit_user sysname DEFAULT SUSER_SNAME(),  
   audit_changed datetime DEFAULT GETDATE()  
   );  
GO  
CREATE TRIGGER dbo.updEmployeeData   
ON dbo.employeeData   
AFTER UPDATE AS  
/*Check whether columns 2, 3 or 4 have been updated. If any or all  
columns 2, 3 or 4 have been changed, create an audit record. The
bitmask is: power(2,(2-1))+power(2,(3-1))+power(2,(4-1)) = 14. To test   
whether all columns 2, 3, and 4 are updated, use = 14 instead of >0  
(below).*/
  
   IF (COLUMNS_UPDATED() & 14) > 0  
/*Use IF (COLUMNS_UPDATED() & 14) = 14 to see whether all columns 2, 3,   
and 4 are updated.*/  
      BEGIN  
-- Audit OLD record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'OLD',   
            del.emp_id,  
            del.emp_bankAccountNumber,  
            del.emp_salary,  
            del.emp_SSN  
         FROM deleted del;  
  
-- Audit NEW record.  
      INSERT INTO dbo.auditEmployeeData  
         (audit_log_type,  
         audit_emp_id,  
         audit_emp_bankAccountNumber,  
         audit_emp_salary,  
         audit_emp_SSN)  
         SELECT 'NEW',  
            ins.emp_id,  
            ins.emp_bankAccountNumber,  
            ins.emp_salary,  
            ins.emp_SSN  
         FROM inserted ins;  
   END;  
GO  
  
/*Inserting a new employee does not cause the UPDATE trigger to fire.*/  
INSERT INTO employeeData  
   VALUES ( 101, 'USA-987-01', 23000, 'R-M53550M', N'Mendel', N'Roland', 32);  
GO  
  
/*Updating the employee record for employee number 101 to change the   
salary to 51000 causes the UPDATE trigger to fire and an audit trail to   
be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_salary = 51000  
   WHERE emp_id = 101;  
GO  
SELECT * FROM auditEmployeeData;  
GO  
  
/*Updating the employee record for employee number 101 to change both   
the bank account number and social security number (SSN) causes the   
UPDATE trigger to fire and an audit trail to be produced.*/  
  
UPDATE dbo.employeeData  
   SET emp_bankAccountNumber = '133146A0', emp_SSN = 'R-M53550M'  
   WHERE emp_id = 101;  
GO  
SELECT * FROM dbo.auditEmployeeData;  
  
GO  
```  
  
### <a name="b-using-columnsupdated-to-test-more-than-eight-columns"></a>B. Utilisation de COLUMNS_UPDATED pour tester plus de huit colonnes  
Pour tester l'existence de mises à jour affectant des colonnes autres que les huit premières colonnes d'une table, utilisez la fonction `SUBSTRING` afin de tester le bit adéquat retourné par `COLUMNS_UPDATED`. L’exemple suivant vérifie les mises à jour les colonnes `3`, `5`, et `9` dans le `AdventureWorks2012.Person.Person` table.
  
```sql
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'Person.uContact2', N'TR') IS NOT NULL  
    DROP TRIGGER Person.uContact2;  
GO  
CREATE TRIGGER Person.uContact2 ON Person.Person  
AFTER UPDATE AS  
    IF ( (SUBSTRING(COLUMNS_UPDATED(),1,1) & 20 = 20)   
        AND (SUBSTRING(COLUMNS_UPDATED(),2,1) & 1 = 1) )   
    PRINT 'Columns 3, 5 and 9 updated';  
GO  
  
UPDATE Person.Person   
   SET NameStyle = NameStyle,  
      FirstName=FirstName,  
      EmailPromotion=EmailPromotion;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[Opérateurs de bits &#40; Transact-SQL &#41;](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
[CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)  
[Mise à jour &#40; &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/update-trigger-functions-transact-sql.md)
  
  

