---
title: Utiliser un fichier de format pour ignorer un champ de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- format files [SQL Server], skipping data fields
- skipping data fields when importing
ms.assetid: 6a76517e-983b-47a1-8f02-661b99859a8b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bad791f1eab5fbb31976236e6d79c08e8b9adc97
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155817"
---
# <a name="use-a-format-file-to-skip-a-data-field-sql-server"></a>Utiliser un fichier de format pour ignorer un champ de données (SQL Server)
  Le nombre de champs contenus dans un fichier de données peut être supérieur au nombre de colonnes dans la table. Cette rubrique explique comment modifier les fichiers de format non-XML et XML en mappant les colonnes de la table avec les champs de données correspondants et en ignorant les champs supplémentaires afin de prendre en charge un fichier de données contenant davantage de champs.  
  
> [!NOTE]  
>  Vous pouvez utiliser un fichier de format non-XML ou XML pour importer en bloc un fichier de données dans la table à l’aide d’une commande **bcp**, d’une instruction BULK INSERT ou d’une instruction INSERT... SELECT * FROM OPENROWSET(BULK...). Pour plus d’informations, consultez [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-data-file-and-table"></a>Exemples de fichier de données et de table  
 Les fichiers de format modifiés pris en exemple dans cette rubrique sont fondés sur la table et le fichier de données suivants.  
  
### <a name="sample-table"></a>Exemple de table  
 Une table nommée `myTestSkipField` doit être créée dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sous le schéma `dbo`. Pour créer cette table, dans l’Éditeur de requêtes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipField   
   (  
   PersonID smallint,  
   FirstName nvarchar(50) ,  
   LastName nvarchar(50)   
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Fichier de données d'exemple  
 Le fichier de données, `myTestSkipField-c.dat`, contient les enregistrements suivants :  
  
```  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
1,Skipme,DataField3,DataField4  
```  
  
 Pour effectuer l'importation en bloc de données de `myTestSkipField-c.dat` dans la table `myTestSkipField`, le fichier de format doit effectuer les tâches suivantes :  
  
-   mapper le premier champ des données à la première colonne, `PersonID`;  
  
-   ignorer le deuxième champ des données ;  
  
-   mapper le troisième champ des données à la deuxième colonne, `FirstName`;  
  
-   mapper le quatrième champ des données à la troisième colonne, `LastName`.  
  
## <a name="non-xml-format-file-for-more-data-fields"></a>Fichier de format non-XML pour davantage de champs de données  
 Le fichier de format suivant, `myTestSkipField.fmt`, mappe les champs de `myTestSkipField-c.dat` aux colonnes de la table `myTestSkipField`. Ce fichier de format utilise le format de données caractères. Pour ignorer le mappage d'une colonne, vous devez attribuer à son ordre de colonne la valeur 0, à l'image de la colonne `ExtraField` dans le fichier de format.  
  
 Le fichier de format `myTestSkipField.fmt` contient les informations suivantes :  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     PersonID               ""  
2       SQLCHAR       0       100       ","    0     ExtraField             SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      2     FirstName              SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   3     LastName               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe des fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Exemples  
 Cet exemple fait appel à `INSERT ... SELECT * FROM OPENROWSET(BULK...)` et utilise le fichier de format `myTestSkipField.fmt`. Dans cet exemple, le fichier de données `myTestSkipField-c.dat` est importé en bloc dans la table `myTestSkipField`. Pour créer l'exemple de fichier de données et de table, consultez la section « Exemples de fichier de données et de table », plus haut dans cette rubrique.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
   SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.fmt'    
       ) AS t1;  
GO   
```  
  
## <a name="xml-format-file-for-more-data-fields"></a>Fichier de format XML pour davantage de champs de données  
 Le fichier de format présenté dans cet exemple est basé sur un autre fichier de format, `myTestSkipField.xml`, qui utilise un format de données de caractères et dont le nombre et l'ordre des champs correspondent exactement à ceux des colonnes de la table `myTestSkipField`. Pour afficher le contenu de ce fichier de format, consultez [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
 Le fichier de format suivant, `myTestSkipField.xml`, mappe les champs de `myTestSkipField-c.dat` aux colonnes de la table `myTestSkipField`. Ce fichier de format utilise le format de données caractères.  
  
 Le fichier de format `myTestSkipField.xml` contient les informations suivantes :  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="PersonID" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="3" NAME="FirstName" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="LastName" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
### <a name="examples"></a>Exemples  
 Cet exemple fait appel à `INSERT ... SELECT * FROM OPENROWSET(BULK...)` et utilise le fichier de format `myTestSkipField.Xml`. Dans cet exemple, le fichier de données `myTestSkipField-c.dat` est importé en bloc dans la table `myTestSkipField`. Pour créer l'exemple de fichier de données et de table, consultez la section « Exemples de fichier de données et de table », plus haut dans cette rubrique.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipField   
  SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestSkipField-c.dat',  
      FORMATFILE='C:\myTestSkipField.xml'    
       ) AS t1;  
GO  
  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe du schéma XML et pour d’autres exemples de fichiers de format XML, consultez [Fichiers de format XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Utiliser un fichier de format pour mapper les colonnes d’une table aux champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
  
