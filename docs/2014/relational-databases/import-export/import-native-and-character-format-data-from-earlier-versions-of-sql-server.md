---
title: Importer des données au format natif et caractère à partir de versions antérieures de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a87863d3046de695e489e83ec46eb073a7f4761c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531594"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a>Importer des données au format natif et caractère à partir de versions antérieures de SQL Server
  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez utiliser la commande **bcp** pour importer des données au format natif et caractère à partir de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]ou [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , à l’aide du commutateur **-V** . Le commutateur **-V** entraîne l’utilisation par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] des types de données à partir de la version antérieure spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et le format du fichier de données est identique à celui de cette version antérieure.  
  
 Pour spécifier une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour un fichier de données, utilisez le commutateur **-V** avec l’un des qualificateurs suivants :  
  
|Version de SQL Server|Qualificateur|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|**-V80**|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|**-V90**|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|**-V100**|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|**-V 110**|  
  
## <a name="interpretation-of-data-types"></a>Interprétation des types de données  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les versions ultérieures prennent en charge certains nouveaux types. Pour importer un nouveau type de données dans une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieure, ce type de données doit être stocké dans un format lisible par les anciens clients **bcp** . Le tableau ci-dessous résume le mode de conversion des nouveaux types de données pour assurer leur compatibilité avec les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nouveaux types de données dans SQL Server 2005|Types de données compatibles dans la version 6*x*|Types de données compatibles dans la version 70|Types de données compatibles dans la version 80|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|XML|`ntext`|`ntext`|`ntext`|  
|UDT<sup>1</sup>|`image`|`image`|`image`|  
  
 \* Ce type est prise en charge.  
  
 <sup>1</sup> UDT indique un type défini par l’utilisateur.  
  
## <a name="exporting-using--v-80"></a>Exportation à l’aide de -V 80  
 Lorsque vous exportez des données en bloc à l’aide de la **-V80** basculer, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML, et les données UDT en mode natif sont stockées avec un préfixe de 4 octets, comme `text`, `image`et `ntext`données, plutôt que par un préfixe de 8 octets, qui est la valeur par défaut pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures.  
  
## <a name="copying-date-values"></a>Copie de valeurs de date  
 **bcp** utilise l’API de copie en bloc ODBC. Par conséquent, pour importer des valeurs de date dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp** utilise le format de date ODBC (*yyyy-mm-dd hh:mm:ss*[*.f...*]).  
  
 Le **bcp** commande exporte des fichiers de données de format de caractère à l’aide du format par défaut ODBC pour `datetime` et `smalldatetime` valeurs. Par exemple, une colonne `datetime` contenant la date `12 Aug 1998` est copiée en bloc dans un fichier de données en tant que chaîne de caractères `1998-08-12 00:00:00.000`.  
  
> [!IMPORTANT]  
>  Lors de l’importation de données dans un `smalldatetime` champ à l’aide de **bcp**, vérifiez que la valeur des secondes est 00.000 ; sinon l’opération échouera. Le type de données `smalldatetime` ne conserve que les valeurs à la minute la plus proche. BULK INSERT et INSERT ... SELECT * FROM OPENROWSET(BULK...) n'échoueront pas dans ce cas, mais tronqueront la valeur des secondes.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour utiliser des formats de données pour l'importation ou l'exportation en bloc**  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Compatibilité descendante du moteur de base de données SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [CAST et CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
