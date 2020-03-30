---
title: SQLServerException, constructeur (java.lang.Object, java.lang.String, java.lang.String, StreamError, booléen) | Microsoft Docs
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
ms.openlocfilehash: c1cc42a09e455fa42d3f89b05903a22afc945424
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67971124"
---
# <a name="sqlserverexception-constructor-javalangobject-javalangstring-javalangstring-streamerror-boolean"></a>SQLServerException, constructeur (java.lang.Object, java.lang.String, java.lang.String, StreamError, booléen)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Initialise une nouvelle instance de la classe [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) en fonction d’un **objet**, d’un objet **string**, d’un objet **string**, d’un objet **StreamError** et d’une **valeur booléenne**.

## <a name="syntax"></a>Syntaxe  
  
```  

public SQLServerException(java.lang.Object obj,
            java.lang.String errText,
            java.lang.String errState,
            StreamError streamError,
            boolean bStack)

            
```  
  
#### <a name="parameters"></a>Paramètres  
 *obj*  
  
 Mémoire tampon E/S qui a généré l’exception.

 *errText*  
  
 Chaîne contenant le texte de l’erreur.
  
 *sqlState*  
  
 Objet enum qui contient l’état SQL.
 
 *streamError*  
  
 Objet StreamError contenant des détails sur l’erreur.
 
 *bStack*  
  
 Valeur booléenne qui indique si l’arborescence des appels de procédure doit être générée.
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerException, constructeurs](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [SQLServerException, membres](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [SQLServerException, classe](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
