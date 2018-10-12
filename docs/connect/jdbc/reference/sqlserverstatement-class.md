---
title: Classe SQLServerStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7488efcb3392623e6f54cff440a16494c10e0a69
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705347"
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement, classe
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente l'implémentation de base de la fonctionnalité d'instruction JDBC.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Notes   
 La classe SQLServerStatement fournit également un certain nombre de méthodes d’implémentation de classe de base pour l’instruction préparée JDBC et les instructions pouvant être appelées. Le rôle de base de la classe SQLServerStatement est d’exécuter des instructions SQL, puis de retourner des nombres de mises à jour et des jeux de résultats à l’application utilisateur.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerStatement, l’interface ISQLServerStatement et l’interface java.sql.Statement. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
