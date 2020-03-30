---
title: Méthode setAutoCommit (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dbf9b18fdc6b590f085b5be6babd64100006163a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975265"
---
# <a name="setautocommit-method-sqlserverconnection"></a>setAutoCommit, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le mode de validation automatique actuel de cet objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) selon l’état donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *value*  
  
 **true** afin d’activer le mode de validation automatique pour la connexion, **false** pour le désactiver.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setAutoCommit est spécifiée par la méthode setAutoCommit de l’interface java.sql.Connection.  
  
 Si une connexion est en mode de validation automatique, toutes ses instructions SQL sont exécutées et validées en tant que transactions individuelles. Autrement, ses instructions SQL sont regroupées dans des transactions qui prennent fin avec l’appel de la méthode [commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md) ou de la méthode [rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md). Par défaut, les nouvelles connexions sont en mode de validation automatique.  
  
 La validation se produit à la fin de l'instruction ou à l'exécution suivante, selon l'opération qui se produit en premier. Les instructions qui retournent un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), elles, se terminent lorsque le jeu de résultats a été fermé ou lorsque sa dernière ligne a été récupérée. Dans les cas plus avancés, une instruction unique peut retourner plusieurs résultats en plus des valeurs de paramètre de sortie. Dans ces cas, la validation se produit lorsque tous les résultats et valeurs de paramètre de sortie ont été récupérés.  
  
 Lorsque le mode de validation automatique a la valeur **false**, le pilote JDBC démarre implicitement une nouvelle transaction après chaque validation.  
  
> [!NOTE]  
>  Si cette méthode est appelée au cours d'une transaction, la transaction est validée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
