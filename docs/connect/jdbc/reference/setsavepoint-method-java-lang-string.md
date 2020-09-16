---
description: Méthode setSavepoint (java.lang.String)
title: Méthode setSavepoint (java.lang.String, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57ed08c322b8579b92165306397fb26312d95fa3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458410"
---
# <a name="setsavepoint-method-javalangstring"></a>Méthode setSavepoint (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un point de sauvegarde avec le nom donné dans la transaction actuelle, puis retourne le nouvel objet [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) qui le représente.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sName*  
  
 Valeur **String** contenant le nom du point de sauvegarde.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet SavePoint.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setSavePoint est spécifiée par la méthode setSavePoint de l’interface java.sql.Connection.  
  
 L’argument *sName* est automatiquement placé dans une séquence d’échappement par [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [setSavepoint, méthode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
