---
title: "setClientInfo (méthode) (java.lang.String, java.lang.String) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e136cd3eb2330bfd82c531acaa37838ed30e7713
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>Méthode setClientInfo (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la valeur de la propriété d'informations client spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom*  
  
 Chaîne qui contient le nom de la propriété d’informations client à définir.  
  
 *valeur*  
  
 Chaîne qui contient la valeur à affecter à la propriété d’informations client.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setClientInfo est spécifiée par la méthode setClientInfo dans l’interface java.sql.Connection.  
  
 Le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend pas en charge toutes les propriétés d’informations client. Dans la version 2.0 du pilote JDBC, cette méthode génère un avertissement pour une propriété. Les applications doivent utiliser [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) méthode de la [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe pour récupérer un message d’avertissement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
