---
title: Utiliser un fichier de format pour mapper les colonnes d’une table aux champs d’un fichier de données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- mapping columns to fields during import [SQL Server]
- format files [SQL Server], mapping columns to fields
ms.assetid: e7ee4f7e-24c4-4eb7-84d2-41e57ccc1ef1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd08aaa50f307d107a55c838395677e5692914ba
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66011743"
---
# <a name="use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server"></a>Utiliser un fichier de format pour mapper les colonnes d'une table aux champs d'un fichier de données (SQL Server)
  Il se peut que les champs d'un fichier de données ne soient pas dans le même ordre que les colonnes correspondantes présentes dans la table. Cette rubrique présente les fichiers de format XML et non-XML ayant été modifiés de sorte à accepter un fichier de données dont les champs sont organisés dans un ordre différent de celui des colonnes de la table correspondante. Le fichier de format modifié permet de mapper les champs de données sur les colonnes correspondantes de la table.  
  
> [!NOTE]  
>  Vous pouvez utiliser un fichier de format XML ou non XML pour procéder à l’importation en bloc d’un fichier de données dans la table à l’aide d’une commande **bcp**, d’une instruction BULK INSERT ou d’une instruction INSERT ... SELECT * FROM OPENROWSET(BULK...). Pour plus d’informations, consultez [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Exemples de table et de fichier de données  
 Les fichiers de format modifiés pris en exemple dans cette rubrique sont fondés sur la table et le fichier de données suivants.  
  
### <a name="sample-table"></a>Exemple de table  
 Dans les exemples de cette rubrique, une table nommée `myTestOrder` doit être créée dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sous le schéma `dbo` . Pour créer cette table, dans l'Éditeur de requêtes [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestOrder   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) ,  
   Col3 nvarchar(50) ,   
   Col4 nvarchar(50)   
   );  
GO  
  
```  
  
### <a name="data-file"></a>Fichier de données  
 Le fichier de données, `myTestOrder-c.txt`, contient les enregistrements suivants :  
  
```  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
DataField3,DataField2,1,DataField4  
  
```  
  
 Pour importer des données en bloc depuis `myTestSkipCol2-c.dat` dans la table `myTestSkipCol`, le fichier de format doit mapper le premier champ de données à `Col3`, le deuxième champ à `Col2`, le troisième champ à `Col1`, et le quatrième champ à `Col4`.  
  
## <a name="using-a-non-xml-format-file"></a>Utilisation d'un fichier de format non-XML  
 Pour modifier l'ordre d'un mappage de colonne, vous devez modifier la valeur d'ordre de la colonne afin d'indiquer la position du champ de données correspondant.  
  
 L'exemple suivant présente un fichier de format non-XML, `myTestOrder.fmt`, qui mappe les champs de `myTestOrder-c.txt` aux colonnes de la table `myTestOrder`. Pour plus d'informations sur la table et le fichier de données et la manière de les créer, consultez la section « Exemples de fichier de données et de table », plus haut dans cette rubrique. Ce fichier de format utilise le format de données caractères.  
  
 Le fichier de format contient les informations suivantes :  
  
```  
9.0  
4  
1       SQLCHAR       0       100     ","     3     Col3               SQL_Latin1_General_CP1_CI_AS  
2       SQLCHAR       0       100     ","     2     Col2               SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       7       ","     1     Col1               ""  
4       SQLCHAR       0       100     "\r\n"  4     Col4               SQL_Latin1_General_CP1_CI_AS  
  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la structure des fichiers de format non-XML, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant utilise une instruction `BULK INSERT` pour procéder à l'importation en bloc de données issues du fichier de données `myTestOrder-c.txt` vers l'exemple de table `myTestOrder` à l'aide du fichier de format non-XML `myTestOrder.fmt`.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestOrder  
FROM 'C:\myTestOrder-c.txt'   
WITH (formatfile='C:\myTestOrder.fmt');  
GO  
  
```  
  
## <a name="using-an-xml-format-file"></a>Utilisation d'un fichier de format XML  
 L'exemple suivant présente un fichier de format non-XML, `myTestOrder.xml`, qui mappe les champs de `myTestOrder-c.txt` sur les colonnes de la table `myTestOrder`. Pour plus d'informations sur la création du fichier de données et de la table, consultez « Exemples de table et de fichier de données » plus haut dans cette rubrique.  
  
 Le fichier de format `myTestOrder.xml` contient les informations suivantes :  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format"   
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="3" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="1" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la syntaxe du schéma XML et pour d’autres exemples de fichiers de format XML, consultez [Fichiers de format XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant utilise le fournisseur d'ensemble de lignes en bloc `OPENROWSET` pour procéder à l'importation du fichier de données `myTestOrder-c.txt` vers l'exemple de table `myTestOrder` à l'aide du fichier de format XML `myTestOrder.xml` . L'instruction `INSERT... SELECT` spécifie la liste de colonnes de la liste de sélection.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestOrder   
  SELECT Col1, Col2, Col3, Col4  
      FROM  OPENROWSET(BULK  'C:\myTestOrder-c.txt',  
      FORMATFILE='C:\myTestOrder.Xml'    
       ) AS t1;  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)   
 [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
  
