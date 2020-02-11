---
title: Définition des options de regroupement de connexions ODBC | Microsoft Docs
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
ms.openlocfilehash: 43d4fe1ab363326269daf40375e126b930d2548b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901640"
---
# <a name="setting-odbc-connection-pooling-options"></a>Définition des options de mise en pools des connexions ODBC
Le regroupement de connexions permet à une application d’utiliser une connexion à partir d’un pool de connexions qui n’ont pas besoin d’être rétablies pour chaque utilisation. Vous pouvez utiliser l’onglet **regroupement de connexions** de la boîte de dialogue administrateur de sources de **données ODBC** pour activer et désactiver l’analyse des performances. Double-cliquez sur un nom de pilote pour définir le délai d’attente de la connexion.  
  
 Au niveau du pilote, le regroupement de connexions est activé par la valeur de Registre CPTimeout. Cette activation sélective par pilote permet à un administrateur système d’activer le regroupement de connexions uniquement pour les pilotes qui peuvent le prendre en charge. Pour ce faire, vous devez définir la valeur par défaut de CPTimeout lors du programme d’installation du pilote. Double-cliquez sur un nom de pilote pour définir le délai d’attente de la connexion.  
  
 Pour plus d’informations sur le regroupement de connexions, consultez la page relative au [regroupement de connexions ODBC](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Analyse des performances  
 L’analyse des performances assure le suivi des performances de connexion en enregistrant diverses statistiques. Ces statistiques peuvent être personnalisées par le développeur pour inclure des éléments tels que les suivants :  
  
|Compteur|Définition|  
|-------------|----------------|  
|Compteur de connexion forcée ODBC par seconde|Nombre de connexions réelles par seconde effectuées sur le serveur. La première fois que votre environnement porte une charge importante, ce compteur s’affiche très rapidement. Après quelques secondes, elle est supprimée jusqu’à zéro. Il s’agit d’une situation normale lorsque le regroupement de connexions fonctionne. Lorsque les connexions au serveur ont été établies, elles sont utilisées et placées dans le pool pour être réutilisées.|  
|Compteur de déconnexion matérielle ODBC par seconde|Nombre de déconnexions matérielles par seconde émises au serveur. Il s’agit de connexions réelles au serveur qui sont libérées par le regroupement de connexions. Cette valeur augmente de zéro lorsque vous arrêtez tous les clients sur le système et que les connexions commencent à expirer.|  
|Compteur de connexion logicielle ODBC par seconde|Nombre de connexions satisfaites par seconde par le pool : en d’autres termes, connexions à partir de ce pool qui ont été transmises aux utilisateurs. Ce compteur indique si le regroupement fonctionne. En fonction de la charge sur votre serveur, il n’est pas rare d’afficher 40-60 connexions conditionnelles par seconde.|  
|Compteur de déconnexion logicielle ODBC par seconde|Nombre de déconnexions par seconde émises par les applications. Lorsque l’application se libère ou se déconnecte, la connexion est rétablie dans le pool.|  
|Compteur de connexion active ODBC active|Nombre de connexions dans le pool en cours d’utilisation.|  
|Compteur de connexions ODBC actuelles disponibles|Nombre actuel de connexions libres disponibles dans le pool. Il s’agit de connexions actives qui peuvent être utilisées.|  
|Pools actuellement actifs|Nombre de pools actuellement actifs. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexions. Pour plus d’informations, consultez [regroupement de connexions prenant en charge les pilotes](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Pools créés|Nombre de pools actifs, y compris les pools actifs et supprimés. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexions. Pour plus d’informations, consultez [regroupement de connexions prenant en charge les pilotes](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Vous devez spécifier vos propres paramètres de surveillance. Des exemples d’analyse des performances ont été inclus dans cette version d’ODBC.
