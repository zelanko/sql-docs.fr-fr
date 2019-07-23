---
title: Méthode setClob (int, Java. IO. Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 589a2c7a12523658fc5fd58afb46dc8bb959a276
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974597"
---
# <a name="setclob-method-int-javaioreader-long"></a>Méthode setClob (int, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié, qui correspond au nombre de caractères donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader,  
                          long length)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **Entier** qui indique l’index du paramètre.  
  
 *reader*  
  
 Objet lecteur.  
  
 *length*  
  
 Valeur de **type long** qui indique le nombre de caractères dans la valeur de paramètre.  
  
## <a name="remarks"></a>Notes  
 Cette méthode setClob est spécifiée par la méthode setClob de l’interface java.sql.PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [setClob, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
