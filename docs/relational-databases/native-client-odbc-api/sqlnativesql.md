---
title: SQLNativeSql | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e4d2baef508d6273ec6c89cca38961aa22742e69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73926019"
---
# <a name="sqlnativesql"></a>SQLNativeSql
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client répond aux demandes **SQLNativeSql** sans visiter le serveur. La fonction teste efficacement la syntaxe d'instructions SQL. La vérification de la syntaxe ne détermine pas si des identificateurs ou les résultats d'expressions dans les instructions SQL sont valides, et l'exécution du code SQL natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourné par **SQLNativeSql** peut échouer.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNativeSql fonction)](https://go.microsoft.com/fwlink/?LinkID=59358)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
