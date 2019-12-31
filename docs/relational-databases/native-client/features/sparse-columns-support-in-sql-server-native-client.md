---
title: Prise en charge des colonnes éparses dans SQL Native Client
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0271b8e07a6e9ea9b797427a66df097e1114cad4
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247419"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Prise en charge des colonnes éparses dans SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prend en charge les colonnes éparses. Pour plus d’informations sur les colonnes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]éparses dans, consultez [utiliser des colonnes éparses](../../../relational-databases/tables/use-sparse-columns.md) et [utiliser des jeux de colonnes](../../../relational-databases/tables/use-column-sets.md).  
  
 Pour plus d’informations sur la prise en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] charge des colonnes éparses dans Native Client, consultez [prise en charge des colonnes éparses &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) et les [colonnes éparses prennent en charge &#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md).  
  
 Pour plus d’informations sur les exemples d’applications qui illustrent cette fonctionnalité, consultez [Exemples de programmation de données SQL Server](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Scénarios utilisateur pour les colonnes éparses et SQL Server Native Client  
 Le tableau suivant résume les scénarios utilisateur courants avec colonnes éparses pour les utilisateurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
|Scénario|Comportement|  
|--------------|--------------|  
|**Select \* from table** ou IOpenRowset :: OPENROWSET.|Retourne toutes les colonnes qui ne sont pas membres du **column_set** éparses plus une colonne XML qui contient les valeurs de toutes les colonnes non Null qui sont membres du **column_set** éparses.|  
|Référencer une colonne par nom.|La colonne peut être référencée quel que soit l’état de sa colonne éparse ou son appartenance au **column_set**.|  
|Accédez aux colonnes membres du **column_set** par le biais d’une colonne XML calculée.|Vous pouvez avoir accès aux colonnes qui sont membres du **column_set** éparses en sélectionnant le **column_set** par nom. Vous pouvez également insérer et mettre à jour des valeurs dans ces colonnes en mettant à jour le code XML dans la colonne du **column_set**.<br /><br /> La valeur doit être conforme au schéma pour les colonnes du **column_set**.|  
|Récupérer les métadonnées de toutes les colonnes d’une table via SQLColumns avec un modèle de recherche de colonne NULL ou'% ' (ODBC); ou par le biais de l’ensemble de lignes de schéma DBSCHEMA_COLUMNS sans restriction de colonne (OLE DB).|Retourne une ligne pour toutes les colonnes qui ne sont pas membres d’un **column_set**. Si la table possède un **column_set** éparses, une ligne sera retournée pour ce dernier.<br /><br /> Notez que, dans ce cas, des métadonnées ne sont pas retournées pour les colonnes qui sont membres d’un **column_set**.|  
|Récupérer des métadonnées pour toutes les colonnes, quel que soit le caractère épars ou l’appartenance à un **column_set**. De très nombreuses lignes peuvent alors être retournées.|Définissez le champ descripteur SQL_SOPT_SS_NAME_SCOPE sur SQL_SS_NAME_SCOPE_EXTENDED et appelez [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Appelez IDBSchemaRowset :: GetRowset pour l’ensemble de lignes de schéma DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger directement les vues système.|  
|Récupérer des métadonnées uniquement pour les colonnes qui sont membres d’un **column_set**. De très nombreuses lignes peuvent alors être retournées.|Définissez le champ descripteur SQL_SOPT_SS_NAME_SCOPE sur SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET et appelez SQLColumns (ODBC).<br /><br /> Appelez IDBSchemaRowset :: GetRowset pour l’ensemble de lignes de schéma DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Déterminer si une colonne est éparse.|Consultez la SS_IS_SPARSE colonne du jeu de résultats SQLColumns (ODBC).<br /><br /> Consultez la colonne SS_IS_SPARSE de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Déterminer si une colonne est un **column_set**.|Consultez la colonne SS_IS_COLUMN_SET du jeu de résultats SQLColumns. Ou bien consultez l'attribut de colonne SQL_CA_SS_IS_COLUMN_SET (ODBC) spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Consultez la colonne SS_IS_COLUMN_SET de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS Ou consultez *dwFlags* retourné par IColumnsinfo :: GETCOLUMNINFO ou DBCOLUMNFLAGS dans l’ensemble de lignes retourné par IColumnsRowset :: GetColumnsRowset. Pour **column_set** colonnes, DBCOLUMNFLAGS_SS_ISCOLUMNSET sera définie (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Importer et exporter des colonnes éparses via BCP pour une table sans **column_set**.|Aucun changement de comportement depuis les précédentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|Importer et exporter des colonnes éparses via BCP pour une table avec un **column_set**.|La **column_set** est importée et exportée de la même façon que XML. autrement dit, en tant que **varbinary (max)** s’il est lié en tant que type binaire, ou en tant que type **nvarchar (max)** s’il est lié en tant que type **char** ou **WCHAR** .<br /><br /> Les colonnes qui sont membres du **column_set** éparses ne sont pas exportées en tant que colonnes distinctes ; elles sont uniquement exportées dans la valeur du **column_set**.|  
|comportement **queryout** pour BCP.|Aucune modification observée dans la gestion des colonnes explicitement nommées depuis les précédentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.<br /><br /> Les scénarios impliquant des opérations d'importation et d'exportation entre les tables avec des schémas différents peuvent nécessiter une gestion spéciale.<br /><br /> Pour plus d'informations sur BCP, consultez la section « Prise en charge de la copie en bloc (BCP) pour les colonnes éparses » plus loin dans cette rubrique.|  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Les clients de bas niveau retournent uniquement des métadonnées pour les colonnes qui ne sont pas membres du **column_set** éparses pour SQLColumns et DBSCHMA_COLUMNS. Les ensembles de lignes de schéma OLE DB [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] supplémentaires introduits dans Native Client ne seront pas disponibles, ni les modifications apportées à SQLColumns dans ODBC via SQL_SOPT_SS_NAME_SCOPE.  
  
 Les clients de bas niveau peuvent accéder par nom aux colonnes membres du **column_set** éparses et la colonne de **column_set** sera accessible en tant que colonne XML pour les clients [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Prise en charge de la copie en bloc (BCP) pour les colonnes éparses  
 Il n’y a aucune modification de l’API BCP dans ODBC ou OLE DB pour les colonnes éparses ou les fonctionnalités de **column_set** .  
  
 Si une table possède un **column_set**, les colonnes éparses ne sont pas traitées en tant que colonnes distinctes. Les valeurs de toutes les colonnes éparses sont incluses dans la valeur de la **column_set**, qui est exportée de la même façon qu’une colonne XML. autrement dit, en tant que **varbinary (max)** s’il est lié en tant que type binaire, ou en tant que type **nvarchar (max)** s’il est lié en tant que type **char** ou **WCHAR** ). Lors de l’importation, la valeur de **column_set** doit être conforme au schéma du **column_set**.  
  
 Dans le cadre des opérations **queryout**, aucun changement n’intervient dans la manière dont les colonnes explicitement référencées sont gérées. les colonnes de **column_set** ont le même comportement que les colonnes XML et la peu faible n’a aucun effet sur la gestion des colonnes éparses nommées.  
  
 En revanche, si vous faites appel à **queryout** pour l’exportation et référencez par nom les colonnes éparses membres du jeu de colonnes éparses, vous ne pouvez procéder à aucune importation directe dans une table de structure identique. Cela est dû au fait que BCP utilise des métadonnées cohérentes avec une opération **select &#42;** pour l’importation et qu’il ne parvient pas à faire correspondre **column_set** colonnes membres avec ces métadonnées. Pour importer individuellement des colonnes membres de **column_set**, vous devez définir une vue dans la table qui référence les colonnes de **column_set** souhaitées, puis procéder à l’opération d’importation à l’aide de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
