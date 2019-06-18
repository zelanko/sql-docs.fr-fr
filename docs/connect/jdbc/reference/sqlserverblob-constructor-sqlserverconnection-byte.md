---
title: SQLServerBlob, constructeur (SQLServerConnection, byte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection, byte[].SQLServerBlob
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9fe573e3-30db-4828-abab-e9346493e931
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aff7392d2aceab631e5e53cd446696f8ce15ab43
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66773103"
---
# <a name="sqlserverblob-constructor-sqlserverconnection-byte"></a>SQLServerBlob, constructeur (SQLServerConnection, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md) lors de la spécification d’un objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) et d’un tableau d’**octets**.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la version 2.0 du pilote JDBC. Utilisez plutôt la méthode [createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public SQLServerBlob(SQLServerConnection connection,  
                     byte[] data)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *connection*  
  
 Objet SQLServerConnection.  
  
 *data*  
  
 Tableau d’**octets**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerBlob, constructeurs](../../../connect/jdbc/reference/sqlserverblob-constructors.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
