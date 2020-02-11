---
title: Programmabilité du composant WebPart Visionneuse de rapports dans l’intégration SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: 714017b7-1bd6-4950-a3c6-d0df8450a877
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4a0bc7e2d99190e142647ab8732e2d2d48b3ea2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63255125"
---
# <a name="report-viewer-web-part-programmability-in-sharepoint-integration"></a>Programmabilité du composant WebPart Visionneuse de rapports dans l'intégration SharePoint
  Le composant WebPart de la visionneuse de rapports est un contrôle serveur `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart` qui contient un ensemble d'interfaces de programmation d'applications publiques (API) permettant aux développeurs de créer des applications SharePoint personnalisées. Vous pouvez créer des composants WebPart personnalisés qui fournissent les paramètres et le chemin du rapport au composant WebPart Visionneuse de rapports à l’aide de connexions de composants WebPart. Vous pouvez également incorporer le composant WebPart dans une page WebPart SharePoint personnalisée et le personnaliser en utilisant l'API publique.  
  
## <a name="connecting-to-report-viewer-web-part-with-custom-web-parts"></a>Connexion au composant WebPart Visionneuse de rapports avec des composants WebPart personnalisés  
 Le composant WebPart Visionneuse de rapports est un consommateur de connexions aux composants WebPart SharePoint qui implémentent <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> ou `T:Microsoft.SharePoint.WebPartPages.IFilterValues`. Un composant WebPart <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>, tel que le composant WebPart **Documents**, peut fournir le chemin d’un rapport à un composant WebPart Visionneuse de rapports s’il est placé dans la même page de composant WebPart que le composant WebPart Visionneuse de rapports. De même, `T:Microsoft.SharePoint.WebPartPages.IFilterValues` un composant WebPart, tel que le **filtre de texte** ou le **filtre de choix**, peut fournir un paramètre de rapport à un composant WebPart Visionneuse de rapports lorsqu’il est placé sur la même page de composant WebPart que le composant WebPart Visionneuse de rapports.  
  
### <a name="implementing-a-report-path-provider-with-iwebpartrow"></a>Implémentation d'un fournisseur de chemins d'accès au rapport avec IWebPartRow  
 Pour fournir un chemin d'accès au rapport au composant WebPart Visionneuse de rapports via des connexions WebPart, procédez comme suit :  
  
1.  Créez un composant WebPart qui implémente l'interface <xref:System.Web.UI.WebControls.WebParts.IWebPartRow>.  
  
2.  Ajoutez le composant WebPart à la même page WebPart que celle du composant WebPart Visionneuse de rapports.  
  
3.  Connectez votre composant WebPart au composant WebPart Visionneuse de rapports dans l'interface utilisateur du concepteur WebPart.  
  
    > [!NOTE]  
    >  Vous ne pouvez connecter qu'un seul composant WebPart <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> à la fois au composant WebPart Visionneuse de rapports et vous ne pouvez pas connecter simultanément un composant WebPart <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> et un composant WebPart `T:Microsoft.SharePoint.WebPartPages.IFilterValues` au composant WebPart Visionneuse de rapports.  
  
 Pour que le composant WebPart <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> fonctionne correctement avec le composant `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`, procédez comme suit dans la méthode <xref:System.Web.UI.WebControls.WebParts.IWebPartRow.GetRowData%2A>  :  
  
-   Appelez la méthode de rappel avec un objet <xref:System.Data.DataRowView> en tant que paramètre d'entrée.  
  
-   Assurez-vous que l'objet <xref:System.Data.DataRowView> contient une colonne appelée « DocUrl » qui inclut le chemin d'accès au rapport.  
  
    > [!NOTE]  
    >  Le composant WebPart Visionneuse de rapports dans le complément pour [!INCLUDE[offSPServ](../includes/offspserv-md.md)] 2010 prend également en charge la réception des données de chemin d'accès au rapport par le biais de la colonne « FileRef ».  
  
### <a name="implementing-a-report-parameter-provider-with-ifiltervalues"></a>Implémentation d'un fournisseur de paramètres de rapport avec IFilterValues  
 Un composant WebPart qui implémente `T:Microsoft.SharePoint.WebPartPages.IFilterValues` peut fournir une valeur de paramètre au composant WebPart Visionneuse de rapports. La valeur de paramètre envoyée au composant WebPart Visionneuse de rapports est soumise aux mêmes restrictions appliquées au paramètre de rapport comme indiqué dans la définition de rapport (type de données, valeurs valides, etc.).  
  
 Pour fournir un paramètre de rapport au composant WebPart Visionneuse de rapports, procédez comme suit :  
  
1.  Créez un composant WebPart qui implémente l'interface `T:Microsoft.SharePoint.WebPartPages.IFilterValues`.  
  
2.  Ajoutez le composant WebPart à la même page que le `T:Microsoft.ReportingServices.SharePoint.UI.WebParts.ReportViewerWebPart`.  
  
3.  Connectez votre composant WebPart `T:Microsoft.SharePoint.WebPartPages.IFilterValues` au composant WebPart Visionneuse de rapports dans l'interface utilisateur du concepteur WebPart.  
  
    > [!NOTE]  
    >  Vous pouvez connecter plusieurs composants WebPart `T:Microsoft.SharePoint.WebPartPages.IFilterValues` à la fois au composant WebPart Visionneuse de rapports. Toutefois, vous ne pouvez pas connecter simultanément un composant WebPart <xref:System.Web.UI.WebControls.WebParts.IWebPartRow> et un composant WebPart `T:Microsoft.SharePoint.WebPartPages.IFilterValues` au composant WebPart Visionneuse de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface de IFilterValues](https://msdn.microsoft.com/library/office/microsoft.sharepoint.webpartpages.ifiltervalues\(v=office.15\).aspx)  
  
  
