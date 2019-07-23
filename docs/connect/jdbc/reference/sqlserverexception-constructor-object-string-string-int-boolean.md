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
ms.openlocfilehash: 72ae0e8ed3c65a795723326d7ca49e2f5a909f18
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67971148"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-int-boolean"></a>Constructeur SQLServerException (java.lang.Object, java.lang.String, java.lang.String, int, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) en fonction d’un **objet**, d’un objet **String** , d’un objet **String** , d’un **entier**et d’un **booléen**.

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
  
 Mémoire tampon d’e/s qui a généré l’exception.

 *errText*  
  
 Chaîne contenant le texte de l’erreur.
  
 *sqlState*  
  
 Objet enum qui contient l’état SQL.
 
 *errNum*  
  
 Entier qui contient le code d’erreur de l’exception.
 
 *bStack*  
  
 Valeur booléenne qui indique si la trace de la pile doit être générée.
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
