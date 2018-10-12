---
title: Méthode getXAConnection () | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7cffeb3479174f5bc79eff52331f5a9d0e46e65
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687677"
---
# <a name="getxaconnection-method-"></a>Méthode getXAConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Essaie d'établir une connexion de base de données physique qui peut être utilisée dans une transaction distribuée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet XAConnection.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes   
 Cette méthode getXAConnection est spécifiée par la méthode getXAConnection dans l’interface javax.sql.XADataSource.  
  
> [!NOTE]  
>  Cette méthode est généralement appelée par les implémentations de regroupement de connexions XA et non par le code d'application JDBC normal.  
  
## <a name="see-also"></a> Voir aussi  
 [getXAConnection, méthode &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource, méthodes](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource, membres](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource, classe](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
