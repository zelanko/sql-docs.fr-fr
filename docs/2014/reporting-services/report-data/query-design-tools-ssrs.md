---
title: Interroger des outils de conception dans le rapport concepteur SQL Server Data Tools (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- graphical query designer [Reporting Services]
- MDX query designer [Reporting Services]
- text-based query designer [Reporting Services]
- DMX [Reporting Services]
- query designers [Reporting Services]
- generic query designer See text-based query designer
- Reporting Services, query designers
- semantic queries [Reporting Services]
- Report Model Query Designer
ms.assetid: a8139a9d-4aeb-4e64-96f3-564edf60479f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: fa4be367b9f04fb8d96bb228b7d040aae0e120d5
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56041260"
---
# <a name="query-design-tools-in-report-designer-sql-server-data-tools-ssrs"></a>Outils de conception de requête dans les outils de données SQL Server du Concepteur de rapports (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fournit différents outils de conception de requêtes que vous pouvez utiliser pour créer des requêtes de dataset dans le Concepteur de rapports. Le type de source de données utilisé détermine la disponibilité d'un concepteur de requêtes particulier. En outre, certains Concepteurs de requêtes offrent d'autres modes afin que vous puissiez choisir s'il convient de travailler en mode visuel ou directement dans le langage de requête. Cette rubrique présente chaque outil et décrit le type de source de données que chacun prend en charge. Les outils suivants sont décrits dans cette rubrique :  
  
-   [Concepteur de requêtes textuel](#Textbased)  
  
-   [Concepteur de requêtes graphique](#Graphical)  
  
-   [Concepteur de requêtes Modèle de rapport](#Model)  
  
-   [Concepteur de requêtes MDX](#MDX)  
  
-   [Concepteur de requêtes DMX](#DMX)  
  
-   [Concepteur de requêtes SAP NetWeaver BI](#SAPBW)  
  
-   [Concepteur de requêtes Hyperion Essbase](#Hyperion)  
  
 Tous les outils de conception de requêtes fonctionnent dans l’environnement de conception de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] quand vous travaillez avec un modèle de projet de Report Server ou de l’Assistant Projet Report Server. Pour plus d’informations sur l’utilisation des concepteurs de requêtes, consultez [Concepteurs de requêtes Reporting Services](../reporting-services-query-designers.md).  
  
##  <a name="Textbased"></a> Concepteur de requêtes textuel  
 Le concepteur de requêtes textuel est l’outil de génération de requêtes adopté par défaut pour la plupart des sources de données relationnelles prises en charge, notamment [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], Oracle, Teradata, OLE DB, XML et ODBC. Contrairement au concepteur de requêtes graphique, cet outil de conception de requêtes ne valide pas la syntaxe des requêtes lors de leur conception. L'image suivante présente le concepteur de requêtes textuel.  
  
 ![Concepteur de requêtes générique pour les requêtes de données relationnelles](../../analysis-services/media/rsqd-dsaw-sql-generic.gif "Concepteur de requêtes générique pour les requêtes de données relationnelles")  
  
 Le concepteur de requêtes textuel est recommandé pour la création de requêtes complexes, à l'aide de procédures stockées, d'interrogation de données XML et d'écriture de requêtes dynamiques. Selon la source de données, vous pouvez peut-être cliquer sur le bouton **Modifier en tant que texte** dans la barre d’outils pour basculer entre le concepteur de requêtes graphique et le concepteur de requêtes textuel. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes textuel](../text-based-query-designer-user-interface.md).  
  
##  <a name="Graphical"></a> Concepteur de requêtes graphique  
 Le concepteur de requêtes graphique permet de créer ou de modifier des requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] qui s’exécutent sur une base de données relationnelle. Cet outil de conception de requêtes est utilisé dans plusieurs produits [!INCLUDE[msCoName](../../../includes/msconame-md.md)] et dans d'autres composants de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Selon le type de source de données, il prend en charge les modes Text, StoredProcedure et TableDirect. L'image suivante présente le concepteur de requêtes graphique.  
  
 ![Concepteur de requêtes graphique pour requêtes SQL](../media/rsqd-dsaw-sql.gif "Concepteur de requêtes graphique pour requêtes SQL")  
  
 Vous pouvez cliquer sur le bouton **Modifier en tant que texte** dans la barre d’outils pour basculer entre le concepteur de requêtes graphique et le concepteur de requêtes textuel. Pour plus d’informations, consultez [Interface utilisateur du concepteur de requêtes graphique](graphical-query-designer-user-interface.md).  
  
##  <a name="Model"></a> Concepteur de requêtes Modèle de rapport  
 Le concepteur de requêtes Modèle de rapport sert à créer ou à modifier des requêtes qui s'exécutent dans un modèle de rapport SMDL publié sur un serveur de rapports. Les rapports qui s'exécutent sur des modèles prennent en charge l'exploration de données consultables à l'aide de clics. La requête détermine le chemin de l'exploration des données au moment de l'exécution. L'image suivante présente le concepteur de requêtes Modèle de rapport.  
  
 ![Interface utilisateur du Concepteur de requêtes SMDL](../media/rsqd-dsawmodel-smql.gif "Interface utilisateur du Concepteur de requêtes SMDL")  
  
 Pour utiliser le concepteur de requêtes Modèle de rapport, vous devez définir une source de données qui pointe vers un modèle publié. Lorsque vous définissez un dataset pour la source de données, vous pouvez ouvrir la requête de dataset dans le concepteur de requêtes Modèle de rapport. Le concepteur de requêtes Modèle de rapport peut être utilisé en mode graphique ou textuel. Vous pouvez cliquer sur le bouton **Modifier en tant que texte** dans la barre d’outils pour basculer entre le concepteur de requêtes graphique et le concepteur de requêtes textuel. Pour plus d’informations, consultez [Interface utilisateur du concepteur de requêtes de modèle de rapport](report-model-query-designer-user-interface.md).  
  
##  <a name="MDX"></a> Concepteur de requêtes MDX  
 Le concepteur de requêtes MDX (Multidimensional Expression) permet de créer ou de modifier des requêtes exécutées sur une source de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] avec des cubes multidimensionnels. L'image suivante présente le concepteur de requêtes MDX après définition de la requête et du filtre.  
  
 ![Concepteur de requêtes MDX Analysis Services, mode Création](../../analysis-services/media/rsqd-dsawas-mdx-designmode.gif "Concepteur de requêtes MDX Analysis Services, mode Création")  
  
 Pour utiliser le concepteur de requêtes MDX, vous devez définir une source de données possédant un cube Analysis Services disponible, valide et traité. Lorsque vous définissez un dataset pour la source de données, vous pouvez ouvrir la requête dans le concepteur de requêtes MDX. Si nécessaire, utilisez les boutons MDX et DMX sur la barre d'outils pour commuter entre les modes MDX et DMX. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes MDX Analysis Services](analysis-services-mdx-query-designer-user-interface.md).  
  
##  <a name="DMX"></a> Concepteur de requêtes DMX  
 Le concepteur de requêtes DMX (Data Mining Prediction Expression) permet de créer ou de modifier des requêtes exécutées sur une source de données [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] avec des modèles d'exploration de données. L'image suivante présente le concepteur de requêtes DMX après sélection du modèle et des tables d'entrée.  
  
 ![Concepteur de requêtes DMX Analysis Services, mode Création](../media/rsqd-dsawas-dmx-designmode.gif "Concepteur de requêtes DMX Analysis Services, mode Création")  
  
 Pour utiliser le concepteur de requêtes DMX, vous devez définir une source de données possédant un modèle d'exploration de données disponible et valide. Lorsque vous définissez un dataset pour la source de données, vous pouvez ouvrir la requête dans le concepteur de requêtes DMX. Si nécessaire, utilisez les boutons MDX et DMX sur la barre d'outils pour commuter entre les modes MDX et DMX. Après la sélection du modèle, vous pouvez créer des requêtes de prédiction d'exploration de données qui fournissent des données à un rapport. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes DMX Analysis Services](analysis-services-dmx-query-designer-user-interface.md).  
  
##  <a name="SAPBW"></a> Concepteur de requêtes SAP NetWeaver BI  
 Le concepteur de requêtes [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] permet de récupérer des données d’une base de données [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] . Pour utiliser ce concepteur de requêtes, vous devez avoir une source de données [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] possédant au moins une requête InfoCube, MultiProvider ou web définie. L'image suivante présente le concepteur de requêtes [!INCLUDE[SAP_DPE_BW_1](../../../includes/sap-dpe-bw-1-md.md)] .  
  
 ![Concepteur de requêtes avec MDX en mode Création](../media/rsqd-dssapbw-mdx-designmode.gif "Concepteur de requêtes avec MDX en mode Création")  
  
##  <a name="Hyperion"></a> Concepteur de requêtes Hyperion Essbase  
 Le concepteur de requêtes [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] permet de récupérer des données à partir de bases de données et d'applications [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] . L'image suivante présente le concepteur de requêtes [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] .  
  
 ![Concepteur de requêtes pour la source de données Hyperion Essbase](../media/rsqd-dshyperionessbase-mdx-designmode.gif "Concepteur de requêtes pour la source de données Hyperion Essbase")  
  
 Pour utiliser ce concepteur de requêtes, vous devez avoir une source de données [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] possédant au moins une base de données. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes SAP NetWeaver BI](sap-netweaver-bi-query-designer-user-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de Reporting Services](../tools/reporting-services-tools.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Didacticiels sur Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)   
 [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [Créer une source de données incorporée ou partagée &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)  
  
  
