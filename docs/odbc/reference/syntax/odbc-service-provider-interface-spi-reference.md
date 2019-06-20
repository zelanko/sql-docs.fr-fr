---
title: Référence de l’Interface (SPI) du fournisseur de Service ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e3d83f0aa27641c9dde164f51319a0e78d456ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653247"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Informations de référence sur l’interface SPI ODBC
En règle générale, ODBC défini une interface de programmation d’applications (API). Les fonctions dans l’API peuvent être appelées par les applications, et elles doivent être implémentées à l’intérieur du Gestionnaire de pilotes et le pilote.  
  
 Avec l’ajout de la fonctionnalité de regroupement de connexions prenant en charge de pilote, ODBC présente l’interface de fournisseur de service (SPI). Les fonctions dans le SPI sont utilisées pour la communication entre le Gestionnaire de pilotes et le pilote. Fonctions SPI sont implémentées par le pilote ; le Gestionnaire de pilotes n’expose pas de fonctions SPI aux applications. Applications ne doivent pas appeler directement ces fonctions.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
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
 [Développement de la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Regroupement de connexions du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
