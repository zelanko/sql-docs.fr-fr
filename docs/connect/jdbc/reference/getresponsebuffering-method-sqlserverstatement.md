---
title: "Méthode getResponseBuffering (SQLServerStatement) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7d17eb34ef5acdeea9870d1b330423c015bf23a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>Méthode getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la réponse mise en mémoire tampon de mode pour cette [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient une minuscule **complète** ou **adaptive**.  
  
## <a name="remarks"></a>Notes  
 **Adaptive** spécifie la mise en mémoire tampon minimale des données lorsque cela est nécessaire.  
  
 **complète** spécifie la lecture de l’ensemble de résultats à partir du serveur en cours d’exécution.  
  
 **Adaptive** est la valeur par défaut du pilote JDBC versions 2.0 et 3.0. **complète** a la valeur par défaut avant la version 2.0 du pilote JDBC.  
  
 Pour plus d’informations sur l’utilisation du mode de mise en mémoire tampon de réponse, consultez [à l’aide de mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setResponseBuffering &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

