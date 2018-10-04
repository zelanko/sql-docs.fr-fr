---
title: Page propriétés générales, rapports (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 66c99d28-ab41-45f0-bf02-ed560293595d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e8606f2ee9afeb0e5e3ab0663290471b0d2d4463
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206161"
---
# <a name="general-properties-page-reports-report-manager"></a>Page Propriétés générales, Rapports (Gestionnaire de rapports)
  La page Propriétés générales des rapports vous permet de renommer, supprimer, déplacer ou remplacer la définition de rapport. Vous pouvez également utiliser cette page pour créer un rapport lié. Des informations détaillées sur l'utilisateur qui a créé et modifié le rapport, et la date des modifications sont affichées dans la partie supérieure de la page.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a>Pour ouvrir la page Propriétés générales pour un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez afficher ou configurer des propriétés.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom du rapport. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et certains symboles. N'utilisez pas les caractères ; ? : \@ & = +, $ * \< >  
  
 " ou / lorsque vous spécifiez un nom.  
  
 **Description**  
 Entrez une description du rapport. Cette description apparaît dans la page Contenu. Elle est visible par les utilisateurs qui sont autorisés à accéder au rapport.  
  
 **Masquer en mode liste**  
 Activez cette option pour masquer le rapport pour les utilisateurs qui utilisent le mode de visualisation Liste dans le Gestionnaire de rapports. Le mode Liste est le format d'affichage par défaut lorsque vous parcourez l'arborescence des dossiers du serveur de rapports. En mode Liste, les noms et les descriptions des éléments sont affichés sur la largeur de la page. Un autre format d'affichage, le mode Détails, est également disponible. En mode Détails, les descriptions ne sont pas affichées, mais cette vue fournit d'autres informations sur l'élément. Vous pouvez masquer un élément en mode Liste, mais pas en mode Détails. Pour restreindre l'accès à un élément, vous devez créer une attribution de rôle.  
  
 **Appliquer**  
 Cliquez pour enregistrer vos modifications.  
  
 **Supprimer**  
 Cliquez pour supprimer le rapport de la base de données du serveur de rapports. La suppression d'un rapport entraîne celle de l'historique de rapport et de tous les abonnements et les planifications propres au rapport associés. Si le rapport est associé à des rapports liés, ces derniers deviennent non valides.  
  
 **Déplacer**  
 Cliquez pour déplacer un rapport dans l'arborescence des dossiers du serveur de rapports. Un clic sur ce bouton permet d'ouvrir la page Déplacer les éléments dans laquelle vous pouvez parcourir les dossiers pour sélectionner un nouvel emplacement. Pour plus d’informations, consultez [Page déplacer les éléments &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Créer un rapport lié**  
 Cliquez pour ouvrir la page Nouveau rapport lié. Pour plus d’informations sur cette page et les rapports liés, consultez [Page nouveau rapport lié &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md).  
  
 **Enregistrer**  
 Cliquez pour extraire une copie en lecture seule de la définition de rapport. Selon les associations de fichiers définies sur votre ordinateur, le fichier s'ouvre dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou une autre application. Dans la plupart des cas, le rapport s'ouvre dans un fichier XML.  
  
 La copie que vous avez ouverte est identique à la définition de rapport d'origine qui a été initialement publiée sur le serveur de rapports. Toutes les propriétés qui ont été définies pour le rapport après sa publication (telles que les paramètres et les propriétés de source de données) ne sont pas reflétées dans le fichier que vous ouvrez.  
  
 Vous pouvez modifier la définition de rapport et l'enregistrer dans un nouveau fichier dans un dossier partagé, et télécharger la définition vers le serveur de rapports sous la forme d'un nouvel élément. Les modifications que vous apportez à la définition de rapport lorsqu’il est ouvert dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (ou une autre application) ne sont pas enregistrées directement sur le serveur de rapports. Vous devez télécharger le fichier pour publier le rapport modifié sur le serveur de rapports.  
  
 **Remplacer**  
 Cliquez pour remplacer la définition de rapport utilisée dans le rapport actuel par une définition différente d'un fichier .rdl situé dans le système de fichiers. Si vous mettez à jour une définition de rapport, vous devez redéfinir les paramètres de la source de données une fois la mise à jour terminée.  
  
 **Changer le lien**  
 Cliquez pour sélectionner une autre définition de rapport pour le rapport lié. Cette option apparaît si le rapport est un rapport lié. Si le rapport est un rapport lié, vous pouvez définir cette propriété pour remplacer la définition de rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Le Gestionnaire de rapports &#40;SSRS en Mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
