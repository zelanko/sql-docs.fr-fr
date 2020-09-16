---
title: Informations dans les interfaces d'erreur
description: Le pilote OLE DB Driver pour SQL Server communique certaines informations d’erreur et d’état dans les interfaces d’erreurs IErrorInfo, IErrorRecords et ISQLErrorInfo définies par OLE DB.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 023926ff67c85dcf8d95499b8281853bf7b3b1f3
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860004"
---
# <a name="information-in-error-interfaces"></a>Informations dans les interfaces d'erreur
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server signale certaines informations d’erreur et d’état dans les interfaces d’erreur **IErrorInfo**, **IErrorRecords** et **ISQLErrorInfo** définies par OLE DB.  
  
 OLE DB Driver pour SQL Server prend en charge les fonctions membres **IErrorInfo** comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetDescription**|Chaîne du message d'erreur descriptive.|  
|**GetGUID**|GUID de l'interface ayant défini l'erreur.|  
|**GetHelpContext**|Non pris en charge. Retourne toujours zéro.|  
|**GetHelpFile**|Non pris en charge. Retourne toujours la valeur Null.|  
|**GetSource**|Chaîne « Pilote Microsoft OLE DB pour SQL Server »|  
  
 OLE DB Driver pour SQL Server prend en charge les fonctions membres **IErrorRecords** accessibles au consommateur comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Remplit une structure ERRORINFO avec des informations de base sur une erreur. Une structure ERRORINFO contient des membres qui identifient la valeur de retour HRESULT pour l'erreur, ainsi que le fournisseur et l'interface auxquels l'erreur s'applique.|  
|**GetCustomErrorObject**|Retourne une référence sur les interfaces **ISQLErrorInfo** et [ISQLServerErrorInfo](https://docs.microsoft.com/sql/connect/oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db?view=sql-server-ver15).|  
|**GetErrorInfo**|Retourne une référence sur une interface **IErrorInfo**.|  
|**GetErrorParameters**|OLE DB Driver pour SQL Server ne retourne pas de paramètres au consommateur par le biais de **GetErrorParameters**.|  
|**GetRecordCount**|Nombre d'enregistrements d'erreur disponibles.|  
  
 OLE DB Driver pour SQL Server prend en charge les paramètres **ISQLErrorInfo::GetSQLInfo** comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Retourne une valeur SQLSTATE pour l'erreur. Les valeurs SQLSTATE sont définies dans les spécifications SQL-92, ODBC et ISO SQL, et API. Ni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ni OLE DB Driver pour SQL Server ne définissent de valeurs SQLSTATE spécifiques à l'implémentation.|  
|*plNativeError*|Retourne le numéro d’erreur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de **master.dbo.sysmessages** s’il est disponible. Les erreurs natives sont disponibles après une tentative d'initialisation réussie d'une source de données OLE DB Driver pour SQL Server. Avant la tentative, OLE DB Driver pour SQL Server retourne toujours zéro.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
