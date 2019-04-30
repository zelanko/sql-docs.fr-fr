---
title: Connecter un filtre ou le composant WebPart Documents (Reporting Services en Mode intégré SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Filter Web Part [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
- Documents Web Part [Reporting Services]
ms.assetid: 6a303135-c0ef-44cd-a423-1cea8df3dcf3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d1d249662ef306e2b1608582b5b61271098ccf42
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63266440"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a>Connecter un composant WebPart de filtre ou de documents (Reporting Services en mode intégré SharePoint)
  Si vous utilisez un produit SharePoint, vous pouvez créer un tableau de bord ou une page WebPart qui inclut un composant WebPart de filtre ou un composant WebPart de documents et un composant WebPart Visionneuse de rapports. Les versions prises en charge sont [!INCLUDE[SPF2010](../includes/spf2010-md.md)] et [!INCLUDE[SPS2010](../includes/sps2010-md.md)]. [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] et [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 sont également pris en charge. En connectant un composant WebPart de filtre, les utilisateurs qui sélectionnent des valeurs de filtre dans un composant WebPart de filtre peuvent envoyer la valeur à un rapport paramétrable sur la même page. En connectant un composant WebPart de documents, les utilisateurs qui cliquent sur des rapports dans la bibliothèque de documents peuvent afficher les rapports dans un composant WebPart de visionneuse de rapports adjacent.  
  
 Le composant WebPart de filtre sert à envoyer des valeurs à un ou plusieurs paramètres d'un rapport. Pour utiliser un composant WebPart de filtre, le rapport doit disposer de paramètres concernant ce composant qui sont compatibles avec les valeurs, le type de données et le format envoyés par le composant WebPart.  
  
 Le composant WebPart de documents est associé à la bibliothèque de documents du site d'accueil. Pour afficher, ajouter ou supprimer des éléments de la bibliothèque de documents, cliquez sur **Afficher tout le contenu du site**. Dans Bibliothèques, cliquez sur **Documents**. Vous pouvez utiliser les menus **Nouveau**, **Télécharger**et **Actions** pour gérer les éléments de la bibliothèque de documents.  
  
### <a name="to-connect-a-filter-web-part"></a>Pour connecter un composant WebPart de filtre  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans **Tous les composants WebPart**, dans la catégorie **Divers** , sélectionnez **Visionneuse de rapports SQL Server Reporting Services**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Dans une autre zone de la même page ou du même tableau de bord de composants WebPart, cliquez sur **Ajouter un composant WebPart**.  
  
7.  Dans **Tous les composants WebPart**, dans la section **Filtres** , sélectionnez un composant WebPart.  
  
8.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
9. Dans la zone qui contient le composant WebPart, cliquez sur le menu **modifier** du composant WebPart, pointez sur **Connexions**, sur **Envoyer les valeurs de filtre à**, puis sélectionnez **Visionneuse de rapports** - *nom de rapport*.  
  
10. Vérifiez vos modifications et enregistrez la page.  
  
### <a name="to-connect-a-documents-web-part"></a>Pour connecter un composant WebPart de documents  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans **Tous les composants WebPart**, dans la section **Listes et bibliothèque** , sélectionnez **Documents**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Cliquez au bas du volet d’outils sur **Appliquer** , puis sur **OK** pour fermer le volet.  
  
7.  Dans une autre zone de la même page ou du même tableau de bord de composants WebPart, cliquez sur **Ajouter un composant WebPart**.  
  
8.  Dans **Tous les composants WebPart**, dans la catégorie **Divers** , sélectionnez **Visionneuse de rapports SQL Server Reporting Services.**  
  
9. Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
10. Dans la zone qui contient le composant WebPart, cliquez sur le menu **modifier** du composant WebPart, pointez sur **Connexions**, sur **Source des définitions de rapport**, puis sélectionnez **Documents**.  
  
11. Vérifiez vos modifications et enregistrez la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter le composant WebPart Visionneuse de rapports à une page web &#40;Reporting Services en mode intégré SharePoint&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)   
 [Composant WebPart Visionneuse de rapports sur un site SharePoint](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personnaliser le composant WebPart Visionneuse de rapports](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
