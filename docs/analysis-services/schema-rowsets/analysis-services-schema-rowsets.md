---
title: "Analysis Services des ensembles de lignes de schéma | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d6e87251e1ab08a87929cd3dba78a584e7c62fd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-schema-rowsets"></a>Ensembles de lignes de schéma Analysis Services
  Les ensembles de lignes de schéma sont des tables prédéfinies qui contiennent des informations sur les objets et l'état du serveur Analysis Services, notamment les schémas de base de données, les sessions actives, les connexions, les commandes et les travaux qui s'exécutent sur le serveur. Vous pouvez interroger les tables d'ensembles de lignes de schéma dans une fenêtre de script XML/A dans SQL Server Management Studio, exécuter une requête DMV sur un ensemble de lignes de schéma, ou créer une application personnalisée qui incorpore les informations d'ensemble de lignes de schéma (par exemple, une application de création de rapport qui récupère la liste des dimensions disponibles pouvant être utilisées pour créer un rapport).  
  
> [!NOTE]  
>  Si vous utilisez des ensembles de lignes de schéma XML/a un script, les informations qui sont retournées dans le *résultat* paramètre de la [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) (méthode) est structurée selon les dispositions de colonne d’ensemble de lignes décrites dans cette section. Le fournisseur XMLA ([!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis) prend en charge les ensembles de lignes requis par la spécification XML for Analysis. Le fournisseur XMLA prend également en charge certains ensembles de lignes de schéma standard pour les fournisseurs de sources de données OLE DB, OLE DB pour OLAP et OLE DB pour l'exploration de données. Les ensembles de lignes pris en charge sont décrits dans les rubriques suivantes :  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique| Description|  
|-----------|-----------------|  
|[Ensembles de lignes de schéma XML for Analysis](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Décrit les ensembles de lignes XMLA pris en charge par le fournisseur XMLA.|  
|[Ensembles de lignes de schéma OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Décrit les ensembles de lignes de schéma OLE DB pris en charge par le fournisseur XMLA.|  
|[Ensembles de lignes de schéma OLE DB pour OLAP](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Décrit les ensembles de lignes de schéma OLE DB pour OLAP pris en charge par le fournisseur XMLA.|  
|[Ensembles de lignes de schéma d’exploration de données](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Décrit les ensembles de lignes de schéma pour l'exploration de données pris en charge par le fournisseur XMLA.|  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux données de modèle multidimensionnel &#40; Analysis Services - données multidimensionnelles &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Utiliser des vues de gestion dynamique &#40;DMV&#41; pour surveiller Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
