---
title: setNClob, méthode (java.lang.String, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c1b95ee7-7e82-418f-8f30-948589086f63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1af4961609b132ebf6b508b54386e4c02ee3e6e8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850077"
---
# <a name="setnclob-method-javalangstring-javaioreader-long"></a>Méthode setNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié, qui correspond au nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader,  
              long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *reader*  
  
 Un objet de lecteur.  
  
 *length*  
  
 Un **long** qui indique le nombre de caractères dans le flux.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode doit être utilisée pour **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** les types de données de paramètre.  
  
 Cette méthode setNClob est spécifiée par la méthode setNClob de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a> Voir aussi  
 [setNClob, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
