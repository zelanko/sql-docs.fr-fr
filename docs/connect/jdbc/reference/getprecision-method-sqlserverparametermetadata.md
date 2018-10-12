---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32913e5120afb71f4773318acc1b34c9daed892a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813293"
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
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la précision du paramètre désigné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getPrecision est spécifiée par la méthode getPrecision dans l’interface java.sql.ParameterMetaData.  
  
 Pour les types de nombres, cette méthode obtient le nombre de décimales. Pour les types de caractères, elle obtient la longueur maximale en caractères. Pour les types binaires, elle obtient la longueur maximale en octets. Lorsque le nombre de chiffres n'est pas connu, cette méthode retourne la valeur « 0 ».  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerParameterMetaData, méthodes](../../../connect/jdbc/reference/sqlserverparametermetadata-methods.md)   
 [SQLServerParameterMetaData, membres](../../../connect/jdbc/reference/sqlserverparametermetadata-members.md)   
 [SQLServerParameterMetaData, classe](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)  
  
  
