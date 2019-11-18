---
title: Prise en charge FILESTREAM | Microsoft Docs
description: Prise en charge de FILESTREAM dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 09/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: da67f050eba24ecf040124533c9d98c3f3f6bfec
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056732"
---
# <a name="filestream-support"></a>Prise en charge de FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

À partir de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], OLE DB pilote pour SQL Server prend en charge la fonctionnalité FILESTREAM améliorée. Pour obtenir des exemples, consultez [FileStream et OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md).  

FILESTREAM permet de stocker et d'accéder à de grandes valeurs binaires, soit par le biais de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], soit par accès direct au système de fichiers Windows. Une grande valeur binaire est une valeur supérieure à 2 gigaoctets (Go). Pour plus d’informations sur la prise en charge améliorée de FILESTREAM, consultez [filestream &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
Lorsqu’une connexion de base de données est ouverte, **\@\@TEXTSIZE** est défini avec la valeur -1 (« illimité ») par défaut.  
  
Il est également possible d'accéder et de mettre à jour des colonnes FILESTREAM à l'aide d'API de système de fichiers Windows.  
  
Pour plus d’informations, consultez [Accéder à des données FILESTREAM avec OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Interrogation de colonnes FILESTREAM  
Les ensembles de lignes de schéma dans OLE DB ne signalent pas si une colonne est une colonne FILESTREAM. ITableDefinition dans OLE DB ne peut pas être utilisé pour créer une colonne FILESTREAM.    
  
Pour créer des colonnes FILESTREAM ou détecter les colonnes existantes qui sont des colonnes FILESTREAM, vous pouvez utiliser la colonne **is_filestream** de l’affichage catalogue [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).  
  
Par exemple :  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilité de niveau supérieur  
Si votre client a été compilé à l’aide de OLE DB pilote pour SQL Server et que l’application se connecte à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), le comportement **varbinary (max)** est compatible avec le comportement introduit par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Autrement dit, la taille maximale des données retournées est limitée à 2 Go. Pour les valeurs de résultat supérieures à 2 Go, une troncation se produit et un avertissement « Troncation à droite de la chaîne de données » est retourné. 
  
Lorsque la compatibilité de type de données est définie à 80, le comportement client est cohérent avec le comportement client de bas niveau.  
  
Pour les clients qui utilisent SQLOLEDB ou d’autres fournisseurs publiés avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary(max)** est mappé à l’image.  
  
## <a name="comments"></a>Commentaires
- Pour envoyer et recevoir des valeurs **varbinary (max)** supérieures à 2 Go, une application utilise **DBTYPE_IUNKNOWN** dans les liaisons de paramètres et de résultats. Pour les paramètres, le fournisseur doit appeler IUnknown :: QueryInterface pour ISequentialStream et pour les résultats qui retournent ISequentialStream.  

-  Pour OLE DB, la vérification relative aux valeurs ISequentialStream est assouplie. Lorsque *wType* est **DBTYPE_IUNKNOWN** dans la structure **DBBINDING** , la vérification de la longueur peut être désactivée en omettant **DBPART_LENGTH** de *dwPart* ou en définissant la longueur des données (au décalage *obLength* dans le tampon de données) sur ~ 0. Dans ce cas, le fournisseur ne vérifiera pas la longueur de la valeur et demandera et retournera toutes les données disponibles par le biais du flux de données. Cette modification sera appliquée à tous les types d'objets volumineux (LOB) et XML, mais uniquement en cas de connexion à des serveurs [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] (ou ultérieurs). Cela offrira une plus grande souplesse aux développeurs, tout en maintenant la cohérence et la compatibilité descendante des applications existantes et des serveurs de niveau inférieur.  Cette modification affecte toutes les interfaces qui transfèrent des données, à l’de IRowset :: GetData, ICommand :: Execute et IRowsetFastLoad :: InsertRow.
 

## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
