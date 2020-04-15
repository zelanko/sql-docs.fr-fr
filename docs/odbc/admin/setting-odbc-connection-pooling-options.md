---
title: Définir les options de mise en commun des connexions ODBC (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1d8e66c506518b77320347ce9120254aa1cae287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307194"
---
# <a name="setting-odbc-connection-pooling-options"></a>Définition des options de mise en pools des connexions ODBC
La mise en commun des connexions permet à une application d’utiliser une connexion à partir d’un pool de connexions qui n’ont pas besoin d’être rétablies pour chaque utilisation. Vous pouvez utiliser l’onglet **Connexion Pooling** de la boîte de dialogue **ODBC Data Source Administrator** pour activer et désactiver la surveillance des performances. Double-cliquez sur un nom du pilote pour définir la période d’inséquement de connexion.  
  
 Au niveau du conducteur, la mise en commun des connexions est activée par la valeur du registre CPTimeout. Cette activation sélective par conducteur permet à un administrateur système d’activer la mise en commun des connexions pour uniquement les pilotes qui peuvent le prendre en charge. Il est accompli en définissant la valeur par défaut de CPTimeout pendant le programme d’installation du pilote. Double-cliquez sur un nom du pilote pour définir la période d’inséquement de connexion.  
  
 Pour plus d’informations sur la mise en commun des connexions, voir [ODBC Connection Pooling](../../odbc/reference/develop-app/driver-manager-connection-pooling.md).  
  
## <a name="performance-monitoring"></a>Analyse des performances  
 La surveillance des performances suit les performances de connexion en enregistrant une variété de statistiques. Ces statistiques peuvent être personnalisées par le développeur pour inclure des éléments tels que les éléments suivants :  
  
|Compteur|Définition|  
|-------------|----------------|  
|Compteur de connexion dur ODBC par seconde|Le nombre de connexions réelles par seconde qui sont faites au serveur. La première fois que votre environnement porte une lourde charge, ce compteur va monter très rapidement. Après quelques secondes, il tombera à zéro. C’est la situation normale lorsque la mise en commun des connexions fonctionne. Lorsque les connexions au serveur ont été établies, elles seront utilisées et placées dans la piscine pour être réutilisés.|  
|Compteur de déconnexion dur ODBC par seconde|Nombre de déconnexions dures par seconde émises au serveur. Il s’agit de connexions réelles au serveur qui sont libérés par mise en commun de connexion. Cette valeur passera de zéro lorsque vous arrêterez tous les clients sur le système et que les connexions commencent à s’arrêter.|  
|Compteur de connexion douce ODBC par seconde|Le nombre de connexions satisfaites par la piscine par seconde en d’autres termes, les connexions de ce pool qui ont été remis aux utilisateurs. Ce compteur indique si la mise en commun fonctionne. Selon la charge sur votre serveur, il n’est pas rare que cela affiche 40-60 connexions douces par seconde.|  
|Compteur de déconnexion douce ODBC par seconde|Nombre de déconnexions par seconde émises par les demandes. Lorsque l’application est communiquée ou se déconnecte, la connexion est remise dans la piscine.|  
|Compteur de connexion active actuel ODBC|Nombre de connexions dans la piscine qui sont actuellement utilisées.|  
|Compteur de connexion libre courant ODBC|Le nombre actuel de connexions gratuites disponibles dans la piscine. Ce sont des connexions en direct qui sont disponibles pour une utilisation.|  
|Piscines actuellement actives|Nombre de piscines actuellement actives. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexion. Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
|Piscines créées|Nombre de piscines actives, y compris les piscines actives et enlevées. Ce compteur a été ajouté dans Windows 8, pour les pilotes qui gèrent les connexions dans le pool de connexion. Pour plus d’informations, voir [Driver-Aware Connection Pooling](../../odbc/reference/develop-app/driver-aware-connection-pooling.md).|  
  
 Vous devez spécifier vos propres paramètres de surveillance. Des échantillons pour la surveillance des performances ont été inclus dans cette version de l’ODBC.
