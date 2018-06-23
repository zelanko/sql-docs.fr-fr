---
title: Pour plus d’informations dans les Interfaces d’erreur | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6057ecaddf37f0b0a8b6fab50ac6aef5d4840515
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141279"
---
# <a name="information-in-error-interfaces"></a>Informations dans les interfaces d'erreur
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client signale certaines informations d’erreur et d’état dans les interfaces d’erreur défini par OLE DB **IErrorInfo**, **IErrorRecords**, et **ISQLErrorInfo** .  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client **IErrorInfo** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetDescription**|Chaîne du message d'erreur descriptive.|  
|**GetGUID**|GUID de l'interface ayant défini l'erreur.|  
|**GetHelpContext**|Non pris en charge. Retourne toujours zéro.|  
|**GetHelpFile**|Non pris en charge. Retourne toujours la valeur Null.|  
|**GetSource**|Chaîne « Microsoft SQL Server Native Client ».|  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge disponibles de consommateur **IErrorRecords** membre fonctionne comme suit.  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|**GetBasicErrorInfo**|Remplit une structure ERRORINFO avec des informations de base sur une erreur. Une structure ERRORINFO contient des membres qui identifient la valeur de retour HRESULT pour l'erreur, ainsi que le fournisseur et l'interface auxquels l'erreur s'applique.|  
|**GetCustomErrorObject**|Retourne une référence sur les interfaces **ISQLErrorInfo,** et [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).|  
|**GetErrorInfo**|Retourne une référence à un **IErrorInfo** interface.|  
|**GetErrorParameters**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client ne retourne pas de paramètres au consommateur via **GetErrorParameters**.|  
|**GetRecordCount**|Nombre d'enregistrements d'erreur disponibles.|  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client **ISQLErrorInfo::GetSQLInfo** paramètres comme suit.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pbstrSQLState*|Retourne une valeur SQLSTATE pour l'erreur. Les valeurs SQLSTATE sont définies dans les spécifications SQL-92, ODBC et ISO SQL, et API. Ni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ni le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif défini par les valeurs SQLSTATE spécifiques à l’implémentation.|  
|*plNativeError*|Retourne le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] numéro d’erreur de **master.dbo.sysmessages** lorsqu’il est disponible. Erreurs natives sont disponibles après une tentative d’initialiser un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données du fournisseur OLE DB Native Client. Avant la tentative, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif retourne toujours zéro.|  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](errors.md)  
  
  