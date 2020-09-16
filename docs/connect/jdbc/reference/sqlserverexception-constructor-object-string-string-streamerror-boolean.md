---
description: SQLServerException, constructeur (java.lang.Object, java.lang.String, java.lang.String, StreamError, booléen)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0ee96aa32378e69f01fb8865cd773c30287416
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450484"
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
 [Classe SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
