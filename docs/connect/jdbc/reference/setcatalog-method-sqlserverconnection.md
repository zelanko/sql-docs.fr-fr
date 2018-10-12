---
title: Méthode setCatalog (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a123f6d8a51bdb20f5a90bec39eb4b44b19f110e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622767"
---
# <a name="setcatalog-method-sqlserverconnection"></a>Méthode setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom de catalogue donné pour sélectionner un sous-espace de la base de données de cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) servant d’emplacement de travail.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalog*  
  
 Un **chaîne** qui contient le nom du catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setCatalog est spécifiée par la méthode setCatalog dans l’interface java.sql.Connection.  
  
 Le *catalogue* argument est ignoré par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automatiquement. Cette méthode permet de définir la propriété catalog de l’objet Connection. La propriété n'est pas définie implicitement de quelque autre façon.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
