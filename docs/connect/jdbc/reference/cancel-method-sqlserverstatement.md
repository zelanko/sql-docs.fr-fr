---
title: Cancel, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.cancel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276bd9c1-9329-4fc9-9622-ed673c83a12d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bd0845e6bebf1365ab8c26cb48bda2a92a6b4e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840167"
---
# <a name="cancel-method-sqlserverstatement"></a>Méthode cancel (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annule l’instruction SQL actuellement exécutée par cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void cancel()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode d’annulation est spécifiée par la méthode cancel dans l’interface java.sql.Statement.  
  
 Lors de l'exécution d'une instruction qui produit un ensemble unique et important de résultats avant uniquement, en lecture seule, un ensemble initial de lignes uniquement doit vous intéresser dans le jeu de résultats retourné. Dans ce cas, l’application peut appeler la méthode [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) de l’objet d’instruction associé avant de fermer le jeu de résultats, afin de réduire le temps de traitement nécessaire pour ignorer les lignes restantes inutiles. Nous vous recommandons de faire la part entre le temps de traitement gagné et le temps, ainsi que l'aller-retour jusqu'au serveur requis pour annuler l'exécution, lorsque la décision doit être prise d'utiliser cette technique ou pas.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
