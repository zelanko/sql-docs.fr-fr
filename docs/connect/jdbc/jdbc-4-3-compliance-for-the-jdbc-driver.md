---
title: JDBC 4.3 conformité pour le pilote JDBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33b218598871e570fa99d212d565c834718de1d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3 conformité pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Versions antérieures de Microsoft JDBC Driver 6.4 pour SQL Server sont conformes pour les spécifications de l’API Java Database Connectivity 4.2. Cette section ne s’applique pas pour les versions antérieures à la version 6.4.  
  
 Actuellement, 6.4 de pilote JDBC Microsoft pour SQL Server est Java 9 compatibles, mais il n’est pas entièrement conforme pour les spécifications de 4.3 de API de connectivité de base de données Java. Pour qui vient d’être introduit l’API JDBC 4.3, si ce n’est pas pris en charge par le pilote, le pilote lève une SQLFeatureNotSupportedException.