---
title: Créer un rapport lié | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0df6a3bdb6f542b02b62ccf4aa6614da290551f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66102698"
---
# <a name="create-a-linked-report"></a>Créer un rapport lié
  Un rapport lié est un élément de serveur de rapports qui fournit un point d'accès à un rapport existant. Au niveau conceptuel, il est assimilable au raccourci d'un programme que vous utilisez pour exécuter une application ou ouvrir un fichier.  
  
 Un rapport lié est issu d'un rapport existant et il reste fidèle à la définition de rapport d'origine. Il hérite toujours des propriétés de la source de données et de la mise en page du rapport d'origine. Toutes les autres propriétés et toutes les autres valeurs peuvent différer, notamment la sécurité, les paramètres, l'emplacement, les abonnements et les planifications.  
  
 Vous créez un rapport lié lorsque vous voulez créer des versions supplémentaires d'un rapport existant. Ainsi, vous pouvez trouver pratique d'utiliser un rapport de ventes régional unique pour créer des rapports spécifiques aux régions pour tous vos secteurs de ventes.  
  
 Bien que les rapports liés soient généralement basés sur des rapports paramétrés, il n'est pas obligatoire de recourir à des rapports paramétrés. Vous pouvez créer des rapports liés dès lors que vous souhaitez déployer un rapport existant avec des paramètres différents.  
  
### <a name="to-create-a-linked-report"></a>Pour créer un rapport lié  
  
1.  Dans le Gestionnaire de rapports, accédez au dossier qui contient le rapport à lier, puis ouvrez le menu d’options et cliquez sur **Créer un rapport lié**.  
  
2.  Indiquez un nom pour le nouveau rapport lié. Tapez éventuellement une description.  
  
3.  Pour sélectionner un autre dossier pour le rapport, cliquez sur **Modifier l’emplacement**. Cliquez ensuite sur le dossier à utiliser ou tapez son nom dans la zone **Emplacement** . [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Si vous ne sélectionnez aucun dossier, le rapport lié est créé dans le dossier actif (où est stocké le rapport sur lequel il est basé).  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Le rapport lié s’ouvre.  
  
     L'icône d'un rapport lié est différente des autres éléments gérés par un serveur de rapports. L'icône ci-après indique un rapport lié :  
  
     ![Icône Rapport lié](../media/hlp-16linked.gif "Icône Rapport lié")  
  
## <a name="see-also"></a>Voir aussi  
 [Ouvrir et fermer un rapport &#40;Gestionnaire de rapports&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [Page Nouveau rapport lié &#40;Gestionnaire de rapports&#41;](../new-linked-report-page-report-manager.md)   
 [Page Choisir l’emplacement de l’élément &#40;Gestionnaire de rapports&#41;](../choose-item-location-page-report-manager.md)   
 [Page Propriétés générales, Rapports &#40;Gestionnaire de rapports&#41;](../general-properties-page-reports-report-manager.md)   
 [Concepts de Reporting Services &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)  
  
  
