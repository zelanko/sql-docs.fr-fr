---
title: Méthode getMaxBinaryLiteralLength (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxBinaryLiteralLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 42e49ff9-8072-44e4-ad75-c864c3a4ad8c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b10b7bc63a4d3defc1d0465dd675bc9d7d6f872
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67982364"
---
# <a name="getmaxbinaryliterallength-method-sqlserverdatabasemetadata"></a>Méthode getMaxBinaryLiteralLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de caractères hexadécimaux autorisé par cette base de données dans un littéral binaire inline.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxBinaryLiteralLength()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal de caractères hexadécimaux autorisé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxBinaryLiteralLength est spécifiée par la méthode getMaxBinaryLiteralLength de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
