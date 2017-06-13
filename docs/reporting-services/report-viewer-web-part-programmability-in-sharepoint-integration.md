---
title: "Rapport de programmabilité du composant WebPart Visionneuse de l’intégration SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6e176aafa062c1184ff120cc1e886b9f5e244712
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Programmabilité du composant WebPart Visionneuse de rapports dans l'intégration SharePoint
  Le composant WebPart Visionneuse de rapports est un contrôle serveur, qui contient un ensemble de public application programming interface (API) qui permet aux développeurs de créer des applications SharePoint personnalisées. Vous pouvez créer des composants WebPart personnalisés et de les fournir le chemin du rapport et les paramètres pour le WebPart Visionneuse de rapports à l’aide des connexions WebPart. Vous pouvez également incorporer le composant WebPart dans une page WebPart SharePoint personnalisée et le personnaliser en utilisant l'API publique.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Connexion au composant WebPart Visionneuse de rapports avec des composants WebPart personnalisés  
 Le composant WebPart Visionneuse de rapports est un consommateur de connexion aux composants WebPart SharePoint qui implémentent <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> ou T:Microsoft.SharePoint.WebPartPages.IFilterValues. Un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> WebPart, telles que la **Documents** peut fournir un chemin d’accès du rapport à une partie Web de visionneuse de rapport lorsqu’elle est placée sur la même page de composant WebPart que le composant WebPart Visionneuse de rapports. De même, un serveur Web T:Microsoft.SharePoint.WebPartPages.IFilterValues partie, tels que les **filtre de texte** ou **filtre choix**, peut fournir un paramètre de rapport à une partie Web de visionneuse de rapport lorsqu’elle est placée sur la même page de composant WebPart que le composant WebPart Visionneuse de rapports.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Implémentation d'un fournisseur de chemins d'accès au rapport avec IWebPartRow  
 Pour fournir un chemin d'accès au rapport au composant WebPart Visionneuse de rapports via des connexions WebPart, procédez comme suit :  
  
1.  Créez un composant WebPart qui implémente l'interface <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>.  
  
2.  Ajoutez le composant WebPart à la même page WebPart que celle du composant WebPart Visionneuse de rapports.  
  
3.  Connectez votre composant WebPart au composant WebPart Visionneuse de rapports dans l'interface utilisateur du concepteur WebPart.  
  
    > [!NOTE]  
    >  Vous ne pouvez connecter une <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> WebPart pour le composant WebPart Visionneuse de rapports à la fois, vous ne pouvez pas connecter simultanément un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> WebPart et un composant WebPart T:Microsoft.SharePoint.WebPartPages.IFilterValues pour le composant WebPart Visionneuse de rapports en même temps.  
  
 Pour votre <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> WebPart fonctionnent correctement avec le T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart, vous devez procédez comme suit le <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A> méthode :  
  
-   Appelez la méthode de rappel avec un objet <xref:System.Data.DataRowView> en tant que paramètre d'entrée.  
  
-   Assurez-vous que l'objet <xref:System.Data.DataRowView> contient une colonne appelée « DocUrl » qui inclut le chemin d'accès au rapport.  
  
    > [!NOTE]  
    >  Le composant WebPart Visionneuse de rapports dans le complément pour [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 prend également en charge la réception des données de chemin d'accès au rapport par le biais de la colonne « FileRef ».  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Implémentation d'un fournisseur de paramètres de rapport avec IFilterValues  
 Un composant WebPart qui implémente T:Microsoft.SharePoint.WebPartPages.IFilterValues peut fournir une valeur de paramètre pour le composant WebPart Visionneuse de rapports. La valeur de paramètre envoyée au composant WebPart Visionneuse de rapports est soumise aux mêmes restrictions appliquées au paramètre de rapport comme indiqué dans la définition de rapport (type de données, valeurs valides, etc.).  
  
 Pour fournir un paramètre de rapport au composant WebPart Visionneuse de rapports, procédez comme suit :  
  
1.  Créer un composant WebPart qui implémente l’interface T:Microsoft.SharePoint.WebPartPages.IFilterValues.  
  
2.  Ajouter le composant WebPart à la même page que le T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart.  
  
3.  Se connecter à votre composant WebPart T:Microsoft.SharePoint.WebPartPages.IFilterValues pour le composant WebPart Visionneuse de rapports dans l’interface utilisateur du Concepteur Web basée sur des composants WebPart.  
  
    > [!NOTE]  
    >  Vous pouvez connecter plusieurs composants WebPart T:Microsoft.SharePoint.WebPartPages.IFilterValues pour le composant WebPart Visionneuse de rapports à la fois. Toutefois, vous ne pouvez pas connecter simultanément un <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> WebPart et un composant WebPart T:Microsoft.SharePoint.WebPartPages.IFilterValues pour le composant WebPart Visionneuse de rapports en même temps.  
  
  
