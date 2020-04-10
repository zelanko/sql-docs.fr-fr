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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb6b459f8193daebb69ad67ffaab5beab526f710
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920391"
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
  
  
