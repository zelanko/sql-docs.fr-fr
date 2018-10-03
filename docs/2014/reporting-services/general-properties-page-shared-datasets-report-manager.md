---
title: Page propriétés générales, Datasets partagés (rapport Gestionnaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 24e303409568f028ff57cf189cad4f1022111e82
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202729"
---
# <a name="general-properties-page-shared-datasets-report-manager"></a>Page Propriétés générales, Datasets partagés (Gestionnaire de rapports)
  La page Dataset partagé permet d'afficher et de gérer les propriétés d'un élément de dataset partagé.  
  
 Dans le Gestionnaire de rapports, vous ne pouvez pas afficher ou modifier la définition du dataset partagé, y compris la requête. Pour modifier la définition, vous devez utiliser un outil de création permettant d'ouvrir et de modifier la définition, puis l'enregistrer sur le serveur de rapports.  
  
 Avec un dataset partagé, vous pouvez gérer les paramètres d'un dataset séparément des rapports, des composants et des autres éléments de catalogue qui l'utilisent.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-shared-dataset-properties-page-for-a-shared-dataset"></a>Pour ouvrir la page des propriétés de dataset partagé d'un dataset partagé  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le dataset partagé dont vous souhaitez configurer les propriétés.  
  
2.  Pointez sur le dataset partagé, puis cliquez sur la flèche déroulante.  
  
3.  Dans la liste déroulante, cliquez sur **Gérer**. La page des propriétés générales s'affiche.  
  
## <a name="options"></a>Options  
 **Nom**  
 Permet de taper le nom du dataset partagé afin d'identifier l'élément dans l'arborescence des dossiers du serveur de rapports.  
  
 **Description**  
 Permet de fournir des informations sur le dataset partagé. Cette description apparaît dans la page Contenu.  
  
 **Masquer en mode liste**  
 Permet de masquer le dataset partagé pour les utilisateurs qui recourent au mode Liste dans le Gestionnaire de rapports. Le mode Liste est le format d'affichage par défaut lorsque vous parcourez l'arborescence des dossiers du serveur de rapports. En mode Liste, les noms et les descriptions des éléments sont affichés sur la largeur de la page. Un autre format d'affichage, le mode Détails, est également disponible. En mode Détails, les descriptions ne sont pas affichées, mais cette vue fournit d'autres informations sur l'élément. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Délai d’exécution de requête**  
 Tapez la valeur en secondes du délai d'expiration de la requête. Si la valeur est 0, la requête n'est soumise à aucun délai d'expiration.  
  
 **Appliquer**  
 Enregistrez vos modifications.  
  
 **Supprimer**  
 Permet de supprimer le dataset partagé de la base de données du serveur de rapports. La suppression d'un dataset partagé désactive les rapports ou les versions mises en cache. Pour réactiver un rapport, vous devez l'ouvrir dans un outil de création de rapports et spécifier un dataset portant le même nom et utilisant la même collection de champs. Vous pouvez également mettre à jour chaque référence de région de données pour qu'elle utilise un dataset différent avec la même collection de champs.  
  
 **Déplacer**  
 Permet de déplacer un dataset partagé dans l'arborescence des dossiers du serveur de rapports. Un clic sur ce bouton permet d'ouvrir la page Déplacer les éléments dans laquelle vous pouvez parcourir les dossiers pour sélectionner un nouvel emplacement. Pour plus d’informations, consultez [Page déplacer les éléments &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Télécharger**  
 Permet d'extraire une copie de la définition du dataset partagé. Selon les associations de fichiers définies sur votre ordinateur, le fichier s'ouvre dans Visual Studio ou une autre application. Dans la plupart des cas, le dataset partagé s'ouvre dans un fichier XML.  
  
 **Remplacer**  
 Permet de remplacer la définition du dataset partagé par une définition différente d'un fichier .rds situé dans le système de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Contenu de la Page &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Options d’actualisation de cache &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)   
 [Page mise en cache, Datasets partagés &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md)   
 [Gérer des Datasets partagés](report-data/manage-shared-datasets.md)   
 [Cache des Datasets partagés &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md)  
  
  
