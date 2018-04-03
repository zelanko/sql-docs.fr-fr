---
title: Prise en charge FILESTREAM | Documents Microsoft
description: Prise en charge FILESTREAM dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dc1a2d5e22e190eeed7bbdab27ee415f12552819
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="filestream-support"></a>Prise en charge de FILESTREAM
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

FILESTREAM permet de stocker et d'accéder à de grandes valeurs binaires, soit par le biais de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], soit par accès direct au système de fichiers Windows. Une grande valeur binaire est une valeur supérieure à 2 gigaoctets (Go). Pour plus d’informations sur la prise en charge améliorée de FILESTREAM, consultez [FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md).  
  
Lorsqu’une connexion de base de données est ouverte, **@@TEXTSIZE**  a la valeur -1 (« illimité »), par défaut.  
  
Il est également possible d'accéder et de mettre à jour des colonnes FILESTREAM à l'aide d'API de système de fichiers Windows.  
  
Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Prise en charge FILESTREAM &#40;OLE DB&#41;](../../oledb/ole-db/filestream-support-ole-db.md)    
  
-   [Accéder à des données FILESTREAM avec OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>Interrogation de colonnes FILESTREAM  
Les ensembles de lignes de schéma dans OLE DB ne signalent pas si une colonne est une colonne FILESTREAM. ITableDefinition dans OLE DB ne peut pas être utilisée pour créer une colonne FILESTREAM.    
  
Pour créer des colonnes FILESTREAM ou détecter les colonnes existantes sont des colonnes FILESTREAM, vous pouvez utiliser la **is_filestream** colonne de la [sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md) affichage catalogue.  
  
Par exemple :  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>Compatibilité de bas niveau  
Si votre client a été compilé à l’aide du pilote OLE DB pour SQL Server, et l’application se connecte à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]), puis **varbinary (max)** comportement est compatible avec le comportement introduit par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Autrement dit, la taille maximale des données retournées est limitée à 2 Go. Pour les valeurs de résultat supérieures que 2 Go, une troncation se produit et un avertissement « troncation à droite chaîne données » est renvoyé. 
  
Lorsque la compatibilité de type de données est définie à 80, le comportement client est cohérent avec le comportement client de bas niveau.  
  
Pour les clients qui utilisent SQLOLEDB ou autres fournisseurs qui ont été publiés avant la [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], **varbinary (max)** sera mappé à l’image.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
