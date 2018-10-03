---
title: Classe SQLServerCallableStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38d85e88e8095cc5e2f41af045c36f230fbd43de
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810157"
---
# <a name="sqlservercallablestatement-class"></a>Classe SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Permet de spécifier le nom de la procédure stockée à appeler avec les paramètres d'entrée et de sortie. Cette classe offre également la possibilité de récupérer la valeur de l'état retourné avec la syntaxe ? = call( ?, ..) syntax.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Implémente :** [ ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Étend :** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Notes   
 SQLServerCallableStatement permet de spécifier le nom de la procédure stockée à appeler avec des paramètres d’entrée et de sortie. SQLServerCallableStatement fournit également la possibilité de récupérer la valeur de retour d’état avec le `? = call( ?, ..)` syntaxe.  
  
 Cette classe prend en charge la Désencapsulation dans la classe SQLServerCallableStatement, interface ISQLServerCallableStatement, interface java.sql.CallableStatement et les classes et interfaces prises en charge par SQLServerPreparedStatement pour la Désencapsulation. Pour plus d’informations, consultez [Wrappers et Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Lorsque un des SQLServerCallableStatement définie des méthodes est appelé pour un type, si ce type est en conflit avec le type spécifié avec [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md), le type spécifié par la dernière méthode set SQLServerCallableStatement est utilisé. Toutefois, cela peut entraîner des erreurs dues à une conversion de types de données qui sont incompatibles. Si la méthode SQLServerCallableStatement n’est pas appelée, le type spécifié avec le premier appel de [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) est utilisé.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 est conforme à la recommandation JDBC 4.0, selon laquelle un jeu de résultats et des mises à jour multiples doivent être récupérés avant les paramètres OUT. Si les paramètres OUT sont récupérés avant que le jeu de résultats et les mises à jour n'aient été complètement traités, les résultats et les mises à jour qui n'auront pas été traités seront perdus.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerCallableStatement, membres](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
