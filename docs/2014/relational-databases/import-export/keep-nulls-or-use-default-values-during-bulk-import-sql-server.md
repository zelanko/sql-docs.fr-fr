---
title: Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], null values
- bulk importing [SQL Server], default values
- data formats [SQL Server], null values
- bulk rowset providers [SQL Server]
- bcp utility [SQL Server], null values
- BULK INSERT statement
- default values
- OPENROWSET function, bulk importing
- data formats [SQL Server], default values
ms.assetid: 6b91d762-337b-4345-a159-88abb3e64a81
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4753e1097dee300d4d806c42b71954e6e557ed12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63063940"
---
# <a name="keep-nulls-or-use-default-values-during-bulk-import-sql-server"></a>Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l'importation en bloc (SQL Server)
  Par défaut, lorsque des données sont importées dans une table, la commande **bcp** et l’instruction BULK INSERT inspectent toutes les valeurs par défaut définies pour les colonnes de la table. Par exemple, si un fichier de données contient un champ NULL, la valeur par défaut de la colonne est chargée à la place. La commande **bcp** et l’instruction BULK INSERT vous permettent de spécifier que les valeurs NULL doivent être conservées.  
  
 À l'opposé, une instruction INSERT standard conserve la valeur NULL au lieu d'insérer une valeur par défaut. L'instruction INSERT ... SELECT * FROM OPENROWSET(BULK...) présente le même comportement de base que l'instruction INSERT standard mais elle prend également en charge un indicateur de table pour l'insertion des valeurs par défaut.  
  
> [!NOTE]  
>  Pour obtenir des exemples de fichiers de format qui ignorent une colonne de table, consultez [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md).  
  
## <a name="sample-table-and-data-file"></a>Exemples de table et de fichier de données  
 Pour exécuter les exemples proposés dans cette rubrique, vous devez créer un exemple de table et un exemple de fichier de données.  
  
### <a name="sample-table"></a>Exemple de table  
 Les exemples requièrent la création d'une table nommée **MyTestDefaultCol2** dans l'exemple de base de données **AdventureWorks** sous le schéma **dbo** . Pour créer cette table, dans l'éditeur de requêtes [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , exécutez le code suivant :  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE MyTestDefaultCol2   
(Col1 smallint,  
Col2 nvarchar(50) DEFAULT 'Default value of Col2',  
Col3 nvarchar(50)   
);  
GO  
  
