---
title: Suspendre le traitement des rapports et des abonnements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66100920"
---
# <a name="pause-report-and-subscription-processing"></a>Suspendre le traitement des rapports et des abonnements
  Vous ne pouvez pas suspendre directement un rapport ou un abonnement. Cependant, vous pouvez bloquer le traitement du rapport et de l'abonnement avant le démarrage du processus ou lorsqu'une connexion à une source de données est établie. Vous pouvez également empêcher le traitement d'un rapport ou d'un abonnement en le rendant inaccessible aux utilisateurs.  
  
 Les stratégies suivantes permettent d'empêcher temporairement l'exécution d'un processus.  
  
## <a name="modify-role-assignments-to-prevent-access"></a>Modifier les attributions de rôles afin d'empêcher les accès  
 Le meilleur moyen de rendre un rapport indisponible consiste à supprimer temporairement l'attribution de rôle qui permet d'accéder au rapport. Cette méthode peut s'appliquer à tous les rapports, quelle que soit la façon dont est établie la connexion à la source de données. Elle a une incidence uniquement sur le rapport et n'affecte pas la mise en œuvre des autres rapports ou éléments.  
  
 Pour supprimer une attribution de rôle, ouvrez la page Propriétés de sécurité du rapport dans le Gestionnaire de rapports. Si le rapport hérite de la sécurité d’un parent, cliquez sur **Modifier la sécurité de l’élément** pour créer une stratégie de sécurité restrictive qui supprime les attributions de rôles offrant un accès étendu. Par exemple, vous pouvez supprimer une attribution de rôle qui fournit un accès à Tout le monde et conserver l’attribution de rôle offrant un accès à un petit groupe d’utilisateurs, comme le groupe Administrateurs.  
  
## <a name="disable-a-shared-data-source"></a>Désactiver une source de données partagée  
 L'un des avantages de l'utilisation de sources de données partagées est que vous pouvez désactiver celles-ci pour empêcher l'exécution d'un rapport ou d'un abonnement piloté par les données. La désactivation d'une source de données partagée déconnecte le rapport de sa source externe. Lorsqu'elle est désactivée, la source de données n'est plus disponible pour les rapports et les abonnements qui l'utilisent. Pour désactiver une source de données partagée, ouvrez-la dans le Gestionnaire de rapports et désactivez la case à cocher **Activer cette source de données** .  
  
 Notez que le rapport continue à se charger même si la source de données n'est pas disponible. Le rapport ne contient pas de données, mais les utilisateurs dotés des autorisations appropriées peuvent accéder aux pages des propriétés, aux paramètres de sécurité, à l'historique de rapport et aux informations d'abonnement associés à ce rapport.  
  
## <a name="pause-a-shared-schedule"></a>Suspendre une planification partagée  
 Si un rapport ou un abonnement s'exécute à partir d'une planification partagée, vous pouvez suspendre la planification pour empêcher le traitement. Tous les traitements de rapports et d'abonnements pilotés par la planification sont reportés jusqu'à la reprise de la planification. Pour plus d’informations, consultez [suspendre et reprendre des planifications partagées](schedules.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services serveur de rapports &#40;le mode natif&#41;](../report-server/reporting-services-report-server-native-mode.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Page Propriétés de sécurité, éléments &#40;Gestionnaire de rapports&#41;](../security-properties-page-items-report-manager.md)  
  
  
