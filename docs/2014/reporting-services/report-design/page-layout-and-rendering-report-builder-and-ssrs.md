---
title: Mise en page et rendu (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e2358653-35bc-4496-810a-d3ccf02f229f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df28762c61f548b47c4da4a31fe1d1fd42fbf65a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105509"
---
# <a name="page-layout-and-rendering-report-builder-and-ssrs"></a>Mise en page et rendu (Générateur de rapports et SSRS)
  Lorsque vous créez des rapports, il est important de comprendre le comportement des convertisseurs [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] afin de garantir que le rapport rendu aura l'apparence souhaitée, notamment en termes de mise en page et de sauts de page. Vous souhaiterez probablement aussi vous assurer que le rapport rendu sera ajusté au format de papier utilisé couramment dans votre organisation.  
  
 Lorsque vous affichez des rapports dans le Gestionnaire de rapports ou dans le volet de visualisation du Générateur de rapports ou du Concepteur de rapports, le rapport est tout d'abord restitué par le convertisseur HTML. Vous pouvez ensuite exporter le rapport vers différents formats tels qu'Excel ou un fichier séparé par des virgules (CSV). Le rapport exporté peut alors être utilisé pour une analyse supplémentaire dans Excel ou comme source de données pour des applications prenant en charge l'importation et l'utilisation de fichiers de données CSV.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclut un ensemble de convertisseurs pour exporter des rapports dans différents formats. Chaque convertisseur applique des règles lors du rendu des rapports. Lorsque vous exportez un rapport vers un format de fichier différent, particulièrement dans le cas de convertisseurs tels que le convertisseur PDF d'Adobe Acrobat, qui effectue la pagination en fonction de la taille de la page physique, vous devrez peut-être modifier la mise en page du rapport pour que le rapport exporté ait l'apparence souhaitée et s'imprime correctement une fois les règles de rendu appliquées.  
  
 Pour obtenir les meilleurs résultats pour un rapport exporté, vous devez fréquemment employer un processus itératif dans lequel vous créez et affichez un aperçu du rapport dans le Générateur de rapports ou le Concepteur de rapports, puis exportez le rapport vers le format par défaut, examinez le rapport exporté, et enfin vous lui apportez les modifications souhaitées.  
  
 Cette rubrique présente des informations sur les extensions de rendu Reporting Services et explique comment les utiliser.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="PageLayout"></a>Mise en page et éléments de rapport  
 Les éléments de rapport sont des éléments de disposition associés à différents types de données de rapport. Les éléments Table, Matrice, Liste, Graphique et Jauge sont des éléments de rapport de région de données, chacun d'eux établissant un lien vers un dataset de rapport. Lorsque le rapport est traité, la région de données s'étend sur la page du rapport (transversalement et vers le bas) pour afficher des données. D'autres éléments de rapport établissent un lien vers un seul élément et l'affichent. Un élément de rapport **Image** établit un lien vers une image. Un élément de rapport **Zone de texte** contient soit du texte simple comme un titre, soit une expression qui peut inclure des références à des champs prédéfinis, des paramètres de rapport ou des champs de dataset. Les éléments de rapport **Ligne** et **Rectangle** fournissent des éléments graphiques simples sur la page de rapport. L'élément **Rectangle** peut aussi être un conteneur pour d'autres éléments de rapport. Un rapport peut contenir des sous-rapports.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]vous permet de placer les éléments de rapport n'importe où sur l'aire de conception. Vous pouvez positionner, agrandir et réduire de manière interactive la forme initiale de l'élément de rapport à l'aide de lignes d'alignement et de poignées de redimensionnement. Vous pouvez placer les régions de données avec différents jeux de données, ou même des données identiques dans différents formats, côte à côte. Lorsque vous placez un élément de rapport sur l'aire de conception, il a une taille et une forme par défaut, ainsi qu'une relation initiale par rapport à tous les autres éléments de rapport. Vous pouvez placer de nombreux éléments de rapport pour créer des conceptions de rapport plus complexes. Par exemple, des graphiques ou des images dans les cellules de table, les tables dans les cellules de table et plusieurs images dans un rectangle. Outre l'organisation et l'apparence que vous souhaitez obtenir dans le rapport, le placement des éléments de rapport dans des conteneurs tels que des rectangles permet de contrôler la façon dont les éléments de rapport sont affichés dans la page du rapport.  
  
 Un rapport peut s'étendre sur plusieurs pages et comporter un en-tête et un pied de page répétés sur chaque page. Il peut contenir des éléments graphiques comme des images et des lignes et avoir plusieurs polices, couleurs et styles, qui peuvent se baser sur des expressions.  
  
