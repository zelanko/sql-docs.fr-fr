---
title: "Méthode getTime (int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerCallableStatement.getTime (int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 6c13dea2-511f-48dc-b3db-2d3b72ccc9de
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aca269a257f8e34c6b436b79d99fd2d9dd9779d9
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="gettime-method-int"></a>Méthode getTime (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu'objet java.sql.Time dans le langage de programmation Java en fonction de l'index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Time getTime(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de l’heure.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTime est spécifiée par la méthode getTime dans l’interface java.sql.CallableStatement.  
  
 Consultez le graphique intitulé « Conversions de méthode d’accesseur get » dans [présentation des Conversions de Type de données](../../../connect/jdbc/understanding-data-type-conversions.md) pour voir quelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] des types de données peuvent être récupérés avec cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getTime &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
