---
title: Utiliser un fichier de format pour importer des données en bloc (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], format files
- format files [SQL Server], importing data using
ms.assetid: 2956df78-833f-45fa-8a10-41d6522562b9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1f144e5e4f70fdef954dd91452df6bc9275409b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48073509"
---
# <a name="use-a-format-file-to-bulk-import-data-sql-server"></a>Utiliser un fichier de format pour importer des données en bloc (SQL Server)
  Cette rubrique illustre l'utilisation d'un fichier de format dans les importations en bloc. Le fichier de format met en relation les champs du fichier de données avec les colonnes de la table.  Vous pouvez opter pour un fichier de format XML ou non-XML pour importer des données en bloc quand vous utilisez une commande **bcp** ou une instruction BULK INSERT ou INSERT... SELECT * FROM OPENROWSET(BULK...)[!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  Pour qu'un fichier de format fonctionne avec un fichier de données de caractères Unicode, tous les champs d'entrée doivent être des chaînes de texte Unicode (autrement dit, des chaînes Unicode de taille fixe ou terminées par un caractère).  
  
> [!NOTE]  
>  Si vous n’êtes pas familiarisé avec les fichiers de format, consultez [les fichiers de Format Non-XML &#40;SQL Server&#41; ](xml-format-files-sql-server.md) et [fichiers de Format XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
## <a name="format-file-options-for-bulk-import-commands"></a>Options des fichiers de format pour les commandes d'importation en bloc  
 Le tableau ci-dessous récapitule l'option de fichier de format de chaque commande d'importation en bloc.  
  
|Commande de chargement en bloc|Utilisation de l'option de fichier de format|  
|------------------------|-----------------------------------|  
|BULK INSERT|FORMATFILE = '*chemin_fichier_format*'|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|FORMATFILE = '*chemin_fichier_format*'|  
|**bcp** … **in**|**-f** *format_file*|  
  
 Pour plus d’informations, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) ou [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Pour exporter ou importer en bloc des données SQLXML, utilisez l'un des types de données ci-dessous dans votre fichier de format : SQLCHAR ou SQLVARYCHAR (les données sont envoyées dans la page de codes du client ou dans la page de codes inhérente au classement) ; SQLNCHAR ou SQLNVARCHAR (les données sont envoyées au format Unicode) ; SQLBINARY ou SQLVARYBIN (les données sont envoyées sans être converties).  
  
## <a name="examples"></a>Exemples  
 Les exemples de cette section illustrent l’utilisation des fichiers de format pour importer des données en bloc au moyen de la commande **bcp** et des instructions BULK INSERT et INSERT... SELECT * FROM OPENROWSET(BULK...). Avant de pouvoir exécuter un des exemples d'importation en bloc, vous devez créer un exemple de table, de fichier de données et de fichier de format.  
  
### <a name="sample-table"></a>Exemple de table  
 Une table nommée **myTestFormatFiles** doit être créée dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] sous le schéma **dbo** . Pour créer cette table, dans l'éditeur de requêtes [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestFormatFiles (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50),  
   Col4 nvarchar(50)  
   );  
GO  
```  
  
### <a name="sample-data-file"></a>Fichier de données d'exemple  
 Les exemples utilisent un fichier de données d'exemple, `myTestFormatFiles-c.Dat`, qui contient les enregistrements suivants. Pour créer le fichier de données, à l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
10,Field2,Field3,Field4  
15,Field2,Field3,Field4  
46,Field2,Field3,Field4  
58,Field2,Field3,Field4  
```  
  
### <a name="sample-format-files"></a>Exemple de fichiers de format  
 Certains exemples de cette section utilisent un fichier de format XML, `myTestFormatFiles-f-x-c.Xml`, d'autres exemples un fichier de format non XML. Ces deux types de fichiers utilisent des formats de données de type caractère et une marque de fin de champ non définie par défaut (,).  
  
#### <a name="the-sample-non-xml-format-file"></a>Exemple de fichier de format non XML  
 L’exemple suivant a recours à la commande **bcp** pour générer un fichier de format XML à partir de la table `myTestFormatFiles` . Le fichier `myTestFormatFiles.Fmt` contient les informations suivantes :  
  
