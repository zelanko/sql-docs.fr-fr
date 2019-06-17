---
title: setNClob, méthode (java.lang.String, java.io.Reader) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a595679a-89b7-4b18-9ad2-d9cb13af2a28
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a40fe037074a446610a93ea1851e3f10403f6391
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800404"
---
# <a name="setnclob-method-javalangstring-javaioreader"></a>Méthode setNClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet Reader spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *reader*  
  
 Un objet de lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être utilisée pour **NCHAR**, **NVARCHAR**, **NTEXT**, et **XML** les types de données de paramètre.  
  
 Cette méthode setNClob est spécifiée par la méthode setNClob de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [setNClob, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
