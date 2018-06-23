---
title: Ensemble de lignes MDSCHEMA_SETS | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_SETS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: edc33b87256fb680225eaaa087ff655be1b82851
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154291"
---
# <a name="mdschemasets-rowset"></a>Ensemble de lignes MDSCHEMA_SETS
  Décrit les ensembles actuellement définis dans une base de données, y compris les ensembles de niveau session.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_SETS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom de la base de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Nom du cube.|  
|`SET_NAME`|`DBTYPE_WSTR`||Nom de l'ensemble, tel que spécifié dans l'instruction `CREATE SET`.|  
|`SCOPE`|`DBTYPE_I4`||Étendue de l'ensemble :<br /><br /> -   `MDSET_SCOPE_GLOBAL` (`1`)<br />-   `MDSET_SCOPE_SESSION` (`2`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Non pris en charge.|  
|`EXPRESSION`|`DBTYPE_WSTR`||Expression pour l'ensemble.|  
|`DIMENSIONS`|`DBTYPE_WSTR`||Liste des hiérarchies incluses dans l'ensemble, délimitée par des virgules.|  
|`SET_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée à l'ensemble. L'étiquette ou la légende est utilisée principalement à des fins d'affichage.|  
|`SET_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Chaîne qui identifie le chemin d'accès du dossier d'affichage que l'application cliente utilise pour afficher le jeu. Le séparateur de niveau de dossier est défini par l'application cliente. Pour les outils et les clients fournis par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barre oblique inverse (\\) est le séparateur de niveau. Pour fournir plusieurs dossiers d’affichage, utilisez un point-virgule ( ;) pour séparer les dossiers.|  
|`SET_EVALUATION_CONTEXT`|`DBTYPE_I4`||Contexte de l'ensemble. L'ensemble peut être statique ou dynamique.<br /><br /> Les valeurs possibles pour cette colonne sont les suivantes :<br /><br /> -MDSET_RESOLUTION_STATIC = 1<br />-MDSET_RESOLUTION_DYNAMIC = 2|  
  
 L'ensemble de lignes est trié selon `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_SETS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SET_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCOPE`|`DBTYPE_I4`|Facultatif.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|Facultatif. **Remarque :** qu’une seule hiérarchie peut être incluse, et seuls les jeux nommés dont les hiérarchies correspondent exactement à la restriction sont retournés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  