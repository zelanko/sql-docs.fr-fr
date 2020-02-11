---
title: Connecter un composant WebPart de filtre ou de documents (Reporting Services en mode intégré SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
ms.openlocfilehash: 062733f1ee68cd90ccc1b9a15d0cadc06b7e6f89
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109716"
---
# <a name="connect-filter-or-documents-web-part-reporting-services-in-sharepoint-integrated-mode"></a>Connecter un composant WebPart de filtre ou de documents (Reporting Services en mode intégré SharePoint)
  Si vous utilisez un produit SharePoint, vous pouvez créer un tableau de bord ou une page WebPart qui inclut un composant WebPart de filtre ou un composant WebPart de documents et un composant WebPart Visionneuse de rapports. Les versions prises en charge sont [!INCLUDE[SPF2010](../includes/spf2010-md.md)] et [!INCLUDE[SPS2010](../includes/sps2010-md.md)]. 
  [!INCLUDE[winSPServ3](../includes/winspserv3-md.md)] et [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2007 sont également pris en charge. En connectant un composant WebPart de filtre, les utilisateurs qui sélectionnent des valeurs de filtre dans un composant WebPart de filtre peuvent envoyer la valeur à un rapport paramétrable sur la même page. En connectant un composant WebPart de documents, les utilisateurs qui cliquent sur des rapports dans la bibliothèque de documents peuvent afficher les rapports dans un composant WebPart de visionneuse de rapports adjacent.  
  
 Le composant WebPart de filtre sert à envoyer des valeurs à un ou plusieurs paramètres d'un rapport. Pour utiliser un composant WebPart de filtre, le rapport doit disposer de paramètres concernant ce composant qui sont compatibles avec les valeurs, le type de données et le format envoyés par le composant WebPart.  
  
 Le composant WebPart de documents est associé à la bibliothèque de documents du site d'accueil. Pour afficher, ajouter ou supprimer des éléments de la bibliothèque de documents, cliquez sur **Afficher tout le contenu du site**. Dans Bibliothèques, cliquez sur **Documents**. Vous pouvez utiliser les menus **Nouveau**, **Télécharger**et **Actions** pour gérer les éléments de la bibliothèque de documents.  
  
### <a name="to-connect-a-filter-web-part"></a>Pour connecter un composant WebPart de filtre  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans **tous les composants WebPart**, dans la catégorie **divers** , sélectionnez **SQL Server Reporting Services visionneuse de rapports**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Dans une autre zone de la même page ou du même tableau de bord de composant WebPart, cliquez sur **Ajouter un composant WebPart**.  
  
7.  Dans **tous les composants WebPart**, dans la section **filtres** , sélectionnez un composant WebPart.  
  
8.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
9. Dans la zone qui contient le composant WebPart, cliquez sur le menu **modifier** du composant WebPart, pointez sur **connexions**, sur **Envoyer les valeurs de filtre à**, puis sélectionnez **visionneuse** - de rapports*nom du rapport*.  
  
10. Vérifiez vos modifications et enregistrez la page.  
  
### <a name="to-connect-a-documents-web-part"></a>Pour connecter un composant WebPart de documents  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans **tous les composants WebPart**, dans la section **listes et bibliothèque** , sélectionnez **documents.**  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Cliquez au bas du volet d’outils sur **Appliquer** , puis sur **OK** pour fermer le volet.  
  
7.  Dans une autre zone de la même page ou du même tableau de bord de composant WebPart, cliquez sur **Ajouter un composant WebPart**.  
  
8.  Dans **tous les composants WebPart**, dans la catégorie **divers** , sélectionnez **SQL Server Reporting Services visionneuse de rapports.**  
  
9. Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
10. Dans la zone qui contient le composant WebPart, cliquez sur le menu **modifier** du composant WebPart, pointez sur **connexions**, pointez sur **afficher les définitions de rapport à partir de**, puis sélectionnez **documents**.  
  
11. Vérifiez vos modifications et enregistrez la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajoutez le composant WebPart Visionneuse de rapports à une page Web &#40;Reporting Services en mode intégré SharePoint&#41;](report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)   
 [Composant WebPart Visionneuse de rapports sur un site SharePoint](../../2014/reporting-services/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personnaliser le composant WebPart Visionneuse de rapports](../../2014/reporting-services/customize-the-report-viewer-web-part.md)  
  
  
