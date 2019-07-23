---
title: Composants du pilote OLE DB Driver pour SQL Server | Microsoft Docs
description: Composants OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], components
- components [OLE DB Driver for SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5a5124519bd95ec02e93a007d9881ec80814cfc8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989318"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Composants OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB pilote pour SQL Server contient les composants suivants:  

|Composant|Description|  
|---------------|-----------------|  
|msoledbsql.dll|Fichier de bibliothèque de liens dynamiques (DLL) qui contient tous les OLE DB pilote pour la fonctionnalité SQL Server.|  
|msoledbsqlr.rll|Fichier de ressources associé pour le pilote OLE DB pour la bibliothèque SQL Server.|   
|msoledbsql.h|Le OLE DB pilote du fichier d’en-tête SQL Server qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote OLE DB pour SQL Server. Ce fichier d’en-tête remplace le fichier d’en-tête SQLOLEDB. h.<br /><br /> Remarque: vous pouvez référencer msoledbsql. h et SQLOLEDB. h dans le même programme tant que sqloledb. h est défini en premier.|  
|msoledbsql.lib|Fichier de bibliothèque nécessaire pour appeler directement la fonction [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) qui fait partie du pilote OLE DB pour SQL Server.<br /><br /> Remarque : Si vous référencez le fichier msoledbsql.lib dans votre code de programmation, vous devez vérifier que le fichier msoledbsql.dll se trouve dans votre chemin système et dans le chemin système des utilisateurs qui emploient votre application.|  

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
