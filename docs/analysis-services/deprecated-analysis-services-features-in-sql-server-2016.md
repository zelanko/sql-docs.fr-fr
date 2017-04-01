---
title: "Fonctionnalit&#233;s Analysis Services d&#233;conseill&#233;es dans SQL Server 2016 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Analysis Services, compatibilité descendante"
  - "SSAS, compatibilité descendante"
  - "SQL Server Analysis Services, compatibilité descendante"
  - "fonctionnalités déconseillées [Analysis Services]"
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 52
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 52
---
# Fonctionnalit&#233;s Analysis Services d&#233;conseill&#233;es dans SQL Server 2016
  Un *fonctionnalité déconseillée* est destinée à être supprimée dans une prochaine version, mais elle reste prise en charge et incluse dans la version actuelle à des fins de rétrocompatibilité. En règle générale, une fonctionnalité déconseillée est supprimée d’une version majeure, souvent des deux versions de l’annonce d’origine. Par exemple, les fonctionnalités déconseillées annoncées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] sont susceptibles de ne pas être prises en charge par [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 **Non prise en charge dans la prochaine version majeure de SQL Server**  
  
|||  
|-|-|  
|**Catégorie**|**Fonctionnalité**|  
|(Multidimensionnel)|Partitions distantes|  
|(Multidimensionnel)|Groupes de mesures liés distants|  
|(Multidimensionnel)|Écriture différée dimensionnelle|  
|(Multidimensionnel)|Dimensions liées|  
  
 **Non prise en charge dans une future version de SQL Server**  
  
|||  
|-|-|  
|**Catégorie**|**Fonctionnalité**|  
|(Multidimensionnel)|Notifications de table SQL Server pour la mise en cache proactive.  <br />La solution de remplacement consiste à utiliser l’interrogation pour la mise en cache proactive. <br />Consultez [Mise en cache proactive &#40;dimensions&#41;](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md) et [Mise en cache proactive &#40;partitions&#41;](../Topic/Proactive%20Caching%20\(Partitions\).md).|  
|(Multidimensionnel)|Cubes de session. Il n’existe aucune solution de remplacement.|  
|(Multidimensionnel)|Cubes locaux. Il n’existe aucune solution de remplacement.|  
|Tabulaire|Les niveaux de compatibilité 1100 et 1103 des modèles tabulaires ne seront pas pris en charge dans une future version. La solution consiste à mettre les modèles au niveau de compatibilité 1200, en convertissant les définitions de modèle en métadonnées tabulaires. Consultez [Compatibility Level for Tabular models in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).|  
|Outils|SQL Server Profiler pour la capture de traces<br /><br /> La solution consiste à utiliser le Générateur de profils d’événements étendus, intégré dans SQL Server Management Studio.  <br /> Consultez [Surveiller Analysis Services avec des événements étendus SQL Server](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md).|  
|Outils|Server Profiler pour Trace Replay <br />Remplacement. Il n’existe aucune solution de remplacement.|  
|Objets de gestion de trace et API de trace|Objets Microsoft.AnalysisServices.Trace (contenant les API des objets Analysis Services de trace et de relecture). La solution de remplacement est multiple :<br /><br /> -   Configuration de trace : Microsoft.SqlServer.Management.XEvent<br />-   Lecture de trace : Microsoft.SqlServer.XEvent.Linq<br />-   Relecture de trace : Aucune|  
  
> [!NOTE]  
>  Les fonctionnalités précédemment annoncées comme déconseillées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] restent en place. Le code prenant en charge ces fonctionnalités n’ayant pas encore été supprimé du produit, bon nombre de celles-ci sont toujours présentes dans cette version. Des fonctions précédemment déconseillées peuvent être accessibles, mais elles restent considérées comme déconseillées et peuvent, à ce titre, être physiquement retirées du produit à tout moment pendant la version [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Il est vivement recommandé de ne pas utiliser les fonctionnalités déconseillées dans les nouveaux modèles ou applications basés sur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## Voir aussi  
 [Compatibilité descendante Analysis Services](../analysis-services/analysis-services-backward-compatibility.md)   
 [Fonctionnalités Analysis Services interrompues dans SQL Server 2016](../analysis-services/discontinued-analysis-services-functionality-in-sql-server-2016.md)  
  
  