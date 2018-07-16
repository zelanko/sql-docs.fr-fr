---
title: Conserver des valeurs d’identité lors de l’importation de données en bloc (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: data-movement
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server], bulk imports
- data formats [SQL Server], identity values
- bulk importing [SQL Server], identity values
ms.assetid: 45894a3f-2d8a-4edd-9568-afa7d0d3061f
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5870c305e74435b6c21fe0a4f872629216203990
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242559"
---
# <a name="keep-identity-values-when-bulk-importing-data-sql-server"></a>Conserver des valeurs d'identité lors de l'importation de données en bloc (SQL Server)
  Les fichiers de données contenant des valeurs d'identité peuvent être importés en bloc dans une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, les valeurs de la colonne d'identité du fichier de données importé sont ignorées et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affecte automatiquement des valeurs uniques. Ces valeurs uniques reposent sur les valeurs de départ et d'incrément spécifiées lors de la création de la table.  
  
 Si les fichiers de données ne contiennent pas de valeurs pour la colonne d'identificateur de la table, vous devez utiliser un fichier de format pour préciser si la colonne d'identificateur de la table doit être ignorée lors de l'importation de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assigne automatiquement des valeurs uniques pour la colonne.  
  
 Pour empêcher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d'assigner des valeurs d'identité lors de l'importation en bloc de lignes de données dans une table, utilisez le qualificateur de commande de conservation d'identité approprié. Lorsque vous spécifiez un qualificateur de conservation d'identité, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les valeurs d'identité du fichier de données. Ces qualificateurs sont les suivants :  
  
|Command|Qualificateur de conservation d'identité|Type de qualificateur|  
|-------------|------------------------------|--------------------|  
|`bcp`|**-E**|Commutateur|  
|BULK INSERT|KEEPIDENTITY|Argument|  
|INSERT ... SELECT * FROM OPENROWSET(BULK...)|KEEPIDENTITY|Indicateur de table|  
  
 Pour plus d’informations, consultez [bcp Utility](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql), [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql), [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql), [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql) et [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).  
  
> [!NOTE]  
>  Pour créer un numéro à incrémentation automatique qui peut être utilisé dans plusieurs tables ou être appelé par des applications sans faire référence à une table, consultez [Numéros de séquence](../sequence-numbers/sequence-numbers.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples de cette rubrique importent les données en bloc au moyen de INSERT ... SELECT * FROM OPENROWSET(BULK...), et conservent les valeurs par défaut.  
  
### <a name="sample-table"></a>Exemple de table  
 Dans ces exemples d’importation en bloc, la table **myTestKeepNulls** est créée dans l’exemple de base de données **AdventureWorks** sous le schéma **dbo**. Pour créer cette table. dans l'éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez le code suivant :  
  
```  
USE AdventureWorks;  
GO  
SELECT * INTO HumanResources.myDepartment   
   FROM HumanResources.Department  
      WHERE 1=0;  
GO  
SELECT * FROM HumanResources.myDepartment;  
```  
  
 Dans la table **Department** sur laquelle repose `myDepartment`, l’option IDENTITY_INSERT est désactivée (valeur OFF). Ainsi, pour importer des données dans une colonne d’identité, vous devez spécifier KEEPIDENTITY ou **-E**.  
  
### <a name="sample-data-file"></a>Fichier de données d'exemple  
 Le fichier de données utilisé dans les exemples d'importation en bloc contient des données exportées en bloc à partir de la table `HumanResources.Department` dans leur format natif. Pour créer le fichier de données, à l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
bcp AdventureWorks.HumanResources.Department out myDepartment-n.Dat -n -T  
```  
  
### <a name="sample-format-file"></a>Fichier de format d'exemple  
 Dans cet exemple d'importation en bloc, le fichier de format XML (`myDepartment-f-x-n.Xml`) utilise des formats de données natifs. Ce fichier de format est ici créé à l'aide de la commande `bcp`, à partir de la table `HumanResources.Department` de la base de données `AdventureWorks`. À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks.HumanResources.Department format nul -n -x -f myDepartment-f-n-x.Xml -T  
```  
  
 Pour plus d’informations sur la création d’un fichier de format, consultez [Créer un fichier de format &#40;SQL Server&#41;](create-a-format-file-sql-server.md).  
  
### <a name="a-using-bcp-and-keeping-identity-values"></a>A. Utilisation de bcp et conservation des valeurs d'identité  
 Cet exemple montre comment conserver les valeurs d'identité dans le cadre d'une importation de données en bloc avec la commande `bcp`. Le `bcp` commande utilise le fichier de format `myDepartment-f-n-x.Xml`et contient les commutateurs suivants :  
  
|Qualificateurs|Description|  
|----------------|-----------------|  
|**-E**|Précise que les valeurs d'identité du fichier de données doivent être utilisées pour la colonne d'identité.|  
|**-T**|Spécifie que le `bcp` utilitaire se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une connexion approuvée.|  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks.HumanResources.myDepartment in C:\myDepartment-n.Dat -f C:\myDepartment-f-n-x.Xml -E -T  
  
```  
  
### <a name="b-using-bulk-insert-and-keeping-identity-values"></a>B. Utilisation de BULK INSERT et conservation des valeurs d'identité  
 Dans l'exemple suivant, l'instruction BULK INSERT est utilisée pour importer des données en bloc dans la table `myDepartment-c.Dat` à partir du fichier `AdventureWorks.HumanResources.myDepartment` . L'instruction utilise le fichier de format `myDepartment-f-n-x.Xml` et inclut l'option KEEPIDENTITY pour assurer la conservation des valeurs d'identité éventuellement présentes dans le fichier de données.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
BULK INSERT HumanResources.myDepartment  
   FROM 'C:\myDepartment-n.Dat'  
   WITH (  
      KEEPIDENTITY,  
      FORMATFILE='C:\myDepartment-f-n-x.Xml'  
   );  
GO  
SELECT * FROM HumanResources.myDepartment;  
  
```  
  
### <a name="c-using-openrowset-and-keeping-identity-values"></a>C. Utilisation de OPENROWSET et conservation des valeurs d'identité  
 Dans l'exemple suivant, le fournisseur d'ensembles de lignes en bloc OPENROWSET sert à importer des données en bloc dans la table `myDepartment-c.Dat` à partir du fichier `AdventureWorks.HumanResources.myDepartment` . L'instruction utilise le fichier de format `myDepartment-f-n-x.Xml` et inclut l'indicateur KEEPIDENTITY pour assurer la conservation des valeurs d'identité éventuellement présentes dans le fichier de données.  
  
 Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
DELETE HumanResources.myDepartment;  
GO  
  
INSERT INTO HumanResources.myDepartment  
   with (KEEPIDENTITY)  
   (DepartmentID, Name, GroupName, ModifiedDate)  
   SELECT *  
      FROM  OPENROWSET(BULK 'C:\myDepartment-n.Dat',  
      FORMATFILE='C:\myDepartment-f-n-x.Xml') as t1;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
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
  
1.  [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)  
  
2.  [Spécifier une longueur de préfixe dans des fichiers de données à l’aide de bcp &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
3.  [Spécifier le type de stockage de fichiers à l’aide de bcp &#40;SQL Server&#41;](specify-file-storage-type-by-using-bcp-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Indicateurs de table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)  
  
  
