---
title: Exportation vers Microsoft Word (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cd8ae26-4682-4473-8f15-af084951defd
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 2720d4e3a767a66768909bccad6cf1a7fdf78722
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141993"
---
# <a name="exporting-to-microsoft-word-report-builder-and-ssrs"></a>Exportation vers Microsoft Word (Générateur de rapports et SSRS)
  L’extension de rendu Word restitue des rapports dans le format natif de [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. Il s'agit du format Office Open XML.  
  
 Le convertisseur Word est compatible avec [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010, ainsi qu'avec [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003 moyennant l'installation préalable du Module de compatibilité pour formats de fichiers [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Word, Excel et PowerPoint. Pour plus d'informations sur le module de compatibilité, consultez [Module de compatibilité pour formats de fichiers Microsoft Office Word, Excel et PowerPoint](http://go.microsoft.com/fwlink/?LinkID=205622).  
  
 Le type de contenu des fichiers générés par ce convertisseur est **application/vnd.openxmlformats-officedocument.wordprocessingml.document** et l'extension des fichiers est .docx.  
  
 La version précédente de l'extension de rendu Word, compatible avec [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003, est renommée Word 2003. Seule l'extension de rendu Word est disponible par défaut. Vous devez mettre à jour les fichiers de configuration Reporting Services pour rendre l'extension de rendu Word 2003 disponible. Le type de contenu des fichiers générés par le convertisseur Word 2003 est **application/vnd.ms-word** et l'extension des noms de fichiers est .doc.  
  
> [!IMPORTANT]  
>  Le [!INCLUDE[ofprword](../../includes/ofprword-md.md)] extension de rendu 2003 est déconseillée. Pour plus d’informations, consultez [fonctionnalités déconseillées dans SQL Server Reporting Services dans SQL Server 2014](../deprecated-features-in-sql-server-reporting-services-ssrs.md).  
  
 Après avoir exporté le rapport dans un document Word, vous pouvez modifier le contenu de votre rapport et concevoir des rapports de style document comme des étiquettes de publipostage, des bons de commande ou des lettres types.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="ReportItemsWord"></a> Éléments de rapport dans Word  
 Les rapports exportés vers Word apparaissent sous la forme d'une table imbriquée qui représente le corps du rapport. Une région de données de tableau matriciel est rendue sous la forme d'une table imbriquée qui reflète la structure de la région de données dans le rapport. Les zones de texte et les rectangles sont rendus sous la forme d'une cellule dans la table. La valeur de zone de texte est affichée à l'intérieur de la cellule.  
  
 Les images, graphiques, barres de données, graphiques sparkline, cartes, indicateurs et jauges sont rendus sous la forme d'une image statique dans une cellule de table. Les liens hypertexte et liens d'extraction de ces éléments de rapport sont rendus. Les plans et zones sur lesquels il est possible de cliquer dans un graphique ne sont pas pris en charge.  
  
 Les rapports en colonnes de style bulletin d'informations ne sont pas rendus dans Word. Les images et couleurs d'arrière-plan du corps du rapport ainsi que de la page ne sont pas rendus.  
  
##  <a name="Pagination"></a> Pagination  
 Une fois que le rapport est ouvert dans Word, Word le repagine entièrement en fonction de la taille de la page. La repagination peut provoquer l'insertion de sauts de page à des endroits où vous n'aviez pas l'intention d'en ajouter, et, dans certains cas, peut engendrer la présence dans le rapport exporté de deux sauts de page consécutifs dans une ligne ou l'ajout de pages vides. Vous pouvez essayer de modifier la pagination de Word en ajustant les marges de page.  
  
 Ce convertisseur ne prend en charge que les sauts de page logiques.  
  
### <a name="page-sizing"></a>Dimensionnement de page  
 Lorsque le rapport est rendu, la hauteur et la largeur de page Word sont définies par les propriétés RDL suivantes : hauteur et largeur du format de papier, marges de page gauche et droite, ainsi que marges de page supérieure et inférieure.  
  
### <a name="page-width"></a>Largeur de page  
 Word prend en charge des largeurs de page allant jusqu'à 22 pouces. Si le rapport dépasse cette largeur, le convertisseur rendra tout de même le rapport. Toutefois, Word n'affichera pas le contenu du rapport en mode Impression ou Lecture. Pour afficher les données, passez en mode Normal ou Web. Dans ces modes, Word réduit la quantité d'espaces et affiche par conséquent une part plus importante du contenu du rapport.  
  
 Au moment du rendu, le rapport s'élargit autant que nécessaire, jusqu'à la limite de 22 pouces, pour afficher le contenu. La largeur minimale du rapport se base sur la propriété RDL Width dans le volet Propriétés.  
  
##  <a name="DocumentProperties"></a> Propriétés du document  
 Le convertisseur Word écrit les métadonnées suivantes dans le fichier DOCX.  
  
|Propriétés des éléments de rapport|Description|  
|-------------------------------|-----------------|  
|Report Title (titre du rapport)|Titre|  
|Report.Author|Auteur|  
|Report.Description|Commentaires|  
  
##  <a name="ReportHeadersFooters"></a> En-têtes et pieds de page  
 Les en-têtes et pieds de page sont rendus sous la forme de régions d'en-tête et de pied de page dans Word. Si un numéro de page de rapport ou une expression qui indique le nombre total de pages du rapport apparaît dans l'en-tête ou le pied de page du rapport, ils sont convertis en champ Word afin que le numéro de page exact soit affiché dans le rapport rendu. Si la hauteur d'en-tête ou de pied de page est définie dans le rapport, Word ne peut pas prendre en charge ce paramètre. La propriété PrintOnFirstPage peut, dans certaines circonstances, spécifier si le texte d’un en-tête et d’un pied de page est imprimé sur la première page d’un rapport. Si le rapport rendu contient plusieurs pages et si chaque page contient seulement une section, vous pouvez alors attribuer à PrintOnFirstPage la valeur False et le texte est supprimé sur la première page. Sinon, le texte est imprimé indépendamment de la valeur de la propriété PrintOnFirstPage.  
  
 Le convertisseur Word essaie d'analyser toutes les expressions dans les en-têtes et les pieds de page de rapport lorsque des rapports sont exportés vers Word. De nombreux formulaires d'expressions procèdent à une analyse et les valeurs attendues s'affichent dans les pieds de page et les en-têtes de toutes les pages du rapport.  
  
 Toutefois, lorsqu'un pied de page ou un en-tête de page contient une expression complexe qui retourne des valeurs différentes sur des pages différentes d'un rapport, la même valeur peut s'afficher sur toutes les pages du rapport. Les numéros de page dans les deux expressions suivantes ne sont pas incrémentés dans le rapport exporté. Le numéro de page se traduit par la même valeur sur toutes les pages du rapport.  
  
-   `="Page: " + Globals!PageNumber.ToString + " of " + Globals!TotalPages.ToString`  
  
-   `=Avg(Fields!YTDPurchase.Value, "Sales") & " Page Number " & Globals!PageNumber`  
  
 Cela se produit parce que le convertisseur Word analyse le rapport et recherche les champs pertinents à la pagination tels que **PageNumber** et **TotalPages** et ne gère que des références simples, sans appels à une fonction. Dans ce cas, l'expression appelle la fonction **ToString** . Les deux expressions suivantes sont équivalentes et permettent d'obtenir l'une comme le résultat escompté lorsque vous prévisualisez le rapport dans le Générateur de rapports ou le Concepteur de rapports ou restituez le rapport publié dans le Gestionnaire de rapports ou une bibliothèque SharePoint. Toutefois, le convertisseur Word analyse uniquement la seconde expression et restitue les numéros de page corrects.  
  
-   **Expression complexe :**  l'expression est `="Average Sales " & Avg(Fields!YTDPurchase.Value, "Sales") & " Page Number " & Globals!PageNumber`  
  
-   **Expression avec séquence de texte :** Texte **Montant moyen des ventes**, et expression,  `=Avg(Fields!YTDPurchase.Value, "Sales)`, et texte, **Numéro de page**, et expression `=Globals!PageNumber`  
  
 Pour éviter ce problème, utilisez plusieurs séquences de texte plutôt qu'une expression complexe lorsque vous utilisez des expressions dans les pieds de page et les en-têtes. Les deux expressions suivantes sont équivalentes. La première est une expression complexe, la seconde utilise des séquences de texte. Le convertisseur Word analyse uniquement la seconde expression avec succès.  
  
##  <a name="Interactivity"></a> Interactivité  
 Certains éléments interactifs sont pris en charge dans Word. Vous trouverez ci-dessous une description de comportements spécifiques.  
  
### <a name="show-and-hide"></a>Afficher et masquer  
 Le convertisseur Word rend les éléments de rapport en fonction de leur état au moment du rendu. Si l'état d'un élément de rapport est masqué, l'élément de rapport n'est pas rendu dans le document Word. Si l'état d'un élément de rapport est affiché, l'élément de rapport est rendu dans le document Word. La fonctionnalité d'activation et de désactivation n'est pas prise en charge dans Word.  
  
### <a name="document-map"></a>Explorateur de documents  
 S'il existe des étiquettes Explorateur de documents dans le rapport, elles sont rendues sous la forme d'étiquettes de table des matières Word sur les éléments de rapport et groupes respectifs. L'étiquette Explorateur de documents est utilisée comme texte d'étiquette pour les étiquettes de table des matières. Le lien cible est positionné près de l'élément sur lequel l'étiquette est définie. La table des matières n'est pas créée pour vous dans le document Word, mais vous pouvez générer votre propre table des matières à l'aide des étiquettes Explorateur de documents rendues dans le rapport.  
  
### <a name="hyperlink-and-drillthrough-links"></a>Liens hypertexte et liens d'extraction  
 Les liens hypertexte et liens d'extraction dans les éléments de rapport de type zone de texte et image sont rendus sous la forme de liens hypertexte dans le document Word. Lorsque vous cliquez sur le lien hypertexte, le navigateur Web par défaut s'ouvre et accède à l'URL. Lorsque vous cliquez sur le lien hypertexte d'extraction, un accès est effectué au serveur de rapports d'origine.  
  
### <a name="interactive-sorting"></a>Tri interactif  
 Le contenu du rapport est rendu en fonction du mode de tri actuel dans la région des données de rapport. Word ne prend pas en charge le tri interactif. Une fois le rapport rendu, vous pouvez appliquer un tri de table dans Word.  
  
### <a name="bookmarks"></a>Signets  
 Les signets du rapport sont rendus sous la forme de signets Word. Les liens de signet sont rendus sous la forme de liens hypertexte qui se connectent aux étiquettes de signet dans le document. Les étiquettes de signet ne doivent pas comporter plus de 40 caractères. Le seul caractère spécial pouvant être utilisé dans une étiquette de signet est le trait de soulignement (_). Les caractères spéciaux non pris en charge sont supprimés du nom d'étiquette de signet. Par ailleurs, si le nom dépasse 40 caractères, il est tronqué. Si des noms de signet sont en double dans le rapport, les signets ne sont pas rendus dans Word.  
  
##  <a name="WordStyleRendering"></a> Rendu des styles Word  
 Voici une description succincte du rendu des styles dans Word.  
  
### <a name="color-palette"></a>Palette de couleurs  
 Les couleurs rendues dans le rapport sont rendues dans le document Word.  
  
### <a name="border"></a>Bordure  
 Les bordures des éléments de rapport autres que les bordures de page sont rendues sous la forme de bordures de cellule de tableau Word.  
  
##  <a name="SquigglyLines"></a> Traits ondulés dans les rapports exportés  
 Lorsqu'elles sont exportées et affichées dans Word, les données ou les constantes de rapport peuvent être soulignées par des traits ondulés rouges ou verts. Les traits rouges ondulés identifient les erreurs d'orthographe. Les traits verts ondulés identifient les erreurs de grammaire. Cela se produit lorsque le rapport comprend des mots non conformes à la vérification linguistique (orthographe et grammaire) de la langue d'édition spécifiée dans Word. Par exemple, les titres des colonnes de rapport en anglais seront probablement soulignés par des traits rouges ondulés si le rapport est rendu dans une version espagnole de Word. Les erreurs d'orthographe sont plus courantes dans les rapports que les erreurs de grammaire car les rapports comprennent généralement uniquement du texte court, des phrases ou des paragraphes incomplets.  
  
 La présence de traits ondulés dans les rapports implique que le rapport comporte des erreurs, ce qui n'est probablement pas le cas. Vous pouvez supprimer les lignes ondulées en modifiant la langue de vérification du rapport. Pour modifier la langue de vérification, sélectionnez le contenu du rapport et spécifiez la langue appropriée. Vous pouvez sélectionner tout ou seulement une partie du contenu. Dans Word 2010, l'option de langue, **Définir la langue de la vérification**, se trouve dans la zone **Langue** de l'onglet **Révision** . Après avoir mis à jour le contenu, vous devez réenregistrer le document.  
  
 En fonction de la version de la langue de votre programme Office, les outils de vérification linguistique (par exemple, dictionnaire) de la langue choisie sont inclus dans le programme ou fournis dans un pack linguistique [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office dont vous faites l'acquisition.  
  
 Les rubriques suivantes fournissent des informations supplémentaires sur le paramétrage des options d'Office et de Word.  
  
-   Modifier la langue d'édition dans les **Préférences linguistiques de Microsoft Office 2010** ou dans la boîte de dialogue **Options de Word** dans Word. Pour plus d'informations, consultez [Définir les préférences de langue pour l’édition, l’affichage ou l’aide](http://office.microsoft.com/word-help/enable-the-use-of-other-languages-in-your-office-programs-HA010354783.aspx?CTT=1).  
  
-   Ajouter des packs linguistiques Office et modifier la langue d'édition. Pour plus d'informations, consultez [Définir les préférences de langue pour l’édition, l’affichage ou l’aide](http://office.microsoft.com/word-help/enable-the-use-of-other-languages-in-your-office-programs-HA010354783.aspx?CTT=1) et [Options linguistiques d'Office 2010](http://office.microsoft.com/language/).  
  
> [!NOTE]  
>  Lorsque vous modifiez la langue d'édition dans les **Préférences linguistiques de Microsoft Office 2010** ou dans la boîte de dialogue **Options de Word** dans Word, la modification s'applique à tous les programmes Office.  
  
##  <a name="WordLimitations"></a> Limitations Word  
 [!INCLUDE[ofprword](../../includes/ofprword-md.md)]applique les limitations suivantes :  
  
-   Les tableaux Word prennent en charge au maximum 63 colonnes. Si le rapport en contient plus et que vous essayez de le rendre, Word fractionne le tableau. Les colonnes supplémentaires sont placées en position adjacente aux 63 colonnes affichées dans le corps du rapport. Les colonnes du rapport risquent par conséquent de ne pas être alignées comme prévu.  
  
-   Word prend en charge une largeur de page maximale de 22 pouces de large et de 22 pouces de haut. Si votre contenu dépasse 22 pouces, certaines données risquent de ne pas s'afficher en mode Impression.  
  
-   Word ignore les paramètres de hauteur des en-têtes et pieds de page.  
  
-   Une fois le rapport exporté, Word le pagine à nouveau. Cela peut entraîner l'ajout de sauts de page supplémentaires dans le rapport rendu.  
  
-   Word ne répète pas les lignes d’en-tête en page deux et suivantes, même si vous définissez la propriété RepeatOnNewPage de la ligne d’en-tête statique dans un tableau matriciel (table, matrice ou liste) sur `True`. Vous pouvez définir des sauts de page explicites dans votre rapport pour forcer l'apparition de lignes d'en-tête sur les nouvelles pages. Toutefois, étant donné que Word applique sa propre pagination au rapport rendu exporté vers Word, les résultats peuvent varier et la ligne d'en-tête peut ne pas se répéter comme prévu. La ligne d'en-tête statique est la ligne qui contient les en-têtes de colonne.  
  
-   Les zones de texte s'agrandissent lorsqu'elles contiennent des espaces insécables.  
  
-   Lorsque du texte est exporté vers Word, le texte avec les ornements de police dans certaines polices peut générer des glyphes inattendus ou manquants dans le rapport rendu.  
  
##  <a name="WordBenefits"></a> Avantages de l'utilisation du convertisseur Word  
 En plus de rendre les fonctionnalités qui sont nouvelles dans [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010 disponibles pour l’exportation des rapports, les fichiers *.docx des rapports exportés ont tendance à être plus petite. Les rapports exportés à l'aide du convertisseur Word sont généralement beaucoup plus petits que les mêmes rapports exportés à l'aide du convertisseur Word 2003.  
  
## <a name="backward-compatibility-of-exported-reports"></a>Compatibilité descendante des rapports exportés  
 Vous pouvez sélectionner un mode de compatibilité Word et définir les options de compatibilité. Le convertisseur Word crée des documents avec le mode de compatibilité activé. En enregistrant de nouveau les documents avec le mode de compatibilité désactivé, il est possible que la mise en page du document soit modifiée.  
  
 Si vous désactivez le mode de compatibilité, puis enregistrez de nouveau un rapport, la mise en page du rapport peut être modifiée de façon inattendue.  
  
##  <a name="AvailabilityWord"></a> Disponibilité du convertisseur Word 2003  
 Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], le convertisseur Word par défaut est la version qui assure un rendu au format natif de [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. Il s'agit de l'option **Word** listée dans les menus **Exporter** du Gestionnaire de rapports et de SharePoint. La version antérieure, compatible uniquement avec [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003, est maintenant nommée Word 2003 et est listée dans les menus sous ce nom. L'option de menu **Word 2003** n'est pas visible par défaut ; toutefois, un administrateur peut la rendre visible en mettant à jour le fichier de configuration RSReportServer. Pour exporter des rapports à partir de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] à l'aide du convertisseur Word 2003, vous devez mettre à jour le fichier de configuration RSReportDesigner. Toutefois, le fait de rendre le convertisseur Word 2003 visible ne permet pas d'en disposer dans tous les scénarios. Dans la mesure où le fichier de configuration RSReportServer réside sur le serveur de rapports, les outils ou produits à partir desquels vous exportez les rapports doivent être connectés à un serveur de rapports pour permettre la lecture du fichier de configuration. Si vous utilisez des outils ou produits en mode déconnecté ou en mode local, le fait de rendre le convertisseur Word 2003 visible n'a aucun effet. L'option de menu **Word 2003** demeure inaccessible. Si vous rendez le convertisseur Word 2003 visible dans le fichier de configuration RSReportDesigner, l'option de menu **Word 2003** est toujours disponible dans l'aperçu de rapport [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] .  
  
 L'option de menu **Word 2003** n'est jamais visible dans les scénarios suivants :  
  
-   Utilisation du Générateur de rapports en mode déconnecté et affichage de l'aperçu d'un rapport dans le Générateur de rapports. Cela se produit à la fois dans le [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] et les versions autonomes du Générateur de rapports.  
  
-   Utilisation du composant WebPart Visionneuse de rapports en mode local alors que la batterie de serveurs SharePoint n'est pas intégrée à un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez [Rapports en mode local et rapports en mode connecté dans la Visionneuse de rapports &#40;Reporting Services en mode SharePoint&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
 Si le convertisseur **Word 2003** est configuré pour être visible, les options de menu **Word** et **Word 2003** sont disponibles dans les scénarios suivants :  
  
-   Utilisation du Gestionnaire de rapports lorsque Reporting Services est installé en mode natif.  
  
-   Utilisation du site SharePoint lorsque Reporting Services est installé en mode intégré SharePoint.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et affichage de l'aperçu des rapports.  
  
-   Connexion du Générateur de rapports à un serveur de rapports. Cela peut être un [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] ou une version autonome du Générateur de rapports.  
  
-   Utilisation du composant WebPart Visionneuse de rapports en mode distant.  
  
 Le code XML suivant affiche les éléments des deux extensions de rendu Word dans les fichiers de configuration RSReportServer et RSReportDesigner :  
  
 `<Extension Name="WORDOPENXML" Type="Microsoft.ReportingServices.Rendering.WordRenderer.WordOpenXmlRenderer.WordOpenXmlDocumentRenderer,Microsoft.ReportingServices.WordRendering"/>`  
  
 `<Extension Name="WORD" Type="Microsoft.ReportingServices.Rendering.WordRenderer.WordDocumentRenderer,Microsoft.ReportingServices.WordRendering" Visible="false"/>`  
  
 L'extension WORDOPENXML définit le convertisseur Word pour [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2007-2010. L'extension WORD définit la version [!INCLUDE[ofprword](../../includes/ofprword-md.md)] 2003. `Visible = “false”` indique que le convertisseur Word 2003 est masqué. Pour plus d’informations, consultez [fichier de Configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md) et [RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md).  
  
##  <a name="Differences"></a> Différences entre les convertisseurs Word et Word 2003  
 Les rapports rendus avec les convertisseurs Word ou Word 2003 peuvent être très facilement confondus. Toutefois, vous pouvez remarquer des différences mineures entre les deux formats Word ou Word 2003.  
  
##  <a name="DeviceInfo"></a> Paramètres d'informations de périphérique  
 Vous pouvez modifier certains paramètres par défaut de ce convertisseur, par exemple omettre les liens hypertexte et d'extraction ou développer tous les éléments pouvant être activés/désactivés quel que soit l'état d'origine de l'élément au moment du rendu, ce en modifiant les paramètres d'informations de périphérique. Pour plus d’informations, consultez [Word Device Information Settings](../word-device-information-settings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [Fonctionnalité interactive des différentes Extensions de rendu de rapport &#40;rapport Générateur et SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [Rendu des éléments de rapport &#40;Générateur de rapports et SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  