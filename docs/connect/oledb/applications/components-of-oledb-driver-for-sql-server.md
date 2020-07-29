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
ms.openlocfilehash: c88ef12d636dd5b10e1b7b3cd9418df3e058325b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007054"
---
# <a name="components-of-ole-db-driver-for-sql-server"></a>Composants OLE DB Driver pour SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server contient les composants suivants :  

|Composant|Description|  
|---------------|-----------------|  
|msoledbsql.dll|Fichier DLL (Dynamic-Link Library) contenant l’ensemble des fonctionnalités OLE DB Driver pour SQL Server.|  
|msoledbsqlr.rll|Fichier de ressources qui accompagne la bibliothèque OLE DB Driver pour SQL Server.|   
|msoledbsql.h|Fichier d'en-tête OLE DB Driver pour SQL Server qui contient toutes les nouvelles définitions nécessaires à l’utilisation d’OLE DB Driver pour SQL Server. Ce fichier d'en-tête remplace le fichier d'en-tête sqloledb.h.<br /><br /> Remarque : Vous pouvez référencer msoledbsql.h et sqloledb.h dans le même programme tant que sqloledb.h est défini en premier.|  
|msoledbsql.lib|Fichier de bibliothèque nécessaire pour appeler directement la fonction [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) qui fait partie d’OLE DB Driver pour SQL Server.<br /><br /> Remarque : Si vous référencez le fichier msoledbsql.lib dans votre code de programmation, vous devez vérifier que le fichier msoledbsql.dll se trouve dans votre chemin système et dans le chemin système des utilisateurs qui emploient votre application.|  

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
