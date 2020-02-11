---
title: SQLStatistics | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLStatistics function
ms.assetid: e60101ae-a5f5-432f-a32a-d8e6fb0cbde8
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 103331bfff23e5fd315baf37407d385523a7b63d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73785372"
---
# <a name="sqlstatistics"></a>SQLStatistics
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLStatistics** peut être exécuté sur un curseur statique. Toute tentative d'exécution de **SQLStatistics** sur un curseur pouvant être mis à jour (curseur de jeu de clés ou curseur dynamique) retourne SQL_SUCCESS_WITH_INFO pour indiquer que le type de curseur a été modifié.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLStatistics, fonction](https://go.microsoft.com/fwlink/?LinkId=59372)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
