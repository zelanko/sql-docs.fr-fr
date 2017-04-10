---
title: "Fonctionnalit&#233;s Analysis Services prises en charge par les &#233;ditions de SQL Server 2016 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
  - "analysis-services/multidimensional-tabular"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f09d7be1-bd63-43f8-b91c-bf19166b4457
caps.latest.revision: 4
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 3
---
# Fonctionnalit&#233;s Analysis Services prises en charge par les &#233;ditions de SQL Server 2016
Cette rubrique fournit des détails sur les fonctionnalités prises en charge par les différentes éditions de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 La version d’évaluation de SQL Server est disponible pendant une période d’évaluation de 180 jours.  
  
 Pour obtenir les dernières notes de publication, voir [SQL Server 2016 Release Notes](../sql-server/sql-server-2016-release-notes.md). Pour plus d’informations sur les nouveautés, consultez [Nouveautés d’Analysis Services](../analysis-services/what-s-new-in-analysis-services.md).
    
 **Essayez SQL Server 2016 !**    
    
 > [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[ Télécharger SQL Server 2016 à partir du Centre d’évaluation](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Petite machine virtuelle Azure](../analysis-services/media/azure-virtual-machine-small.png) **[Faites tourner une machine virtuelle sur laquelle SQL Server 2016 est déjà installé](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    
    
  
 Pour les fonctionnalités prises en charge par les éditions Evaluation Edition et Developer Edition, consultez SQL Server Enterprise Edition.
  
 Pour accéder au tableau d’une technologie SQL Server, cliquez sur son lien : 
 
 -  [Analysis Services](#SSAS)  
  
-   [Modèle sémantique BI (multidimensionnel)](#BIMD)  
  
-   [Modèle sémantique BI (tabulaire)](#BIT)  
  
-   [Power Pivot pour SharePoint](#PPSP)  
  
-   [Exploration de données](#DM)  
  
-   [Clients Business Intelligence](#BIC)  

##  <a name="SSAS"></a> Analysis Services  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Bases de données partagées évolutives|Oui||||||Oui|  
|Sauvegarder/Restaurer et Attacher/Détacher des bases de données|Oui|Oui|||||Oui|  
|Synchroniser des bases de données|Oui||||||Oui|  
|Instances de cluster de basculement Always On|Oui<br /><br /> Le nombre de nœuds correspond au maximum du système d’exploitation|Oui<br /><br /> Prise en charge de 2 nœuds|||||Oui<br /><br /> Le nombre de nœuds correspond au maximum du système d’exploitation|  
|Programmabilité (AMO, ADOMD.Net, OLEDB, XML/A, ASSL, TMSL)|Oui|Oui|||||Oui|  
  
##  <a name="BIMD"></a> Modèle sémantique BI (multidimensionnel)  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Mesures semi-additives|Oui|Non <sup>1</sup>|||||Oui|  
|Hierarchies|Oui|Oui|||||Oui|  
|Indicateurs de performance clés|Oui|Oui|||||Oui|  
|Perspectives|Oui||||||Oui|  
|Actions|Oui|Oui|||||Oui|  
|Intelligence comptable|Oui|Oui|||||Oui|  
|Time Intelligence|Oui|Oui|||||Oui|  
|Cumuls personnalisés|Oui|Oui|||||Oui|  
|Cube d'écriture différée|Oui|Oui|||||Oui|  
|Dimensions d'écriture différée|Oui||||||Oui|  
|Cellules d'écriture différée|Oui|Oui|||||Oui|  
|Extraction|Oui|Oui|||||Oui|  
|Types de hiérarchies avancés (parent-enfant et irrégulières)|Oui|Oui|||||Oui|  
|Dimensions avancées (dimensions de référence, plusieurs-à-plusieurs)|Oui|Oui|||||Oui|  
|Dimensions et mesures liées|Oui|Oui  <sup>2</sup> |||||Oui|  
|Translations|Oui|Oui|||||Oui|  
|Aggregations|Oui|Oui|||||Oui|  
|Partitions multiples|Oui|Oui, jusqu'à 3|||||Oui|  
|Mise en cache proactive|Oui||||||Oui|  
|Assemblys personnalisés (procédures stockées)|Oui|Oui|||||Oui|  
|Requêtes et scripts MDX|Oui|Oui|||||Oui|  
|Requêtes DAX|Oui|Oui|||||Oui|  
|Modèle de sécurité basé sur les rôles|Oui|Oui|||||Oui|  
|Sécurité au niveau de la dimension et de la cellule|Oui|Oui|||||Oui|  
|Stockage évolutif de chaîne|Oui|Oui|||||Oui|  
|Modèles de stockage MOLAP, ROLAP et HOLAP|Oui|Oui|||||Oui|  
|Transport XML binaire et compressé|Oui|Oui|||||Oui|  
|Traitement de type envoi de données (push)|Oui||||||Oui|  
|Écriture différée directe|Oui||||||Oui|  
|Expressions de mesure|Oui||||||Oui|  
  
 <sup>1</sup> La mesure semi-additive LastChild est prise en charge dans l’édition Standard, contrairement à d’autres mesures semi-additives, telles que None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren et ByAccount. Les mesures additives, telles que Sum, Count, Min, Max, et les mesures non additives (DistinctCount) sont prises en charge dans toutes les éditions.  
  <sup>2</sup> L’édition Standard prend en charge la liaison des mesures et des dimensions dans la même base de données, mais pas à partir d’autres bases de données ou instances.
   
##  <a name="BIT"></a> Modèle sémantique BI (tabulaire)  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Hierarchies|Oui|Oui|||||Oui|  
|Indicateurs de performance clés|Oui|Oui|||||Oui|  
|Perspectives|Oui||||||Oui|  
|Translations|Oui|Oui|||||Oui|  
|Calculs DAX, requêtes DAX, requêtes MDX|Oui|Oui|||||Oui|  
|Sécurité au niveau des lignes|Oui|Oui|||||Oui|  
|Partitions multiples|Oui||||||Oui|  
|Mode de stockage en mémoire|Oui|Oui|||||Oui|  
|Mode de stockage DirectQuery|Oui||||||Oui|  
  
##  <a name="PPSP"></a> Power Pivot pour SharePoint  
  
|Fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Intégration de batterie de serveurs SharePoint selon l'architecture de service partagé|Oui||||||Oui|  
|Création de rapports d'utilisation|Oui||||||Oui|  
|Règles de contrôle d'intégrité|Oui||||||Oui|  
|Galerie Power Pivot|Oui||||||Oui|  
|Actualisation des données Power Pivot|Oui||||||Oui|  
|Flux de données Power Pivot|Oui||||||Oui|  
  
##  <a name="DM"></a> Exploration de données  
  
|Nom de la fonctionnalité|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Algorithmes standard|Oui|Oui|||||Oui|  
|Outils d’exploration de données (Assistants, éditeurs, générateurs de requêtes)|Oui|Oui|||||Oui|  
|Validation croisée|Oui||||||Oui|  
|Modèles sur les sous-ensembles filtrés de données de structure d'exploration de données|Oui||||||Oui|  
|Série chronologique : fusion personnalisée entre les méthodes ARTXP et ARIMA|Oui||||||Oui|  
|Série chronologique : prédiction avec les nouvelles données|Oui||||||Oui|  
|Requêtes d’exploration de données simultanées illimitées|Oui||||||Oui|  
|Configuration avancée et options de paramétrage pour les algorithmes d’exploration de données|Oui||||||Oui|  
|Prise en charge des algorithmes de plug-in|Oui||||||Oui|  
|Traitement de modèle parallèle|Oui||||||Oui|  
|Série chronologique : prédiction inter-série|Oui||||||Oui|  
|Attributs illimités pour les règles d'association|Oui||||||Oui|  
|Prédiction de séquence|Oui||||||Oui|  
|Plusieurs cibles de prédiction pour naïve Bayes, réseau neuronal et régression logistique|Oui||||||Oui|  
  
##  <a name="BIC"></a> Clients Business Intelligence  
 Les applications logicielles clientes suivantes sont disponibles dans le Centre de téléchargement Microsoft ; elles ont pour but de vous aider à créer des documents décisionnels qui s’exécutent sur une instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Lorsque vous hébergez ces documents dans un environnement serveur, utilisez une édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui prend en charge ce type de document. Le tableau suivant identifie quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient les fonctionnalités de serveur obligatoires pour héberger les documents créés dans ces applications clientes.  
  
|Nom de l’outil|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Développeur|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Compléments d’exploration de données pour Excel et Visio 2010 (.xlsx, .vsdx)|Oui|Oui|||||Oui|  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010 et 2013 (.xlsx)|Oui||||||Oui|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] (.xlsx)|Oui||||||Oui|  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] est un complément Excel permettant de créer des classeurs avec un modèle de données.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] ne dépend pas de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], mais [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] est requis pour le partage et la collaboration sur des classeurs Excel avec un modèle de données dans SharePoint. Cette fonctionnalité est disponible dans le cadre de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition.  
>   
>      Dans Excel 2016, la fonctionnalité Power Pivot est intégrée, donc vous n’avez plus besoin du complément Power Pivot.  
> 2.  Le tableau ci-dessus identifie les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] requises pour activer ces outils clients ; toutefois, ces outils peuvent accéder aux données hébergées sur n’importe quelle édition de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 ## Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
 [Spécifications de produit pour SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [Installation de SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)  

