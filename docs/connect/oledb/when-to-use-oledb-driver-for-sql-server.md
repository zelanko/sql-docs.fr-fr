---
title: Quand utiliser OLE DB Driver pour SQL Server | Microsoft Docs
description: Quand utiliser OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d4e83751fe83db3ab678547a3a1fde68b5db22df
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107671"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Quand utiliser OLE DB Driver for SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server est une technologie que vous pouvez utiliser pour accéder aux données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  Pour en savoir plus sur les différentes technologies d’accès aux données, consultez [Data Access Technologies Road Map](http://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Avant d’utiliser OLE DB Driver for SQL Server comme technologie d’accès aux données de votre application, vous devez prendre en compte plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser OLE DB Driver for SQL Server. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB existantes, vous devez d’abord décider si vous avez besoin d’accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Mais si vous devez accéder à ces nouvelles fonctionnalités, telles que le [type de données xml](../../t-sql/xml/xml-transact-sql.md), vous devez utiliser OLE DB Driver for SQL Server.  
  
 Les deux OLE DB Driver pour SQL Server et MDAC prennent en charge l’isolation de transaction validée à l’aide de la version de ligne, mais uniquement pilote OLE DB SQL Server prend en charge la capture instantanée d’isolation des transactions de lecture. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour plus d’informations sur les différences entre le pilote OLE DB pour SQL Server et MDAC, consultez [mise à jour d’une Application vers OLE DB Driver pour SQL Server à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a> Voir aussi  
 [OLE DB Driver for SQL Server](../oledb/oledb-driver-for-sql-server.md)     
 [Rubriques de procédures liées à OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
