---
title: Ajouter le composant WebPart Visionneuse de rapports à une page Web (Reporting Services en mode intégré SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 468acea55c334ffda169daff2b5da4c417348a3e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66104288"
---
# <a name="add-the-report-viewer-web-part-to-a-web-page-reporting-services-in-sharepoint-integrated-mode"></a>Ajouter le composant WebPart Visionneuse de rapports à une page Web (Reporting Services en mode intégré SharePoint)
  Vous pouvez utiliser le composant WebPart Visionneuse de rapports pour afficher les rapports qui s'exécutent sur un serveur de rapports configuré en mode intégré SharePoint. Vous pouvez utiliser le composant WebPart pour afficher les fichiers de définition de rapport (.rdl) que vous avez créés dans le Générateur de rapports ou le Concepteur de rapports, et que vous avez téléchargés vers une bibliothèque.  
  
 Vous pouvez ajouter le composant WebPart de visionneuse de rapports à une page Web si vous souhaitez incorporer un rapport dans cette page.  
  
> [!NOTE]  
>  Même si leurs noms sont identiques, le composant WebPart Visionneuse de rapports installé par le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est différent du composant WebPart Visionneuse de rapports inclus dans le fichier RSWebParts.cab. Les instructions de cette rubrique sont spécifiques au composant WebPart Visionneuse de rapports installé à l'aide du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Pour ajouter un composant WebPart à une page Web, vous devez disposer de l'autorisation Ajouter et personnaliser les pages au niveau du site. Si vous utilisez des paramètres de sécurité par défaut, cette autorisation est accordée aux membres du groupe **Propriétaires** qui ont le niveau d’autorisation Contrôle total.  
  
### <a name="to-embed-a-report-in-a-web-page"></a>Pour incorporer un rapport dans une page Web  
  
1.  Ouvrez ou créez la page ou le tableau de bord de composant WebPart.  
  
2.  Dans **Actions de site**, cliquez sur **Modifier la page**.  
  
3.  Cliquez sur **Ajouter un composant WebPart**.  
  
4.  Dans la liste de catégories WebPart, sélectionnez la catégorie **Divers** , puis **Visionneuse de rapports SQL Server Reporting Services**.  
  
5.  Cliquez sur **Ajouter**. Le composant WebPart est ajouté en haut de la zone. Vous pouvez le faire glisser vers un autre emplacement de la zone.  
  
6.  Dans la visionneuse, cliquez sur **Cliquez ici pour ouvrir le volet d’outils**.  
  
7.  Sélectionnez un rapport dans une bibliothèque de la collection de sites actuelle en cliquant sur le bouton Parcourir (**...**). Vous pouvez également taper l'URL du rapport. Pour déterminer l’URL d’un rapport, cliquez avec le bouton droit sur le rapport, puis sélectionnez **Propriétés**. Ne cliquez pas sur la flèche orientée vers le bas en regard du rapport ; l'URL du rapport n'est pas indiquée dans la page Afficher les propriétés de l'élément. Si vous copiez et collez l’URL à partir de la boîte de dialogue **Propriétés** , remplacez l’encodage d’URL « %20 » par un espace (par exemple « Company%20Sales » doit s’écrire « Company Sales »).  
  
    > [!NOTE]  
    >  Chaque composant WebPart Visionneuse de rapports contient un seul rapport. L'URL doit correspondre au chemin d'accès complet d'un rapport situé sur le site SharePoint actuel ou sur un site inclus dans la même batterie de serveurs ou application Web. L'URL doit correspondre à une bibliothèque de documents ou à un dossier situé dans une bibliothèque de documents contenant le rapport. L'URL de rapport doit inclure l'extension de fichier .rdl. Si le rapport dépend d'un modèle ou de fichiers de source de données partagée, vous n'avez pas besoin de spécifier ces fichiers dans l'URL. Le rapport contient les références aux fichiers nécessaires.  
  
8.  Tant que le volet d'outils est ouvert, vous pouvez définir certaines propriétés afin de modifier l'apparence et la mise en page par défaut.  
  
9. Cliquez au bas du volet d’outils sur **Appliquer** , puis sur **OK** pour fermer le volet.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant WebPart Visionneuse de rapports sur un site SharePoint](../report-viewer-web-part-on-a-sharepoint-site.md)   
 [Personnaliser le composant WebPart Visionneuse de rapports](../customize-the-report-viewer-web-part.md)   
 [Octroi d’autorisations sur des éléments de serveur de rapports sur un site SharePoint](../security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](../install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