##  <a name="ReportSections"></a> Sections de rapport  
 Un rapport se compose de trois principales sections : un en-tête de page facultatif, un pied de page facultatif et un corps de rapport. L'en-tête et le pied de page du rapport ne sont pas vraiment des sections à part du rapport ; ils se composent des éléments de rapport placés en haut et en bas du corps du rapport. L'en-tête et le pied de page répètent le même contenu en haut et en bas de chaque page du rapport. Vous pouvez placer des images, des zones de texte et des lignes dans les en-têtes et les pieds de page. Vous pouvez placer tous les types d'élément de rapport dans le corps du rapport.  
  
 Vous pouvez définir des propriétés sur les éléments de rapport pour les masquer ou les afficher initialement sur la page. Vous pouvez définir des propriétés de visibilité sur les lignes, colonnes ou groupes pour les régions de données et fournir des boutons bascule pour permettre à l'utilisateur d'afficher ou de masquer de façon interactive les données de rapport. Vous pouvez définir la visibilité ou la visibilité initiale à l'aide d'expressions, notamment des expressions basées sur les paramètres de rapport.  
  
 Lorsqu'un rapport est traité, ses données sont associées aux éléments de disposition du rapport et les données combinées sont envoyées à un convertisseur de rapport. Le convertisseur respecte des règles prédéfinies pour l'expansion des éléments de rapport et détermine la quantité de données tenant sur chaque page. Pour concevoir un rapport facile à lire et optimisé pour le convertisseur que vous prévoyez d'utiliser, vous devez comprendre les règles utilisées pour contrôler la pagination dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour plus d’informations, voir [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).  
  
##  <a name="RenderingExtensions"></a> Convertisseurs  
 Reporting Services inclut un jeu de convertisseurs, également connu sous le nom d'extensions de rendu, que vous pouvez utiliser pour exporter des rapports vers des formats différents. Il existe trois types de convertisseurs :  
  
-   **Convertisseurs de données** Les convertisseurs de données suppriment du rapport toute la mise en forme et les informations relatives à la disposition et affichent uniquement les données. Le fichier résultant peut être utilisé pour importer les données de rapport brutes dans un autre type de fichier, tel qu'Excel, une autre base de données, un message de données XML ou une application personnalisée. Les convertisseurs de données disponibles sont : CSV et XML.  
  
    > [!NOTE]  
    >  Bien qu'il ne permette l'exportation directe vers un autre format, l'outil de rendu Atom génère des fichiers de données à partir de rapports.  
  
