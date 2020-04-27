---
title: Page de propriétés options d’instantanés (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f6641f59-5267-4f57-8957-63b93d1a9679
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7a73f3be75a7f0cadf633943aeafffb7217d8e29
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66101159"
---
# <a name="snapshot-options-properties-page-report-manager"></a>Page de propriétés Options d'instantanés (Gestionnaire de rapports)
  La page de propriétés Options d'instantanés vous permet de planifier les instantanés de rapport qui doivent être ajoutés à l'historique de rapport et de définir la limite du nombre d'instantanés de rapport qui sont stockés dans l'historique.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]de, consultez [services de base de données supplémentaires](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md#Add_DBServices).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-snapshot-options-properties-page-for-a-report"></a>Pour ouvrir la page de propriétés Options d'instantanés pour un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez configurer les propriétés d'instantanés de rapport.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Options d'instantanés** .  
  
## <a name="options"></a>Options  
 **Autoriser la création manuelle de l'historique de rapport**  
 Activez cette case à cocher pour ajouter des instantanés à l'historique de rapport en fonction des besoins. L'activation de cette case à cocher entraîne l'affichage du bouton **Nouvel instantané** dans la page Historique.  
  
 **Stocker tous les instantanés d'exécution de rapport dans l'historique**  
 Activez cette case à cocher pour copier un instantané de rapport que vous avez généré selon les propriétés d'exécution de rapport dans l'historique de rapport. Vous pouvez définir les propriétés d'exécution de rapport pour exécuter un rapport à partir d'un instantané générée. En définissant cette propriété d'historique de rapport, vous pouvez conserver un enregistrement de tous les instantanés des rapports générés au fil du temps en plaçant des copies de ces derniers dans un historique de rapport.  
  
 **Utilisez la planification ci-dessous pour ajouter des instantanés à l'historique de rapport.**  
 Activez cette case à cocher pour ajouter des instantanés à l'historique de rapport suivant une planification. Vous pouvez créer une planification qui est utilisée exclusivement à cet effet ou sélectionner une planification partagée prédéfinie si celle-ci contient les informations de planification désirées.  
  
 **Sélectionner le nombre d'instantanés à conserver**  
 Sélectionnez une des options ci-dessous pour contrôler le nombre de rapports qui sont conservés dans l'historique de rapport. Les paramètres d'historique de rapport varient pour chaque rapport.  
  
-   Sélectionnez **Utiliser le paramètre par défaut** pour conserver le paramètre par défaut. L'administrateur du serveur de rapports contrôle un paramètre principal pour le stockage de l'historique de rapport. Si vous choisissez cette option, le nombre d'instantanés conservés dépend de ce paramètre principal.  
  
-   Sélectionnez **Conserver un nombre illimité d'instantanés dans l'historique de rapport** pour conserver tous les instantanés d'historique de rapport. Vous devez supprimer manuellement des instantanés pour réduire la taille de l'historique de rapport.  
  
-   Sélectionnez **Limiter les copies de l'historique de rapport** pour conserver un nombre défini d'instantanés. Lorsque la limite est atteinte, des copies anciennes sont supprimées de l'historique de rapport pour libérer de l'espace pour les nouvelles copies.  
  
 L'historique de rapport est stocké dans la base de données du serveur de rapports. Si vous avez des rapports volumineux ou en nombre important pour lesquels vous souhaitez conserver un historique, envisagez de limiter le volume d'historique de rapport pour mieux gérer l'espace disque nécessaire de la base de données du serveur de rapports.  
  
 **appliquer**  
 Cliquez pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajoutez un instantané à l’historique de rapport &#40;Gestionnaire de rapports&#41;](report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Créer, modifier et supprimer des instantanés dans l'historique de rapport](report-server/create-modify-and-delete-snapshots-in-report-history.md)   
 [Aide F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
