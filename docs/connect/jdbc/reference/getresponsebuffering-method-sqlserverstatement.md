---
title: Méthode getResponseBuffering (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf5a9ee4d4aa001103840ba8768ba338baa42db8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67980402"
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>Méthode getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le mode de mise en mémoire tampon des réponses de cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant une minuscule, **full** ou **adaptative**.  
  
## <a name="remarks"></a>Notes  
 **adaptive** consiste à mettre en mémoire tampon le moins de données possible lorsque cela s’impose.  
  
 **full** consiste à lire l’intégralité du résultat du serveur à l’exécution.  
  
 **adaptive** est la valeur par défaut dans les versions 2.0 et 3.0 du pilote JDBC. **full** était la valeur par défaut avant la version 2.0 du pilote JDBC.  
  
 Pour plus d’informations sur le mode de mise en mémoire tampon des réponses, consultez [Utiliser la mise en mémoire tampon adaptative](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Voir aussi  
 [setResponseBuffering, méthode &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
