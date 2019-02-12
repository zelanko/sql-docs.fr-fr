---
title: Rechercher des parties de rapports et définir un dossier par défaut (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ae8fddf7e008c1c97c30c18deb2d8aec60b77415
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56009581"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a>Rechercher des parties de rapports et définir un dossier par défaut (Générateur de rapports et SSRS)
  Pour créer un rapport, la façon la plus simple consiste à ajouter des parties de rapports existantes, telles que des tables et des graphiques, à votre rapport à partir de la bibliothèque de parties de rapports. Lorsque vous ajoutez une partie de rapport à votre rapport, vous ajoutez également tout ce qu'elle doit comporter pour fonctionner. Par exemple, toute partie de rapport qui affiche des données dépend d'un dataset, autrement dit, une requête et une connexion à une source de données. Après avoir ajouté la partie de rapport à votre rapport, vous pouvez la modifier comme vous le souhaitez.  
  
 Vous pouvez définir un dossier par défaut pour publier des parties de rapports sur le serveur de rapports ou le site SharePoint intégré avec un serveur de rapports.  
  
 Pour plus d’informations, consultez [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
### <a name="to-browse-for-report-parts"></a>Pour rechercher des parties de rapports  
  
1.  Dans le menu **Insérer** , cliquez sur **Parties de rapports**.  
  
     Si vous n’êtes pas déjà connecté, cliquez sur **Connectez-vous à un serveur de rapports**, puis entrez le nom.  
  
    > [!NOTE]  
    >  Vous devez être connecté à un serveur de rapports pour rechercher des parties de rapports.  
  
2.  Vous pouvez limiter votre recherche en spécifiant des détails sur la partie de rapport. Tapez tout ou partie du nom et de la description dans la zone de **recherche** ou cliquez sur **Ajouter des critères** et ajoutez des valeurs pour un ou plusieurs de ces champs :  
  
    -   Créé par  
  
    -   Date de création  
  
    -   Date de dernière modification  
  
    -   Auteur de la dernière modification  
  
    -   Dossier du serveur  
  
    -   Type  
  
     Par exemple, pour rechercher une image, cliquez sur **Ajouter des critères**, puis sur **Type**. Dans la zone de liste déroulante, cochez la case **Image** , appuyez sur Entrée, puis cliquez sur la loupe Rechercher.  
  
    > [!NOTE]  
    >  Pour les valeurs **Créé par** et **Auteur de la dernière modification** , recherchez le nom d’utilisateur de la personne tel qu’il est représenté sur le serveur de rapports.  
  
### <a name="to-set-a-default-folder-for-report-parts"></a>Pour définir un dossier par défaut pour les parties de rapport  
  
1.  Cliquez sur **Générateur de rapports**, puis sur **Options**.  
  
2.  Dans la boîte de dialogue **Options** , sous l’onglet **Paramètres** , tapez un nom de dossier dans la zone de texte **Publier les parties de rapports dans ce dossier par défaut** .  
  
 Le Générateur de rapports créera ce dossier si vous êtes autorisé à créer des dossiers sur le serveur de rapports et que le dossier n'existe pas encore.  
  
 Vous n'avez pas à redémarrer le Générateur de rapports pour que ce paramètre entre en vigueur.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherchez les mises à jour ou désactiver les mises à jour &#40;Générateur de rapports et SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md)   
 [Parties de rapports &#40;Générateur de rapports et SSRS&#41;](../report-parts-report-builder-and-ssrs.md)   
 [Parties de rapports et datasets dans le Générateur de rapports](../report-data/report-parts-and-datasets-in-report-builder.md)   
 [Résoudre les problèmes de parties de rapports &#40;Générateur de rapports et SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [Publier et republier des parties de rapports &#40;Générateur de rapports et SSRS&#41;](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
