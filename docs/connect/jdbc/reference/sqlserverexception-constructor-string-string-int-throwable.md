---
description: Constructeur SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable)
title: Constructeur SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb84d0c1216047f28ed980806129ff1e21c08bb6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450434"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>Constructeur SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) en fonction d’un objet **string**, d’un objet **string**, d’un **entier** et d’un objet **jetable**.

## <a name="syntax"></a>Syntaxe  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Paramètres  
 *errText*  
  
 Chaîne contenant le texte de l’erreur.
  
 *errState*  
  
 Chaîne contenant l’état de l’erreur.
 
 *errNum*  
  
 Entier qui contient le code d'erreur de l'exception.
 
 *cause*  
  
 Objet jetable qui contient la cause de l’exception.
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Classe SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
