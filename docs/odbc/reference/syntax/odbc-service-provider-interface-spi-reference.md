---
title: Référence de l’interface des fournisseurs de services de l’ODBC (SPI) (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9739abd13bf2c4bed1b1b3a31c18c683594705a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298907"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Informations de référence sur l’interface SPI ODBC
Traditionnellement, ODBC définissait une interface de programmation d’applications (API). Les fonctions de l’API peuvent être appelées par des applications et elles doivent être mises en œuvre à l’intérieur du Driver Manager et du conducteur.  
  
 Avec l’ajout de la fonction de mise en commun des connexions consciente du conducteur, ODBC introduit l’interface fournisseur de services (SPI). Les fonctions dans le SPI sont utilisées pour la communication entre le Driver Manager et le conducteur. Les fonctions SPI sont mises en œuvre par le conducteur; le Driver Manager n’expose pas les fonctions SPI aux applications. Les applications ne doivent pas appeler ces fonctions directement.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [SQLCleanupConnectionPoolID (EN anglais)](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID (SQLGetPoolID)](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect (SQLPoolConnect)](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection (SQLRateConnection)](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo (en anglais)](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo (en anglais)](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Développer la sensibilisation à la piscine de connexion chez un conducteur d’ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Regroupement de connexions du gestionnaire de pilotes](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
