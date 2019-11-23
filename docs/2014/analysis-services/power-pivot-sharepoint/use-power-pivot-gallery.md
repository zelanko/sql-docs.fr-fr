---
title: Utiliser la Galerie PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 09/01/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9ff92d1-787a-4f34-990f-6676b61875d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3e4dd52a33fbfb84f65658db6c645a5317b39c44
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874487"
---
# <a name="use-powerpivot-gallery"></a>Utiliser la Galerie PowerPivot
  La Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] est une bibliothèque de documents SharePoint à usage spécial qui fournit des options d'aperçu et de gestion des documents pour les classeurs Excel publiés et des rapports Reporting Services contenant des données PowerPivot et d'autres types de documents.  
  
> [!NOTE]  
>  En fonction de la configuration de votre serveur, vous pouvez voir des messages d'avertissement ou d'erreur dans la zone d'aperçu de documents spécifiques. Les messages peuvent apparaître lorsqu'un classeur Excel est configuré pour actualiser automatiquement ses données à chacune de ses ouvertures. Des messages d'avertissement de l'actualisation des données apparaîtront à la place d'une image d'aperçu si Excel Services est configuré pour afficher des messages d'erreur pour avertir de l'actualisation des données. Les administrateurs de la batterie de serveurs ou du service peuvent modifier les paramètres de configuration pour permettre l'affichage d'un aperçu de la feuille de travail réelle. Pour plus d'informations, consultez [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
##  <a name="bkmk_top"></a> Dans cette rubrique  
  
