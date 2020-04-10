---
title: Méthode setClob (int, java.io.Reader, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 157882dd-1a96-4501-a895-46e88a49266e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 373af12cda9700eeab6912baf21c12015c1a82d3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927156"
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
  
 **int** indiquant l’index du paramètre.  
  
 *reader*  
  
 Objet Reader.  
  
 *length*  
  
 **long** indiquant le nombre de caractères dans la valeur de paramètre.  
  
## <a name="remarks"></a>Notes  
 Cette méthode setClob est spécifiée par la méthode setClob de l’interface java.sql.PreparedStatement.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [setClob, méthode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
