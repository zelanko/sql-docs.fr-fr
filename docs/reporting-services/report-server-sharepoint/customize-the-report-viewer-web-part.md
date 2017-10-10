---
title: Personnaliser le composant WebPart Visionneuse de rapports | Documents Microsoft
ms.custom: 
ms.date: 09/25/2017
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
ms.openlocfilehash: 38f23cf5d75c47be55e1820a4421a507a73df54e
ms.contentlocale: fr-fr
ms.lasthandoff: 10/06/2017

---
# <a name="customize-the-report-viewer-web-part"></a>Personnaliser le composant WebPart Visionneuse de rapports

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)])

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Vous pouvez utiliser le composant WebPart Visionneuse de rapports pour afficher les rapports qui s’exécutent sur un serveur de rapports est configuré pour l’intégration SharePoint. Les rapports consultables comprennent des fichiers de définition de rapport (.rdl) et des rapports Générateur de rapports. Rapports s’ouvrent automatiquement dans le composant WebPart Visionneuse de rapports dans une nouvelle page, mais vous pouvez également ajouter un composant WebPart Visionneuse de rapports à un site ou une page web existante si vous souhaitez obtenir un rapport particulier soit toujours visible sur cette page.

> [!NOTE]
> Bien qu’ils ont des noms identiques, la visionneuse de rapports WebPart installé via le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] complément diffère le composant WebPart Visionneuse de rapports qui est inclus dans le fichier RSWebParts.cab. Les instructions fournies dans cette rubrique sont spécifiquement pour le composant WebPart Visionneuse de rapports est installé par le biais du [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Add-in.

 Vous pouvez personnaliser le composant WebPart Visionneuse de rapports comme suit :  
  
-   Modifier l’apparence du composant WebPart en définissant des propriétés.  
  
-   choisissez quelles fonctionnalités de création de rapport interactives sont disponibles sur la barre d'outils Rapports ;  
  
-   spécifiez quelles zones d'affichage sont disponibles ; Le composant WebPart Visionneuse de rapports a une zone d’affichage de rapports, une zone de paramètres et une zone d’informations d’identification.  
  
 Vous ne pouvez pas étendre le composant WebPart Visionneuse de rapports pour prendre en charge différents types de fichiers, et ne peut pas remplacer la barre d’outils rapport avec une barre d’outils personnalisée ou ajouter de nouvelles fonctionnalités à la barre d’outils existante. Si vous avez besoin de personnalisation des fonctionnalités standards, vous devez créer un composant WebPart personnalisé.  

## <a name="setting-web-part-properties"></a>Définition des propriétés du composant WebPart

 Un composant WebPart possède des propriétés personnalisées qui permettent de configurer des fonctionnalités spécifiques. Un composant WebPart possède également des propriétés communes qui sont standard pour chaque composant WebPart.  
  
### <a name="change-default-properties"></a>Modifier les propriétés par défaut

 Le composant WebPart Visionneuse de rapports possède des propriétés par défaut qui conviennent parfaitement à l’ouverture des rapports à la demande à partir d’une bibliothèque ou un dossier. Par défaut, tous les contrôles disponibles sont affichés dans la barre d’outils, et de hauteur et largeur sont définies pour utiliser tout l’espace disponible sur la page web. Si vous souhaitez modifier les propriétés par défaut, vous pouvez personnaliser le composant WebPart via **paramètres du Site**.  
  
1.  Dans le menu **Actions de site** , cliquez sur **Paramètres du site**.  
  
2.  Sous Galeries, cliquez sur **WebPart**.  
  
3.  Cliquez sur **ReportViewer.dwp**.  
  
4.  Ouvrez le volet Outils et définissez les propriétés de votre choix.  
  
### <a name="customize-an-embedded-report-viewer-in-a-web-page"></a>Personnaliser une visionneuse de rapports incorporé dans une page web

 Vous pouvez définir des propriétés pour ajuster la visionneuse de rapports dans une page web. La Visionneuse de rapports peut utiliser le même style et les couleurs que la page qui la contient. Vous pouvez masquer tout ou une partie de la barre d'outils, de l'explorateur de document et de la zone des paramètres pour maximiser la zone d'affichage des rapports dans l'espace alloué. Le rapport utilise toujours les styles qui lui sont attribués à sa création ; vous ne pouvez pas personnaliser l'aspect des rapports après leur publication dans une bibliothèque SharePoint.  
  
 Si vous incorporez le composant WebPart Visionneuse de rapports dans une page web, vous devez définir le **URL de rapport** propriété à un rapport spécifique. Dans le cas contraire, la Visionneuse de rapports affiche des instructions de liaison à un rapport. Vous ne pouvez pas personnaliser ou supprimer les instructions.  
  
### <a name="custom-properties-of-the-report-viewer-web-part"></a>Propriétés personnalisées du composant WebPart Visionneuse de rapports

 Lors de la définition des propriétés personnalisées, sachez que certaines propriétés sont utilisées uniquement lorsque le composant WebPart Visionneuse de rapports est incorporé dans une page. Les exemples comprennent le titre, la hauteur, la largeur, le style de cadre et la zone. D'autres propriétés, de barre d'outils et de paramètres par exemple, sont utilisées indépendamment de l'affichage de la Visionneuse de rapports dans une page ou de l'ouverture d'un rapport en mode page entière.  
  
 Les propriétés personnalisées du composant WebPart Visionneuse de rapports sont répertoriées ci-dessous.  
  
|Propriété|Description|  
|--------------|-----------------|  
|Rapport|Chemin d'accès complet d'un rapport situé sur le site SharePoint actuel ou sur un site inclus dans la même batterie de serveurs ou application Web. Pour obtenir les résultats optimaux lors de la définition de propriétés supplémentaires, cliquez sur Appliquer après avoir spécifié l'URL du rapport.|  
|Cible du lien hypertexte|Code HTML standard qui spécifie le cadre cible permettant d'afficher le contenu lié au sein du document actuel. Pour les rapports qui comportent des liens hypertexte vers des sites Web externes, vous pouvez spécifier si un document cible doit s'ouvrir à la place du rapport existant dans la fenêtre active, ou s'il doit s'ouvrir dans une nouvelle fenêtre de navigateur. Les valeurs valides sont **_Top**, **_Blank**et **_Self**. **_Top** utilise la fenêtre active, **_Blank** charge le document dans une nouvelle fenêtre de navigateur et **_Self** ouvre le document dans le cadre actif. Bien que **_Parent** est une valeur valide pour l’attribut cible au format HTML, ne l’utilisez pas pour un composant WebPart Visionneuse de rapports est incorporé dans une page.|  
|Génération automatique de composant WebPart titre|Un titre généré qui inclut le nom du composant WebPart Visionneuse de rapports et le nom du rapport, séparé par un tiret. Si le rapport n'a pas de titre, le nom du fichier de rapport est utilisé. Le titre est visible lorsque vous ajoutez un composant WebPart à une page. Si cette case à cocher est activée, le titre est généré chaque fois que la page est actualisée.|  
|Génération automatique de lien des détails du composant WebPart|Un lien hypertexte généré qui apparaît au-dessus du WebPart. Vous pouvez cliquer sur le lien afin d'ouvrir le rapport dans une nouvelle page, en mode page entière.|  
|Afficher l'élément de menu Générateur de rapports|Affiche ou masque l’option de menu **Actions** pour ouvrir le Générateur de rapports.|  
|Afficher l'élément de menu Abonnement|Affiche ou masque l’option de menu **Actions** pour créer un abonnement pour le rapport.|  
|Afficher l'élément de menu Imprimer|Affiche ou masque l’option de menu **Actions** pour imprimer le rapport.|  
|Afficher l'élément de menu Exporter|Affiche ou masque l’option de menu **Actions** pour exporter le rapport.|  
|Afficher le bouton Actualiser|Affiche ou masque le bouton Actualiser sur la barre d'outils.|  
|Afficher les commandes de navigation entre les pages|Affiche ou masque les boutons de navigation dans les rapports sur la barre d'outils. Cette option modifie la visibilité de tous les contrôles de navigation.|  
|Afficher le bouton Précédente|Affiche ou masque le bouton Précédente sur la barre d'outils.|  
|Afficher les commandes de recherche|Affiche ou masque les commandes de recherche sur la barre d'outils. Les commandes de recherche autorisent un utilisateur à rechercher le texte dans le rapport rendu. Cette option modifie la visibilité de toutes les commandes de recherche.|  
|Afficher le contrôle de zoom|Affiche ou masque le contrôle de zoom sur la barre d'outils.|  
|Afficher le bouton Flux Atom|Affiche ou masque le bouton Flux Atom sur la barre d'outils.<br /><br /> ![htmlviewer_datafeed](../../reporting-services/media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|  
|Emplacement de la barre d'outils|Détermine l'emplacement de la barre d'outils dans la visionneuse de rapports. Les valeurs possibles sont **Top** et **Bottom**.|  
|Zone de message|Les valeurs valides sont **Affiché**, **Réduit**et **Caché**. **Affiché** affiche de la zone Paramètres pour les rapports qui comportent des valeurs paramétrables et qui nécessitent une entrée utilisateur comme condition d’exécution du rapport. Utilisez **Caché** si tous les paramètres du rapport sont spécifiés et si vous ne voulez pas que la zone des paramètres soit visible par les utilisateurs.|  
|Largeur de la zone des paramètres|Vous pouvez choisir l'unité de mesure et la valeur. La valeur par défaut est 200 pixels. Cette propriété doit respecter une seule exigence, elle doit être supérieure à zéro.|  
|Explorateur de documents|Contrôle de navigation entre les rapports qui est défini dans le rapport et qui permet d'accéder en un seul clic à des sections spécifiques d'un rapport. Il est disponible dans les rapports HTML. L'Explorateur de documents s'affiche dans une zone réductible en regard de la zone d'affichage du rapport. Les valeurs valides sont **Affiché**, **Réduit**et **Caché**. Si un Explorateur de documents est défini pour un rapport, la zone est développée par défaut, sauf si marqué comme masqué ou réduit dans les propriétés du composant WebPart. Si l'Explorateur de documents est réduit, vous pouvez cliquer sur la flèche pour le développer.|  
|Largeur de la zone de l'explorateur de documents|Vous pouvez choisir l'unité de mesure et la valeur. La valeur par défaut est 200 pixels. Cette propriété doit respecter une seule exigence, elle doit être supérieure à zéro.|  
|Charger les paramètres|Récupérez les propriétés de paramètre pour le rapport. Tous les rapports n'ont pas des paramètres. Si le rapport n'a pas de paramètres, aucune valeur n'est retournée. Si vous définissez les propriétés d'un rapport que vous venez de télécharger, vous risquez de recevoir une erreur indiquant que la connexion à la source de données a été supprimée. Si cela se produit, réinitialisez la connexion, puis terminez la définition des propriétés des paramètres une fois la connexion spécifiée. Pour plus d’informations sur la configuration de la connexion, consultez [créer et gérer des Sources de données partagées &#40; Reporting Services dans SharePoint intégré en Mode &#41; ](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).<br /><br /> Pour obtenir des résultats optimaux, cliquez sur **Appliquer** avant de cliquer sur Charger les paramètres.<br /><br /> Une fois que vous avez chargé les propriétés des paramètres, vous pouvez les définir de la même façon que dans les pages de propriétés des paramètres du rapport. Pour plus d’informations sur la façon de définir les paramètres, consultez [définir les paramètres sur un rapport publié &#40; Reporting Services dans SharePoint intégré en Mode &#41; ](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).|  

## <a name="customizing-the-toolbar"></a>Personnalisation de la barre d’outils

 La barre d'outils s'affiche sous le titre et s'étend sur toute la partie supérieure du rapport. La barre d’outils fournit un menu **Actions** , la navigation entre les pages pour les rapports paginés, l’actualisation et le zoom. Elle inclut un contrôle d'Explorateur de documents pour les rapports qui disposent d'un Explorateur de documents. Le menu **Actions** comprend des commandes permettant d’exporter un rapport, de rechercher du texte ou des nombres dans un rapport, d’imprimer un rapport et d’ouvrir le rapport dans le Générateur de rapports.  
  
 Vous ne pouvez pas ajouter de nouvelles commandes au menu  **Actions** mais vous pouvez le personnaliser en modifiant les options visibles aux utilisateurs. Pour modifier la visibilité des boutons de barre d’outils et des contrôles, vous modifiez les options de la **visibilité des éléments de barre d’outils** section du composant WebPart. Vous pouvez également supprimer la commande **Imprimer** ou des formats d’exportation spécifiques en rendant ces fonctionnalités inaccessibles sur le serveur de rapports. Les contrôles de navigation entre les pages sont disponibles pour les rapports qui comportent des sauts de page ; à défaut, le rapport est constitué d'une seule page de longueur variable. La commande**Actualiser** permet de traiter à nouveau le rapport à l’aide des paramètres actuels du rapport. Pour afficher tous les contrôles sur une seule ligne, définissez la largeur globale du composant WebPart au moins égale à 400 pixels.  

## <a name="customizing-the-viewing-area"></a>Personnalisation de la zone d’affichage

 Une zone d'affichage sert à afficher les rapports. La zone d'affichage du rapport est partagée avec les zones Paramètres et Informations d'identification, si celles-ci sont utilisées. Si des informations d'identification sont requises, la zone Informations d'identification s'affiche en regard d'une zone d'affichage du rapport vide. La zone Informations d'identification disparaît une fois que l'utilisateur fournit les informations d'identification et qu'il exécute le rapport. Pour personnaliser le texte invitant les utilisateurs à fournir des informations d’identification, modifiez les propriétés de connexion de la source de données. Pour plus d’informations, consultez [créer et gérer des Sources de données partagées &#40; Reporting Services dans SharePoint intégré en Mode &#41; ](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76).  
  
 La zone Paramètres fournit des champs permettant d'entrer des valeurs avant l'exécution du rapport. Elle n'est utilisée que lorsqu'une définition de rapport comprend des paramètres. Lorsque les zones de la zone paramètres ou informations d’identification sont affichés, l’affichage du rapport est ajustée pour utiliser la largeur restante du composant WebPart. Vous pouvez définir des propriétés sur le composant WebPart pour personnaliser la largeur de paramètres. Vous pouvez également définir les étiquettes qui s'affichent en regard des paramètres individuels sur la page. Pour plus d’informations sur la modification des étiquettes de paramètres, consultez [définir les paramètres sur un rapport publié &#40; Reporting Services dans SharePoint intégré en Mode &#41; ](../../reporting-services/report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).  
  
## <a name="see-also"></a>Voir aussi

 [Composant WebPart Visionneuse de rapports sur un SharePoint Site](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [Ajouter le composant WebPart Visionneuse de rapports à une page web](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
