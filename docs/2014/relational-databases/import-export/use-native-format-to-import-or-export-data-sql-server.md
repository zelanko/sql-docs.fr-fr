---
title: Utiliser le format natif pour importer ou exporter des données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- native data format [SQL Server]
- data formats [SQL Server], native
ms.assetid: eb279b2f-0f1f-428f-9b8f-2a7fc495b79f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2e91899172dfc6d640df0c33c77e32de3c1c21c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66011662"
---
# <a name="use-native-format-to-import-or-export-data-sql-server"></a>Utiliser le format natif pour importer ou exporter des données (SQL Server)
  Il est recommandé d'utiliser le format natif lorsque vous transférez des données en bloc entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen d'un fichier de données qui ne contient pas de caractères appartenant à un jeu de caractères étendus/codés sur deux octets (DBCS).  
  
> [!NOTE]  
>  Pour transférer des données en bloc entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen d'un fichier de données qui contient des caractères appartenant à un jeu de caractères étendus/codés sur deux octets, utilisez de préférence le format natif Unicode. Pour plus d’informations, consultez [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
 Le format natif préserve les types de données native d'une base de données. Il est destiné aux transferts de données à haute vitesse entre des tables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous utilisez un fichier de format, les tables source et cible ne doivent pas nécessairement être identiques. Le transfert de données se déroule en deux étapes :  
  
1.  exportation en bloc des données d'une table source vers un fichier de données ;  
  
2.  importation en bloc des données d'un fichier de données vers la table cible.  
  
 L'utilisation d'un format natif entre tables identiques permet de gagner du temps et de l'espace puisque les conversions superflues des types de données à partir de et vers le format caractère sont éliminées. Pour atteindre la vitesse de transfert optimale, quelques contrôles sont effectués au niveau du formatage des données. Pour empêcher que des problèmes ne surviennent au niveau des données chargées, tenez compte des restrictions suivantes.  
  
## <a name="restrictions"></a>Restrictions  
 Pour importer des données au format natif, veillez à ce que les conditions suivantes soient réunies :  
  
-   Le fichier de données doit être au format natif.  
  
-   Soit la table cible doit être compatible avec le fichier de données (qui doit présenter le nombre voulu de colonnes, avec les mêmes types de données, longueur de colonne, état NULL, etc.), soit vous devez utiliser un fichier de format pour mapper chacun des champs sur sa colonne correspondante.  
  
    > [!NOTE]  
    >  Si vous importez des données d'un fichier qui ne concorde pas avec la table cible, l'importation peut réussir mais les valeurs de données insérées dans la table cible peuvent être incorrectes. En effet, les données du fichier sont interprétées en se basant sur le format de la table cible. Par conséquent, tout défaut de correspondance entraîne l'insertion de valeurs incorrectes. Cependant, en aucun cas une telle non-correspondance peut-elle provoquer des incohérences logiques ou physiques dans la base de données.  
  
     Pour plus d’informations sur l’utilisation de fichiers de format, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
 Une importation réussie n'endommage pas la table cible.  
  
## <a name="how-bcp-handles-data-in-native-format"></a>Traitement des données au format natif par l'utilitaire bcp  
 Cette section comporte des remarques spécifiques liées à la manière dont l'utilitaire **bcp** exporte et importe les données au format natif.  
  
-   Données non-caractère  
  
     Cet utilitaire emploie le format de données binaires interne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour écrire des données non-caractère d'une table vers un fichier de données.  
  
-   Données `char` ou `varchar`  
  
     Au début de chaque `char` ou `varchar` champ, **bcp** ajoute la longueur du préfixe.  
  
    > [!IMPORTANT]  
    >  En mode natif, l'utilitaire **bcp** convertit par défaut les caractères de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en caractères OEM avant de les copier dans un fichier de données. **L’utilitaire bcp** convertit les caractères d’un fichier de données en caractères ANSI avant de les importer en bloc dans une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Au cours de ces conversions, il est possible que des données caractères étendus soient perdues. Dans le cas de caractères étendus, vous devez soit utiliser le format natif Unicode, soit spécifier une page de codes.  
  
