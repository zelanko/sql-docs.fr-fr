---
title: Amélioration des performances et de la fiabilité avec le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b82c2758dbc796ec29dd7304ee821a1a018af0a8
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920734"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Amélioration des performances et de la fiabilité avec le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Un aspect du développement d'applications commun à toutes les applications est le besoin constant d'amélioration des performances et de la fiabilité. Il existe un certain nombre de techniques pour y parvenir en utilisant le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
Les rubriques de cette section décrivent plusieurs techniques d'amélioration des performances et de la fiabilité des applications lors de l'utilisation du pilote JDBC.  

## <a name="in-this-section"></a>Contenu de cette section

|Rubrique|Description|  
|-----------|-----------------|  
|[Fermeture d'objets inutilisés](../../connect/jdbc/closing-objects-when-not-in-use.md)|Décrit l'importance de la fermeture des objets du pilote JDBC lorsqu'ils ne sont plus nécessaires.|  
|[Gestion de la taille des transactions](../../connect/jdbc/managing-transaction-size.md)|Décrit les techniques d'amélioration des performances des transactions.|  
|[Utilisation d'instructions et de jeux de résultats](../../connect/jdbc/working-with-statements-and-result-sets.md)|Décrit les techniques d'amélioration des performances lors de l'utilisation des objets Statement ou ResultSet.|  
|[Utilisation de la mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md)|Décrit une fonctionnalité de mise en mémoire tampon adaptative, conçue pour récupérer tout type de données de grande valeur sans la charge liée au temps de traitement des curseurs côté serveur.|  
|[Colonnes éparses](../../connect/jdbc/sparse-columns.md)|Décrit la prise en charge des colonnes éparses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le pilote JDBC.|  
|[Préparation de la mise en cache des métadonnées d'instruction pour le pilote JDBC](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Décrit les techniques permettant d’améliorer les performances avec des requêtes d’instructions préparées.|
|[Utilisation de l'API de copie en bloc pour l'opération d'insertion par lot](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|Décrit comment activer l’API de copie en bloc pour les opérations d’insertion de lot et ses avantages.|

## <a name="see-also"></a>Voir aussi

[Présentation du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
