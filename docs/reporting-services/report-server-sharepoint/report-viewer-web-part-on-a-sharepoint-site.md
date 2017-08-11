---
title: Composant WebPart Visionneuse de rapports sur un Site SharePoint | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: b6341a73-172f-4632-a9e9-cc79fed3f36b
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0604356dc5bb7bd964679ef2da4f891900183b78
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="report-viewer-web-part-on-a-sharepoint-site"></a>Composant WebPart Visionneuse de rapports sur un site SharePoint
  Le composant WebPart Visionneuse de rapports est un composant WebPart personnalisé qui est installé par le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. Vous pouvez utiliser le composant WebPart pour afficher les rapports, naviguer parmi ces derniers, les imprimer et les exporter sur un serveur de rapports configuré pour s'exécuter en mode intégré SharePoint. Le composant WebPart Visionneuse de rapports est associé aux fichiers de définition de rapport (.rdl) traités par un serveur de rapports [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous ne pouvez pas l'utiliser avec d'autres documents de rapport que vous créez dans d'autres produits logiciels.  
  
 Pour installer le composant WebPart, vous devez exécuter le programme d'installation du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Vous ne devez pas installer ou désinstaller le composant WebPart indépendamment. Celui-ci fait partie du complément et ne peut être installé que par le package d'installation du complément. Le nom de fichier du composant WebPart Visionneuse de rapports est ReportViewer.dwp. Ce fichier est situé dans le dossier Program Files\Fichiers communs\Microsoft Shared\web server extensions\12\template\features\reportserver et ne doit pas être déplacé vers d'autres dossiers.  
  
 Pour pouvoir utiliser le composant WebPart, vous devez avoir installé et configuré le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et avoir configuré le serveur de rapports pour l'intégration SharePoint. Vous devez également disposer de rapports à afficher dans la visionneuse. Vous ne pouvez ouvrir que les rapports qui se trouvent dans une bibliothèque, un dossier de bibliothèque ou un historique de rapport, ou ceux qui sont liés entre un composant WebPart de bibliothèque et un composant WebPart Visionneuse de rapports. Vous ne pouvez pas ouvrir les rapports enregistrés en tant que pièces jointes d'un élément dans une liste personnalisée.  
  
 Vous pouvez définir les propriétés du composant WebPart Visionneuse de rapports afin de contrôler l'apparence de la barre d'outils et des zones d'affichage, ainsi que pour lier le composant WebPart à un rapport spécifique. La visionneuse de rapports affiche soit un rapport vers lequel vous définissez un lien explicite, soit un fichier .rdl que vous ouvrez.  
  
 Vous ne pouvez pas lier plusieurs rapports à une seule instance de visionneuse de rapports, mais si vous souhaitez regrouper les rapports, vous pouvez créer un tableau de bord ou une page Web qui intègre plusieurs instances du composant WebPart Visionneuse de rapports sur une seule page.  
  
 Le composant WebPart comprend une zone d'affichage, une barre d'outils, une zone réductible pour la définition des informations d'identification et des paramètres, ainsi que des propriétés. L'image suivante illustre le composant WebPart et l'exemple de rapport Company Sales ainsi que les options d'exportation que vous pouvez sélectionner à partir de la barre d'outils.  
  
 ![Composant WebPart Visionneuse de rapports](../../reporting-services/report-server-sharepoint/media/rs-sharepointrvwebpart.gif "composant WebPart Visionneuse de rapports")  
  
## <a name="web-part-components"></a>Composants WebPart  
 La zone d'affichage montre un rapport au format HTML. Selon la configuration du composant WebPart, la zone d'affichage peut soit être agrandie à sa taille maximale afin de montrer le rapport en mode page entière, soit partager l'espace disponible avec les volets adjacents et une barre d'outils.  
  
 La barre d'outils fournit des fonctionnalités de navigation entre les pages, de recherche, de zoom et d'exportation, de sorte que vous puissiez afficher un rapport dans un autre format d'application. Elle fournit également une fonctionnalité d'impression facultative, elle permet d'obtenir une sortie imprimée paginée pour les rapports HTML et de modifier les paramètres relatifs à la mise en page et aux marges. Le menu**Imprimer**, **Ouvrir avec le Générateur de rapports, S’abonner**, **Exporter** et **Imprimer** . Les contrôles de navigation entre les pages et de zoom se trouvent directement sur la barre d'outils.  
  
> [!NOTE]  
>  Vous ne pouvez pas personnaliser la barre d'outils sauf si vous écrivez le code correspondant ; toutefois, vous pouvez définir des propriétés permettant de masquer une partie ou l'ensemble de ses contrôles.  
  
