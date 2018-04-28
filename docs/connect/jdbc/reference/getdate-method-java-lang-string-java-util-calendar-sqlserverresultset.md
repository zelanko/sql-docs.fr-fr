---
title: colonne de getDate (méthode) (java.util.Calendar) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerResultSet.getDate (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3fa2a72a-7499-44ec-8f76-a8e646e0190c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4d54e70fa0fdd0d464ca9993f00353d060944ff
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getdate-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Méthode getDate (java.lang.String, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de colonne désigné dans la ligne actuelle de ce [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet comme un objet java.sql.Date dans le langage de programmation, à l’aide de l’objet de calendrier donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Date getDate(java.lang.String colName,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Nom de colonne*  
  
 A **chaîne** qui contient le nom de colonne.  
  
 *licences d’accès client*  
  
 Un objet de calendrier.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet Date.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getDate est spécifiée par la méthode getDate dans l’interface java.sql.ResultSet.  
  
 Cette méthode retourne une partie de date valide d’un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] type de données datetime ou smalldatetime, avec la partie heure définie sur l’heure de référence Java 00:00 (minuit) dans le fuseau horaire du calendrier fourni.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
