---
title: Méthode createClob (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 291016047ab29d4e563e2a7248c4cd4624669ef9
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927704"
---
# <a name="createclob-method-sqlserverconnection"></a>Méthode createClob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crée un objet Clob sans aucune donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet Clob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode createClob est spécifiée par la méthode createClob de l’interface java.sql.Connection.  
  
 Cette méthode évite d’avoir à utiliser le [Constructeur SQLServerClob &#40;SQLServerConnection, java.lang.String&#41;](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
