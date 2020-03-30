---
title: Quand utiliser le pilote OLE DB pour SQL Server | Microsoft Docs
description: Quand utiliser OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 74bd79c24b913cd3c3d2f782b77cf2bb4c23e397
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015179"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Quand utiliser OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server est une technologie que vous pouvez utiliser pour accéder aux données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Pour en savoir plus sur les différentes technologies d’accès aux données, consultez [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Avant d’utiliser OLE DB Driver for SQL Server comme technologie d’accès aux données de votre application, vous devez prendre en compte plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser OLE DB Driver for SQL Server. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB existantes, vous devez d’abord décider si vous avez besoin d’accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Mais si vous devez accéder à ces nouvelles fonctionnalités, telles que le [type de données xml](../../t-sql/xml/xml-transact-sql.md), vous devez utiliser OLE DB Driver for SQL Server.  
  
 OLE DB Driver pour SQL Server et MDAC prennent tous deux en charge l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne, mais seul OLE DB Driver pour SQL Server prend en charge l'isolation de la transaction d'instantané. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour plus d’informations sur les différences entre OLE DB Driver pour SQL Server et MDAC, consultez [Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Voir aussi  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Rubriques de procédures liées à OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