-   Données `sql_variant`  
  
     Si des données `sql_variant` sont stockées en tant que SQLVARIANT dans un fichier de données au format natif, elles conservent l'ensemble de leurs caractéristiques. Les métadonnées qui enregistrent le type de données de chaque valeur de données sont stockées en même temps que celle-ci. Elles sont employées pour recréer la valeur de données avec le même type de données dans une colonne `sql_variant` de destination.  
  
     Si le type de données de la colonne de destination n'est pas `sql_variant`, chaque valeur de données est convertie au type de données de la colonne de destination, suivant les règles normales de la conversion implicite de données. Si une erreur survient pendant la conversion des données, le traitement actif est annulé. Toute valeur `char` ou `varchar` transférée entre des colonnes `sql_variant` peut faire l'objet de problèmes de conversion des pages de codes.  
  
     Pour plus d’informations sur la conversion de données, consultez [Conversion de types de données &#40;moteur de base de données&#41;](/sql/t-sql/data-types/data-type-conversion-database-engine).  
  
## <a name="command-options-for-native-format"></a>Options de commande pour le format natif  
 Vous pouvez importer des données au format natif dans une table à l’aide de l’utilitaire **bcp** ou des instructions BULK INSERT ou INSERT ... SELECT \* FROM OPENROWSET(BULK...). Si vous utilisez une commande **bcp** ou une instruction BULK INSERT, vous pouvez spécifier le format de données dans la ligne de commande. Pour une instruction INSERT ... SELECT * FROM OPENROWSET(BULK...), vous devez spécifier le format de données dans un fichier de format.  
  
 Le format natif est pris en charge par les options de ligne de commande suivantes :  
  
|Command|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-n**|Provoque le **bcp** utilitaire à utiliser les types de données natif des données.<sup> 1</sup>|  
|BULK INSERT|DATAFILETYPE **=’** native **’**|Utilise les types de données native ou widenative des données. Notez que DATAFILETYPE n'est pas nécessaire si un fichier de format spécifie les types de données.|  
  
 <sup>1</sup> charger natif ( **- n**) les données dans un format compatible avec les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des clients, utilisez le **-V** basculer. Pour plus d’informations, consultez [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 Pour plus d’informations, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) ou [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Vous pouvez également spécifier le formatage par champ dans un fichier de format. Pour plus d’informations, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples ci-après indiquent comment exporter en bloc des données au format natif par le biais de **bcp** , et importer en bloc ces mêmes données à l’aide de BULK INSERT.  
  
### <a name="sample-table"></a>Exemple de table  
 Une table nommée **myTestNativeData** doit être créée dans l'exemple de base de données **AdventureWorks** sous le schéma **dbo** . Avant de commencer, vous devez créer cette base de données. Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez :  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Pour remplir cette table et afficher le contenu résultant, exécutez les instructions suivantes :  
  
```  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Utilisation de l'utilitaire bcp pour exporter en bloc des données au format natif  
 Pour exporter des données de la table vers le fichier de données, utilisez **bcp** avec l’option **out** et les qualificateurs suivants :  
  
|Qualificateurs|Description|  
|----------------|-----------------|  
|**-n**|Spécifie les types de données natifs.|  
|**-T**|Spécifie que l'utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une connexion approuvée qui utilise la sécurité intégrée. Si **-T** n’est pas spécifié, vous devez indiquer **-U** et **-P** pour vous connecter.|  
  
 Dans l'exemple suivant, des données sont exportées en bloc au format natif de la table `myTestNativeData` vers un nouveau fichier de données nommé `myTestNativeData-n.Dat`. À l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
bcp AdventureWorks..myTestNativeData out C:\myTestNativeData-n.Dat -n -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Utilisation de BULK INSERT pour importer en bloc des données au format natif  
 L'exemple suivant utilise l'instruction BULK INSERT pour importer les données du fichier de données `myTestNativeData-n.Dat` dans la table `myTestNativeData`. Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , exécutez :  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestNativeData   
    FROM 'C:\myTestNativeData-n.Dat'   
   WITH (DATAFILETYPE='native');   
GO  
SELECT Col1,Col2,Col3 FROM myTestNativeData  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [sql_variant &#40;Transact-SQL&#41;](/sql/t-sql/data-types/sql-variant-transact-sql)   
 [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
  
