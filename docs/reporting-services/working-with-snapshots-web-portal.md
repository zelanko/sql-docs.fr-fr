---
title: "Utilisation des instantanés (portail web) | Documents Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ae20556-e243-4a60-b076-9fd9e82c7355
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f158c027acfd2acdf7a745c640babad561ec0d20
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="working-with-snapshots-web-portal"></a>Utilisation des instantanés (portail web)

[!INCLUDE[ssrs-appliesto-sql2016-preview](../includes/ssrs-appliesto-sql2016-preview.md)]

Vous pouvez contrôler si les instantanés sont créés pour un rapport en sélectionnant le **points de suspension (...)**  d’un rapport, en sélectionnant **gérer** et en sélectionnant **mise en cache** ou **instantanés d’historique**.  
  
> [!NOTE]
> Le service SQL Server Agent doit être démarré.  
   
Vous pouvez créer un instantané du cache, afin d’accélérer le chargement de propriétés d’exécution spécifiques. Vous pouvez également utiliser des instantanés d’historique pour capturer des points dans le temps.  
  
## <a name="creating-a-cache-snapshot"></a>Création d’un instantané du cache  
  
Vous pouvez créer un instantané de la manière suivante.  
  
![ssRSWebPortal-report-caching4](../reporting-services/media/ssrswebportal-report-caching4.png)  
  
1.  Dans la page **Mise en cache** , sélectionnez **Toujours exécuter ce rapport sur les instantanés prégénérés** pour activer les options de création d’un instantané.  
  
2.  Sélectionnez **Créer des instantanés de cache selon une planification** si vous voulez planifier un instantané périodique. Vous pouvez ensuite utiliser une planification partagée, ou définir une planification personnalisée pour actualiser l’instantané.  
  
3.  Sélectionnez **Créer un instantané du cache quand je clique sur Appliquer dans cette page** si vous souhaitez créer un instantané du cache dès maintenant. Si vous sélectionnez cette option, l’instantané n’est pas actualisé.  
  
## <a name="create-modify-and-delete-history-snapshots"></a>Créer, modifier et supprimer des instantanés d’historique  
  
Pour utiliser des instantanés d’historique, gérez un rapport, puis sélectionnez **Instantanés d’historique**.  
  
La page **Instantanés d’historique** vous permet d’afficher des instantanés de rapport qui sont générés et stockés dans le temps. Selon les options définies sur le serveur de rapports, l’historique peut contenir uniquement les instantanés les plus récents.  
  
Un historique de rapport est toujours affiché dans le contexte du rapport dont il est issu. Vous ne pouvez pas afficher l'historique de tous les rapports sur un serveur de rapports dans un seul emplacement.  
  
Pour générer un instantané d’historique, le rapport doit pouvoir s’exécuter sans assistance (c’est-à-dire qu’il doit utiliser les informations d’identification stockées ; les rapports paramétrables doivent contenir des valeurs de paramètres par défaut pour tous les paramètres). Un historique de rapport peut être généré manuellement ou sous forme d'opération planifiée. Les propriétés d'historique du rapport déterminent les modes de création de l'historique de rapport.  
  
![ssRSWebPortal-historysnapshots1](../reporting-services/media/ssrswebportal-historysnapshots1.png)  
   
1.  Pour créer un instantané d’historique, sélectionnez **+ Nouvel instantané d’historique**. Cette opération traite le rapport et ajoute une entrée à la liste.  
  
2.  Vous pouvez parcourir les paramètres pour définir des planifications et des stratégies de rétention.  
  
3.  Vous pouvez sélectionner un instantané d’historique pour l’afficher. Les instantanés qui apparaissent dans l'historique de rapport ne sont différenciés que par la date et l'heure de leur création. Il n'y a aucun moyen de déterminer si un instantané a été généré par une opération manuelle ou planifiée.  
  
### <a name="schedule-and-settings"></a>Planification et paramètres  
  
Sélectionnez **Planification et paramètres** pour afficher des options supplémentaires pour la planification et le contrôle de la rétention des instantanés créés.  
  
![ssRSWebPortal-historysnapshots2](../reporting-services/media/ssrswebportal-historysnapshots2.png)  
   
Vous pouvez créer les instantanés selon une planification définie par vos soins. Vous pouvez également empêcher la création d’instantanés par d’autres personnes. Décocher la case **Autoriser les utilisateurs à créer manuellement des instantanés** désactive le bouton **+ Nouvel instantané d’historique**.  
  
Vous pouvez également définir la façon dont vous souhaitez conserver les instantanés.  
  
**Enregistrer également les instantanés de cache dans l’historique de rapport**  
  
Vous pouvez sélectionner cette option pour copier un instantané de rapport que vous avez généré selon les propriétés d’exécution de rapport dans l’historique de rapport. Vous pouvez définir les propriétés d'exécution de rapport pour exécuter un rapport à partir d'un instantané générée. En définissant cette propriété d'historique de rapport, vous pouvez conserver un enregistrement de tous les instantanés des rapports générés au fil du temps en plaçant des copies de ces derniers dans un historique de rapport.

## <a name="next-steps"></a>Étapes suivantes

[Portail Web](../reporting-services/web-portal-ssrs-native-mode.md)  
[Utilisation des rapports paginés](working-with-paginated-reports-web-portal.md)  
[Travailler avec les Datasets partagés](../reporting-services/work-with-shared-datasets-web-portal.md)

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
