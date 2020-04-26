---
title: Choisir un programme de résolution | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 17c751898aee25fa98bfeb6c2a7e1f1143bc61ae
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62931628"
---
# <a name="choose-a-resolver"></a>Choisir un résolveur
  Lors du choix d'un résolveur, considérez l'importance de la résolution des conflits dans votre application et si vous pouvez utiliser l'outil de résolution des conflits par défaut basé sur les priorités ou si vous devez utiliser un résolveur d'articles.  
  
 Si vos données sont partitionnées sans que plusieurs utilisateurs écrivent dans les mêmes partitions, et que votre topologie de réplication est relativement simple (un éditeur et quelques abonnés), les conflits seront rares ou inexistants. Dans ce type d'environnement, vous n'avez probablement pas besoin d'une stratégie complexe de résolution des conflits. Une stratégie utilisant les paramètres par défaut de résolution de conflits, des abonnements clients et une règle du type « la première modification l'emporte », est recommandée. Si la topologie est plus complexe (utilisant par exemple des Abonnés de réédition), des abonnements serveur avec des priorités spécifiques peuvent être plus appropriés.  
  
 Un résolveur d'articles est recommandé si votre entreprise requiert une solution plus avancée que celle qui est disponible avec le résolveur par défaut. Si vous choisissez d'utiliser un résolveur d'articles, il est recommandé d'utiliser un gestionnaire de logique métier. Pour plus d’informations, consultez [Exécuter la logique métier lors de la synchronisation de fusion](execute-business-logic-during-merge-synchronization.md).  
  
 Enfin, le choix entre utiliser le résolveur par défaut et utiliser un résolveur d'articles doit être basé sur les besoins de l'application en termes de données et de logique métier. Par exemple, considérez des employés entrant des données sur le classement des clients dans un ensemble de tables non partitionnées au niveau de différents abonnés. Ces employés sont répartis en plusieurs catégories professionnelles (directeurs de filiale, directeurs de gamme de produits, personnel des ventes), et la catégorie professionnelle détermine les données prioritaires. Dans ce cas, il est possible de créer un résolveur d'articles qui utilise les données de la catégorie professionnelle de l'article pour déterminer celui qui l'emporte en cas de conflit.  
  
 Lorsque des conflits sont susceptibles de se produire assez fréquemment, voici les décisions les plus importantes à prendre en considération lors de la mise en œuvre d'une stratégie de résolution de conflits.  
  
|Problème de résolution de conflits|Recommandation|  
|-------------------------------|--------------------|  
|Différentes catégories d'utilisateurs nécessitent des valeurs de priorité différentes.|Utilisez le résolveur par défaut et créez des abonnements serveur avec des valeurs de priorité différentes.<br /><br /> -Ou-<br /><br /> Utilisez un résolveur d'article qui reconnaît une colonne de valeur d'autorité dans l'article pour contribuer à résoudre tout conflit.|  
|Nécessité d'une solution de résolution de conflit du type “ le premier l'emporte ”.|Utilisez le résolveur par défaut et créez des abonnements clients.|  
|La modification d'une même ligne de données par plusieurs utilisateurs est acceptable, du moment qu'aucune modification conflictuelle n'est apportée à la même colonne.|Utilisez soit le résolveur par défaut soit un résolveur d'articles où le suivi au niveau des colonnes est activé.|  
|Les multiples modifications de valeurs dans une ligne doivent être signalées comme un conflit.|Utilisez soit le résolveur par défaut soit un résolveur d'articles où le suivi au niveau des lignes est activé.|  
|De multiples modifications de valeurs dans un enregistrement logique doivent être signalées comme un conflit.|Utilisez le résolveur par défaut avec un suivi au niveau des enregistrements logiques (les enregistrements logiques ne prennent pas en charge les résolveurs personnalisés ni les gestionnaires de logique métier).|  
|Les données de résultat d'un conflit doivent être différentes des données de conflit originales.|Utilisez un résolveur d'articles qui calcule les nouvelles valeurs.|  
  
## <a name="see-also"></a>Voir aussi  
 [Detecting and Resolving Conflicts in Logical Records](advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Détection et résolution des conflits de réplication de fusion avancée](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Republier des données](../republish-data.md)  
  
  
