---
title: Méthode setNCharacterStream pour lecteur-chaîne objet | Microsoft Docs
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
ms.openlocfilehash: 34eb40d6c36f5c1586ac690de5e9fc354c8fd1f3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973872"
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
  
 **Chaîne** qui indique le nom du paramètre.  
  
 *value*  
  
 Objet lecteur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setNCharacterStream est spécifiée par la méthode setNCharacterStream dans l’interface java. Sql. CallableStatement.  
  
 Cette méthode doit être utilisée pour les types de données **nchar**, **nvarchar**, **ntext**et **XML** .  
  
## <a name="see-also"></a>Voir aussi  
 [setNCharacterStream, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
