---
title: getNClob, méthode (java.lang.String) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36571f7c-b335-4249-8f83-51dcb6923aec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0a7241be8ab1c8ffcaf6b4eb143740f3ca09161d
ms.sourcegitcommit: ef15fa253d98c62538bf9b6fe191af7f8ef8f6c8
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49991132"
---
# <a name="getnclob-method-javalangstring-sqlserverresultset"></a>Méthode getNClob (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de la colonne désignée dans la ligne actuelle de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet NClob dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.NClob getNClob(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnLabel*  
  
 **String** contenant l’étiquette de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet NClob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getNClob est spécifiée par la méthode getNClob de l’interface java.sql.ResultSet.  
  
 Cette méthode est prise en charge uniquement sur **nvarchar (max)**, **ntext**, et **xml** colonnes. L'utilisation de cette méthode sur n'importe quel autre type de données entraîne la levée d'une exception.  
  
## <a name="see-also"></a> Voir aussi  
 [getNClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
