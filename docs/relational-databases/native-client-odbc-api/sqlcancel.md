---
title: SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1758088319a712564fe2f11a136f5833b12111f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014699"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  La rubrique [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) indique que dans ODBC 2.x, si une application appelle **SQLCancel** alous qu'aucun traitement n'est en cours sur l'instruction, **SQLCancel** a le même effet que **SQLFreeStmt** avec l'option **SQL_CLOSE** ; ce compoutement est défini uniquement par souci d'exhaustivité et les applications doivent appeler **SQLFreeStmt** ou **SQLCloseCursou** to close cursous. Mais même si votre application [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit 3.5.x ou version ultérieure pour l'API ODBC, la fonction **SQLCancel** utilisera le comportement ODBC 2.x.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
