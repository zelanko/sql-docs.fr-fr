---
title: Prise en charge des colonnes éparses dans SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 79151d13f5b90e7da8ea50d3472d05ed46423e2e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225755"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Prise en charge des colonnes éparses dans SQL Server Native Client
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prend en charge les colonnes éparses. Pour plus d’informations sur les colonnes éparses dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [utiliser des colonnes éparses](../../tables/use-sparse-columns.md) et [utiliser des jeux de colonnes](../../tables/use-column-sets.md).  
  
 Pour plus d’informations sur les colonnes éparses prennent en charge dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, consultez [colonnes éparses prennent en charge &#40;ODBC&#41; ](../odbc/sparse-columns-support-odbc.md) et [colonnes éparses prennent en charge &#40;OLE DB&#41; ](../ole-db/sparse-columns-support-ole-db.md) .  
  
 Pour plus d’informations sur les exemples d’applications qui illustrent cette fonctionnalité, consultez [Exemples de programmation de données SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Scénarios utilisateur pour les colonnes éparses et SQL Server Native Client  
 Le tableau suivant résume les scénarios utilisateur courants avec colonnes éparses pour les utilisateurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
|Scénario|Comportement|  
|--------------|--------------|  
|**Sélectionnez \* à partir de la table** ou IOpenRowset::OpenRowset.|Retourne toutes les colonnes qui ne sont pas membres du `column_set` éparse plus une colonne XML qui contient les valeurs de toutes les colonnes non NULL qui sont membres du `column_set` éparse.|  
|Référencer une colonne par nom.|La colonne peut être référencée quel que soit l'état de sa colonne éparse ou son appartenance à `column_set`.|  
|Accédez aux colonnes membres de `column_set` par le biais d'une colonne XML calculée.|Vous pouvez avoir accès aux colonnes qui sont membres du `column_set` éparse en sélectionnant le `column_set` par nom. Vous pouvez également insérer et mettre à jour des valeurs dans ces colonnes en mettant à jour le code XML dans la colonne `column_set`.<br /><br /> La valeur doit être conforme au schéma pour les colonnes `column_set`.|  
|Récupérer des métadonnées pour toutes les colonnes dans une table via SQLColumns avec un modèle de recherche de colonne NULL ou '%' (ODBC) ; ou via l’ensemble de lignes de schéma DBSCHEMA_COLUMNS sans aucune restriction de colonne (OLE DB).|Retourne une ligne pour toutes les colonnes qui ne sont pas membres d'un `column_set`. Si la table possède un `column_set` éparse, une ligne sera retournée pour ce dernier.<br /><br /> Notez que, dans ce cas, des métadonnées ne sont pas retournées pour les colonnes qui sont membres d'un `column_set`.|  
|Extraire les métadonnées de toutes les colonnes, quel que soit le caractère éparse ou l'appartenance à un `column_set`. De très nombreuses lignes peuvent alors être retournées.|Définissez le champ de descripteur SQL_SOPT_SS_NAME_SCOPE sur SQL_SS_NAME_SCOPE_EXTENDED et appelez [SQLColumns](../../native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Appeler IDBSchemaRowset::GetRowset pour l’ensemble de lignes de schéma DBSCHEMA_COLUMNS_EXTENDED (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application peut interroger directement les vues système.|  
|Extraire les métadonnées uniquement pour les colonnes qui sont membres d'un `column_set`. De très nombreuses lignes peuvent alors être retournées.|Définissez le champ de descripteur SQL_SOPT_SS_NAME_SCOPE sur SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET et appelez SQLColumns (ODBC).<br /><br /> Appeler IDBSchemaRowset::GetRowset pour l’ensemble de lignes de schéma DBSCHEMA_SPARSE_COLUMN_SET (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Déterminer si une colonne est éparse.|Consultez la colonne SS_IS_SPARSE du jeu de résultats SQLColumns (ODBC).<br /><br /> Consultez la colonne SS_IS_SPARSE de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Déterminer si une colonne est un `column_set`.|Consultez la colonne SS_IS_COLUMN_SET du jeu de résultats SQLColumns. Ou bien consultez l'attribut de colonne SQL_CA_SS_IS_COLUMN_SET (ODBC) spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Consultez la colonne SS_IS_COLUMN_SET de l'ensemble de lignes de schéma DBSCHEMA_COLUMNS Ou consultez *dwFlags* retournée par IColumnsinfo::GetColumnInfo ou bien DBCOLUMNFLAGS dans l’ensemble de lignes retourné par IColumnsRowset::GetColumnsRowset. Pour les colonnes `column_set`, DBCOLUMNFLAGS_SS_ISCOLUMNSET est défini (OLE DB).<br /><br /> Ce scénario n'est pas possible depuis une application qui utilise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client à partir d'une version antérieure à [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. Toutefois, une telle application offre la possibilité d'interroger les vues système.|  
|Importer et exporter des colonnes éparses via BCP pour une table sans aucune `column_set`.|Aucun changement de comportement depuis les précédentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|Importer et exporter des colonnes éparses via BCP pour une table sans `column_set`.|Le `column_set` est importé et exporté de la même façon en tant que XML ; autrement dit, en tant que `varbinary(max)` si lié sous la forme d’un type binaire ou `nvarchar(max)` si liées en tant qu’un `char` ou **wchar** type.<br /><br /> Les colonnes qui sont membres du `column_set` éparse ne sont pas exportées en tant que colonnes distinctes ; elles sont uniquement exportées dans la valeur du `column_set`.|  
|Comportement de `queryout` pour BCP.|Aucune modification observée dans la gestion des colonnes explicitement nommées depuis les précédentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.<br /><br /> Les scénarios impliquant des opérations d'importation et d'exportation entre les tables avec des schémas différents peuvent nécessiter une gestion spéciale.<br /><br /> Pour plus d'informations sur BCP, consultez la section « Prise en charge de la copie en bloc (BCP) pour les colonnes éparses » plus loin dans cette rubrique.|  
  
## <a name="down-level-client-behavior"></a>Comportement de client de bas niveau  
 Les clients de bas niveau retournent des métadonnées uniquement pour les colonnes qui ne sont pas membres d’éparse `column_set` pour SQLColumns et DBSCHMA_COLUMNS. L’autres ensembles de lignes de schéma OLE DB introduites dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client ne sera pas disponible, ni les modifications apportées à SQLColumns dans ODBC via SQL_SOPT_SS_NAME_SCOPE.  
  
 Les clients de bas niveau peuvent accéder par nom aux colonnes membres du `column_set` épars et la colonne `column_set` sera accessible en tant que colonne XML pour les clients [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Prise en charge de la copie en bloc (BCP) pour les colonnes éparses  
 Que ce soit dans ODBC ou OLE DB, aucune modification de l'API BCP n'a été effectuée pour les colonnes éparses ou les fonctionnalités `column_set`.  
  
 Si une table possède un `column_set`, les colonnes éparses ne sont pas traitées en tant que colonnes distinctes. Les valeurs de toutes les colonnes éparses sont incluses dans la valeur de la `column_set`, qui est exporté de la même façon qu’une colonne XML ; autrement dit, en tant que `varbinary(max)` si lié sous la forme d’un type binaire ou `nvarchar(max)` si liées en tant qu’un `char` ou **wchar** type). Lors de l'importation, la valeur `column_set` doit être conforme au schéma du `column_set`.  
  
 Dans le cadre des opérations `queryout`, aucun changement n'intervient dans la manière dont les colonnes explicitement référencées sont gérées. Les colonnes `column_set` affichent le même comportement que les colonnes XML et le caractère éparse n'a aucune incidence sur la gestion des colonnes éparses nommées.  
  
 En revanche, si vous faites appel à `queryout` pour l'exportation et référencez par nom les colonnes éparses membres du jeu de colonnes éparses, vous ne pouvez procéder à aucune importation directe dans une table de structure identique. Il s’agit étant donné que BCP utilise des métadonnées cohérentes avec une **sélectionnez \***  opération pour l’importation et ne peut pas correspondre à `column_set` colonnes membres avec ces métadonnées. Pour importer individuellement des colonnes membres `column_set`, vous devez définir une vue dans la table qui référence les colonnes `column_set` souhaitées, puis procédez à l'opération d'importation à l'aide de la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../sql-server-native-client-programming.md)  
  
  
