---
title: Exécution de Transactions avec le pilote JDBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afbb776f-05dc-4e79-bb25-2c340483e401
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba3c37d70e6457907540abcec19daa275573b414
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="performing-transactions-with-the-jdbc-driver"></a>Exécution de transactions avec le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le traitement de transactions est une condition obligatoire pour toutes les applications qui doivent garantir la cohérence de leurs données permanentes. Avec la [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], traitement des transactions peut être effectué localement ou distribué. Les transactions sont des modules d'exécution ACID (Atomicité, Cohérence, Isolation et Durabilité).  
  
 Les rubriques de cette section décrivent la manière dont le pilote JDBC prend en charge les transactions, y compris les niveaux d'isolation, les points d'enregistrement de transactions et la fonction holdability du jeu de résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Présentation des transactions](../../connect/jdbc/understanding-transactions.md)|Présente la manière dont les transactions sont utilisées avec le pilote JDBC.|  
|[Présentation des transactions XA](../../connect/jdbc/understanding-xa-transactions.md)|Présente la manière dont les transactions XA sont utilisées avec le pilote JDBC.|  
|[Présentation des niveaux d’isolation](../../connect/jdbc/understanding-isolation-levels.md)|Décrit les différents niveaux d'isolation pris en charge par le pilote JDBC.|  
|[Utilisation de points de sauvegarde](../../connect/jdbc/using-savepoints.md)|Décrit la manière d'utiliser le pilote JDBC avec des points d'enregistrement de transactions.|  
|[Utilisation de la fonctionnalité de mise en attente](../../connect/jdbc/using-holdability.md)|Décrit la manière d'utiliser le pilote JDBC avec la fonction holdability du jeu de résultats.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
