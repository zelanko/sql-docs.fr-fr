---
title: Préparation de la mise en cache des métadonnées d'instruction pour le pilote JDBC
description: Découvrez comment JDBC Driver pour SQL Server met en cache les instructions préparées pour améliorer les performances en minimisant les appels à la base de données et comment contrôler son comportement.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67b35e04ede8608d222c8fc31d89bfd01b093ba7
ms.sourcegitcommit: 129f8574eba201eb6ade1f1620c6b80dfe63b331
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87435389"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Préparation de la mise en cache des métadonnées d'instruction pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cet article fournit des informations sur les deux changements mis en œuvre pour améliorer les performances du pilote.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Traitement par lot d’instructions d’annulation d’instructions préparées
Depuis la version 6.1.6-preview, une amélioration des performances a été mise en œuvre en minimisant les allers-retours du serveur vers SQL Server. Auparavant, pour chaque requête prepareStatement, un appel à une instruction d’annulation était également envoyé. À présent, le pilote traite par lot les requêtes d’annulation jusqu’au seuil « ServerPreparedStatementDiscardThreshold », qui a une valeur par défaut de 10.

> [!NOTE]  
>  Les utilisateurs peuvent modifier la valeur par défaut à l’aide de la méthode suivante : setServerPreparedStatementDiscardThreshold(int value)

Autre modification introduite à partir de 6.1.6-Preview : le pilote appelle toujours sp_prepexec. À présent, pour la première exécution d’une instruction préparée, le pilote appelle sp_executesql et, pour le reste, il exécute sp_prepexec et lui affecte un descripteur. Pour plus d’informations, cliquez [ici](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Les utilisateurs peuvent modifier le comportement par défaut des versions précédentes qui appellent toujours sp_prepexec en affectant à enablePrepareOnFirstPreparedStatementCall la valeur **true** à l’aide de la méthode suivante : setEnablePrepareOnFirstPreparedStatementCall(boolean value)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Liste des nouvelles API introduites avec cette modification en vue du traitement par lot d’instructions Unprepare pour des instructions préparées

 **SQLServerConnection**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Retourne le nombre d’actions d’annulation d’instructions préparées actuellement en suspens.|
|void closeUnreferencedPreparedStatementHandles()|Force l’exécution des demandes d’annulation pour les instructions préparées ignorées en suspens.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Retourne le comportement d’une instance de connexion spécifique. Si la valeur est false, la première exécution appelle sp_executesql sans préparer d’instruction. À la deuxième exécution, elle appelle sp_prepexec et configure un handle d’instruction préparée. Les exécutions suivantes appellent sp_execute. Cela évite d’utiliser sp_unprepare lors de la fermeture de l’instruction préparée si l’instruction n’est exécutée qu’une seule fois. La valeur par défaut de cette option peut être modifiée en appelant setDefaultEnablePrepareOnFirstPreparedStatementCall().|
|void setEnablePrepareOnFirstPreparedStatementCall(boolean value)|Spécifie le comportement d’une instance de connexion spécifique. Si la valeur est false, la première exécution appelle sp_executesql sans préparer d’instruction. À la deuxième exécution, elle appelle sp_prepexec et configure un handle d’instruction préparée. Les exécutions suivantes appellent sp_execute. Cela évite d’utiliser sp_unprepare lors de la fermeture de l’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|int getServerPreparedStatementDiscardThreshold()|Retourne le comportement d’une instance de connexion spécifique. Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare. La valeur par défaut de cette option peut être modifiée en appelant getDefaultServerPreparedStatementDiscardThreshold().|
|void setServerPreparedStatementDiscardThreshold(int value)|Spécifie le comportement d’une instance de connexion spécifique. Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. S’il est défini sur > 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare.|

 **SQLServerDataSource**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|Si cette configuration est false, la première exécution d’une instruction préparée appelle sp_executesql sans préparer d’instruction. À la deuxième exécution, elle appelle sp_prepexec et configure un handle d’instruction préparée. Les exécutions suivantes appellent sp_execute. Cela évite d’utiliser sp_unprepare lors de la fermeture de l’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Si cette configuration retourne la valeur false, la première exécution d’une instruction préparée appelle sp_executesql sans préparer d’instruction. À la deuxième exécution, elle appelle sp_prepexec et configure un handle d’instruction préparée. Les exécutions suivantes appellent sp_execute. Cela évite d’utiliser sp_unprepare lors de la fermeture de l’instruction préparée si l’instruction n’est exécutée qu’une seule fois.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare|
|int getServerPreparedStatementDiscardThreshold()|Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. S’il est défini sur {@literal >} 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare.|

## <a name="prepared-statement-metadata-caching"></a>Mise en cache des métadonnées de l’instruction préparée
Depuis la version 6.3.0-Preview, le pilote JDBC Microsoft pour SQL Server prend en charge la mise en cache des instructions préparées. Avant la version 6.3.0-Preview, si un utilisateur exécutait une requête déjà préparée et mise en cache, l’appel de cette même requête n’entraînait pas sa préparation. À présent, le pilote recherche la requête dans le cache, identifie le descripteur, puis exécute la requête avec sp_execute.
La mise en cache des métadonnées d'instruction préparée est **désactivée** par défaut. Pour l’activer, vous devez appeler la méthode suivante sur l’objet de connexion :

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Par exemple : `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Liste des nouvelles API introduites avec cette modification en vue de la mise en cache des métadonnées d'instruction préparée

 **SQLServerConnection**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean value)|Définit le regroupement d’instructions sur true ou false.|
|boolean getDisableStatementPooling()|Retourne la valeur true si le regroupement d’instructions est désactivé.|
|void setStatementPoolingCacheSize(int value)|Spécifie la taille du cache d’instructions préparées pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementPoolingCacheSize()|Retourne la taille du cache d’instructions préparées pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementHandleCacheEntryCount()|Retourne le nombre actuel de handles d’instruction préparée regroupés.|
|boolean isPreparedStatementCachingEnabled()|Indique si le regroupement d’instructions est activé ou non pour cette connexion.|

 **SQLServerDataSource**
 
|Nouvelle méthode|Description|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolean disableStatementPooling)|Définit le regroupement d’instructions sur true ou false|
|boolean getDisableStatementPooling()|Retourne la valeur true si le regroupement d’instructions est désactivé.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Spécifie la taille du cache d’instructions préparées pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|
|int getStatementPoolingCacheSize()|Retourne la taille du cache d’instructions préparées pour cette connexion. Une valeur inférieure à 1 signifie aucun cache.|

## <a name="see-also"></a>Voir aussi  
 [Amélioration des performances et de la fiabilité avec le pilote JDBC](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
