---
title: Prise en charge de UTF-16 dans OLE DB Driver pour SQL Server | Microsoft Docs
description: Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8374545412ca244e6af643ed10f101a714985da6
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108141"
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un résultat de colonne ou d’un paramètre de sortie et que le caractère **wchar** écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d’une paire de substitution, et si le caractère **wchar** suivant est un point de code de substitut faible, OLE DB Driver pour SQL Server n’ajoutera pas le point de code de substitut étendu à la mémoire tampon.  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
