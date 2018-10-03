---
title: OLE DB pour OLAP Schema Rowsets | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd2e29e03617ccc3929ca0845e2b703e406cbfb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172969"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Ensembles de lignes de schéma OLE DB pour OLAP
  Le fournisseur XMLA ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis) prend en charge les ensembles de lignes de schéma OLE DB pour OLAP suivants.  
  
> [!NOTE]  
>  Pour vérifier si un fournisseur de source de données particulier prend en charge un ensemble de lignes, utilisez la `DISCOVER_ENUMERATIONS` ensemble de lignes avec le [Discover](../../xmla/xml-elements-methods-discover.md) (méthode).  
  
 Vous trouverez également des informations détaillées sur ces ensembles de lignes en recherchant la rubrique « OLAP Schema Rowsets » dans MSDN Library à cela [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Ensemble de lignes de schéma<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[DISCOVER_INSTANCES, ensemble de lignes](discover-instances-rowset.md)|Décrit les instances sur le serveur.|  
|[Ensemble de lignes DISCOVER_KEYWORDS &#40;OLE DB pour OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|Énumère une liste de mots réservés par le fournisseur.|  
|[MDSCHEMA_ACTIONS, ensemble de lignes](mdschema-actions-rowset.md)|Décrit les actions qui peuvent être disponibles pour les applications clientes.|  
|[MDSCHEMA_CUBES, ensemble de lignes](mdschema-cubes-rowset.md)|Décrit la structure des cubes d'une base de données.|  
|[MDSCHEMA_DIMENSIONS, ensemble de lignes](mdschema-dimensions-rowset.md)|Décrit les dimensions partagées et privées dans une base de données.|  
|[MDSCHEMA_FUNCTIONS, ensemble de lignes](mdschema-functions-rowset.md)|Décrit les fonctions qui sont disponibles pour les applications clientes connectées à la base de données.|  
|[MDSCHEMA_HIERARCHIES, ensemble de lignes](mdschema-hierarchies-rowset.md)|Décrit chaque hiérarchie contenue dans une dimension particulière.|  
|[MDSCHEMA_INPUT_DATASOURCES, ensemble de lignes](mdschema-input-datasources-rowset.md)|Décrit les sources de données définies dans la base de données.|  
|[MDSCHEMA_KPIS, ensemble de lignes](mdschema-kpis-rowset.md)|Décrit les indicateurs de performance clés (KPI) dans une base de données.|  
|[MDSCHEMA_LEVELS, ensemble de lignes](mdschema-levels-rowset.md)|Décrit chaque niveau dans une hiérarchie particulière.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS, ensemble de lignes](mdschema-measuregroup-dimensions-rowset.md)|Énumère les dimensions des groupes de mesures.|  
|[MDSCHEMA_MEASUREGROUPS, ensemble de lignes](mdschema-measuregroups-rowset.md)|Décrit les groupes de mesures d'une base de données.|  
|[MDSCHEMA_MEASURES, ensemble de lignes](mdschema-measures-rowset.md)|Décrit chaque mesure dans un cube.|  
|[MDSCHEMA_MEMBERS, ensemble de lignes](mdschema-members-rowset.md)|Décrit les membres d'une base de données.|  
|[MDSCHEMA_PROPERTIES, ensemble de lignes](mdschema-properties-rowset.md)|Décrit les propriétés des membres au sein d’une base de données.|  
|[MDSCHEMA_SETS, ensemble de lignes](mdschema-sets-rowset.md)|Décrit les ensembles actuellement définis dans une base de données, y compris les ensembles de niveau session.|  
  
 <sup>1</sup> tous les ensembles de lignes schéma répertoriés ici sont pris en charge par le fournisseur de source de données MSOLAP pour le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] fournisseur XMLA.  
  
## <a name="see-also"></a>Voir aussi  
 [Ensemble de lignes DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md)   
 [Ensembles de lignes de schéma Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
