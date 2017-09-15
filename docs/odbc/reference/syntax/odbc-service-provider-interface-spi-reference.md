---
title: "Référence de l’Interface (SPI) du fournisseur de Service ODBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a4521d90f3e7eda4167062bd8bc1299921b0e31d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-service-provider-interface-spi-reference"></a>Référence de l’Interface (SPI) du fournisseur de Service ODBC
En règle générale, ODBC définie par une interface de programmation d’applications (API). Les fonctions de l’API peuvent être appelées par les applications et elles doivent être implémentées à l’intérieur du Gestionnaire de pilotes et le pilote.  
  
 Avec l’ajout de la fonctionnalité de regroupement de connexions prenant en charge de pilote, ODBC présente l’interface de fournisseur de service (SPI). Les fonctions dans l’interface SPI sont utilisées pour la communication entre le Gestionnaire de pilotes et le pilote. Fonctions SPI sont implémentées par le pilote ; le Gestionnaire de pilotes n’expose pas de fonctions SPI aux applications. Applications ne doivent pas appeler directement ces fonctions.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
 Cette section contient les rubriques suivantes  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Développement de reconnaissance du Pool de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Regroupement de connexions du Gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
