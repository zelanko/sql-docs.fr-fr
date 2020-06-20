---
title: Utiliser le format natif Unicode pour importer ou exporter des données (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- Unicode [SQL Server], bulk importing and exporting
- data formats [SQL Server], Unicode native
ms.assetid: a6213308-f3d5-406e-9029-19d8bb3367f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: beae2f836de16dedf3be6d8c196910c53be02266
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85026287"
---
# <a name="use-unicode-native-format-to-import-or-export-data-sql-server"></a>Utiliser le format natif Unicode pour importer ou exporter des données (SQL Server)
  Le format natif Unicode est utile quand vous devez copier des informations d’une installation de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une autre. L'utilisation du format natif pour les données qui ne sont pas de type caractère (char) permet de gagner du temps, puisque vous supprimez les conversions inutiles des types de données depuis et vers le format caractère. L'utilisation du format caractère Unicode pour toutes les données de type caractère évite la perte des caractères étendus lorsque vous transférez en bloc des données entre des serveurs utilisant des pages de codes différentes. Un fichier de données au format natif Unicode peut être lu par toutes les méthodes d'importation en bloc.  
  
 Le format natif Unicode est recommandé pour le transfert en bloc des données entre plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais d'un fichier de données qui contient des caractères étendus ou des caractères codés sur deux octets (DBCS). Pour les données qui ne sont pas de type caractère, le format natif Unicode utilise des types de données (bases de données) natifs. Pour les données de type caractère (par exemple `char`, `nchar`, `varchar`, `nvarchar`, `text`, `varchar(max)`, `nvarchar(max)` et `ntext`), le format natif Unicode utilise le format de données de type caractère Unicode.  
  
 Les données `sql_variant` qui sont stockées en tant que SQLVARIANT dans un fichier de données au format natif Unicode fonctionnent de la même manière que le fichier de données au format natif, sauf que les valeurs `char` et `varchar` sont converties en `nchar` et `nvarchar`, ce qui double l'espace de stockage nécessaire pour les colonnes affectées. Les métadonnées d'origine sont conservées, et les valeurs sont reconverties en leur type de données `char` et `varchar` d'origine lorsqu'elles sont importées en bloc dans une colonne de table.  
  
## <a name="command-options-for-unicode-native-format"></a>Options de commande pour le format natif Unicode  
 Vous pouvez importer des données au format natif Unicode dans une table à l’aide de la commande **BCP**, Bulk Insert ou Insert... SELECT \* FROM OPENROWSET (BULK...). Pour une commande **BCP** ou une instruction BULK INSERT, vous pouvez spécifier le format de données sur la ligne de commande. Pour une instruction INSERT... SELECT * FROM OPENROWSET(BULK...), vous devez spécifier le format de données dans un fichier de format.  
  
 Le format natif Unicode est reconnu par les options suivantes :  
  
|Commande|Option|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-N**|Fait en sorte que l’utilitaire **BCP** utilise le format natif Unicode, qui utilise des types de données (base de données) natifs pour toutes les données non-caractères et le format de données caractères Unicode pour toutes les données de type caractère (,,,, `char` `nchar` `varchar` `nvarchar` `text` et `ntext` ).|  
|BULK INSERT|DATAFILETYPE **= '** widenative **'**|Utilisez le format natif Unicode lorsque vous importez en bloc des données.|  
  
 Pour plus d’informations, consultez [Utilitaire bcp](../../tools/bcp-utility.md), [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) ou [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
> [!NOTE]  
>  Vous pouvez également spécifier le formatage par champ dans un fichier de format. Pour plus d’informations, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="examples"></a>Exemples  
 Les exemples ci-après indiquent comment exporter en bloc des données au format natif par le biais de **bcp** , et importer en bloc ces mêmes données à l’aide de BULK INSERT.  
  
### <a name="sample-table"></a>Exemple de table  
 Les exemples utilisent une table nommée **myTestUniNativeData**, qui doit être créée dans l’exemple de base de données **AdventureWorks** sous le schéma **dbo**. Avant de commencer, vous devez créer cette base de données. Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE myTestUniNativeData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 Pour remplir cette table et afficher le contenu résultant, exécutez les instructions suivantes :  
  
```  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3');  
INSERT INTO myTestUniNativeData(Col1,Col2,Col3)  
   VALUES(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData  
  
```  
  
### <a name="using-bcp-to-bulk-export-native-data"></a>Utilisation de l'utilitaire bcp pour exporter en bloc des données au format natif  
 Pour exporter des données de la table vers le fichier de données, utilisez **bcp** avec l’option **out** et les qualificateurs suivants :  
  
|Qualificateurs|Description|  
|----------------|-----------------|  
|**-N**|Spécifie les types de données natifs.|  
|**-T**|Spécifie que l'utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec une connexion approuvée qui utilise la sécurité intégrée. Si **-T** n’est pas spécifié, vous devez indiquer **-U** et **-P** pour vous connecter.|  
  
 Dans l'exemple suivant, des données sont exportées en bloc au format natif de la table `myTestUniNativeData` vers un nouveau fichier de données nommé `myTestUniNativeData-N.Dat`. À l'invite de commandes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, entrez :  
  
```  
bcp AdventureWorks..myTestUniNativeData out C:\myTestUniNativeData-N.Dat -N -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-native-data"></a>Utilisation de BULK INSERT pour importer en bloc des données au format natif  
 L'exemple suivant utilise l'instruction BULK INSERT pour importer les données du fichier de données `myTestUniNativeData-N.Dat` dans la table `myTestUniNativeData`. Dans l'Éditeur de requête [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], exécutez :  
  
```  
USE AdventureWorks;  
GO  
BULK INSERT myTestUniNativeData   
    FROM 'C:\myTestUniNativeData-N.Dat'   
   WITH (DATAFILETYPE='widenative');   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniNativeData;  
GO  
  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
