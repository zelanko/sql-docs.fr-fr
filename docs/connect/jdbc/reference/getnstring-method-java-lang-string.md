---
description: Méthode getNString (java.lang.String)
title: Méthode getNString (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b351e999-85bf-498b-915a-f91d89134bce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e76cfb9175b07d4d7bfae843f0011fe006abc05
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435211"
---
# <a name="getnstring-method-javalangstring"></a>Méthode getNString (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre **NCHAR**, **NVARCHAR** ou **LONGNVARCHAR** désigné sous forme de chaîne dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.lang.String getNString(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getNString est spécifiée par la méthode getNString de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [getNString, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [Méthodes SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)  
  
  
