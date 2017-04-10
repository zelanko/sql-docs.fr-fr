---
title: "Ajouter le composant WebPart Visionneuse de rapports &#224; une page Web (Reporting Services en mode int&#233;gr&#233; SharePoint) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "intégration SharePoint [Reporting Services], affichage des rapports"
  - "composants WebPart [Reporting Services]"
  - "intégration SharePoint [Reporting Services], WebParts"
  - "WebPart Visionneuse de rapports [Reporting Services], composant"
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Ajouter le composant WebPart Visionneuse de rapports &#224; une page Web (Reporting Services en mode int&#233;gr&#233; SharePoint)
  Vous pouvez utiliser le composant WebPart Visionneuse de rapports pour afficher les rapports qui s'exécutent sur un serveur de rapports configuré en mode intégré SharePoint. Vous pouvez utiliser le composant WebPart pour afficher les fichiers de définition de rapport (.rdl) que vous avez créés dans le Générateur de rapports ou le Concepteur de rapports, et que vous avez téléchargés vers une bibliothèque.  
  
 Vous pouvez ajouter le composant WebPart de visionneuse de rapports à une page Web si vous souhaitez incorporer un rapport dans cette page.  
  
> [!NOTE]  
>  Même si leurs noms sont identiques, le composant WebPart Visionneuse de rapports installé par le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est différent du composant WebPart Visionneuse de rapports inclus dans le fichier RSWebParts.cab. Les instructions de cette rubrique sont spécifiques au composant WebPart Visionneuse de rapports installé à l'aide du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Pour ajouter un composant WebPart à une page Web, vous devez disposer de l'autorisation Ajouter et personnaliser les pages au niveau du site. Si vous utilisez des paramètres de sécurité par défaut, cette autorisation est accordée aux membres du groupe **Propriétaires** qui ont le niveau d’autorisation Contrôle total.  
  
### Pour incorporer un rapport dans une page Web  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans **Actions de site**, cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans la liste de catégories WebPart, sélectionnez la catégorie **Divers**, puis **Visionneuse de rapports SQL Server Reporting Services**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone. Vous pouvez le faire glisser vers un autre emplacement de la zone.  
  
6.  Dans la visionneuse, cliquez sur **Cliquez ici pour ouvrir le volet d’outils**.  
  
7.  Sélectionnez un rapport dans une bibliothèque de la collection de sites actuelle en cliquant sur le bouton Parcourir (**...**). Vous pouvez également taper l'URL du rapport. Pour déterminer l’URL d’un rapport, cliquez avec le bouton droit sur le rapport, puis sélectionnez **Propriétés**. Ne cliquez pas sur la flèche orientée vers le bas en regard du rapport ; l'URL du rapport n'est pas indiquée dans la page Afficher les propriétés de l'élément. Si vous copiez et collez l’URL à partir de la boîte de dialogue **Propriétés**, remplacez l’encodage d’URL « %20 » par un espace (par exemple « Company%20Sales » doit s’écrire « Company Sales »).  
  
    > [!NOTE]  
    >  Chaque composant WebPart Visionneuse de rapports contient un seul rapport. L'URL doit correspondre au chemin d'accès complet d'un rapport situé sur le site SharePoint actuel ou sur un site inclus dans la même batterie de serveurs ou application Web. L'URL doit correspondre à une bibliothèque de documents ou à un dossier situé dans une bibliothèque de documents contenant le rapport. L'URL de rapport doit inclure l'extension de fichier .rdl. Si le rapport dépend d'un modèle ou de fichiers de source de données partagée, vous n'avez pas besoin de spécifier ces fichiers dans l'URL. Le rapport contient les références aux fichiers nécessaires.  
  
8.  Tant que le volet d'outils est ouvert, vous pouvez définir certaines propriétés afin de modifier l'apparence et la mise en page par défaut.  
  
9. Cliquez au bas du volet d’outils sur **Appliquer**, puis sur **OK** pour fermer le volet.  
  
## Voir aussi  
 [Composant WebPart Visionneuse de rapports sur un site SharePoint](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personnaliser le composant WebPart Visionneuse de rapports](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)   
 [Accord d'autorisations sur des éléments de serveur de rapports sur un site SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  