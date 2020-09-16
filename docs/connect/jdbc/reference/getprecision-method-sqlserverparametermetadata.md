---
description: Méthode getPrecision (SQLServerParameterMetaData)
title: Méthode getPrecision (SQLServerParameterMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerParameterMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8bd79484-bab6-423b-978f-d7ec7132ebeb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b0af3f0f87c32038b8d6b16839993de5ae6aa056
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434951"
---
# <a name="getprecision-method-sqlserverparametermetadata"></a>Méthode getPrecision (SQLServerParameterMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de décimales du paramètre désigné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPrecision(int param)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *param*  
  
 **int** indiquant l’index du paramètre.  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant la précision du paramètre désigné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getPrecision est spécifiée par la méthode getPrecision de l’interface java.sql.ParameterMetaData.  
  
 Pour les types de nombres, cette méthode obtient le nombre de décimales. Pour les types de caractères, elle obtient la longueur maximale en caractères. Pour les types binaires, elle obtient la longueur maximale en octets. Lorsque le nombre de chiffres n'est pas connu, cette méthode retourne la valeur « 0 ».  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [Classe SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
