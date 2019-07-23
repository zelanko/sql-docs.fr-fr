---
title: Amélioration des performances et de la fiabilité avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 561b3681336812761f483741ccb7f00833e408ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956496"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Amélioration des performances et de la fiabilité avec le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Un aspect du développement d'applications commun à toutes les applications est le besoin constant d'amélioration des performances et de la fiabilité. Il existe un certain nombre de techniques pour y parvenir en utilisant le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
Les rubriques de cette section décrivent plusieurs techniques d'amélioration des performances et de la fiabilité des applications lors de l'utilisation du pilote JDBC.  

## <a name="in-this-section"></a>Dans cette section

|Rubrique|Description|  
|-----------|-----------------|  
|[Fermeture des objets non utilisés](../../connect/jdbc/closing-objects-when-not-in-use.md)|Décrit l'importance de la fermeture des objets du pilote JDBC lorsqu'ils ne sont plus nécessaires.|  
|[Gestion de la taille des transactions](../../connect/jdbc/managing-transaction-size.md)|Décrit les techniques d'amélioration des performances des transactions.|  
|[Utilisation des instructions et des jeux de résultats](../../connect/jdbc/working-with-statements-and-result-sets.md)|Décrit les techniques permettant d’améliorer les performances lors de l’utilisation de l’instruction ou des objets ResultSet.|  
|[Utilisation de la mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md)|Décrit une fonctionnalité de mise en mémoire tampon adaptative, conçue pour récupérer tout type de données de grande valeur sans la charge liée au temps de traitement des curseurs côté serveur.|  
|[Colonnes éparses](../../connect/jdbc/sparse-columns.md)|Décrit la prise en charge des colonnes éparses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le pilote JDBC.|  
|[Mise en cache des métadonnées d’instruction préparée pour le pilote JDBC](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Décrit les techniques permettant d’améliorer les performances avec des requêtes d’instructions préparées.|
|[Utilisation de l’API de copie en bloc pour l’opération d’insertion par lot](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|Décrit comment activer l’API de copie en bloc pour les opérations d’insertion de lot et ses avantages.|

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
