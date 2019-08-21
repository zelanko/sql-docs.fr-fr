---
title: Préparation de la mise en cache des métadonnées d'instruction pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97224f53bb716abe3b79dd00df12d0eed4a63cec
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027843"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Préparation de la mise en cache des métadonnées d'instruction pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article fournit des informations sur les deux modifications implémentées pour améliorer les performances du pilote.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Traitement par lot d’Unprepare pour les instructions préparées
Depuis la version 6.1.6-Preview, l’amélioration des performances a été mise en œuvre via la minimisation des allers-retours du serveur vers SQL Server. Auparavant, pour chaque requête prepareStatement, un appel à Unprepare a également été envoyé. À présent, le pilote traite par lot les requêtes Unprepare jusqu’au seuil «ServerPreparedStatementDiscardThreshold», qui a une valeur par défaut de 10.

> [!NOTE]  
>  Les utilisateurs peuvent modifier la valeur par défaut à l’aide de la méthode suivante: Setserverpreparedstatementdiscardthreshold, (valeur int)

Une autre modification introduite à partir de 6.1.6-Preview est que, avant cela, le pilote appelle toujours sp_prepexec. À présent, pour la première exécution d’une instruction préparée, le pilote appelle sp_executesql et, pour le REST, il exécute sp_prepexec et lui affecte un descripteur. Vous trouverez plus d’informations [ici](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Les utilisateurs peuvent modifier le comportement par défaut des versions précédentes de toujours appelant sp_prepexec en affectant à enablePrepareOnFirstPreparedStatementCall la **valeur true** à l’aide de la méthode suivante: setenableprepareonfirstpreparedstatementcall, (valeur booléenne )

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Liste des nouvelles API introduites avec cette modification, pour le traitement par lot des instructions préparées pour Unprepare

 **SQLServerConnection**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Retourne le nombre d’actions d’annulation de préparation d’instruction préparée en suspens.|
|void closeUnreferencedPreparedStatementHandles()|Force l’exécution des demandes Unprepare pour toutes les instructions préparées ignorées en suspens.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Retourne le comportement d’une instance de connexion spécifique. Si la valeur est false, la première exécution appelle sp_executesql et ne prépare pas d’instruction. une fois la deuxième exécution effectuée, elle appelle sp_prepexec et configure en fait un descripteur d’instruction préparé. Les exécutions suivantes appellent sp_execute. Cela évite d’avoir à sp_unprepare sur la fermeture d’instruction préparée si l’instruction n’est exécutée qu’une seule fois. La valeur par défaut de cette option peut être modifiée en appelant setDefaultEnablePrepareOnFirstPreparedStatementCall ().|
|void Setenableprepareonfirstpreparedstatementcall, (valeur booléenne)|Spécifie le comportement d’une instance de connexion spécifique. Si la valeur est false, la première exécution appelle sp_executesql et ne prépare pas d’instruction. une fois la deuxième exécution, elle appelle sp_prepexec et configure en fait un descripteur d’instruction préparé. Les exécutions suivantes appellent sp_execute. Cela évite d’avoir à sp_unprepare sur la fermeture d’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|int getServerPreparedStatementDiscardThreshold()|Retourne le comportement d’une instance de connexion spécifique. Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Si le paramètre est < = 1, les actions d’annulation de préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés par lot pour éviter la surcharge de l’appel de sp_unprepare trop souvent. La valeur par défaut de cette option peut être modifiée en appelant getDefaultServerPreparedStatementDiscardThreshold ().|
|void setServerPreparedStatementDiscardThreshold(int value)|Spécifie le comportement d’une instance de connexion spécifique. Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Si le paramètre est < = 1 les actions d’annulation de préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. S’il est défini sur > 1, ces appels sont regroupés pour éviter la surcharge de l’appel de sp_unprepare trop souvent.|

 **SQLServerDataSource**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void Setenableprepareonfirstpreparedstatementcall, (booléen enablePrepareOnFirstPreparedStatementCall)|Si cette configuration est fausse, la première exécution d’une instruction préparée appelle sp_executesql et ne prépare pas d’instruction. une fois la deuxième exécution, elle appelle sp_prepexec et configure un descripteur d’instruction préparé. Les exécutions suivantes appellent sp_execute. Cela évite d’avoir à sp_unprepare sur la fermeture d’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Si cette configuration retourne la valeur false, la première exécution d’une instruction préparée appelle sp_executesql et ne prépare pas d’instruction. une fois la deuxième exécution effectuée, elle appelle sp_prepexec et configure en fait un descripteur d’instruction préparé. Les exécutions suivantes appellent sp_execute. Cela évite d’avoir à sp_unprepare sur la fermeture d’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Si le paramètre est < = 1 les actions d’annulation de préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés pour éviter la surcharge de l’appel de sp_unprepare trop souvent.|
|int getServerPreparedStatementDiscardThreshold()|Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Si le paramètre est < = 1 les actions d’annulation de préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés pour éviter la surcharge d’appel de sp_unprepare trop souvent.|

## <a name="prepared-statement-metatada-caching"></a>Mise en cache de l’instruction préparée métadonnées
Depuis la version 6.3.0-Preview, le pilote JDBC Microsoft pour SQL Server prend en charge la mise en cache des instructions préparées. Avant v 6.3.0-Preview, si l’une d’elles exécute une requête qui a déjà été préparée et stockée dans le cache, l’appel de la même requête n’entraînera pas sa préparation. À présent, le pilote recherche la requête dans le cache et recherche le descripteur et l’exécute avec sp_execute.
La mise en cache des **métadonnées des instructions préparées est désactivée** par défaut. Pour l’activer, vous devez appeler la méthode suivante sur l’objet de connexion:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Par exemple : `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Liste des nouvelles API introduites avec cette modification, pour la mise en cache des métadonnées des instructions préparées

 **SQLServerConnection**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void Setdisablestatementpooling, (valeur booléenne)|Définit le regroupement des instructions sur true ou false.|
|boolean getDisableStatementPooling()|Retourne la valeur true si le regroupement d’instructions est désactivé.|
|void setStatementPoolingCacheSize(int value)|Spécifie la taille du cache d’instructions préparé pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementPoolingCacheSize()|Retourne la taille du cache d’instructions préparé pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementHandleCacheEntryCount()|Retourne le nombre actuel de handles d’instruction préparée regroupés.|
|boolean isPreparedStatementCachingEnabled()|Indique si le regroupement d’instructions est activé ou non pour cette connexion.|

 **SQLServerDataSource**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void Setdisablestatementpooling, (booléen disableStatementPooling)|Définit le regroupement d’instructions sur true ou false|
|boolean getDisableStatementPooling()|Retourne la valeur true si le regroupement d’instructions est désactivé.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Spécifie la taille du cache d’instructions préparé pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementPoolingCacheSize()|Retourne la taille du cache d’instructions préparé pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|

## <a name="see-also"></a>Voir aussi  
 [Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
