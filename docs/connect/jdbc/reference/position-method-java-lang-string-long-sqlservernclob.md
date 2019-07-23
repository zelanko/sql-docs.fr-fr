---
title: position, méthode (java.lang.String, long) (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dd9e30039b0d5ef429b8e729ce36f7b085e5cfc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976465"
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>Méthode position (java.lang.String, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la position de caractère à laquelle la sous-chaîne *searchstr* spécifiée apparaît dans la valeur **NCLOB** représentée par cet objet **NCLOB** .  
  
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
  
## <a name="return-value"></a>Valeur retournée  
 Position à laquelle la sous-chaîne doit s'afficher, ou -1 si elle est absente. La première position est 1.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode de position est spécifiée par la méthode position dans l’interface java. Sql. NClob.  
  
## <a name="see-also"></a>Voir aussi  
 [position, &#40;méthode SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob, méthodes](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob, membres](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob, classe](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
