---
title: Méthode getURL (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getURL Ijnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 75d03ced-3614-4997-9abd-24642b1d1aae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b7b91071c97c46d7516907459539303ddbd45822
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67978334"
---
# <a name="geturl-method-int"></a>Méthode getURL (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné sous forme d’objet URL dans le langage de programmation Java en fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.net.URL getURL(int n)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *n*  
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getURL est spécifiée par la méthode getURL de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getURL, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
