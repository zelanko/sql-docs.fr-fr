---
title: Méthode isValid (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 379d71b2100115bc1192a6f8f744b5afe92e5aed
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921087"
---
# <a name="isvalid-method-sqlserverconnection"></a>Méthode isValid (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) n’a pas été fermé et est toujours valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *timeout*  
  
 **int** spécifiant le nombre de secondes qui doivent s’écouler avant la validation de la connexion.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la connexion est valide ; **false** si la connexion n’est pas valide ou si la validité de la connexion ne peut pas être déterminée avant l’expiration du délai.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isValid est spécifiée par la méthode isValid de l’interface java.sql.Connection.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
