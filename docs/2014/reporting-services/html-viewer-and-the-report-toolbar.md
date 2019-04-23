---
title: Visionneuse HTML et barre d’outils Rapport | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML Viewer [Reporting Services]
- report toolbar [Reporting Services]
ms.assetid: cd86b319-babd-45af-a6a4-f659fdcc40c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 86ac5b6da861477bfd5b8e92feac97068ca5adc9
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934055"
---
# <a name="html-viewer-and-the-report-toolbar"></a>Visionneuse HTML et barre d'outils Rapport
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit une visionneuse HTML utilisée pour afficher des rapports sur demande lorsqu'ils sont demandés auprès du serveur de rapports. La visionneuse HTML offre une infrastructure pour afficher les rapports au format HTML. Elle comporte une barre d'outils Rapport, une section de paramétrage, une section sur les informations d'identification et un explorateur de documents. Cette barre d'outils offre des fonctionnalités qui permettent d'utiliser votre rapport, notamment des options d'exportation qui permettent d'afficher votre rapport dans d'autres formats que le format HTML. La section de paramètre et l'explorateur de documents sont affichés uniquement lorsque vous ouvrez des rapports configurés pour utiliser des paramètres et une commande d'explorateur de documents.  
  
> [!NOTE]  
>  Bien que vous ne puissiez pas modifier la barre d'outils Rapport, vous pouvez configurer les paramètres dans une adresse URL destinée aux rapports pour la masquer dans un rapport. Pour plus d’informations sur le masquage de la barre d’outils des rapports, consultez [Référence de paramètre d’accès URL](url-access-parameter-reference.md).  
  
## <a name="report-toolbar"></a>Barre d'outils Rapport  
 Cette barre d'outils offre des fonctionnalités de navigation entre les pages, de zoom, d'actualisation, de recherche, d'exportation, d'impression et de source de donnés pour les rapports affichés dans l'extension de rendu HTML.  
  
 La fonction d'impression est facultative. Lorsqu'elle est disponible, l'icône Imprimante s'affiche dans la barre d'outils. À la première utilisation, lorsque vous cliquez sur cette icône, vous téléchargez un contrôle ActiveX que vous devez installer. Lorsque ce contrôle est installé, en cliquant sur l'icône Imprimante, vous ouvrez la boîte de dialogue Imprimer qui permet de sélectionner une imprimante parmi celles qui sont configurées sur votre ordinateur. Les paramètres du serveur et du navigateur déterminent la disponibilité de la fonction d'impression. Pour plus d’informations, consultez [Imprimer des rapports à partir d’un navigateur à l’aide du contrôle d’impression &#40;Générateur de rapports et SSRS&#41;](report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) et [Activer et désactiver l’impression côté client pour Reporting Services](report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 La barre d'outils Rapport est identique à celle illustrée ci-dessous. Elle peut être toutefois différente selon les fonctionnalités de rapport ou les options de rendu disponibles.  
  
 ![Report toolbar](media/htmlviewer-toolbar.gif "Report toolbar")  
  
 Le tableau ci-dessous décrit les fonctionnalités couramment utilisées de la barre d'outils Rapport. Chaque fonctionnalité est identifiée par la commande que vous utilisez pour y accéder.  
  
