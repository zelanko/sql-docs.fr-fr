---
title: Page de propriétés générales, modèles (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.general.f1
ms.assetid: 7ad59850-8135-4c4d-95e9-6d705b6d77a8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bdc8abebbf713372caf31429082f9d3fda4cfc42
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018241"
---
# <a name="general-properties-page-models-report-manager"></a>Page Propriétés générales, Modèles (Gestionnaire de rapports)
  La page des propriétés générales des modèles de rapport vous permet de renommer, supprimer, déplacer ou remplacer le fichier de définition de modèle (.smdl). Des informations détaillées sur l'utilisateur qui a créé ou modifié le modèle et la date des modifications sont affichées en haut de la page.  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
###### <a name="to-open-the-general-properties-page-for-a-model"></a>Pour ouvrir la page des propriétés générales pour un modèle  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le modèle pour lequel vous souhaitez afficher ou configurer des propriétés.  
  
2.  Pointez sur le modèle et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page Propriétés générales pour le modèle s'ouvre.  
  
## <a name="options"></a>Options  
 **Nom**  
 Spécifie le nom du modèle. Le nom doit contenir un caractère alphanumérique au minimum. Il peut également comporter des espaces et quelques symboles. N'utilisez pas les caractères suivants dans le nom :  
  
 ; ? : \@ & = + , $ / * \< > | " /  
  
 **Description**  
 Tapez la description du modèle. Cette description apparaît dans la page Contenu. Elle est visible par les utilisateurs qui sont autorisés à accéder au modèle.  
  
 **Masqué dans la vue liste**  
 Activez cette case à cocher pour masquer l'élément lorsque le dossier est défini en mode d'affichage des listes. L'affichage des listes est un mode de consultation du contenu des dossiers qui est pris en charge dans le Gestionnaire de rapports. Vous pouvez définir cette option dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] pour déterminer le mode d'affichage de cet élément dans le Gestionnaire de rapports. Pour plus d’informations sur les modes d’affichage dans le Gestionnaire de rapports, consultez [Page contenu &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md).  
  
 **Appliquer**  
 Cliquez pour enregistrer vos modifications.  
  
 **Supprimer**  
 Cliquez pour supprimer le modèle de la base de données du serveur de rapports. La suppression d'un modèle ne supprime ni la source de données partagée dépendante qui fournit des informations de connexion, ni les rapports qui utilisent le modèle comme une source de données. Toutefois, une fois le modèle supprimé, les rapports qui l'utilisent ne s'exécuteront plus.  
  
 **Déplacer**  
 Cliquez pour déplacer un modèle dans l'arborescence des dossiers du serveur de rapports. Un clic sur ce bouton permet d'ouvrir la page Déplacer les éléments dans laquelle vous pouvez parcourir les dossiers pour sélectionner un nouvel emplacement. Pour plus d’informations, consultez [Page déplacer les éléments &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/move-items-page-report-manager.md).  
  
 **Enregistrer**  
 Cliquez pour enregistrer une copie en lecture seule de la définition du modèle. Selon les associations de fichiers définies sur votre ordinateur, le fichier s'ouvre dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou une autre application. Dans la plupart des cas, le modèle s'ouvre dans un fichier XML.  
  
 La copie que vous avez ouverte est identique à la définition de modèle d'origine qui a été initialement publiée sur le serveur de rapports. Toutes les propriétés qui ont été définies pour le modèle après sa publication (telles que les propriétés de source de données) ne sont pas reflétées dans le fichier que vous ouvrez.  
  
 Vous pouvez modifier la définition du modèle et l'enregistrer dans un nouveau fichier dans un dossier partagé, et télécharger la définition vers le serveur de rapports sous la forme d'un nouvel élément. Les modifications que vous apportez à la définition du modèle lorsqu'il est ouvert dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (ou une autre application) ne sont pas enregistrées directement sur le serveur de rapports. Vous devez télécharger le fichier pour publier le modèle modifié sur le serveur de rapports.  
  
 Notez que, si vous souhaitez ouvrir le modèle de rapport dans le Générateur de modèles, vous devez l'enregistrer en tant que fichier .smdl, puis ajouter le fichier .smdl à un projet dans le Générateur de modèles.  
  
 **Remplacer**  
 Cliquez pour remplacer la définition du modèle par une définition différente d'un fichier .smdl situé dans le système de fichiers. Si vous procédez à la mise à jour d'une définition de modèle, redéfinissez les paramètres de la source de données partagée une fois cette opération terminée.  
  
 **Régénérer le modèle**  
 Cliquez pour régénérer un modèle par défaut qui remplace la version actuelle. Cette option apparaît après que le modèle a été généré. Le modèle généré est basé sur la source de données partagée. Il ne peut pas être personnalisé avant d'être généré. Toutefois, après l'avoir généré, vous pouvez cliquer sur **Modifier** pour ouvrir la définition du modèle, l'enregistrer dans le système de fichiers, puis l'ajouter à un projet dans le Générateur de modèles. Après avoir affiné le modèle, vous pouvez le télécharger sur le serveur de rapports en tant que nouvel élément ou cliquer sur **Mettre à jour** sur cette page pour remplacer le modèle généré par la version que vous avez modifiée dans le Générateur de modèles.  
  
## <a name="see-also"></a>Voir aussi  
 [Lier un rapport ou un modèle à une source de données partagée &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md)   
 [Aide du serveur de rapports dans Management Studio via la touche F1](tools/report-server-in-management-studio-f1-help.md)  
  
  
