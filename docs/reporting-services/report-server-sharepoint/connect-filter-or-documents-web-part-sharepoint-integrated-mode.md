---
title: Connecter un composant WebPart Filtre ou de Documents avec un composant WebPart Visionneuse de rapports Reporting Services | Documents Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 87d4b4a3f0c01804329f3a7b0688632c20ed6c9b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="connect-filter-or-documents-web-part-with-a-reporting-services-report-viewer-web-part"></a>Connecter un composant WebPart Filtre ou de Documents avec un composant WebPart Visionneuse de rapports Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Si vous utilisez un produit SharePoint, vous pouvez créer un tableau de bord ou le composant WebPart Page qui inclut un composant WebPart Filtre ou composant WebPart Documents et un composant WebPart Visionneuse de rapports. Les versions prises en charge sont [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] et [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. [!INCLUDE[winSPServ3](../../includes/winspserv3-md.md)] et [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 sont également pris en charge. En connectant un composant WebPart Filtre, les utilisateurs qui sélectionnent des valeurs de filtre dans un composant WebPart Filtre peuvent envoyer la valeur à un rapport paramétrable sur la même page. En connectant un composant WebPart Documents, les utilisateurs qui cliquent sur des rapports dans la bibliothèque de Documents peuvent afficher le rapport dans un composant WebPart Visionneuse de rapports adjacent.

> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.

 Le composant WebPart filtre est utilisé pour envoyer les valeurs à un ou plusieurs paramètres d’un rapport. Pour utiliser un composant WebPart Filtre, le rapport doit avoir des paramètres définis pour celle-ci sont compatibles avec les valeurs, le type de données et le format envoyés par le composant WebPart.  
  
 Le composant WebPart de Documents est associé à la bibliothèque de Documents du site d’accueil. Pour afficher, ajouter ou supprimer des éléments de la bibliothèque de documents, cliquez sur **Afficher tout le contenu du site**. Dans Bibliothèques, cliquez sur **Documents**. Vous pouvez utiliser les menus **Nouveau**, **Télécharger**et **Actions** pour gérer les éléments de la bibliothèque de documents.  
  
## <a name="connect-a-filter-web-part"></a>Connecter un composant WebPart Filtre
  
1.  Ouvrez ou créez la page de composants WebPart ou d’un tableau de bord.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **ajouter un composant WebPart**.  
  
4.  Dans **tous les composants WebPart**, dans le **divers** catégorie, sélectionnez **visionneuse de rapports SQL Server Reporting Services**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Dans une autre zone dans la même page de composants WebPart ou d’un tableau de bord, cliquez sur **ajouter un composant WebPart**.  
  
7.  Dans **tous les composants WebPart**, dans le **filtres** , sélectionnez un composant WebPart.  
  
8.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
9. Dans la zone qui contient le composant WebPart, cliquez sur le composant WebPart **modifier** menu, pointez sur **connexions**, pointez sur **envoyer des valeurs de filtre à**, puis sélectionnez **rapport Visionneuse** - *nom du rapport*.  
  
10. Vérifiez vos modifications et enregistrez la page.  
  
## <a name="connect-a-documents-web-part"></a>Connecter un composant WebPart Documents  
  
1.  Ouvrez ou créez la page de composants WebPart ou d’un tableau de bord.  
  
2.  Dans le menu **Actions de site** , cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **ajouter un composant WebPart**.  
  
4.  Dans **tous les composants WebPart**, dans le **listes et bibliothèques** section, sélectionnez **Documents.**  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
6.  Cliquez au bas du volet d’outils sur **Appliquer** , puis sur **OK** pour fermer le volet.  
  
7.  Dans une autre zone dans la même page de composants WebPart ou d’un tableau de bord, cliquez sur **ajouter un composant WebPart**.  
  
8.  Dans **tous les composants WebPart**, dans le **divers** catégorie, sélectionnez **visionneuse de rapports SQL Server Reporting Services.**  
  
9. Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone.  
  
10. Dans la zone qui contient le composant WebPart, cliquez sur le composant WebPart **modifier** menu, pointez sur **connexions**, pointez sur **obtenir les définitions de rapport à partir de**, puis sélectionnez  **Documents**.  
  
11. Vérifiez vos modifications et enregistrez la page.  
  
## <a name="see-also"></a>Voir aussi

 [Ajouter le composant WebPart Visionneuse de rapports à une page web](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)   
 [Composant WebPart Visionneuse de rapports sur un SharePoint Site](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personnaliser le composant WebPart de la Visionneuse de rapports](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
