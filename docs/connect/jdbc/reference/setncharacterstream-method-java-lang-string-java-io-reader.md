---
title: chaîne de méthode à l’objet de lecteur - setNCharacterStream | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: fd19fbb8-a878-4d98-a584-e4969d649844
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd76c54e9d40f85c2b74944ee37cdf5a9248d276
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732287"
---
# <a name="setncharacterstream-method-javalangstring-javaioreader"></a>Méthode setNCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                       java.io.Reader value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Un **chaîne** qui indique le nom du paramètre.  
  
 *value*  
  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setNCharacterStream est spécifiée par la méthode setNCharacterStream dans l’interface java.sql.CallableStatement.  
  
 Cette méthode doit être utilisée pour **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** types de données.  
  
## <a name="see-also"></a> Voir aussi  
 [setNCharacterStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
