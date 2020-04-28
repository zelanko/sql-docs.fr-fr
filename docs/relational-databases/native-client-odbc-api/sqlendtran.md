---
title: SQLEndTran | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9f2c4851b4cbb88c0d927aa4739e06501ce5ca1b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298509"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Par défaut, le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ferme le curseur associé à une instruction lorsque **SQLEndTran** valide ou restaure une opération. Les curseurs côté serveur sont fermés à moins qu'ils ne soient statiques. Lorsque **SQLEndTran** valide ou restaure une opération, le comportement du curseur associé à l'instruction est déterminé par la valeur de l'attribut de connexion ODBC du pilote spécifique au fournisseur, SQL_COPT_SS_PRESERVE_CURSORS, défini par [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Détails de l’implémentation de l’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Fonction SQLEndTran](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
