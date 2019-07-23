---
title: Méthode setResponseBuffering (SQLServerStatement) | Microsoft Docs
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
ms.openlocfilehash: a55f1d5695c2595b5ea721680fc77f88d13494ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973108"
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
  
 **Chaîne** qui contient le mode de mise en mémoire tampon des réponses. Le mode valide peut être l’une des chaînes non sensibles à la casse suivantes : **full** ou **adaptive**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 **adaptive** consiste à mettre en mémoire tampon le moins de données possible lorsque cela s’impose.  
  
 **full** consiste à lire l’intégralité du résultat du serveur à l’exécution.  
  
 Adaptive est la valeur par défaut dans les versions 2,0 et 3,0 du pilote JDBC. Full était la valeur par défaut avant la version 2,0 du pilote JDBC.  
  
 La méthode [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) permet de remplacer la propriété **String** de connexion **responseBuffering** de l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) actuel. Pour plus d’informations sur l’utilisation du mode de mise en mémoire tampon des réponses, consultez Utilisation de la [mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Si l’application fournit une valeur de paramètre non valide à la méthode [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md), une exception [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Utilisation de la mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
