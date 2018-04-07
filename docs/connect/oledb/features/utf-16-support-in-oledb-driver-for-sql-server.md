---
title: Prise en charge de UTF-16 dans le pilote OLE DB pour SQL Server | Documents Microsoft
description: Prise en charge de UTF-16 dans le pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a0f710e6f567f789771a80677beb24d24b1c8f5d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="utf-16-support-in-ole-db-driver-for-sql-server"></a>Prise en charge de UTF-16 dans le pilote OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un paramètre de résultat ou de la sortie de colonne et si les **wchar** caractère écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d’un paire de substitution et si la prochaine **wchar** caractère est un point de code de substitution faible, le pilote OLE DB pour SQL Server n’ajoutera pas le point de code de substitut pour la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
  
  
