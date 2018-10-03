---
title: Utilisation des instructions et des jeux de résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cc917534-f5f8-4844-87c8-597c48b4e06d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94a0a5fbf228f7fbf8249e9e75a7e2aebf861065
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690050"
---
# <a name="working-with-statements-and-result-sets"></a>Travail sur des instructions et des jeux de résultats

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Quand vous travaillez avec le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] et les objets Statement et ResultSet qui l’accompagnent, il existe plusieurs techniques que vous pouvez utiliser pour améliorer les performances et la fiabilité de vos applications.

## <a name="use-the-appropriate-statement-object"></a>Utilisez l'objet d'instruction approprié

Quand vous utilisez l’un des objets Statement du pilote JDBC, par exemple l’objet [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) ou [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), vérifiez que vous utilisez l’objet approprié pour la tâche.

- Si vous n’avez pas les paramètres de sortie, il est inutile d’utiliser l’objet SQLServerCallableStatement. Au lieu de cela, utilisez la SQLServerStatement ou l’objet SQLServerPreparedStatement.

- Si vous ne souhaitez pas exécuter l’instruction plusieurs fois, ou que vous n’avez pas IN ou OUT, il est inutile d’utiliser l’objet SQLServerPreparedStatement ou SQLServerCallableStatement. Au lieu de cela, utilisez l’objet SQLServerStatement.

## <a name="use-the-appropriate-concurrency-for-resultset-objects"></a>Utilisez l'accès simultané approprié aux objets ResultSet

Ne demandez pas d'accès simultané pouvant être mis à jour lorsque vous créez des instructions produisant des jeux de résultats, à moins que vous n'ayez réellement l'intention de mettre à jour les résultats. Le modèle de curseur en avant uniquement et en lecture seule est le plus rapide pour lire les petits jeux de résultats.

## <a name="limit-the-size-of-your-result-sets"></a>Limitez la taille de vos jeux de résultats

Utilisez la méthode [setMaxRows](../../connect/jdbc/reference/setmaxrows-method-sqlserverstatement.md) (ou la syntaxe SET ROWCOUNT ou SELECT TOP N SQL) pour limiter le nombre de lignes retournées par des jeux de résultats potentiellement volumineux. Si vous devez gérer des jeux de résultats volumineux, songez à utiliser une mise en mémoire tampon adaptative des réponses en définissant la propriété de chaîne de connexion responseBuffering=adaptive, qui est le mode par défaut. Cette approche permet à l'application de traiter des jeux de résultats volumineux sans nécessiter de curseurs côté serveur ; par ailleurs, elle réduit l'utilisation de la mémoire de l'application. Pour plus d’informations, consultez [à l’aide de mise en mémoire tampon adaptative](../../connect/jdbc/using-adaptive-buffering.md).

## <a name="use-the-appropriate-fetch-size"></a>Utilisez la taille d'extraction appropriée

Pour les curseurs côté serveur en lecture seule, il est nécessaire de choisir entre de nombreux allers-retours vers le serveur ou l'utilisation d'une grande quantité de mémoire dans le pilote. Pour les curseurs de serveurs pouvant être mis à jour, la taille d'extraction influence également la sensibilité des modifications au jeu de résultats et à l'accès simultané du serveur. Les mises à jour des lignes dans le tampon d’extraction actuel ne sont pas visibles tant qu’une méthode explicite [refreshRow](../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md) n’a pas été lancée ou que le curseur n’a pas quitté le tampon d’extraction. Les performances des tampons d'extraction importants seront meilleures (moins de boucles de connexion avec le serveur) ; néanmoins, les tampons sont moins sensibles aux modifications et réduisent l'accès simultané au serveur si CONCUR_SS_SCROLL_LOCKS (1009) est utilisé. Pour une sensibilité maximale aux modifications, utilisez une taille d'extraction de 1. Cependant, notez que cela provoquera une boucle avec le serveur pour chaque ligne extraite.

## <a name="use-streams-for-large-in-parameters"></a>Utilisez des flux pour des paramètres IN importants

Utilisez des flux ou des BLOB et des CLOB matérialisés de manière incrémentielle pour traiter la mise à jour d'importantes valeurs de colonne ou l'envoi d'importants paramètres IN. Le pilote JDBC envoie ces éléments au serveur par plusieurs boucles de connexion, ce qui vous permet de définir et de mettre à jour des valeurs plus importantes que ce que la mémoire peut contenir.

## <a name="see-also"></a> Voir aussi

[Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)