-   [Icônes dans la Galerie PowerPivot](#icons)  
  
-   [Enregistrer un classeur Excel dans la Galerie PowerPivot](#add)  
  
-   [Créer des rapports ou des classeurs basés sur un classeur PowerPivot publié](#newdocs)  
  
-   [Ouvrir un classeur ou un rapport en mode page entière](#view)  
  
-   [Planifier l’actualisation des données pour les classeurs PowerPivot dans la Galerie PowerPivot](#newdr)  
  
-   [Supprimer un classeur ou un rapport dans la Galerie PowerPivot](#delete)  
  
-   [Actualiser une image miniature](#image)  
  
-   [Problèmes connus](#bkmk_known_issues)  
  
 [Prérequis](#prereq)  
  
##  <a name="prereq"></a> Conditions préalables requises  
  
> [!NOTE]  
>  La Galerie PowerPivot requiert Microsoft Silverlight.  Le navigateur Microsoft Edge ne prend pas en charge Silverlight.   
> Pour afficher le contenu de la bibliothèque dans Microsoft Edge, cliquez sur l’onglet **bibliothèque** dans Power Pivot Galerie, puis remplacez la vue de la bibliothèque de documents par **tous les documents**.    
> Pour modifier l’affichage par défaut, cliquez sur l’onglet **Bibliothèque** , puis sur Modifier l’affichage. Cliquez sur Définir cet affichage comme affichage par défaut, puis sur OK pour enregistrer l’affichage par défaut.  
>  Pour plus d’informations sur les éléments pris en charge par Microsoft Edge, consultez le blog Windows, [une pause du passé, partie 2 : dire adieu à ActiveX, VBScript...](http://blogs.windows.com/msedgedev/2015/05/06/a-break-from-the-past-part-2-saying-goodbye-to-activex-vbscript-attachevent/)  
  
 Pour obtenir la liste complète des conditions préalables, consultez [créer et personnaliser la Galerie PowerPivot](create-and-customize-power-pivot-gallery.md).  
  
##  <a name="icons"></a>Icônes dans la Galerie PowerPivot  
 Les icônes fournissent une indication visuelle sur la disponibilité et l'état du contenu.  
  
|Icône|Description|  
|----------|-----------------|  
|![GMNI_PowerPivotGalleryIcon_Hourglass](../media/gmni-powerpivotgalleryicon-hourglass.gif "GMNI_PowerPivotGalleryIcon_Hourglass")|L'icône de sablier apparaît lors de la génération d'une image miniature de chaque page dans le document. Actualisez la page pour afficher la mise à jour de l'image.|  
|![GMNI_PowerPivotGalleryIcon_Truncated](../media/gmni-powerpivotgalleryicon-truncated.gif "GMNI_PowerPivotGalleryIcon_Truncated")|L'icône de pages apparaît lorsqu'un classeur ou un rapport possède plus de pages que la Galerie PowerPivot ne peut en afficher. Pour consulter toutes les pages, vous devez utiliser une application cliente.|  
|![GMNI_PowerPivotGalleryIcon_Error](../media/gmni-powerpivotgalleryicon-error.gif "GMNI_PowerPivotGalleryIcon_Error")|L'icône d'erreur apparaît lorsqu'une image miniature n'a pas pu être restituée pour le document. Le document est publié sur la bibliothèque, mais ne peut pas être restitué dans les vues personnalisées de la bibliothèque Galerie PowerPivot. Vous devez être en mesure de consulter le document dans une application cliente, telle que le complément PowerPivot pour Excel.|  
|![GMNI_PowerPivotGalleryIcon_badtype](../media/gmni-powerpivotgalleryicon-badtype.gif "GMNI_PowerPivotGalleryIcon_badtype")|L'icône de contenu non disponible apparaît lorsque le document que vous avez téléchargé ne peut pas être restitué dans la Galerie PowerPivot. Les types de document pris en charge sont notamment les classeurs et rapports PowerPivot créés dans le Générateur de rapports de SQL Server 2008 R2 Reporting Services.<br /><br /> Cette icône apparaît également si vous recyclez un document de la Corbeille.<br /><br /> Si vous obtenez cette icône pour un document qui présentait auparavant une image d'aperçu valide, vous pouvez actualiser l'image en modifiant une propriété du document, puis en enregistrant vos modifications.|  
|![GMNI_PowerPivotGalleryIcon_Locked](../media/gmni-powerpivotgalleryicon-locked.gif "GMNI_PowerPivotGalleryIcon_Locked")|L'icône de contenu verrouillée apparaît lorsque les images miniatures ont été volontairement désactivées pour ce document. La Galerie PowerPivot ne génère pas d'images miniatures pour les classeurs Excel qui ne contiennent pas de données PowerPivot, ni pour les classeurs PowerPivot ou les rapports Reporting Services qui ne satisfont pas la configuration requise pour la génération d'instantanés. Pour plus d'informations, consultez la section « Configuration requise » de cette rubrique.|  
  
##  <a name="add"></a>Enregistrer un classeur Excel dans la Galerie PowerPivot  
 Vous pouvez publier des classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la bibliothèque à l'aide de toutes les techniques de partage offertes par Excel 2010. Par exemple, dans Excel 2010, vous pouvez utiliser l'option Enregistrer sous pour spécifier tout ou partie d'un chemin d'accès SharePoint à une bibliothèque.  
  
1.  Enregistrez le fichier.  
  
2.  1.  **Excel 2010 :** dans le menu Fichier, cliquez sur **Enregistrer​​ et envoyer**.  
  
    2.  Cliquez sur **Enregistrer dans SharePoint**.  
  
    3.  Cliquez sur **Options de publication** si vous souhaitez utiliser les options Excel Services pour sélectionner des feuilles ou paramètres individuels que vous souhaitez publier. Par exemple, l'onglet Paramètres dans Options Excel Services vous permet de choisir les découpages qui apparaissent dans le classeur publié.  
  
    1.  **Excel 2013 :**  dans le menu Fichier, cliquez sur **Enregistrer**.  
  
    2.  Cliquez sur **Options du Mode Navigateur** si vous souhaitez utiliser les options Excel Services pour sélectionner des feuilles ou paramètres individuels que vous souhaitez publier. Par exemple, l'onglet Paramètres dans Options Excel Services vous permet de choisir les découpages qui apparaissent dans le classeur publié.  
  
3.  Dans la boîte de dialogue Enregistrer sous, dans la zone Nom de fichier, entrez l'URL complète ou partielle de la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Si vous entrez une partie de l'adresse URL (le nom du serveur par exemple), vous pouvez parcourir le site pour rechercher la bibliothèque [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Pour ce faire, cliquez sur **Enregistrer** afin d'établir une connexion au serveur spécifié.  
  
     ![GMNI_ExcelSaveAs](../media/gmni-excelsaveas.gif "GMNI_ExcelSaveAs")  
  
1.  À l'aide de la boîte de dialogue Enregistrer sous, sélectionnez la bibliothèque [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans votre site.  
  
2.  Cliquez sur **Ouvrir** pour ouvrir la bibliothèque.  
  
3.  Cliquez sur **Enregistrer** pour publier le classeur dans la bibliothèque.  
  
 Dans une fenêtre de navigateur, vérifiez que le document s'affiche dans la bibliothèque [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Les documents publiés récemment sont affichés dans la liste. Les paramètres de bibliothèque déterminent où le document apparaît (par exemple, trié par ordre croissant par date, ou alphabétiquement par nom). Vous devrez peut-être actualiser la fenêtre du navigateur pour afficher les ajouts les plus récents.  
  
#### <a name="upload-a-workbook-into-powerpivot-gallery"></a>Télécharger un classeur dans la Galerie PowerPivot  
 Vous avez également la possibilité de télécharger un classeur si vous souhaitez démarrer à partir de SharePoint et sélectionner sur votre ordinateur le fichier à publier.  
  
1.  Dans un site SharePoint, ouvrez la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
2.  Dans le ruban de la bibliothèque, cliquez sur **Documents**.  
  
3.  Dans **Télécharger un document**, sélectionnez une option de téléchargement, puis entrez le nom et l'emplacement du fichier à télécharger. Les paramètres de bibliothèque déterminent où le document apparaît. Vous devrez peut-être actualiser la fenêtre du navigateur pour afficher l'ajout le plus récent.  
  
##  <a name="newdocs"></a>Créer des rapports ou des classeurs basés sur un classeur PowerPivot publié  
 Pour les classeurs [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que vous publiez dans la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , vous pouvez créer d'autres classeurs ou rapports Reporting Services qui utilisent le classeur publié comme source de données connectée.  
  
|||  
|-|-|  
|![GMNI_btn_NewDocReportGallery](../media/gmni-btn-newdocreportgallery.gif "GMNI_btn_NewDocReportGallery")|Cliquez sur la partie du bouton Nouveau rapport représentant une flèche vers le bas pour lancer le Générateur de rapports ou Excel 2010. La Galerie PowerPivot doit utiliser l'une des vues prédéfinies (Théâtre, Galerie ou Carrousel) pour que le bouton Nouveau rapport soit disponible.|  
  
#### <a name="create-report-builder-report"></a>Créer un rapport du Générateur de rapports.  
 Pour créer un rapport basé sur un classeur PowerPivot existant dans la bibliothèque, Reporting Services doit être configuré pour l'intégration SharePoint pour les mêmes sites qui contiennent la Galerie PowerPivot. Lorsque vous sélectionnez l'option Créer un rapport du Générateur de rapports, le Générateur de rapports est téléchargé à partir du serveur de rapports et installé sur la station de travail locale, lors de sa première utilisation. Un fichier de rapport d'espace réservé est créé pour le nouveau rapport et enregistré dans la Galerie PowerPivot. Les informations de connexion au classeur PowerPivot sont automatiquement créées en tant que nouvelle source de données dans le rapport. Ensuite, vous pouvez générer les datasets et la mise en page du rapport dans l'espace de conception. Lorsque vous utilisez le Générateur de rapports pour assembler votre rapport, vous pouvez enregistrer vos modifications et le résultat final sur le document de rapport dans la bibliothèque. Pour éviter des déconnexions de données ultérieures, veillez à conserver les fichiers du classeur et du rapport ensemble dans la même bibliothèque.  
  
#### <a name="open-new-excel-workbook"></a>Ouvrir le nouveau classeur Excel  
 Pour créer un classeur Excel à partir d'un classeur existant, vous devez déjà disposer d'Excel et de [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] sur l'ordinateur local. La sélection de l'option Ouvrir le nouveau classeur Excel entraîne le démarrage d'Excel, l'ouverture d'un fichier de classeur (.xlsx) vierge et le chargement des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en arrière-plan comme source de données connectée. Seules les données provenant de la fenêtre PowerPivot dans le classeur d'origine sont utilisées dans le nouveau classeur. Les tableaux ou graphiques croisés dynamiques du classeur d'origine sont exclus. Le nouveau classeur établit une liaison aux données du classeur d'origine. Les données ne sont pas copiées vers le nouveau classeur.  
  
##  <a name="view"></a> Ouvrir un classeur ou un rapport en mode page entière  
 Cliquez sur une image miniature visible sur le document prévisualisé pour ouvrir celui-ci en mode page entière, indépendamment de l'aperçu de la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s'ouvrent dans un navigateur. Les rapports Reporting Services s'ouvrent dans le composant WebPart Visionneuse de rapports qui fait partie du déploiement de Reporting Services sur un serveur SharePoint.  
  
 Vous avez également la possibilité d'ouvrir le classeur dans Excel sur une station de travail cliente au lieu de l'afficher dans un navigateur. Vous devez disposer d’Excel 2013 ou d’Excel 2010 et du complément [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] pour afficher le fichier. Vous pouvez utiliser Excel 2007 pour ouvrir le fichier, mais pas pour ajouter un tableau croisé dynamique sur les données. Par conséquent, les versions Excel 2013 ou Excel 2010 sont recommandées à la fois pour afficher et pour créer des données PowerPivot. Si vous ne disposez pas des applications requises, vous devez utiliser un navigateur pour afficher le classeur dans SharePoint.  
  
##  <a name="newdr"></a>Planifier l’actualisation des données pour les classeurs PowerPivot dans la Galerie PowerPivot  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] d'un classeur Excel publié peuvent être actualisées à des fréquences planifiées.  
  
|||  
|-|-|  
|![GMNI_btn_NewDataRefreshReportGallery](../media/gmni-btn-newdatarefreshreportgallery.gif "GMNI_btn_NewDataRefreshReportGallery")|Cliquez sur le bouton Gérer l'actualisation des données pour créer ou afficher une planification qui récupère les données mises à jour à partir des sources de données connectées. Pour obtenir des instructions sur la création d’une planification, consultez [planifier une &#40;actualisation&#41;des données PowerPivot pour SharePoint](../schedule-a-data-refresh-powerpivot-for-sharepoint.md).|  
  
##  <a name="delete"></a>Supprimer un classeur ou un rapport dans la Galerie PowerPivot  
 Pour supprimer un document de la bibliothèque, basculez tout d'abord en mode d'affichage Tous les documents.  
  
1.  Dans un site SharePoint, ouvrez la Galerie [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
2.  Dans le ruban, cliquez sur **Bibliothèque**.  
  
3.  Dans Gérer les affichages, dans la liste Affichage actuel, cliquez sur la flèche bas et sélectionnez Tous les documents.  
  
4.  Sélectionnez le classeur ou le rapport que vous voulez supprimer.  
  
5.  Dans Documents (Fichiers), dans Gérer, cliquez sur le bouton **Supprimer un document** .  
  
##  <a name="image"></a> Actualiser une image miniature  
 Utilisez les étapes suivantes pour régénérer une image miniature pour un document dans la Galerie PowerPivot.  
  
1.  Basculez la Galerie PowerPivot en mode Tous les documents. Pour cela, cliquez sur **Bibliothèque** dans le ruban et remplacez **Affichage actuel** par **Tous les documents**.  
  
2.  Sélectionnez le classeur ou le rapport pour lequel vous souhaitez actualiser l'image miniature.  
  
3.  Cliquez sur la flèche Bas à droite, puis sélectionnez **Modifier les propriétés**.  
  
4.  Cliquez sur **Enregistrer**. L'enregistrement du document force le service d'instantanés à régénérer l'image d'aperçu.  
  
##  <a name="bkmk_known_issues"></a> Problèmes connus  
  
### <a name="document-type-is-not-supported"></a>Le type de document n'est pas pris en charge.  
 Le type de contenu **Document de Galerie PowerPivot** n'est pas pris en charge. Si vous activez le type de contenu **Document de Galerie PowerPivot** pour une bibliothèque de documents, et si vous tentez de créer un document de ce type, un message d'erreur semblable à l'un des messages suivants s'affiche :  
  
-   « Nouveau document » nécessite une application et un navigateur Web compatibles avec Microsoft SharePoint Foundation. Pour ajouter un document à cette bibliothèque de documents, cliquez sur le bouton « Télécharger un document ».  
  
-   « L’adresse Internet’ http://[nom du serveur]/testSite/PowerPivot Gallery/ReportGallery/Forms/template. xlsx’n’est pas valide. » Microsoft Excel ne peut pas accéder au fichier’ http://[nom du serveur]/testSite/PowerPivot Gallery/ReportGallery/Forms/template. xlsx'. Plusieurs raisons sont possibles :  
  
 Le type de contenu **Document de Galerie PowerPivot** n'est pas automatiquement ajouté aux bibliothèques de documents. Vous ne rencontrerez pas ce problème à moins que vous n'ayez activé manuellement le type de contenu non pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un emplacement approuvé pour les sites PowerPivot dans l’administration centrale](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [Supprimer la Galerie PowerPivot](delete-power-pivot-gallery.md)   
 [Créer et personnaliser la Galerie PowerPivot](create-and-customize-power-pivot-gallery.md)   
 [Planifier une actualisation &#40;des données PowerPivot pour SharePoint&#41;](../schedule-a-data-refresh-powerpivot-for-sharepoint.md)  
  
  
