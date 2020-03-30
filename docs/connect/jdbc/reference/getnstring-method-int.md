---
title: Méthode getNString (int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2048bb9f-7d9b-4aaa-b135-c716910cc800
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbe3bc040ba79ad7699a571b13b48f2c41965c60
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981423"
---
# <a name="getnstring-method-int"></a>Méthode getNString (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre **NCHAR**, **NVARCHAR** ou **LONGNVARCHAR** désigné sous forme de chaîne dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.lang.String getNString(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterIndex*  
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNString est spécifiée par la méthode getNString de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getNString, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
