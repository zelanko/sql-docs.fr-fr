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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: f398cb4ca6cdeaa9484e01b5ca41ae28b7d9f095
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003364"
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
|**GetCustomErrorObject**|Retourne une référence sur les interfaces **ISQLErrorInfo** et [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1).|  
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
  
  