```  
  
 La deuxième colonne de table, `Col2`, a une valeur par défaut.  
  
### <a name="sample-format-file"></a>Fichier de format d'exemple  
 Certains des exemples d'importation en bloc utilisent un fichier de format non-XML, `MyTestDefaultCol2-f-c.Fmt`, qui correspond exactement à la table `MyTestDefaultCol2`. Pour créer ce fichier de format, à l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, saisissez le code suivant :  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 format nul -c -f C:\MyTestDefaultCol2-f-c.Fmt -t, -r\n -T  
  
```  
  
 Pour plus d’informations sur la création de fichiers de format, consultez [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
### <a name="sample-data-file"></a>Fichier de données d'exemple  
 L'exemple utilise un fichier de données, `MyTestEmptyField2-c.Dat`, dont le deuxième champ ne contient aucune valeur. Le fichier de données `MyTestEmptyField2-c.Dat` contient les enregistrements suivants.  
  
```  
1,,DataField3  
2,,DataField3  
  
```  
  
## <a name="keeping-null-values-with-bcp-or-bulk-insert"></a>Conservation des valeurs NULL à l'aide de la commande bcp ou de l'instruction BULK INSERT  
 Les qualificateurs suivants spécifient qu'un champ vide du fichier de données conserve sa valeur NULL lors de l'importation en bloc, au lieu d'hériter d'une valeur par défaut (s'il y en a une) pour les colonnes de table.  
  
|Command|Qualificateur|Type de qualificateur|  
|-------------|---------------|--------------------|  
|**bcp**|`-k`|Basculer|  
|BULK INSERT|KEEPNULLS<sup>1</sup>|Argument|  
  
 <sup>1</sup> pour BULK INSERT, si les valeurs par défaut ne sont pas disponibles, la colonne de table doit être définie pour autoriser les valeurs null.  
  
> [!NOTE]  
>  Ces qualificateurs désactivent le contrôle des définitions DEFAULT sur une table par ces commandes d'importation en bloc. Toutefois, pour toute instruction INSERT concurrente, des définitions DEFAULT sont attendues.  
  
 Pour plus d’informations, consultez [bcp Utility](../../tools/bcp-utility.md) et [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).  
  
### <a name="examples"></a>Exemples  
 Les exemples de cette section réalisent des importations en bloc à l’aide de la commande **bcp** ou de l’instruction BULK INSERT et conservent les valeurs NULL.  
  
 La deuxième colonne de la table, **Col2**, a une valeur par défaut. Le champ correspondant du fichier de données contient une chaîne vide. Par défaut, lorsque la commande **bcp** ou l’instruction BULK INSERT est utilisée pour importer des données à partir de ce fichier de données dans la table **MyTestDefaultCol2** , la valeur par défaut de la colonne **Col2** est insérée et le résultat suivant est obtenu :  
  
||||  
|-|-|-|  
|`1`|`Default value of Col2`|`DataField3`|  
|`2`|`Default value of Col2`|`DataField3`|  
  
 Pour insérer «`NULL`« au lieu de »`Default value of Col2`», vous devez utiliser le `-k` commutateur ou l’option KEEPNULL, comme illustré dans l’exemple suivant **bcp** et exemples BULK INSERT.  
  
#### <a name="using-bcp-and-keeping-null-values"></a>Utilisation de la commande bcp et conservation des valeurs NULL  
 L’exemple suivant montre comment conserver les valeurs NULL dans une commande **bcp** . La commande **bcp** contient les commutateurs suivants :  
  
|Basculer|Description|  
|------------|-----------------|  
|`-f`|La commande utilise un fichier de format.|  
|`-k`|Pendant l’opération, les colonnes vides doivent conserver une valeur NULL et les colonnes insérées ne doivent pas prendre de valeur par défaut.|  
|`-T`|L'utilitaire bcp se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide d'une connexion approuvée.|  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks..MyTestDefaultCol2 in C:\MyTestEmptyField2-c.Dat -f C:\MyTestDefaultCol2-f-c.Fmt -k -T  
  
```  
  
#### <a name="using-bulk-insert-and-keeping-null-values"></a>Utilisation de l'instruction BULK INSERT et conservation des valeurs NULL  
 L'exemple suivant montre comment utiliser l'option KEEPNULLS dans une instruction BULK INSERT. À partir d'un outil de requête tel que l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT MyTestDefaultCol2  
   FROM 'C:\MyTestEmptyField2-c.Dat'  
   WITH (  
      DATAFILETYPE = 'char',  
      FIELDTERMINATOR = ',',  
      KEEPNULLS  
   );  
GO  
  
```  
  
## <a name="keeping-default-values-with-insert--select--from-openrowsetbulk"></a>Conservation des valeurs par défaut à l'aide de l'instruction INSERT ... SELECT * FROM OPENROWSET(BULK...)  
 Par défaut, l'instruction INSERT ... SELECT * FROM OPENROWSET(BULK...). Toutefois, pour un champ vide du fichier de données, vous pouvez spécifier que la colonne de table correspondante utilise sa valeur par défaut (s'il y en a une). Pour utiliser les valeurs par défaut, spécifiez l'indicateur de table suivant :  
  
|Command|Qualificateur|Type de qualificateur|  
|-------------|---------------|--------------------|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|WITH(KEEPDEFAULTS)|Indicateur de table|  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) et [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
### <a name="examples"></a>Exemples  
 L'exemple d'instruction INSERT ... SELECT * FROM OPENROWSET(BULK...) suivant importe des données en bloc et conserve les valeurs par défaut.  
  
 Pour exécuter les exemples, vous devez créer l'exemple de table **MyTestDefaultCol2** , le fichier de données `MyTestEmptyField2-c.Dat` et utiliser un fichier de format, `MyTestDefaultCol2-f-c.Fmt`. Pour plus d'informations sur la création de ces exemples, consultez la section « Exemples de table et de fichier de données », plus haut dans cette rubrique.  
  
 La deuxième colonne de la table, **Col2**, a une valeur par défaut. Le champ correspondant du fichier de données contient une chaîne vide. Lorsque l'instruction INSERT ... SELECT \* FROM OPENROWSET(BULK...) importe les champs de ce fichier de données dans la table **MyTestDefaultCol2**, par défaut, la valeur NULL est insérée dans la colonne **Col2**, au lieu de la valeur par défaut. Ce comportement par défaut produit le résultat suivant :  
  
||||  
|-|-|-|  
|`1`|`NULL`|`DataField3`|  
|`2`|`NULL`|`DataField3`|  
  
 Pour insérer la valeur par défaut «`Default value of Col2`», au lieu de «`NULL`», vous devez utiliser l'indicateur de table KEEPDEFAULTS, comme le montre l'exemple suivant. À partir d'un outil de requête tel que l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
INSERT INTO MyTestDefaultCol2  
    WITH (KEEPDEFAULTS)  
    SELECT *  
      FROM OPENROWSET(BULK  'C:\MyTestEmptyField2-c.Dat',  
      FORMATFILE='C:\MyTestDefaultCol2-f-c.Fmt'       
      ) as t1 ;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Préparer des données en vue d’une exportation ou d’une importation en bloc &#40;SQL Server&#41;](prepare-data-for-bulk-export-or-import-sql-server.md)  
  
 **Pour utiliser un fichier de format**  
  
-   [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser un fichier de format pour mapper les colonnes d’une table sur les champs d’un fichier de données &#40;SQL Server&#41;](use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer un champ de données &#40;SQL Server&#41;](use-a-format-file-to-skip-a-data-field-sql-server.md)  
  
-   [Utiliser un fichier de format pour ignorer une colonne de table &#40;SQL Server&#41;](use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 **Pour spécifier des formats de données pour la compatibilité lors de l'utilisation de bcp**  
  
-   [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
-   [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
-   [Spécifier le type de stockage de fichiers à l’aide de bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
