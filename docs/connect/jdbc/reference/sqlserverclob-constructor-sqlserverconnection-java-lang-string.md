---
title: SQLServerClob, constructeur (SQLServerConnection, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.SQLServerClob (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7058f4f7-ef3e-4d62-90d1-79299708b1eb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7a539ef893788be9e0200b9f412f8c3ed7652b26
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971799"
---
# <a name="sqlserverclob-constructor-sqlserverconnection-javalangstring"></a>Constructeur SQLServerClob (SQLServerConnection, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md), lorsqu’un objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) et une chaîne de données sont donnés.  
  
> [!NOTE]  
>  Cette méthode a été déconseillée dans la version 2.0 du pilote JDBC. Utilisez plutôt la méthode [createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public SQLServerClob(SQLServerConnection connection,  
                     java.lang.String data)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *connection*  
  
 Objet SQLServerConnection.  
  
 *data*  
  
 Données CLOB.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerClob, constructeurs](../../../connect/jdbc/reference/sqlserverclob-constructors.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
