---
title: À l’aide d’instructions avec des procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44b8e6ed30257841ea685f85238455f895c6ef05
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784193"
---
# <a name="using-statements-with-stored-procedures"></a>Utilisation d'instructions avec des procédures stockées

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Une procédure stockée est une procédure de base de données, similaire à une procédure dans d'autres langages de programmation, qui est contenue dans la base de données elle-même. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez créer des procédures stockées à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou du CLR (Common Language Runtime) et de l’un des langages de programmation Visual Studio 2005, par exemple Visual Basic ou C#. En règle générale, les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent :  
  
- accepter des paramètres d'entrée et retourner plusieurs valeurs sous la forme de paramètres de sortie à la procédure ou au lot appelant ;  
  
- contenir des instructions de programmation qui exécutent des opérations dans la base de données, y compris l'appel d'autres procédures ;  
  
- retourner une valeur d'état à une procédure ou à un lot appelant pour indiquer une réussite ou un échec (et la raison de l'échec).  
  
> [!NOTE]  
> Pour plus d’informations sur les procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez « Procédures stockées » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Pour utiliser des données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une procédure stockée, le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fournit les classes [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) et [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). La classe que vous utilisez dépend des paramètres d'entrée (IN) ou de sortie (OUT) requis par la procédure stockée. Si la procédure stockée ne nécessite aucun paramètre IN ou OUT, vous pouvez utiliser la classe SQLServerStatement ; si la procédure stockée est appelée plusieurs fois, ou requiert uniquement des paramètres IN, vous pouvez utiliser la classe SQLServerPreparedStatement. Si la procédure stockée requiert les deux IN et les paramètres de sortie, vous devez utiliser la classe SQLServerCallableStatement. Vous ne devez utiliser la classe SQLServerCallableStatement que si la procédure stockée nécessite des paramètres OUT.  
  
> [!NOTE]  
> Les procédures stockées peuvent également retourner des nombres de mises à jour et des jeux de résultats multiples. Pour plus d’informations, consultez [à l’aide d’une procédure stockée avec un nombre de mise à jour](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) et [à l’aide de plusieurs jeux de résultats](../../connect/jdbc/using-multiple-result-sets.md).  
  
Quand vous utilisez le pilote JDBC pour appeler une procédure stockée avec des paramètres, vous devez utiliser la séquence d’échappement SQL `call` conjointement avec la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La syntaxe complète de la séquence d’échappement `call` est la suivante :  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
> Pour plus d’informations sur la `call` et autres SQL séquences d’échappement, consultez [à l’aide les séquences d’échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
Les rubriques composant cette section décrivent comment appeler des procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du pilote JDBC et de la séquence d’échappement SQL `call`.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Utilisation d’une procédure stockée sans paramètres](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|Décrit la méthode d'utilisation du pilote JDBC pour exécuter des procédures stockées ne contenant pas de paramètres d'entrée ou de sortie.|  
|[Utilisation d’une procédure stockée avec des paramètres d’entrée](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|Décrit la méthode d'utilisation du pilote JDBC pour exécuter des procédures stockées contenant des paramètres d'entrée.|  
|[Utilisation d’une procédure stockée avec des paramètres de sortie](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|Décrit la méthode d'utilisation du pilote JDBC pour exécuter des procédures stockées contenant des paramètres de sortie.|  
|[Utilisation d’une procédure stockée avec retour d’état](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|Décrit la méthode d'utilisation du pilote JDBC pour exécuter des procédures stockées contenant des valeurs de retour d'état.|  
|[Utilisation d’une procédure stockée avec un compteur des mises à jour](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|Décrit la méthode d'utilisation du pilote JDBC pour exécuter des procédures stockées qui retournent des nombres de mises à jour.|  
  
## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec le pilote JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
