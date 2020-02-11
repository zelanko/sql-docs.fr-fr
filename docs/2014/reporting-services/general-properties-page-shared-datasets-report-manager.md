---
title: Page Propriétés générales, datasets partagés (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10798e41-24c3-4e69-893b-7ee6af7fc958
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf433f27a5d8dc7f5e0efcf6f5774ed292d1e1a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109064"
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
  
 **Masquer en mode Liste**  
 Permet de masquer le dataset partagé pour les utilisateurs qui recourent au mode Liste dans le Gestionnaire de rapports. Le mode Liste est le format d'affichage par défaut lorsque vous parcourez l'arborescence des dossiers du serveur de rapports. En mode Liste, les noms et les descriptions des éléments sont affichés sur la largeur de la page. Un autre format d'affichage, le mode Détails, est également disponible. En mode Détails, les descriptions ne sont pas affichées, mais cette vue fournit d'autres informations sur l'élément. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Délai de requête**  
 Tapez le nombre de secondes avant l’expiration de la requête. Si la valeur est égale à 0, la requête n’expire pas.  
  
 **Appliquer**  
 Enregistrez vos modifications.  
  
 **Supprimer**  
 Permet de supprimer le dataset partagé de la base de données du serveur de rapports. La suppression d'un dataset partagé désactive les rapports ou les versions mises en cache. Pour réactiver un rapport, vous devez l'ouvrir dans un outil de création de rapports et spécifier un dataset portant le même nom et utilisant la même collection de champs. Vous pouvez également mettre à jour chaque référence de région de données pour qu'elle utilise un dataset différent avec la même collection de champs.  
  
 **Déplacer**  
 Permet de déplacer un dataset partagé dans l'arborescence des dossiers du serveur de rapports. Un clic sur ce bouton permet d'ouvrir la page Déplacer les éléments dans laquelle vous pouvez parcourir les dossiers pour sélectionner un nouvel emplacement. Pour plus d’informations, consultez [page déplacer des éléments &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Downloader**  
 Permet d'extraire une copie de la définition du dataset partagé. Selon les associations de fichiers définies sur votre ordinateur, le fichier s'ouvre dans Visual Studio ou une autre application. Dans la plupart des cas, le dataset partagé s'ouvre dans un fichier XML.  
  
 **Lieu**  
 Permet de remplacer la définition du dataset partagé par une définition différente d'un fichier .rds situé dans le système de fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Page contenu &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Aide (F1) Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Options d’actualisation du cache &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/cache-refresh-options-report-manager.md)   
 [Page mise en cache, datasets partagés &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/caching-page-shared-datasets-report-manager.md)   
 [Gérer des datasets partagés](report-data/manage-shared-datasets.md)   
 [Mettre en cache les datasets partagés &#40;SSRS&#41;](report-server/cache-shared-datasets-ssrs.md)  
  
  
