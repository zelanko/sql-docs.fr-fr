---
description: Méthode setNString (SQLServerCallableStatement)
title: Méthode setNString (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6494300b-7fc0-4076-8311-22d35a96cdc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb8178f04919afb403499e79f0af646f670485f0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458651"
---
# <a name="setnstring-method-sqlservercallablestatement"></a>Méthode setNString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le paramètre désigné selon l’objet String spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setNString(java.lang.String parameterName, java.lang.String value)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *parameterName*  
  
 **Chaîne** indiquant le nom du paramètre.  
  
 *value*  
  
 Objet String.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doit être utilisée pour les types de données **NCHAR**, **NVARCHAR**, **NTEXT** et **XML**.  
  
 Cette méthode setNString est spécifiée par la méthode setNString de l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
