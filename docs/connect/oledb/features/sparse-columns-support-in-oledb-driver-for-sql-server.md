---
title: Prise en charge des colonnes éparses dans OLE DB Driver pour SQL Server | Microsoft Docs
description: Découvrez comment OLE DB Driver pour SQL Server prend en charge des colonnes éparses et consultez des informations sur les colonnes éparses dans SQL Server.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sparse columns, OLE DB Driver for SQL Server
- sparse columns, OLE DB
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1397d69f72cfc1362decf84959046d581befea5b
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862282"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>Prise en charge des colonnes éparses dans OLE DB Driver pour SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server prend en charge les colonnes éparses. Pour plus d’informations sur les colonnes éparses dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [Utiliser des colonnes éparses](../../../relational-databases/tables/use-sparse-columns.md) et [Utiliser des jeux de colonnes](../../../relational-databases/tables/use-column-sets.md).  
  
 Pour obtenir plus d'informations sur la prise en charge des colonnes éparses dans OLE DB Driver pour SQL Server, consultez [Prise en charge des colonnes éparses &#40;OLE DB&#41;](../../oledb/ole-db/sparse-columns-support-ole-db.md).  
  
 Pour plus d’informations sur les exemples d’applications qui illustrent cette fonctionnalité, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>Scénarios utilisateur pour les colonnes éparses et OLE DB Driver pour SQL Server  
 Le tableau suivant résume les scénarios utilisateur courants avec colonnes éparses pour les utilisateurs OLE DB Driver pour SQL Server :  
  
|Scénario|Comportement|  
|--------------|--------------|  
|**select \* from table** or IOpenRowset::OpenRowset.|Retourne toutes les colonnes qui ne sont pas membres du **column_set** éparses plus une colonne XML qui contient les valeurs de toutes les colonnes non Null qui sont membres du **column_set** éparses.|  
|Référencer une colonne par nom.|La colonne peut être référencée quel que soit l’état de sa colonne éparse ou son appartenance au **column_set**.|  
|Accédez aux colonnes membres du **column_set** par le biais d’une colonne XML calculée.|Vous pouvez avoir accès aux colonnes qui sont membres du **column_set** éparses en sélectionnant le **column_set** par nom. Vous pouvez également insérer et mettre à jour des valeurs dans ces colonnes en mettant à jour le code XML dans la colonne du **column_set**.<br /><br /> La valeur doit être conforme au schéma pour les colonnes du **column_set**.|  
|Extraire les métadonnées de toutes les colonnes dans une table via l'ensemble de lignes de schéma DBSCHEMA_COLUMNS sans restriction de colonne (OLE DB).|Retourne une ligne pour toutes les colonnes qui ne sont pas membres d’un **column_set**. Si la table possède un **column_set** éparses, une ligne sera retournée pour ce dernier.<br /><br /> Notez que, dans ce cas, des métadonnées ne sont pas retournées pour les colonnes qui sont membres d’un **column_set**.|  
|Récupérer des métadonnées pour toutes les colonnes, quel que soit le caractère épars ou l’appartenance à un **column_set**. De très nombreuses lignes peuvent alors être retournées.|Appelez IDBSchemaRowset::GetRowset pour l'ensemble de lignes de schéma DBSCHEMA_COLUMNS_EXTENDED.|  
|Récupérer des métadonnées uniquement pour les colonnes qui sont membres d’un **column_set**. De très nombreuses lignes peuvent alors être retournées.|Appelez IDBSchemaRowset::GetRowset pour l’ensemble de lignes de schéma DBSCHEMA_SPARSE_COLUMN_SET.|  
|Déterminer si une colonne est éparse.|Consultez la colonne SS_IS_SPARSE de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS (OLE DB).|  
|Déterminer si une colonne est un **column_set**.|Consultez la colonne SS_IS_COLUMN_SET de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS Ou consultez *dwFlags* retourné par IColumnsinfo::GetColumnInfo ou DBCOLUMNFLAGS dans l’ensemble de lignes retourné par IColumnsRowset::GetColumnsRowset. Pour les colonnes de **column_set**, DBCOLUMNFLAGS_SS_ISCOLUMNSET est défini.|  
|Importer et exporter des colonnes éparses via BCP pour une table sans **column_set**.|Aucun changement de comportement depuis les précédentes versions d’OLE DB Driver pour SQL Server.|  
|Importer et exporter des colonnes éparses via BCP pour une table avec un **column_set**.|**column_set** est importé et exporté de la même façon que le code XML, c’est-à-dire sous la forme **varbinary(max)** s’il est lié en tant que type binaire, ou sous la forme **nvarchar(max)** s’il est lié en tant que type **char** ou **wchar**.<br /><br /> Les colonnes qui sont membres du **column_set** éparses ne sont pas exportées en tant que colonnes distinctes ; elles sont uniquement exportées dans la valeur du **column_set**.|  
|Comportement de **queryout** pour BCP.|Aucune modification observée dans la gestion des colonnes explicitement nommées depuis les précédentes versions d’OLE DB Driver pour SQL Server.<br /><br /> Les scénarios impliquant des opérations d'importation et d'exportation entre les tables avec des schémas différents peuvent nécessiter une gestion spéciale.<br /><br /> Pour plus d'informations sur BCP, consultez la section « Prise en charge de la copie en bloc (BCP) pour les colonnes éparses » plus loin dans cette rubrique.|  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Les clients de bas niveau retournent uniquement des métadonnées pour les colonnes qui ne sont pas membres du **column_set** éparses pour SQLColumns et DBSCHMA_COLUMNS.
  
 Les clients de bas niveau peuvent accéder par nom aux colonnes membres du **column_set** éparses et la colonne de **column_set** sera accessible en tant que colonne XML pour les clients [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Prise en charge de la copie en bloc (BCP) pour les colonnes éparses  
 Aucune modification n’a été apportée à l’API BCP dans OLE DB pour les colonnes éparses ou les fonctionnalités **column_set**.  
  
 Si une table possède un **column_set**, les colonnes éparses ne sont pas traitées en tant que colonnes distinctes. Les valeurs de l'ensemble des colonnes éparses sont incluses dans la valeur du **column_set** qui est exporté de la même manière qu'une colonne XML, à savoir sous la forme **varbinary(max)** s'il est lié en tant que type binaire ou sous la forme **nvarchar(max)** s'il est lié en tant que type **char** ou **wchar**. Lors de l'importation, la valeur **column_set** doit être conforme au schéma du **column_set**.  
  
 Dans le cadre des opérations **queryout**, aucun changement n’intervient dans la manière dont les colonnes explicitement référencées sont gérées. Les colonnes de **column_set** affichent le même comportement que les colonnes XML et le caractère épars n’a aucune incidence sur la gestion des colonnes éparses nommées.  
  
 En revanche, si vous faites appel à **queryout** pour l’exportation et référencez par nom les colonnes éparses membres du jeu de colonnes éparses, vous ne pouvez procéder à aucune importation directe dans une table de structure identique. Ceci est lié au fait que BCP utilise des métadonnées cohérentes avec une opération **select \*** pour l’importation et est incapable de faire correspondre les colonnes membres de **column_set** avec ces métadonnées. Pour importer individuellement des colonnes membres de **column_set**, vous devez définir une vue dans la table qui référence les colonnes de **column_set** souhaitées, puis procéder à l’opération d’importation à l’aide de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [OLE DB Driver pour SQL Server](../../oledb/oledb-driver-for-sql-server.md)  
  
  
