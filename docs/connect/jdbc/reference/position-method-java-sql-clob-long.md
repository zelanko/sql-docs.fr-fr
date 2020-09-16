---
description: Méthode position (java.sql.Clob, long)
title: Méthode position (java.sql.Clob, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.position (java.sql.Clob, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2fb34d5-1d34-4764-a795-712d9c6aa313
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d782839bc1a68008c4e86231fdf436b8c6f7a580
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433021"
---
# <a name="position-method-javasqlclob-long"></a>Méthode position (java.sql.Clob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la position de caractère de l'objet CLOB spécifié dans le CLOB, en fonction de la position de départ donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public long position(java.sql.Clob searchstr,  
                     long start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *searchstr*  
  
 Sous-chaîne à rechercher.  
  
 *start*  
  
 Position à laquelle démarrer la recherche. La première position est 1.  
  
## <a name="return-value"></a>Valeur de retour  
 Position à laquelle la sous-chaîne doit s'afficher, ou -1 si elle est absente. La première position est 1.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode position est spécifiée par la méthode position de l’interface java.sql.Clob.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode position &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/position-method-sqlserverclob.md)   
 [SQLServerClob, méthodes](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob, membres](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
