---
title: Quand utiliser le pilote OLE DB pour SQL Server | Documents Microsoft
description: Quand utiliser un pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: cf64d680b0d45bf7b46ba5d07df8a291723bb0cb
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Quand utiliser le pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pilote OLE DB pour SQL Server est une technologie que vous pouvez utiliser pour accéder aux données dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  Pour en savoir plus sur les technologies d’accès aux données différents, consultez [carte routière de données Access Technologies](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 Lorsque vous décidez s’il faut utiliser le pilote OLE DB pour SQL Server en tant que la technologie d’accès aux données de votre application, vous devez considérer plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le pilote OLE DB pour SQL Server. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB existantes, le principal problème est que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Mais si vous avez besoin accéder à ces nouvelles fonctionnalités, telles que la [type de données xml](../../t-sql/xml/xml-transact-sql.md), vous devez utiliser le pilote OLE DB pour SQL Server.  
  
 Les deux pilote OLE DB pour SQL Server et MDAC lecture d’isolation de transaction validée à l’aide de la version de la ligne, mais uniquement pilote OLE DB pour SQL Server prend en charge la capture instantanée d’isolation des transactions. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour plus d’informations sur les différences entre le pilote OLE DB pour SQL Server et MDAC, consultez [mise à jour d’une Application de pilote OLE DB pour SQL Server à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server OLE DB pilote](../oledb/oledb-driver-for-sql-server-programming.md)     
 [Rubriques de procédures OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
