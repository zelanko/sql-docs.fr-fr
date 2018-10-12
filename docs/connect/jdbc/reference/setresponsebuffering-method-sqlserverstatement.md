---
title: setResponseBuffering, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 946792cc2f1d2f96f51785322e211ec959dc3722
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47820777"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>Méthode setResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le mode de mise en mémoire tampon des réponses de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) selon **String full** ou **adaptive**, sans respect de la casse.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *value*  
  
 Un **chaîne** qui contient le mode de mise en mémoire tampon de réponse. Le mode valide peut être l’une des chaînes non sensibles à la casse suivantes : **full** ou **adaptive**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 **adaptive** consiste à mettre en mémoire tampon le moins de données possible lorsque cela s’impose.  
  
 **full** consiste à lire l’intégralité du résultat du serveur à l’exécution.  
  
 « Adaptive » est la valeur par défaut dans le pilote JDBC version 2.0 et 3.0. la valeur par défaut avant la version 2.0 du pilote JDBC a été complète.  
  
 La méthode [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) permet de remplacer la propriété **String** de connexion **responseBuffering** de l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) actuel. Pour plus d’informations sur l’utilisation de la réponse en mode de mise en mémoire tampon, consultez [à l’aide de mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Si l’application fournit une valeur de paramètre non valide à la méthode [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md), une exception [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) est levée.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Utilisation de la mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
