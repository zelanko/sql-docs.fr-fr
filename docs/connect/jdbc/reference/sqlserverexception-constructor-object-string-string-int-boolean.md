---
title: Constructeur SQLServerException (java.lang.Object, java.lang.String, java.lang.String, int, boolean) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b8c39021b8afac5631e44cddd8874cbf22975a3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670027"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>Constructeur SQLServerException (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe en fonction d’un **objet**, un **chaîne** objet, un **chaîne** (objet), un **int**et un **booléenne**.

## <a name="syntax"></a>Syntaxe  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            int errNum,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Paramètres  
 *obj*  
  
 La mémoire tampon d’e/s qui a généré l’exception.

 *errText*  
  
 Chaîne contenant le texte d’erreur.
  
 *sqlState*  
  
 Un objet d’énumération qui contient l’état SQL.
 
 *errNum*  
  
 Int qui contiennent le code d’erreur pour l’exception.
 
 *bStack*  
  
 Valeur booléenne qui indique si la trace de pile doit être générée.
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
