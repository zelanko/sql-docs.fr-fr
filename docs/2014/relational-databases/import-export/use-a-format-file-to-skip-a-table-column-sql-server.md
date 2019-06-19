---
title: Utiliser un fichier de format pour ignorer une colonne de table (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- skipping columns when importing
- format files [SQL Server], skipping columns
ms.assetid: 30e0e7b9-d131-46c7-90a4-6ccf77e3d4f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 80c5c5b2f4e6d4f691b7c3977ae2f715f5424e7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011690"
---
# <a name="use-a-format-file-to-skip-a-table-column-sql-server"></a>Utiliser un fichier de format pour ignorer une colonne de table (SQL Server)
  Cette rubrique décrit les fichiers de format. Vous pouvez utiliser un fichier de format pour ignorer l'importation d'une colonne de table lorsque le champ n'existe pas dans le fichier de données. Un fichier de données peut contenir moins de champs qu'il n'y a de colonnes dans la table uniquement si les colonnes ignorées peuvent être NULL et/ou avoir une valeur par défaut.  
  
## <a name="sample-table-and-data-file"></a>Exemples de table et de fichier de données  
 Les exemples suivants nécessitent une table nommée `myTestSkipCol` dans la base de données exemple [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] sous le schéma **dbo** . Créez cette table comme suit :  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestSkipCol   
   (  
   Col1 smallint,  
   Col2 nvarchar(50) NULL,  
   Col3 nvarchar(50) not NULL  
   );  
GO  
```  
  
 Les exemples suivants utilisent un fichier de données d'exemple, `myTestSkipCol2.dat`, doté uniquement de deux champs alors que la table correspondante contient trois colonnes :  
  
```  
1,DataForColumn3  
1,DataForColumn3  
1,DataForColumn3  
  
```  
  
 Pour importer des données en bloc depuis `myTestSkipCol2.dat` dans la table `myTestSkipCol` , le fichier de format doit mapper le premier champ de données à `Col1`, le deuxième champ à `Col3`, en ignorant `Col2`.  
  
## <a name="using-a-non-xml-format-file"></a>Utilisation d'un fichier de format non-XML  
 Vous pouvez modifier un fichier de format non XML pour ignorer une colonne de table. En règle générale, cette opération consiste à faire appel à l’utilitaire **bcp** pour créer un fichier de format non-XML par défaut et à modifier le fichier par défaut dans un éditeur de texte. Le fichier de format modifié doit mapper chaque champ existant à une colonne de table correspondante et indiquer quelle(s) colonne(s) de table ignorer. Il existe deux alternatives pour modifier un fichier de données non XML par défaut. Quoi qu'il en soit, elles indiquent toutes deux que le champ de données n'existe pas dans le fichier de données et qu'aucune donnée ne sera insérée dans la colonne correspondante de la table.  
  
### <a name="creating-a-default-non-xml-format-file"></a>Création d'un fichier de format non XML par défaut  
 Cette rubrique utilise le fichier de format non-XML par défaut créé pour l’exemple de table `myTestSkipCol` en faisant appel à la commande **bcp** suivante :  
  
```  
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.fmt -c -T  
```  
  
 La commande précédente crée un fichier de format non XML, `myTestSkipCol_Default.fmt`. Ce fichier de format s’appelle un *fichier de format par défaut* car il est au format généré par **bcp**. Généralement, un fichier de format par défaut décrit une correspondance unique entre les champs données-fichier et les colonnes de table.  
  
> [!IMPORTANT]  
>  Vous devrez peut-être spécifier le nom de l'instance de serveur à laquelle vous vous connectez. Vous devrez aussi peut-être spécifier le nom d'utilisateur et le mot de passe. Pour plus d’informations, consultez [bcp Utility](../../tools/bcp-utility.md).  
  
 L'illustration suivante montre les valeurs dans les exemples de fichier de format par défaut. L'illustration montre également le nom de chaque champ fichier-format.  
  
 ![fichier de format non-XML par défaut pour myTestSkipCol](../../database-engine/media/mytestskipcol-f-c-default-fmt.gif "fichier de format non-XML par défaut pour myTestSkipCol")  
  
> [!NOTE]  
>  Pour plus d’informations sur les champs de fichier de format, consultez [Fichiers de format non-XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="methods-for-modifying-a-non-xml-format-file"></a>Méthodes de modification d'un fichier de format non XML  
 Pour ignorer une colonne de table, modifiez le fichier de format non XML par défaut et modifiez-le à l'aide de l'une des méthodes alternatives suivantes :  
  
-   La méthode recommandée consiste en une procédure de trois étapes. Commencez par supprimer les lignes de fichier-format qui correspondent à un champ manquant dans le fichier de données. Puis, réduisez la valeur « Ordre des champs du fichier hôte » de chaque ligne de fichier-format qui suit une ligne supprimée. L'objectif est les valeurs « Ordre des champs du fichier hôte » séquentielles, 1 à *n*, qui reflète la position réelle de chaque champ de données dans le fichier de données. Enfin, réduisez la valeur du champ « Nombre de colonnes » pour refléter le nombre réel de champs figurant dans le fichier de données.  
  
     L'exemple suivant est basé sur le fichier de format par défaut pour la table `myTestSkipCol` et créé dans la section « Création d'un fichier de format non XML par défaut », plus haut dans cette rubrique. Ce fichier de format modifié mappe le premier champ de données à `Col1`, ignore `Col2`, et mappe le deuxième champ de données à `Col3`. La ligne de `Col2` a été supprimée. Les autres modifications apparaissent en gras :  
  
    ```  
    9.0  
    2  
    1       SQLCHAR       0       7       "\t"     1     Col1         ""  
    2       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
    ```  
  
-   Pour ignorer une colonne de table, vous pouvez aussi modifier la définition de la ligne du fichier-format qui correspond à la colonne de table. Dans cette ligne de fichier-format, les valeurs « longueur de préfixe », « longueur des données du fichier hôte » et « ordre des colonnes du serveur » doivent être égales à 0. De plus, les champs « terminateur » et « classement des colonnes » doivent avoir la valeur "" (NULL).  
  
     La valeur « nom de la colonne du serveur » nécessite une chaîne non vide même si le nom de la colonne à proprement dit n'est pas nécessaire Les champs de format restants nécessitent leurs valeurs par défaut.  
  
     L'exemple suivant provient aussi du fichier de format par défaut pour la table `myTestSkipCol` . Les valeurs qui doivent être 0 ou NULL sont en gras.  
  
    ```  
    9.0  
    3  
    1       SQLCHAR       0       7       "\t"     1     Col1         ""  
    2       SQLCHAR       00""0     Col2         ""  
    3       SQLCHAR       0       100     "\r\n"   3     Col3         SQL_Latin1_General_CP1_CI_AS  
    ```  
  
### <a name="examples"></a>Exemples  
 Les exemples suivants sont aussi basés sur l'exemple de table `myTestSkipCol` et l'exemple de fichier de données `myTestSkipCol2.dat` créés dans la section « Exemple de table et de fichier de données », plus haut dans cette rubrique.  
  
#### <a name="using-bulk-insert"></a>Utilisation de BULK INSERT  
 Cet exemple décrit l'utilisation de l'un ou l'autre des fichiers de format non XML modifiés et créés dans la section « Méthodes de modification d'un fichier de format non XML », plus haut dans cette rubrique. Dans cet exemple, le fichier de format modifié est intitulé `C:\myTestSkipCol2.fmt`. Pour utiliser `BULK INSERT` afin d'importer en bloc le fichier de données `myTestSkipCol2.dat` , exécutez le code suivant dans l'éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] :  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestSkipCol   
   FROM 'C:\myTestSkipCol2.dat'   
   WITH (FORMATFILE = 'C:\myTestSkipCol2.fmt');  
GO  
SELECT * FROM myTestSkipCol;  
GO  
```  
  
## <a name="using-an-xml-format-file"></a>Utilisation d'un fichier de format XML  
 Avec un fichier de format XML, vous ne pouvez pas ignorer une colonne lorsque vous procédez à une importation directement dans une table à l’aide d’une commande **bcp** ou d’une instruction BULK INSERT. Néanmoins, vous pouvez importer toutes les colonnes d'une table hormis la dernière. Pour ignorer toutes les colonnes à l'exception de la dernière, vous devez créer une vue de la table cible contenant uniquement les colonnes figurant dans le fichier de données. Vous pouvez ensuite importer en bloc les données de ce fichier dans la vue.  
  
 Pour utiliser un fichier de format XML afin d'ignorer une colonne de table à l'aide de OPENROWSET(BULK...), vous devez fournir une liste explicite des colonnes dans la liste de sélection mais aussi dans la table cible, comme ci-dessous :  
  
 INSERT ...<column_list> SELECT <column_list> FROM OPENROWSET(BULK...)  
  
### <a name="creating-a-default-xml-format-file"></a>Création d'un fichier de format XML par défaut  
 Les exemples de fichiers de format modifiés sont basés sur l'exemple de table `myTestSkipCol` et de fichier de données créés dans la section « Exemple de table et de fichier de données », plus haut dans cette rubrique. La commande **bcp** suivante crée un fichier de format XML par défaut pour la table `myTestSkipCol` :  
  
```  
bcp AdventureWorks2012..myTestSkipCol format nul -f myTestSkipCol_Default.xml -c -x -T  
```  
  
 Le fichier de format non XML par défaut résultant décrit une correspondance unique entre les champs données-fichier et les colonnes de table de la manière suivante :  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
  <FIELD ID="3" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col2" xsi:type="SQLNVARCHAR"/>  
  <COLUMN SOURCE="3" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
> [!NOTE]  
>  Pour plus d’informations sur la structure des fichiers de format XML, consultez [Fichiers de format XML &#40;SQL Server&#41;](xml-format-files-sql-server.md).  
  
### <a name="examples"></a>Exemples  
 Les exemples de cette section utilisent l'exemple de table `myTestSkipCol` et l'exemple de fichier de données `myTestSkipCol2.dat` de la section « Exemple de table et de fichier de données », plus haut dans cette rubrique. Pour effectuer l'importation de `myTestSkipCol2.dat` dans la table `myTestSkipCol` , les exemples font appel au fichier de format XML modifié, `myTestSkipCol2-x.xml`. Ces exemples sont basés sur le fichier de format créé dans la section « Création d'un fichier de format XML par défaut », plus haut dans cette rubrique.  
  
```  
<?xml version="1.0"?>  
<BCPFORMAT xmlns="https://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
 <RECORD>  
  <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="," MAX_LENGTH="7"/>  
  <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="100" COLLATION="SQL_Latin1_General_CP1_CI_AS"/>  
 </RECORD>  
 <ROW>  
  <COLUMN SOURCE="1" NAME="Col1" xsi:type="SQLSMALLINT"/>  
  <COLUMN SOURCE="2" NAME="Col3" xsi:type="SQLNVARCHAR"/>  
 </ROW>  
</BCPFORMAT>  
```  
  
#### <a name="using-openrowsetbulk"></a>Utilisation de OPENROWSET(BULK...)  
 L'exemple suivant utilise le fournisseur d'ensembles de lignes en bloc `OPENROWSET` et le fichier de format `myTestSkipCol2.xml` . Dans cet exemple, le fichier de données `myTestSkipCol2.dat` est importé en bloc dans la table `myTestSkipCol` . L'instruction contient une liste explicite des colonnes dans la liste de sélection et aussi dans la table cible.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks2012;  
GO  
INSERT INTO myTestSkipCol  
  (Col1,Col3)  
    SELECT Col1,Col3  
      FROM  OPENROWSET(BULK  'C:\myTestSkipCol2.Dat',  
      FORMATFILE='C:\myTestSkipCol2.Xml'    
       ) as t1 ;  
GO  
```  
  
#### <a name="using-bulk-import-on-a-view"></a>Utilisation de BULK IMPORT dans une vue  
 L'exemple suivant crée la vue `v_myTestSkipCol` dans la table `myTestSkipCol` . Cette vue ignore la deuxième colonne de la table, `Col2`. L'exemple utilise ensuite l'instruction `BULK INSERT` pour importer le fichier de données `myTestSkipCol2.dat` dans cette vue.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
CREATE VIEW v_myTestSkipCol AS  
    SELECT Col1,Col3  
    FROM myTestSkipCol;  
GO  
  
USE AdventureWorks2012;  
GO  
BULK INSERT v_myTestSkipCol  
FROM 'C:\myTestSkipCol2.dat'  
WITH (FORMATFILE='C:\myTestSkipCol2.xml');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)   
 [Utiliser un fichier de format pour mapper les colonnes d’une table aux champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)   
 [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
  
