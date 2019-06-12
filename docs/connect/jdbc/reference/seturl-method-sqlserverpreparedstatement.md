---
title: setURL, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d853b2f3-fb72-4d4b-8997-f4a45a9dfefc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fc8f47e7c4f5b92658735b8ca904655020f58d2f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66783235"
---
# <a name="seturl-method-sqlserverpreparedstatement"></a>setURL, méthode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon la valeur d'URL donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setURL(int parameterIndex,  
                         java.net.URL x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterindex*  
  
 Un **int** qui indique le numéro de paramètre.  
  
 *x*  
  
 Un objet d’URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setURL est spécifiée par la méthode setURL de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