|Utilisez cette icône ou cette commande||Pour|  
|------------------------------|-|--------|  
|![Commandes de navigation entre les pages](media/htmlviewer-pagenav.gif "Commandes de navigation entre les pages")|**Commandes de navigation entre les pages**|Ouvrir la première ou la dernière page d'un rapport, faire défiler un rapport page par page et ouvrir une page particulière d'un rapport. Pour afficher une page spécifique, tapez le numéro de page et appuyez sur Entrée.|  
|![Commandes d'affichage des pages](media/htmlviewer-pagesize.gif "Commandes d'affichage des pages")|**Commandes d'affichage des pages**|Agrandir ou réduire la taille de la page d'un rapport. Outre les modifications des pourcentages, vous pouvez sélectionner **Largeur de page** pour ajuster la longueur horizontale d’une page d’un rapport à la fenêtre du navigateur ou **Page entière** pour ajuster la longueur verticale d’un rapport à la fenêtre du navigateur. **Internet Explorer 5.5 et versions ultérieures prennent en charge l'option** Zoom [!INCLUDE[msCoName](../includes/msconame-md.md)] .|  
|![Champ de recherche](media/htmlviewer-search.gif "Champ de recherche")|**Champ de recherche**|Rechercher du contenu dans un rapport en tapant un terme ou une phrase que vous souhaitez trouver (la longueur maximale de la valeur est de 256 caractères). La recherche ne respecte pas la casse et commence au niveau de la page ou de la section actuellement sélectionnée. Seul le contenu visible est compris dans une opération de recherche. Pour rechercher d'autres occurrences de la même valeur, cliquez sur **Suivant**.|  
|![Formats d'exportation](media/htmlviewer-export.GIF "Formats d'exportation")|**Formats d'exportation**|Ouvrir une nouvelle fenêtre de navigateur et effectuer le rendu du rapport dans le format sélectionné. Les formats disponibles sont déterminés par les extensions de rendu installées sur le serveur de rapports. Le format TIFF est recommandé pour l'impression. Cliquez sur **Exporter** pour afficher le rapport dans le format sélectionné.|  
|![Icône Explorateur de documents](media/htmlviewer-docmap.GIF "Icône Explorateur de documents")|**Icône Explorateur de documents**|Afficher ou masquer le volet de l'explorateur de documents dans un rapport qui comprend un explorateur de documents. Un explorateur de documents est un contrôle de navigation entre les rapports similaire au volet de navigation d'un site Web. Vous pouvez cliquer sur des éléments dans l'explorateur de documents pour naviguer jusqu'à un groupe, une page ou un sous-rapport spécifique.|  
|![Icône Imprimante](media/printer-icon.gif "Icône Imprimante")|**Icône Imprimante**|Ouvre la boîte de dialogue Imprimer qui permet de spécifier les options d'impression et d'imprimer un rapport. À la première utilisation, lorsque vous cliquez sur cette icône, vous téléchargez le contrôle de l'impression.|  
||**Icônes d'affichage ou de masquage**|Afficher ou masquer les champs de valeurs de paramètre et le bouton **Afficher le rapport** dans un rapport qui contient des paramètres.|  
|![Bouton d’actualisation du navigateur sur la barre d’outils du rapport](media/htmlviewer-refresh.GIF "Bouton d’actualisation du navigateur sur la barre d’outils du rapport")|**Icône d'actualisation de rapport**|Actualiser le rapport. Les données des rapports actifs seront actualisées. Les rapports mis en cache sont rechargés à partir de l'emplacement où ils sont stockés.|  
|![htmlviewer_datafeed](media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|**Icône de source de données**|Sources de données générées à partir de rapports.|  
  
### <a name="about-export-formats"></a>Formats d'exportation  
 À partir de la barre d'outils Rapport, vous pouvez choisir d'afficher votre rapport sous divers formats. Les formats disponibles sont déterminés par les extensions de rendu installées sur le serveur de rapports. Lorsque vous sélectionnez un autre format, une seconde fenêtre de navigateur affiche le rapport en utilisant une visionneuse associée au format d'exportation sélectionné. Si aucune visionneuse n'est disponible pour le format sélectionné, vous pouvez choisir un autre format.  
  
 Les formats d'exportation ci-dessous sont compris dans une installation d'un serveur de rapports par défaut. La liste des formats d'exportation disponibles peut être différente de celle indiquée ci-dessous.  
  
|Format d'exportation|Description|  
|-------------------|-----------------|  
|XML|Affiche un rapport rédigé dans la syntaxe XML. Les rapports affichés au format XML ouvrent une nouvelle fenêtre du navigateur.|  
|CSV|Affiche un rapport dans lequel les données sont délimitées par des virgules. Vous pouvez ouvrir le rapport dans une application associée au format de fichier CSV.|  
|Fichier Acrobat (PDF)|Permet d'afficher un rapport à l'aide d'une visionneuse PDF côté client. Vous devez disposer d'un logiciel d'affichage du format PDF (par exemple Adobe Acrobat Reader) pour utiliser ce format.|  
|Excel|Permet d'afficher le rapport dans [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel.|  
|Archive Web|Permet d'afficher un rapport dans un format HTML encodé MIME qui conserve les images et le contenu lié avec un rapport.|  
|Fichier TIFF|Permet d'afficher un rapport dans la visionneuse TIFF par défaut. Pour certains clients [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows, il s'agit de la visionneuse des images et des télécopies Windows. Sélectionnez ce format pour afficher un rapport dans une disposition par page.|  
  
## <a name="parameters"></a>Paramètres  
 Les paramètres sont des valeurs qui permettent de sélectionner des données spécifiques (ils sont notamment utilisés pour terminer une requête qui sélectionne les données pour votre rapport ou pour filtrer le jeu de résultats). Les paramètres couramment utilisés dans les rapports comprennent les dates, les noms et les ID. Lorsque vous spécifiez une valeur pour un paramètre, le rapport contient uniquement les données qui correspondent à cette valeur (par exemple, les données d'un employé basées sur le paramètre ID de l'employé). Les paramètres correspondent aux champs contenus dans le rapport. Une fois un paramètre spécifié, cliquez sur **Afficher le rapport** pour obtenir les données.  
  
 L'auteur d'un rapport définit les valeurs de paramètres valides pour chaque rapport. Un administrateur de rapports peut également définir des valeurs de paramètres. Pour déterminer les valeurs de paramètres valides de votre rapport, contactez l'auteur ou l'administrateur de rapports.  
  
## <a name="credentials"></a>Informations d'identification  
 Les informations d'identification sont les valeurs de nom d'utilisateur et de mot de passe qui autorisent l'accès à une source de données. Une fois les informations d'identification spécifiées, cliquez sur **Afficher le rapport** pour obtenir les données. Si un rapport requiert que vous vous connectiez, cela signifie que les données que vous êtes autorisé à afficher peuvent être différentes de celles qu'un autre utilisateur peut afficher. Par conséquent, deux utilisateurs peuvent exécuter le même rapport et obtenir des résultats différents. En outre, certains rapports contiennent des zones masquées qui sont révélées selon les informations d'identification de connexion utilisateur ou les sélections effectuées dans le rapport. Les zones masquées sont exclues des opérations de recherche, ce qui entraîne des résultats de recherche différents de ceux obtenus lorsque toutes les parties du rapport sont visibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