```  
9.0  
4  
1       SQLCHAR       0       7       ","      1     Col1         ""  
2       SQLCHAR       0       100     ","      2     Col2         SQL_Latin1_General_CP1_CI_AS  
3       SQLCHAR       0       100     ","      3     Col3         SQL_Latin1_General_CP1_CI_AS  
4       SQLCHAR       0       100     "\r\n"   4     Col4         SQL_Latin1_General_CP1_CI_AS  
```  
  
 Pour utiliser la commande **bcp** avec l’option **format** pour créer ce fichier de format, dans l’invite de commandes Windows, tapez :  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -f myTestFormatFiles.Fmt -T  
  
```  
  
 Pour plus d’informations sur la création d’un fichier de format, consultez [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
#### <a name="the-sample-xml-format-file"></a>Exemple de fichier de format XML  
 L’exemple suivant a recours à la commande **bcp** pour générer un fichier de format XML à partir de la table `myTestFormatFiles` . Le fichier `myTestFormatFiles.Xml` contient les informations suivantes :  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="4" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="4" NAME="Col4" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
 Pour utiliser la commande **bcp** avec l’option **format** pour créer ce fichier de format, dans l’invite de commandes Windows, tapez :  
  
```  
bcp AdventureWorks2012..MyTestFormatFiles format nul -c -t, -x -f myTestFormatFiles.Xml -T  
```  
  
### <a name="using-bcp"></a>Utilisation de la commande bcp  
 L’exemple suivant a recours à la commande **bcp** pour importer des données en bloc à partir du fichier de données `myTestFormatFiles-c.Dat` dans la table `HumanResources.myTestFormatFiles` de l’exemple de base de données. Cet exemple utilise le fichier de format XML `MyTestFormatFiles.Xml`. Il supprime toutes les lignes existantes de la table avant d'importer le fichier de données.  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks2012..myTestFormatFiles in C:\myTestFormatFiles-c.Dat -f C:\myTestFormatFiles.Xml -T  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur cette commande, consultez [Utilitaire bcp](../../tools/bcp-utility.md).  
  
### <a name="using-bulk-insert"></a>Utilisation de BULK INSERT  
 Dans l'exemple suivant, l'instruction BULK INSERT est utilisée pour importer des données en bloc à partir du fichier de données `myTestFormatFiles-c.Dat` dans la table `HumanResources.myTestFormatFiles` dans l'exemple de base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Cet exemple utilise le fichier de format non XML `MyTestFormatFiles.Fmt`. Il supprime toutes les lignes existantes de la table avant d'importer le fichier de données.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks2012;  
GO  
DELETE myTestFormatFiles;  
GO  
BULK INSERT myTestFormatFiles   
   FROM 'C:\myTestFormatFiles-c.Dat'   
   WITH (FORMATFILE = 'C:\myTestFormatFiles.Fmt');  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur cette instruction, consultez [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="using-the-openrowset-bulk-rowset-provider"></a>Utilisation du fournisseur d'ensembles de lignes en bloc OPENROWSET  
 Dans l'exemple suivant, la commande `INSERT ... SELECT * FROM OPENROWSET(BULK...)` est utilisée pour importer des données en bloc à partir du fichier de données `myTestFormatFiles-c.Dat` dans la table `HumanResources.myTestFormatFiles` dans l'exemple de base de données `AdventureWorks` . Cet exemple utilise le fichier de format XML `MyTestFormatFiles.Xml`. Il supprime toutes les lignes existantes de la table avant d'importer le fichier de données.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez :  
  
```  
USE AdventureWorks2012;  
DELETE myTestFormatFiles;  
GO  
INSERT INTO myTestFormatFiles  
    SELECT *  
      FROM  OPENROWSET(BULK  'C:\myTestFormatFiles-c.Dat',  
      FORMATFILE='C:\myTestFormatFiles.Xml'       
      ) as t1 ;  
GO  
SELECT * FROM myTestFormatFiles;  
GO  
```  
  
 Lorsque vous avez terminé d'utiliser la table d'exemple, vous pouvez la supprimer au moyen de l'instruction suivante :  
  
```  
DROP TABLE myTestFormatFiles  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la clause OPENROWSET BULK, consultez [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
## <a name="additional-examples"></a>Autres exemples  
 [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
 [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
 [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md)   
 [Fichiers de format XML &#40;SQL Server&#41;](xml-format-files-sql-server.md)  
  
  
