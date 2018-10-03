---
title: Définition des Options de regroupement de connexions ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling [ODBC]
- ODBC data source administrator [ODBC], connection pooling options
- ODBC data source administrator [ODBC], performance monitoring
ms.assetid: 037e2f78-f204-40f4-b4ab-d9cdf562012b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 46b6f5d7e6af3726558f5cee72f00ff06e13ab89
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812055"
---
# <a name="setting-odbc-connection-pooling-options"></a>Définition des options de mise en pools des connexions ODBC
Le regroupement de connexions permet à une application d’utiliser une connexion à partir d’un pool de connexions que vous n’avez pas besoin d’être rétablies à chaque utilisation. Vous pouvez utiliser la **le regroupement de connexions** onglet de la **administrateur de sources de données ODBC** boîte de dialogue pour activer et désactiver l’analyse des performances. Double-cliquez sur un nom de pilote pour définir la période de délai d’attente de connexion.  
  
 Au niveau du pilote, le regroupement de connexions est activé par la valeur de Registre CPTimeout. Ce pilote sélectif l’activation permet à un administrateur système activer le regroupement de connexions pour simplement les pilotes qui peuvent prendre en charge. Il s’effectue en définissant la valeur par défaut CPTimeout pendant le programme d’installation du pilote. Double-cliquez sur un nom de pilote pour définir la période de délai d’attente de connexion.  
  
 Pour plus d’informations sur le regroupement de connexions, consultez [le regroupement de connexions ODBC](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Analyse des performances  
 Analyse des performances assure le suivi des performances de connexion en enregistrant une série de statistiques. Ces statistiques peuvent être personnalisés par le développeur à inclure les éléments suivants :  
  
|Compteur|Définition|  
|-------------|----------------|  
|Compteur de disque dur de connexion ODBC par seconde|Le nombre de connexions par seconde qui sont envoyées au serveur. La première fois que votre environnement comporte une charge importante, ce compteur vont monter très rapidement. Après quelques secondes, elle sera remise à zéro. Il s’agit de la situation normale lorsque le regroupement de connexions fonctionne. Lorsque les connexions au serveur ont été établies, elles seront utilisées et placés dans le pool pour une réutilisation.|  
|ODBC dur déconnecter compteur par seconde|Le nombre de disques durs déconnexions par seconde émis vers le serveur. Il s’agit des connexions vers le serveur qui sont publiées par le regroupement de connexions. Cette valeur augmente à partir de zéro lorsque vous arrêtez tous les clients sur le système et les connexions commencent à expirer.|  
|Compteur de connexion de manière réversible ODBC par seconde|Le nombre de connexions satisfaits par le pool par seconde, en d’autres termes, les connexions à partir de ce pool qui ont été transmises aux utilisateurs. Ce compteur indique si le regroupement fonctionne. En fonction de la charge sur votre serveur, il n’est pas rare pour cette option pour afficher les connexions de manière réversible de 40 à 60 par seconde.|  
|Compteur de déconnexion de manière réversible ODBC par seconde|Le nombre de déconnexions par seconde émis par les applications. Lorsque l’application libère ou se déconnecte, la connexion est placée dans le pool.|  
|Compteur de connexion Active actuelle ODBC|Le nombre de connexions dans le pool qui sont actuellement en cours d’utilisation.|  
|Compteur de connexion libre cours ODBC|Le nombre actuel de connexions libres disponibles dans le pool. Il s’agit des connexions actives qui sont disponibles pour utilisation.|  
|Pools actuellement Active.|Le nombre de pools actuellement actives. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexions. Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Pools créés|Le nombre de pools actives, y compris les pools actifs et supprimés. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexions. Pour plus d’informations, consultez [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Vous devez spécifier vos propres paramètres de surveillance. Exemples pour l’analyse des performances ont été inclus avec cette version d’ODBC.
