---
title: Référence de l’Interface (SPI) du fournisseur de Service ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bd481d7344345578f830374f7049a917e60eb68
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
 [Regroupement de connexions du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
