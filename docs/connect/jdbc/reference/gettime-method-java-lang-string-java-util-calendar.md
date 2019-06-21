---
title: getTime, méthode (java.lang.String, java.util.Calendar) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d4c67c2-a3c8-4a26-a159-89c5d63fda0b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6b9d74778d3ff1fc62b5549fbea7e0f97bf1e477
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778879"
---
# <a name="gettime-method-javalangstring-javautilcalendar"></a>Méthode getTime (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre désigné en tant qu’objet java.sql.Time dans le langage de programmation, en fonction du nom du paramètre fourni, en utilisant l’objet Calendar spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *sCol*  
  
 Valeur **chaîne** qui contient le nom du paramètre.  
  
 *cal*  
  
 Un objet de calendrier.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de temps.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTime est spécifiée par la méthode getTime de l’interface java.sql.CallableStatement.  
  
 Consultez le graphique intitulé « Conversions de méthode d’accesseur get » dans [Conversions de types de données de présentation](../../../connect/jdbc/understanding-data-type-conversions.md) pour voir quelle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les types de données peuvent être récupérés avec cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [getTime, méthode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
