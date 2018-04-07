---
title: Prendre en charge des stratégies pour le pilote OLE DB pour SQL Server | Documents Microsoft
description: Stratégies de prise en charge pour le pilote OLE DB pour SQL Server
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 374660fdba66e5c445ae441d988a3701de548427
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Stratégies de prise en charge pour le pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cet article décrit les divers composants d’accès aux données peuvent être utilisés avec le pilote OLE DB pour SQL Server.  

## <a name="server-support"></a>Prise en charge de serveur  
 Pilote OLE DB pour SQL Server prend en charge les connexions à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Versions du système d'exploitation prises en charge  
 Le tableau suivant répertorie les systèmes d’exploitation prise en charge pilote OLE DB pour SQL Server.  

|Systèmes d’exploitation pris en charge|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Stratégies de prise en charge ADO  
 Les applications ADO peuvent utiliser le fournisseur OLE DB SQLOLEDB fourni avec Windows si elles n'ont pas besoin des fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  

 Applications ADO peuvent utiliser le pilote OLE DB pour SQL Server, mais pour cela, ils doivent spécifier `DataTypeCompatibility=80` dans les chaînes de connexion. Seules les fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sont disponibles lorsque `DataTypeCompatibility=80` est présent dans les chaînes de connexion.  

## <a name="ole-db-support-policies"></a>Stratégies de prise en charge OLE DB  
Applications peuvent utiliser le fournisseur OLE DB (SQLOLEDB) inclus avec le système d’exploitation Windows. Toutefois, qui est en mode maintenance et n’est plus mis à jour. Vous devez utiliser le pilote OLE DB pour SQL Server (MSOLEDBSQL) à la place.

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
