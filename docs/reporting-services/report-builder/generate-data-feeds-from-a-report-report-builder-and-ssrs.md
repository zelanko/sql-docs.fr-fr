---
title: "Générer des flux de données à partir d’un rapport (Générateur de rapports et SSRS) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
caps.latest.revision: 11
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b49b80de8516e14972b05d7ae91f4f72e765803a
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---

# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Générer des flux de données à partir d'un rapport (Générateur de rapports et SSRS)

Vous pouvez générer des flux de données conformes à Atom à partir de rapports paginés et ensuite utiliser les flux de données dans les applications, telles que Power Pivot, ou Power BI, ce qui peut utiliser des données de flux.  
  
 L'extension de rendu Atom [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] génère un document de service Atom qui répertorie les flux de données disponibles d'un rapport. Le document répertorie au moins un flux de données pour chaque région de données du rapport. Selon le type de région de données et les données affichées par cette région, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] peut générer plusieurs flux de données à partir d'une région de données.  
  
 Le document de service Atom contient un identificateur unique pour chaque flux de données. Par ailleurs, vous utilisez cet identificateur dans une URL afin d'afficher le contenu du flux de données.  
  
 Pour plus d’informations, consultez [Génération de flux de données à partir de rapports &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Pour générer un document de service Atom  
  
1.  du portail web de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , naviguez jusqu’au rapport que vous souhaitez utiliser pour générer des flux de données.  
  
2.  Cliquez sur le rapport.  
  
     Le rapport s'exécute.  
  
3.  Dans la barre d’outils, cliquez sur l’icône **Exporter vers un flux de données** .  
  
     Un message s'affiche pour vous demander si vous souhaitez enregistrer ou ouvrir le document Atom qui contient le flux de données.  
  
4.  Cliquez sur **Enregistrer** pour enregistrer le document dans le système de fichiers, ou cliquez sur **Ouvrir** pour afficher le contenu du document avant de l'enregistrer. **Par défaut, le document s'ouvre dans un navigateur.**  
  
5.  Accédez à l'emplacement d'enregistrement du document.  
  
6.  Modifiez éventuellement le nom du document.  
  
    > [!NOTE]  
    >  Par défaut, le nom du document correspond au nom du rapport.  
  
7.  Assurez-vous que le type du document est **Fichier ATOMSVC**, puis cliquez sur **Enregistrer**.  
  
8.  Si vous le souhaitez, ouvrez le fichier .atomsvc dans un navigateur, un éditeur de texte ou un éditeur XML.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Pour afficher un flux de données conforme à Atom  
  
1.  Si le document de service Atom n'est pas déjà ouvert, recherchez ce dernier et ouvrez-le dans un navigateur tel qu'Internet Explorer.  
  
2.  Copiez l'URL du flux de données que vous souhaitez afficher à partir du document de service Atom dans le navigateur.  
  
     Le format de l'URL est le suivant :  
  
     `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
3.  Appuyez sur Entrée.  
  
     Un message s'affiche pour vous demander si vous souhaitez enregistrer ou ouvrir le document Atom qui contient le flux de données.  
  
4.  Cliquez sur **Enregistrer** pour enregistrer le document dans le système de fichiers, ou cliquez sur **Ouvrir** pour afficher le flux de données avant de l'enregistrer.  
  
5.  Accédez à l'emplacement d'enregistrement du document.  
  
6.  Modifiez éventuellement le nom du document.  
  
    > [!NOTE]  
    >  Par défaut, le nom du document correspond au nom du rapport. Si le document de service Atom contient plusieurs flux, ils utilisent tous le même nom par défaut, à savoir le nom du rapport. Pour les différencier, renommez-les à l'aide de noms explicites.  
  
7.  Assurez-vous que le type du document est **Fichier ATOM**, puis cliquez sur **Enregistrer**.  
  
8.  Si vous le souhaitez, ouvrez le fichier .atom dans un navigateur, un éditeur de texte ou un éditeur XML.  

## <a name="next-steps"></a>Étapes suivantes

[Exporter des rapports](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
