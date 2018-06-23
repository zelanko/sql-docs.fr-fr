---
title: Ensemble de lignes MDSCHEMA_INPUT_DATASOURCES | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_INPUT_DATASOURCES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_INPUT_DATASOURCES rowset
ms.assetid: 12482fd5-16e3-4171-9cb0-76d0d4f5308e
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ba789133cddb1d8b074a58e36ee2018359ae504e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143580"
---
# <a name="mdschemainputdatasources-rowset"></a>Ensemble de lignes MDSCHEMA_INPUT_DATASOURCES
  Décrit les sources de données définies dans la base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `MDSCHEMA_INPUT_DATASOURCES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||Nom du catalogue auquel appartient cette source de données.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||Non pris en charge.|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`||Nom de l'objet source de données.|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`||Type de la source de données. Les valeurs valides sont les suivantes :<br /><br /> -   `Relational`<br />-   `Olap`|  
|`CREATED_ON`|`DBTYPE_DBTIMESTAMP`||Date de création de la source de données.|  
|`LAST_SCHEMA_UPDATE`|`DBTYPE_DBTIMESTAMP`||Date et heure de la dernière modification de la source de données.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Description conviviale de l'action.|  
|`TIMEOUT`|`DBTYPE_UI4`||Délai d'expiration de la source de données.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `MDSCHEMA_INPUT_DATASOURCES` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DATASOURCE_NAME`|`DBTYPE_WSTR`|Facultatif.|  
|`DATASOURCE_TYPE`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  