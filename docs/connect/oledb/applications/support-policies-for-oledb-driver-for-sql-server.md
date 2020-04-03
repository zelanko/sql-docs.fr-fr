---
title: Stratégies de prise en charge d’OLE DB Driver pour SQL Server | Microsoft Docs
description: Stratégies de prise en charge d’OLE DB Driver pour SQL Server
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.custom: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 3f48aa8c68b364db98d1cd3111c11c6635ee5335
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79526824"
---
# <a name="support-policies-for-ole-db-driver-for-sql-server"></a>Stratégies de prise en charge d’OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Cet article décrit les façons dont différents composants d'accès aux données peuvent être utilisés avec OLE DB Driver pour SQL Server.  

## <a name="sql-version-support"></a>Prise en charge des versions SQL  

Le pilote OLE DB pour SQL Server a été testé et prend en charge les connexions aux versions suivantes de SQL Server.

| Version du pilote | Azure SQL Database | Azure SQL DW | Azure SQL Managed Instance | SQL Server 2019 | SQL Server 2017 | SQL Server 2016 | SQL Server 2014 | SQL Server 2012 |
|----|-|-|-|-|-|-|-|-|
|18.3|O|O|O|O|O|O|O|O|
|18.2|O|O|O|O|O|O|O|O|
|18.1|O|O|O| |O|O|O|O|
|18.0|O|O|O| |O|O|O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="supported-operating-system-versions"></a>Versions du système d'exploitation prises en charge  

Le tableau suivant liste les systèmes d’exploitation qui prennent en charge OLE DB Driver pour SQL Server.  

| Version du pilote | Windows Server 2019 | Windows Server 2016 | Windows Server 2012<sup>1</sup> | Windows Server 2012 R2<sup>2</sup> | Windows 10 | Windows 8.1<sup>3</sup> |
|----|-|-|-|-|-|-|
|18.3|O|O|O|O|O|O|
|18.2|O|O|O|O|O|O|
|18.1| |O|O|O|O|O|
|18.0| |O|O|O|O|O|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> Pris en charge sur Windows Server 2012 avec [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  
<sup>2</sup> Pris en charge sur Windows Server 2012 R2 avec la [mise à jour d’avril 2014](https://go.microsoft.com/fwlink/?linkid=2073785) et [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  
<sup>3</sup> Pris en charge sur Windows 8.1 avec la [mise à jour d’avril 2014](https://go.microsoft.com/fwlink/?linkid=2073785) et [KB2999226](https://go.microsoft.com/fwlink/?linkid=2074061).  

> [!NOTE]  
> L’utilisation de la page de codes UTF-8 sur Windows (« Use Unicode UTF-8 for worldwide language support ») n’est pas prise en charge.

## <a name="ado-support-policies"></a>Stratégies de prise en charge d’ADO  

Les applications ADO peuvent utiliser le fournisseur OLE DB SQLOLEDB fourni avec Windows si elles n'ont pas besoin des fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  

Les applications ADO peuvent utiliser OLE DB Driver pour SQL Server, mais dans ce cas elles doivent spécifier `DataTypeCompatibility=80` dans les chaînes de connexion. Seules les fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sont disponibles lorsque `DataTypeCompatibility=80` est présent dans les chaînes de connexion.  

## <a name="ole-db-support-policies"></a>Stratégies de prise en charge d’OLE DB  

Les applications peuvent utiliser le fournisseur OLE DB (SQLOLEDB) fourni avec le système d’exploitation Windows. Toutefois, il est en mode de maintenance et n’est plus mis à jour. Utilisez plutôt OLE DB Driver pour SQL Server (MSOLEDBSQL).

## <a name="see-also"></a>Voir aussi  

[Création d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)
