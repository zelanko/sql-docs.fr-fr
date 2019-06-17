---
title: setFetchSize, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c5d0bd8714714a479f9370ed2c60b626006e1964
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803381"
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fournit un conseil au pilote JDBC concernant le nombre de lignes qui doivent être extraites de la base de données, quand davantage de lignes sont nécessaires pour cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rows*  
  
 Un **int** indiquant le nombre de lignes à extraire.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchSize est spécifiée par la méthode setFetchSize de l’interface java.sql.ResultSet.  
  
 Si la taille d'extraction spécifiée est de zéro, le pilote JDBC ignore la valeur et procède à une estimation de ce que devrait être la taille d'extraction. La valeur par défaut est définie par l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui a créé le jeu de résultats. La taille d'extraction peut être modifiée à tout moment.  
  
 Cette méthode change la taille d'extraction du bloc pour les curseurs côté serveur et prend effet la prochaine fois que le pilote JDBC doit appeler sp_cursorfetch. La définition de la taille d'extraction à zéro permet de restaurer la taille d'extraction par défaut du type de curseur en cours d'utilisation  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
