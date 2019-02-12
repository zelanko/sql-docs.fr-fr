---
title: Planification d’un rapport (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- getting started
- report design
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c13019d5845e0c580b28fef750683044d344a9ab
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56017280"
---
# <a name="planning-a-report-report-builder"></a>Planification d'un rapport (Générateur de rapports)
  Le Générateur de rapports vous permet de créer de nombreux types de rapports. Par exemple, vous pouvez créer des rapports qui indiquent des données de ventes récapitulatives ou détaillées, des tendances de ventes et de marketing, ou bien des rapports opérationnels ou des tableaux de bord. Vous pouvez également créer des rapports qui tirent parti de texte enrichi, tels que des commandes clients, des catalogues de produits ou des lettres types. Tous ces rapports sont créés à l'aide de différentes combinaisons des mêmes blocs de construction dans le Générateur de rapports. Pour créer un rapport utile et facilement compréhensible, il est préférable de le planifier au préalable. Voici quelques éléments à prendre en considération avant de commencer :  
  
-   **Quel format souhaitez-vous affecter au rapport ?**  
  
     Vous pouvez restituer les rapports en ligne dans un navigateur tel que le Gestionnaire de rapports ou les exporter vers d'autres formats tels qu'Excel, Word ou PDF. La forme finale de votre rapport est un aspect important car toutes les fonctionnalités ne sont pas disponibles dans tous les formats d'exportation. Pour plus d’informations, consultez [exportation des rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md).  
  
-   **Quelle structure souhaitez-vous utiliser pour présenter les données dans le rapport ?**  
  
     Pour présenter vos données, vous avez le choix entre des structures tabulaires, matricielles (semblables à un rapport d’analyse croisée ou de tableau croisé dynamique), graphiques, de forme libre, ou toute combinaison de ces structures. Pour plus d’informations, consultez [répertorie &#40;Générateur de rapports et SSRS&#41; ](tables-matrices-and-lists-report-builder-and-ssrs.md) et [graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
-   **Quelle apparence souhaitez-vous donner à votre rapport ?**  
  
     Le Générateur de rapports fournit de nombreux éléments de rapports que vous pouvez ajouter à votre rapport afin d'en faciliter la lecture, de souligner des informations clés, d'aider les utilisateurs à parcourir le rapport, et ainsi de suite. Le fait de savoir quelle apparence vous souhaitez donner au rapport peut déterminer si vous devez utiliser des éléments de rapports tels que des zones de texte, des rectangles, des images ou des lignes. Vous souhaiterez peut-être également afficher ou masquer des éléments, ajouter un explorateur de documents, inclure des rapports ou des sous-rapports d'extraction, ou établir des liaisons vers d'autres rapports. Pour plus d’informations, consultez [Images, zones de texte, rectangles et lignes &#40;&Générateur de rapports et SSRS#41;](rectangles-and-lines-report-builder-and-ssrs.md) et [Tri interactif, Explorateurs de documents et liens &#40;Générateur de rapports et SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md).  
  
-   **Quelles données souhaitez-vous présenter aux utilisateurs ? Les données ou le format doivent-ils être filtrés pour différents publics ?**  
  
     Vous souhaiterez peut-être réduire l'étendue du rapport à des utilisateurs ou des emplacements spécifiques, ou à une période donnée. Pour filtrer les données du rapport, utilisez des paramètres permettant de récupérer et d'afficher uniquement les données souhaitées. Pour plus d'informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md).  
  
-   **Avez-vous besoin de créer vos propres calculs ?**  
  
     Parfois, votre source de données et vos datasets ne contiennent pas les champs exacts nécessaires pour votre rapport. Dans ce cas, il vous faudra peut-être créer vos propres champs calculés. Par exemple, vous souhaiterez peut-être multiplier le prix par unité par la quantité afin d'obtenir un montant des ventes par élément. Les expressions sont également utilisées pour fournir une mise en forme conditionnelle et d'autres fonctionnalités avancées. Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
-   **Voulez-vous masquer initialement des éléments de rapport ?**  
  
     Décidez si vous souhaitez masquer des éléments de rapport, y compris des régions de données, des groupes et des colonnes, lors de la première exécution du rapport. Vous pouvez par exemple présenter initialement un tableau récapitulatif, puis explorer les données plus en détail. Pour plus d’informations, consultez [Action d’exploration &#40;Générateur de rapports et SSRS&#41;](drilldown-action-report-builder-and-ssrs.md).  
  
-   **Comment allez-vous délivrer le rapport ?**  
  
     Vous pouvez enregistrer votre rapport sur votre ordinateur local et continuer à travailler dessus ou l'exécuter localement à des fins d'informations personnelles. Toutefois, pour partager votre rapport avec d'autres personnes, vous devez l'enregistrer sur un serveur de rapports configuré en mode natif, ou sur un serveur de rapports en mode intégré SharePoint. Le fait de l'enregistrer sur un serveur permet à d'autres personnes de l'exécuter lorsqu'elles le souhaitent. En guise d'alternative, l'administrateur du serveur de rapports peut configurer un abonnement au rapport ou la remise du rapport par messagerie électronique à d'autres utilisateurs. Vous pouvez faire remettre le rapport dans un format d'exportation spécifique si vous préférez. Pour plus d’informations, consultez [Recherche, affichage et gestion des rapports &#40;Générateur de rapports et SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de rapports dans SQL Server 2014](../report-builder/report-builder-in-sql-server-2016.md)   
 [Concepts de création de rapport &#40;Générateur de rapports et SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)  
  
  
