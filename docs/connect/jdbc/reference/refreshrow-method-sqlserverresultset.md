---
title: "Méthode refreshRow (SQLServerResultSet) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.refreshRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 89452f34778b07f9e34b074beaf2b1e92f7be135
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="refreshrow-method-sqlserverresultset"></a>Méthode refreshRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualise la ligne actuelle avec sa valeur la plus récente dans la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode refreshRow est spécifiée par la méthode refreshRow dans l’interface java.sql.ResultSet.  
  
 Cette méthode ne peut pas être appelée lorsque le curseur se trouve sur la ligne d'insertion.  
  
 Elle fournit à une application un moyen d'indiquer explicitement au pilote JDBC d'extraire à nouveau les lignes de la base de données.  Une application peut avoir besoin d’appeler cette méthode lorsque le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] est mise en cache ou prérécupération, afin de récupérer de la dernière valeur d’une ligne à partir de la base de données. Le pilote JDBC peut en fait actualiser plusieurs lignes simultanément si la taille d'extraction est supérieure à un.  
  
 Toutes les valeurs sont à nouveau extraites selon le niveau d'isolation de la transaction et la sensibilité du curseur. Si cette méthode est appelée après l’appel à une méthode de mise à jour, mais avant d’appeler le [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) (méthode), les mises à jour apportées à la ligne sont perdues. L'appel de cette méthode influe souvent sur les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
