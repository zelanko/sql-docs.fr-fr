---
title: Ensemble de lignes MDSCHEMA_KPIS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDSCHEMA_KPIS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_KPIS rowset
ms.assetid: 40fb5112-6a90-4455-82b3-8b6322490222
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 77f6dc3fd3f8e9c92fe1d840c9af646269e0effc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124459"
---
# <a name="mdschemakpis-rowset"></a>Ensemble de lignes MDSCHEMA_KPIS
  Décrit les indicateurs de performance clés (KPI) dans une base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_KPIS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Base de données source.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Cube parent de l'indicateur de performance clé.|  
|`MEASUREGROUP_NAME`|`DBTYPE_WSTR`||Groupe de mesures associé pour l'indicateur de performance clé.<br /><br /> Vous pouvez utiliser cette colonne pour déterminer la dimensionnalité de l'indicateur de performance clé. Si «**\<NULL >**», l’indicateur de performance clé sera dimensionné par tous les groupes de mesures.<br /><br /> La valeur par défaut est «**\<NULL >**».|  
|`KPI_NAME`|`DBTYPE_WSTR`||Nom de l'indicateur de performance clé.|  
|`KPI_CAPTION`|`DBTYPE_WSTR`||Étiquette ou légende associée à l'indicateur de performance clé. Principalement utilisée à des fins d'affichage. Si une légende n’existe pas, `KPI_NAME` est retournée.|  
|`KPI_DESCRIPTION`|`DBTYPE_WSTR`||Description explicite de l'indicateur de performance clé.|  
|`KPI_DISPLAY_FOLDER`|`DBTYPE_WSTR`||Chaîne qui identifie le chemin d'accès du dossier d'affichage que l'application cliente utilise pour afficher le membre. Le séparateur de niveau de dossier est défini par l'application cliente. Pour les outils et les clients fournis par [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], la barre oblique inverse (\\) est le séparateur de niveau. Pour fournir plusieurs dossiers d’affichage, utilisez un point-virgule ( ;) pour séparer les dossiers.|  
|`KPI_VALUE`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de mesures pour la valeur de l'indicateur de performance clé.|  
|`KPI_GOAL`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de mesures pour l'objectif de l'indicateur de performance clé.<br /><br /> Retourne `NULL` si l'objectif n'est pas défini.|  
|`KPI_STATUS`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de mesures pour l'état de l'indicateur de performance clé.<br /><br /> Retourne `NULL` si l'état n'est pas défini.|  
|`KPI_TREND`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de mesures pour la tendance de l'indicateur de performance clé.<br /><br /> Retourne `NULL` si la tendance n'est pas définie.|  
|`KPI_STATUS_GRAPHIC`|`DBTYPE_WSTR`||Représentation graphique par défaut de l'indicateur de performance clé.|  
|`KPI_TREND_GRAPHIC`|`DBTYPE_WSTR`||Représentation graphique par défaut de l'indicateur de performance clé.|  
|`KPI_WEIGHT`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de mesures pour le poids de l'indicateur de performance clé.|  
|`KPI_CURRENT_TIME_MEMBER`|`DBTYPE_WSTR`||Nom unique du membre dans la dimension de temps qui définit le contexte temporel de l'indicateur de performance clé.<br /><br /> Retourne `NULL` si aucun membre de temps n'est défini.|  
|`KPI_PARENT_KPI_NAME`|`DBTYPE_WSTR`||Nom de l'indicateur de performance clé parent.|  
|`SCOPE`|`DBTYPE_I4`||Étendue de l'indicateur de performance clé. L'indicateur de performance clé peut être un indicateur de performance clé de session ou un indicateur de performance clé global.<br /><br /> Les valeurs possibles pour cette colonne sont les suivantes :<br /><br /> -MDKPI_SCOPE_GLOBAL = 1<br />-MDKPI_SCOPE_SESSION = 2|  
|`ANNOTATIONS`|`DBTYPE_WSTR`||(Facultatif) Jeu de notes, au format XML.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_KPIS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`KPI_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Facultatif) Bitmap avec l'une des valeurs valides suivantes :<br /><br /> -   `1` CUBE<br />-   `2` DIMENSION<br /><br /> La restriction par défaut est la valeur `1`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  
