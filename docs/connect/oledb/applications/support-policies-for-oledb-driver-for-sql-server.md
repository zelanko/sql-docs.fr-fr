---
title: Stratégies de prise en charge d’OLE DB Driver pour SQL Server | Microsoft Docs
description: Stratégies de prise en charge d’OLE DB Driver pour SQL Server
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b02789c787266a3370e3c5c9bfae50ea337d19db
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381861"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Stratégies de prise en charge d’OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article explique comment différents composants d’accès aux données peuvent être utilisés avec OLE DB pilote pour la SQL Server.  

## <a name="server-support"></a>Prise en charge du serveur  
 OLE DB pilote pour SQL Server prend en charge les connexions à [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] via [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].

## <a name="supported-operating-system-versions"></a>Versions du système d'exploitation prises en charge  
 Le tableau suivant répertorie les systèmes d’exploitation qui prennent en charge OLE DB pilote pour SQL Server.  

| Systèmes d’exploitation pris en charge |  |
|--------------------------------------|---------------------------------|   
| [Mise à jour](https://go.microsoft.com/fwlink/?linkid=2073785) de Microsoft Windows 8.1 + avril 2014  + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows 10<br /><br /> Microsoft Windows Server 2012 + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />[Mise à jour](https://go.microsoft.com/fwlink/?linkid=2073785) de Microsoft Windows Server 2012 R2 + avril 2014  + [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061)<br /><br />Microsoft Windows Server 2016<br /><br />Microsoft Windows Server 2019 |  |


## <a name="ado-support-policies"></a>Stratégies de prise en charge d’ADO  
 Les applications ADO peuvent utiliser le fournisseur OLE DB SQLOLEDB fourni avec Windows si elles n'ont pas besoin des fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  

 Les applications ADO peuvent utiliser le pilote OLE DB pour SQL Server, mais dans ce cas, elles doivent spécifier `DataTypeCompatibility=80` dans les chaînes de connexion. Seules les fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sont disponibles lorsque `DataTypeCompatibility=80` est présent dans les chaînes de connexion.  

## <a name="ole-db-support-policies"></a>Stratégies de prise en charge d’OLE DB  
Les applications peuvent utiliser le fournisseur OLE DB (SQLOLEDB) fourni avec le système d’exploitation Windows. Toutefois, il est en mode de maintenance et n’est plus mis à jour. Utilisez plutôt le pilote OLE DB pour SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>Voir aussi  
 [Création d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)   
