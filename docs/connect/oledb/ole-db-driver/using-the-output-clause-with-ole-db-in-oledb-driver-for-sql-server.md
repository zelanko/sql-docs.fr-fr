---
title: Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server | Microsoft Docs
description: Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|oledb-driver-for-sql-server
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ad3408d0419e408809b151114d83a09d976505fa
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39109391"
---
# <a name="using-the-output-clause-with-ole-db-in-ole-db-driver-for-sql-server"></a>Utilisation de la clause OUTPUT avec OLE DB dans le pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Si vous utilisez une clause OUTPUT dans une commande INSERT, UPDATE, DELETE ou MERGE, le nombre de lignes affectées n’est pas disponible. L’application doit compter le nombre de lignes de l’ensemble de lignes retourné par la clause OUTPUT.  
  
## <a name="see-also"></a> Voir aussi  
 [Création d’une application OLE DB Driver pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md) 
  
  
