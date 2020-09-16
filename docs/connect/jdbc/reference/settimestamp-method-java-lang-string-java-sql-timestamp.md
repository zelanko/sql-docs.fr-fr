---
description: Méthode setTimestamp (java.lang.String, java.sql.Timestamp)
title: Méthode setTimestamp pour la valeur d’horodateur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTimestamp (java.lang.String, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc45b126-3196-47ff-956b-cbc897980ff8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f176b15ac48910cf4ce1de74a284fa5080cbc75
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450681"
---
# <a name="settimestamp-method-javalangstring-javasqltimestamp"></a>Méthode setTimestamp (java.lang.String, java.sql.Timestamp)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur d'horodateur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setTimestamp(java.lang.String sCol,  
                         java.sql.Timestamp t)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *t*  
  
 Un objet Timestamp.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setTimestamp est spécifiée par la méthode setTimestamp de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setTimestamp, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
