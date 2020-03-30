---
title: Fermeture d'objets inutilisés | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 130b639c7a721ea48a12c7e054834da7b61ab0c7
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028362"
---
# <a name="closing-objects-when-not-in-use"></a>Fermeture d'objets inutilisés
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Lorsque vous utilisez les objets de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], en particulier [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) ou l’un des objets Statement, par exemple [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ou [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), fermez-les explicitement à l’aide de leurs méthodes close lorsqu’ils ne sont plus nécessaires. Cela améliore les performances en libérant les ressources de pilote et de serveur le plus tôt possible, au lieu d'attendre que le garbage collector de la machine virtuelle Java ne le fasse pour vous.  
  
 La fermeture des objets est particulièrement importante pour conserver un bon accès simultané sur le serveur lorsque vous utilisez des arrêts de défilement. Les arrêts de défilement dans la dernière mémoire tampon d'extraction accédée sont maintenus jusqu'à la fermeture du jeu de résultats. De même, les handles préparés par instruction sont maintenus jusqu'à ce que l'instruction soit fermée. Si vous réutilisez une connexion pour plusieurs instructions, le fait de fermer les instructions avant de leur permettre de sortir de portée permettra au serveur de nettoyer plus tôt les handles préparés.  
  
## <a name="see-also"></a>Voir aussi  
 [Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
