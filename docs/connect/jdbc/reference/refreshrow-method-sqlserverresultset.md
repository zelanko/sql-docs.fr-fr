---
title: Méthode refreshRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.refreshRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 570a9185a83ecf1af0e47ee25cce5445dca1b958
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975979"
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
 Cette méthode refreshRow est spécifiée par la méthode refreshRow de l’interface java.sql.ResultSet.  
  
 Cette méthode ne peut pas être appelée lorsque le curseur se trouve sur la ligne d'insertion.  
  
 Elle fournit à une application un moyen d'indiquer explicitement au pilote JDBC d'extraire à nouveau les lignes de la base de données. Une application peut être amenée à appeler cette méthode lorsque [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] effectue une mise en cache ou une prérécupération, afin de récupérer la dernière valeur d’une ligne dans la base de données. Le pilote JDBC peut en fait actualiser plusieurs lignes simultanément si la taille d'extraction est supérieure à un.  
  
 Toutes les valeurs sont à nouveau extraites selon le niveau d'isolation de la transaction et la sensibilité du curseur. Si cette méthode est appelée après une méthode de programme de mise à jour, mais avant la méthode [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md), les mises à jour apportées à la ligne sont perdues. L'appel de cette méthode influe souvent sur les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
