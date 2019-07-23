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
ms.openlocfilehash: c8dba5603a0dcd3cb264b8c49883b1aa43101509
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973747"
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
  
 Objet lecteur.  
  
 *length*  
  
 **Valeur de type long** qui indique le nombre de caractères dans le flux.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être utilisée pour les types de données de paramètre **nchar**, **nvarchar**, **ntext**et **XML** .  
  
 Cette méthode setNClob est spécifiée par la méthode setNClob de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setNClob, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
