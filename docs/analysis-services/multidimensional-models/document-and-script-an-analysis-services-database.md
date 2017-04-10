---
title: "Documenter et g&#233;n&#233;rer des scripts pour une base de donn&#233;es Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML for Analysis, scripts"
  - "XMLA, scripts"
  - "scripts [Analysis Services], bases de données"
  - "documentation des bases de données"
  - "bases de données [Analysis Services], documentation"
  - "bases de données [Analysis Services], scripts"
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# Documenter et g&#233;n&#233;rer des scripts pour une base de donn&#233;es Analysis Services
  Après le déploiement d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour sortir les métadonnées de la base de données ou d’un objet contenu dans la base de données, comme un script XMLA (XML for Analysis). Vous pouvez sortir ce script dans une nouvelle fenêtre **Éditeur de requête XMLA**, dans un fichier ou dans le Presse-papiers. Pour plus d’informations, consultez [Référence Analysis Services Scripting Language &#40;ASSL&#41;](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md).  
  
 Le script XMLA généré utilise des éléments ASSL ([!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) pour définir les objets contenus dans le script. Si vous avez généré un script CREATE, le script XMLA obtenu contient une commande XMLA **CREATE** et des éléments ASSL qui peuvent être utilisés pour créer l’intégralité de la structure de la base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur une instance. Si vous avez généré un script ALTER, le script XMLA obtenu contient une commande XMLA **ALTER** et des éléments ASSL qui peuvent être utilisés pour restaurer la structure d’une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] existante dans l’état où la base de données se trouvait au moment de la génération du script.  
  
 Vous pouvez utiliser le script XMLA généré à partir d'une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de nombreuses manières, par exemple :  
  
-   pour maintenir un script de sauvegarde qui vous permet de recréer tous les objets et toutes les autorisations de la base de données ;  
  
-   pour créer ou mettre à jour le code de développement de la base de données ;  
  
-   pour créer un environnement de test ou de développement à partir d'un schéma existant.  
  
## Voir aussi  
 [Modifier ou supprimer une base de données Analysis Services](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Élément Alter &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Élément Create &#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  