-   **Convertisseurs de saut de page conditionnelle** Les convertisseurs de saut de page conditionnelle conservent la disposition et la mise en forme du rapport. Le fichier résultant est optimisé pour l'affichage à l'écran et la remise, par exemple sur une page Web. Les convertisseurs de saut de page conditionnelle disponibles sont les suivants : [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word, archive Web (MHTML) et HTML.  
  
-   **Convertisseurs de saut de page manuel** Les convertisseurs de saut de page manuel conservent la disposition et la mise en forme du rapport. Le fichier résultant est optimisé pour une impression cohérente ou pour l'affichage en ligne du rapport dans un format de livre. Les convertisseurs de saut de page manuel suivants sont pris en charge : TIFF et PDF.  
  
 Lorsque vous affichez un aperçu de rapport dans le Générateur de rapports ou le Concepteur de rapports ou que vous exécutez un rapport dans le Gestionnaire de rapports, le rapport est toujours rendu en premier au format HTML. Après avoir exécuté le rapport, vous pouvez l'exporter vers différents formats de fichiers. Pour plus d’informations, consultez [exportation de rapports &#40;générateur de rapports et&#41;SSRS ](../report-builder/export-reports-report-builder-and-ssrs.md).  
  
  
  
##  <a name="RenderingBehaviors"></a> Comportements de rendu  
 Selon le convertisseur sélectionné, certaines règles sont appliquées lors du rendu du rapport. La combinaison de ces facteurs détermine la façon dont les éléments du rapport s'ajustent sur la page :  
  
-   les règles de rendu ;  
  
-   la largeur et la hauteur des éléments de rapport ;  
  
-   la taille du corps du rapport ;  
  
-   la largeur et la hauteur de la page ;  
  
-   la prise en charge de la pagination spécifique au convertisseur.  
  
 Par exemple, les rapports rendus dans les formats HTML et MHTML sont optimisés pour un affichage sur un écran d'ordinateur sur lequel les pages peuvent avoir différentes longueurs.  
  
 Pour plus d’informations, consultez [Comportements de rendu &#40;Générateur de rapports et SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).  
  
  
  
##  <a name="Pagination"></a> Pagination  
 La pagination fait référence au nombre de pages au sein d'un rapport et à la façon dont les éléments d'un rapport sont réorganisés sur ces pages. La pagination dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dépend de l'extension de rendu que vous utilisez pour afficher et remettre le rapport et des options de saut de page et d'ajustement configurées pour le rapport.  
  
 Pour concevoir avec succès un rapport facile à lire par vos utilisateurs et qui est optimisé pour le convertisseur que vous prévoyez d’utiliser pour remettre votre rapport, vous devez comprendre les règles utilisées pour contrôler la pagination dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Les rapports exportés à l'aide des extensions de rendu des données et de saut de page conditionnelle ne sont en général pas affectés par la pagination. Lorsque vous utilisez une extension de rendu des données, le rapport est restitué comme ensemble de lignes disposé en table au format XML ou CSV. Pour assurer que les données du rapport exporté sont utilisables, vous devez comprendre les règles appliquées pour effectuer le rendu d'un ensemble de lignes aplati disposé en table dans un rapport.  
  
 Lorsque vous utilisez une extension de rendu de saut de page conditionnelle telle que l'extension de rendu HTML, vous souhaiterez peut-être savoir quelle est l'apparence du rapport imprimé et également comment il est restitué par un convertisseur de saut de page manuel tel que PDF. Pendant la création ou la mise à jour d'un rapport, vous pouvez afficher l'aperçu du rapport et l'exporter dans le Générateur de rapports ou le Concepteur de rapports.  
  
 Les convertisseurs de saut de page manuel ont le plus d'impact sur la mise en page du rapport et la taille de la page physique. Pour en savoir plus, consultez [Pagination dans Reporting Services &#40;Générateur de rapports et SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md).  
  
  
  
##  <a name="HowTo"></a> Rubriques de procédures  
 Cette section répertorie les procédures qui vous indiquent pas à pas comment utiliser la pagination dans les rapports.  
  
-   [Ajouter un saut de page &#40;Générateur de rapports et SSRS&#41;](add-a-page-break-report-builder-and-ssrs.md)  
  
-   [Afficher des en-têtes de ligne et de colonne sur plusieurs pages &#40;Générateur de rapports et SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)  
  
-   [Ajouter ou supprimer un en-tête ou un pied de page &#40;Générateur de rapports et SSRS&#41;](add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md)  
  
-   [Laisser les en-têtes visibles lors du défilement d’un rapport &#40;Générateur de rapports et SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
-   [Afficher les numéros de page ou d’autres propriétés de rapport &#40;Générateur de rapports et SSRS&#41;](display-page-numbers-or-other-report-properties-report-builder-and-ssrs.md)  
  
-   [Masquer un en-tête ou un pied de page sur la première ou la dernière page &#40;Générateur de rapports et SSRS&#41;](hide-a-page-header-or-footer-on-the-first-or-last-page-report-builder-and-ssrs.md)  
  
  
  
##  <a name="InThisSection"></a> Dans cette section  
 Les rubriques suivantes fournissent des informations supplémentaires sur la mise en page et le rendu des rapports.  
  
 [En-têtes et pieds de page &#40;Générateur de rapports et SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)  
 Présente des informations sur l'utilisation des en-têtes et des pieds de page dans les rapports et sur le contrôle de la pagination à l'aide de ces éléments.  
  
 [Contrôle des sauts de page, des en-têtes, des colonnes et des lignes &#40;Générateur de rapports et SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md)  
 Présente des informations sur l'utilisation de sauts de page.  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités interactives des différentes extensions de rendu de rapport &#40;Générateur de rapports et SSRS&#41;](../report-builder/interactive-functionality-different-report-rendering-extensions.md)   
 [Exportation de rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
