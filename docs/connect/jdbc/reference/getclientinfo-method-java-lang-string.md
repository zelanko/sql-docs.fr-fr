---
title: Méthode getClientInfo (Java. lang. String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d3005e2b5ae8628ab31ceeb6314159afd796e83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953137"
---
# <a name="getclientinfo-method-javalangstring"></a>Méthode getClientInfo (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la propriété d'informations client spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom*  
  
 Chaîne qui contient le nom de la propriété d’informations client à récupérer.  
  
## <a name="return-value"></a>Valeur retournée  
 Chaîne qui contient la valeur de la propriété d’informations client.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getClientInfo est spécifiée par la méthode getClientInfo dans l’interface java. Sql. Connection.  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ne prend en charge aucune propriété d’informations client. Par conséquent, cette méthode retourne **Null**.  
  
 De façon similaire, les applications peuvent utiliser la méthode [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) de la classe [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) pour récupérer la liste des propriétés d’informations client prises en charge par le pilote. La méthode [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) retourne un jeu de résultats vide.  
  
## <a name="see-also"></a>Voir aussi  
 [getClientInfo, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
