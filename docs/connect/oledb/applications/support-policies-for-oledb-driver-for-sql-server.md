---
title: Stratégies de prise en charge d’OLE DB Driver pour SQL Server | Microsoft Docs
description: Stratégies de prise en charge d’OLE DB Driver pour SQL Server
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ac76aabc7ba96ec5c867d7cb623f81909c577c3d
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106125"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Stratégies de prise en charge d’OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article explique comment divers composants d’accès aux données peuvent être utilisés avec OLE DB Driver pour SQL Server.  

## <a name="server-support"></a>Prise en charge de serveur  
 OLE DB Driver pour SQL Server prend en charge les connexions à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)],[!INCLUDE[ssSQL15](../../../includes/sssql15-md.md)], [!INCLUDE[ssSQL17](../../../includes/sssql17-md.md)], et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Versions du système d'exploitation prises en charge  
 Le tableau suivant répertorie les systèmes d’exploitation prise en charge OLE DB Driver pour SQL Server.  

|Systèmes d’exploitation pris en charge|  
|--------------------------------------|---------------------------------|   
|Microsoft Windows 8.1<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012<br /><br />Microsoft Windows Server 2012 R2<br /><br />Microsoft Windows Server 2016|  

## <a name="ado-support-policies"></a>Stratégies de prise en charge ADO  
 Les applications ADO peuvent utiliser le fournisseur OLE DB SQLOLEDB fourni avec Windows si elles n'ont pas besoin des fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  

 Applications ADO peuvent utiliser le pilote OLE DB pour SQL Server, mais s’ils le font, ils doivent spécifier `DataTypeCompatibility=80` dans les chaînes de connexion. Seules les fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sont disponibles lorsque `DataTypeCompatibility=80` est présent dans les chaînes de connexion.  

## <a name="ole-db-support-policies"></a>Stratégies de prise en charge OLE DB  
Les applications peuvent utiliser le fournisseur OLE DB (SQLOLEDB) fourni avec le système d’exploitation Windows. Toutefois, qui est en mode maintenance et n’est plus mis à jour. Vous devez utiliser le pilote OLE DB pour SQL Server (MSOLEDBSQL) à la place.

## <a name="see-also"></a> Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
