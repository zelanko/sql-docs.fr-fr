---
title: Méthode setNClob (int, Java. IO. Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 11071f8f-0e9b-45f0-b600-aaef7e2815d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dae9fbeb16a5b9c9c881e4250206b7f83344ef78
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973794"
---
# <a name="setnclob-method-int-javaioreader-long"></a>Méthode setNClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié, qui correspond au nombre de caractères spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader,  
                    long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **Entier** qui indique l’index du paramètre.  
  
 *reader*  
  
 Objet Reader indiquant la valeur du paramètre.  
  
 *length*  
  
 Valeur de **type long** qui indique le nombre de caractères dans la valeur de paramètre.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setNClob est spécifiée par la méthode setNClob de l’interface java.sql.PreparedStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setNClob, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
