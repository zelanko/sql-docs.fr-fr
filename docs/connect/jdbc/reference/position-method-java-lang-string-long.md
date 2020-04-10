---
title: Méthode position (java.lang.String, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.position (java.lang.String, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86fad8ed-375a-42e1-b40e-1fa085957a2c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 432ee4fccc21a57130e1bccad9c43b50e2b992ba
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914375"
---
# <a name="position-method-javalangstring-long"></a>Méthode position (java.lang.String, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la position de caractère de la sous-chaîne spécifiée dans l'objet CLOB, en fonction de la position de départ donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long position(java.lang.String searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *searchstr*  
  
 Sous-chaîne à rechercher.  
  
 *start*  
  
 Position à laquelle démarrer la recherche ; la première position est 1.  
  
## <a name="return-value"></a>Valeur de retour  
 Position à laquelle la sous-chaîne doit s'afficher, ou -1 si elle est absente. La première position est 1.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode position est spécifiée par la méthode position de l’interface java.sql.Clob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode position &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [SQLServerClob, méthodes](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob, classe](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
