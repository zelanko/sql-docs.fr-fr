---
title: Le traitement des Options de la Page de propriétés (Gestionnaire de rapports) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28f07c70-7132-4d15-9505-4fdf31dc9cc0
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 17db40e24318fad194ec21ca30e6394f3fe607e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052554"
---
# <a name="processing-options-properties-page-report-manager"></a>Page de propriétés Options de traitement (Gestionnaire de rapports)
  La page de propriétés Options de traitement vous permet de définir les propriétés d'exécution du rapport actuellement sélectionné. Ces options déterminent à quel moment se produit le traitement des données du rapport. Vous pouvez définir ces options pour récupérer les données du rapport aux heures creuses. Si un rapport est consulté fréquemment, vous pouvez mettre en cache de façon temporaire des copies de ce dernier pour éliminer les temps d'attente lorsque plusieurs utilisateurs y accèdent à quelques minutes d'intervalle.  
  
> [!NOTE]  
>  L'historique de rapport, les instantanés d'exécution et les fonctionnalités de mise en cache sont disponibles dans chaque édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-processing-options-properties-page"></a>Pour ouvrir la page de propriétés Options de traitement  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez définir les propriétés de traitement.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Options de traitement** .  
  
## <a name="options"></a>Options  
 **Toujours exécuter ce rapport avec les données les plus récentes**  
 Utilisez cette option si vous souhaitez récupérer les données du rapport lorsqu'un utilisateur le sélectionne. Si une copie mise en cache du rapport est disponible, elle est retournée à l'utilisateur. Sinon, l'extraction et le rendu des données se produisent lorsqu'un utilisateur sélectionne le rapport.  
  
 Sélectionnez **Ne pas mettre en cache les copies temporaires de ce rapport** pour que le rapport soit toujours exécuté avec les données les plus récentes. Chaque utilisateur qui ouvre le rapport déclenche une requête sur la source de données qui contient les données utilisées dans le rapport.  
  
 Sélectionnez **Mettre en cache une copie temporaire du rapport**pour placer une copie temporaire du rapport dans un cache lorsqu’un utilisateur ouvre le rapport pour la première fois. Les utilisateurs suivants qui exécutent le rapport dans la période de mise en cache reçoivent la copie mise en cache du rapport. La mise en cache améliore habituellement les performances, car le rapport est retourné à partir du cache au lieu d'être traité une nouvelle fois.  
  
 Les rapports mis en cache doivent finalement expirer. Spécifiez le nombre de minutes pendant lesquelles la copie mise en cache du rapport doit être enregistrée. Dès qu'une copie temporaire expire, elle n'est plus retournée à partir du cache. La prochaine fois qu'un utilisateur ouvrira le rapport, le serveur de rapports retraitera ce dernier et replacera une copie du rapport actualisé dans le cache.  
  
 Une planification vous permet également de définir une fréquence d'expiration pour un rapport. Pour qu'un rapport mis en cache expire en fin de journée, par exemple, vous pouvez sélectionner une heure durant la nuit après laquelle la copie expire.  
  
 **Afficher ce rapport à partir d’un instantané d’exécution de rapport**  
 Utilisez cette option pour récupérer un rapport qui été stocké comme un instantané au moment de la planification. Lorsque vous choisissez cette option, vous pouvez planifier l'exécution du traitement des données pendant les heures creuses. Contrairement aux copies mises en cache créées lorsqu'un utilisateur ouvre le rapport, un instantané est créé, puis actualisé, suivant une planification. Les instantanés n'expirent pas. Ils restent en service jusqu'à ce qu'ils soient remplacés par de nouvelles versions.  
  
 Les instantanés générés par les paramètres d'exécution de rapport ont les mêmes caractéristiques que les instantanés d'historique de rapport. La seule différence réside dans le fait qu'il n'existe qu'un seul instantané d'exécution de rapport et plusieurs instantanés d'historique de rapport. Les instantanés d'historique de rapport sont accessibles à partir de la page Historique du rapport, qui stocke de nombreuses instances d'un rapport à différents moments. Les utilisateurs ont accès aux instantanés d'exécution de rapport à partir des dossiers (comme pour les rapports actifs). Dans le cas d'instantanés d'exécution de rapport, rien n'indique aux utilisateurs que le rapport est un instantané.  
  
 Sélectionnez l'option connexe **Créer un instantané du rapport lorsque vous cliquez sur le bouton Appliquer de cette page** pour créer un instantané de rapport lorsque vous cliquez sur Appliquer. Ainsi, vous générez immédiatement l'instantané de rapport pour le rendre disponible avant l'heure de début planifiée.  
  
 **Délai d’exécution de rapport**  
 Spécifie si le traitement d'un rapport expire après un certain nombre de secondes. Si vous choisissez le paramètre par défaut, le paramètre du délai d'expiration spécifié dans la page Paramètres du site est utilisé pour le rapport.  
  
 Cette valeur s'applique au traitement du rapport sur le serveur de rapports. Elle ne définit aucun délai d'attente pour le traitement des données sur le serveur de base de données qui fournit les données pour le rapport. Toutefois, la valeur que vous spécifiez doit être suffisante pour terminer le traitement des données et du rapport. Le nombre pour le traitement du rapport commence lorsque le rapport est sélectionné et se termine lors de l'ouverture du rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés de traitement des rapports](report-server/set-report-processing-properties.md)   
 [Mise en cache de rapports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [Aide (F1) de gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  