### <a name="export-action-on-the-report-toolbar"></a>Action d'exportation sur la barre d'outils Rapport  
 Dans le menu**Exporter** , la commande **Exporter** affiche les formats d’application associés aux extensions de rendu déployées sur un serveur de rapports. Pour déterminer si un format spécifique est disponible, vous pouvez ajouter ou supprimer une extension de rendu sur le serveur de rapports ; par ailleurs, vous pouvez également modifier les paramètres de configuration afin de supprimer un format d'exportation particulier de la liste. Vous pouvez également spécifier des paramètres de configuration sur le serveur de rapports afin de contrôler les formats disponibles. Vous pouvez modifier le comportement par défaut d'un format spécifique en ajoutant et en modifiant les paramètres de configuration de l'extension de rendu correspondante.  
  
### <a name="print-action-on-the-report-toolbar"></a>Action d'impression sur la barre d'outils Rapport  
 La commande**Imprimer** du menu **Actions** fournit des fonctionnalités d’impression personnalisées via [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Quand vous cliquez sur **Imprimer**, un contrôle d’impression ActiveX côté client est téléchargé sur l’ordinateur client. Dans la plupart des cas, l’utilisateur qui clique sur **Imprimer** doit avoir les autorisations d’administrateur sur l’ordinateur local. Il est usuel de restreindre les téléchargements de contrôles ActiveX aux utilisateurs qui disposent d'autorisations d'administrateur. Vous pouvez utiliser l'Administration centrale de SharePoint pour activer ou désactiver le téléchargement du contrôle d'impression côté client.  
  
### <a name="find-action-on-the-report-toolbar"></a>Action de Recherche sur la barre d'outils Rapport  
 La commande**Rechercher** du menu **Actions** permet d’accéder à un emplacement cible dans le rapport. Vous pouvez rechercher un contenu dans un rapport en tapant un mot ou une expression que vous souhaitez rechercher. La valeur maximale d'une chaîne de recherche est 256 caractères. Si votre recherche trouve une valeur correspondante dans le rapport, le focus est placé sur la partie du rapport qui contient cette valeur.  
  
 Quand vous entrez une valeur à rechercher, tapez-la telle qu’elle est censée apparaître dans le rapport. Ne posez pas une question de type « quel est le bénéfice moyen pour ce mois-ci » à moins que chaque mot de la phrase ne soit censé figurer dans le rapport.  
  
 Vous ne pouvez rechercher qu'un seul terme ou une seule valeur à la fois. Vous ne pouvez pas utiliser d’opérateurs de recherche (par exemple, **ET** ou **OU**), de symboles ou de caractères génériques. Vous ne pouvez pas effectuer de recherche dans une section croisée des données (par exemple rechercher le chiffre d'affaires correspondant à un mois spécifique pour un produit particulier). Pour ce type d'analyse, utilisez le Générateur de rapports afin de créer des rapports générés interactifs.  
  
 Les paramètres de sécurité de base de données et de modèle qui restreignent l'accès aux données de rapport s'appliquent également aux opérations de recherche. Si vous recherchez une valeur dans un rapport généré interactif qui utilise un modèle comme source de données, et si vous n'avez pas accès à une partie du modèle, les données représentées par cette partie du modèle sont exclues de la recherche.  
  
### <a name="panes-for-specifying-credentials-and-parameters"></a>Volets destinés à la définition des paramètres et des informations d'identification  
 Les volets**Informations d’identification** et **Paramètres** apparaissent en regard de la zone d’affichage. Le volet**Informations d’identification** s’affiche quand la connexion à la source de données du rapport est configurée pour inviter l’utilisateur à entrer un compte et un mot de passe ayant des droits d’accès à la source de données. Le volet**Paramètres** s’affiche quand le rapport accepte une entrée utilisateur liée aux paramètres définis dans le rapport.  
  
### <a name="setting-properties-on-the-report-viewer-web-part"></a>Définition des propriétés du composant WebPart Visionneuse de rapports  
 Les propriétés du composant WebPart incluent des propriétés personnalisées qui sont propres à la visionneuse de rapports et des propriétés générales que vous pouvez définir pour n'importe quel composant WebPart. Pour plus d’informations, consultez [Personnaliser le composant WebPart Visionneuse de rapports](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md).  
  
 Par défaut, les rapports s'ouvrent en mode page entière. Le mode page entière permet d'afficher la barre d'outils qui fournit les fonctionnalités de navigation entre les pages, de recherche, etc. Vous pouvez personnaliser le composant WebPart afin de modifier l'apparence ou le comportement par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Ajouter le composant WebPart Visionneuse de rapports à une Page Web &#40; Reporting Services dans SharePoint intégré en Mode &#41;](../../reporting-services/report-server-sharepoint/add-the-report-viewer-web-part-to-a-web-page.md)  
  
  
