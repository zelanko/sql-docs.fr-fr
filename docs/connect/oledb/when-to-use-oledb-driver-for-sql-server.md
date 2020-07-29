---
title: Quand utiliser OLE DB Driver
description: Découvrez quand utiliser OLE DB Driver pour SQL Server et les concepts d’accès aux données de haut niveau qui le différencient des autres pilotes.
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
ms.openlocfilehash: 114a0e65f6d813bb2d43ca8641e3260e9b88f668
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011895"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Quand utiliser OLE DB Driver pour SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server est une technologie que vous pouvez utiliser pour accéder aux données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Pour en savoir plus sur les différentes technologies d’accès aux données, consultez [Data Access Technologies Road Map](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 Avant d’utiliser OLE DB Driver for SQL Server comme technologie d’accès aux données de votre application, vous devez prendre en compte plusieurs facteurs.  
  
 Pour les nouvelles applications, si vous utilisez un langage de programmation managé tel que Microsoft Visual C# ou Visual Basic et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], qui fait partie du .NET Framework.  
  
 Si vous développez une application COM et que vous devez accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser OLE DB Driver for SQL Server. Si vous n'avez pas besoin d'accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC (Windows Data Access Components).  
  
 Pour les applications OLE DB existantes, vous devez d’abord décider si vous avez besoin d’accéder aux nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous possédez une application déjà rodée qui n'a pas besoin des nouvelles fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez continuer à utiliser WDAC. Mais si vous devez accéder à ces nouvelles fonctionnalités, telles que le [type de données xml](../../t-sql/xml/xml-transact-sql.md), vous devez utiliser OLE DB Driver for SQL Server.  
  
 OLE DB Driver pour SQL Server et MDAC prennent tous deux en charge l'isolation de la transaction de lecture validée à l'aide du contrôle de version de ligne, mais seul OLE DB Driver pour SQL Server prend en charge l'isolation de la transaction d'instantané. (En termes de programmation, l'isolation des transactions de lecture validée avec le contrôle de version de ligne équivaut à la transaction de lecture validée.)  
  
 Pour plus d’informations sur les différences entre OLE DB Driver pour SQL Server et MDAC, consultez [Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a> Voir aussi  
 [OLE DB Driver pour SQL Server](oledb-driver-for-sql-server.md)  
 [Rubriques de procédures liées à OLE DB](ole-db-how-to/ole-db-how-to-topics.md)  
  
  
