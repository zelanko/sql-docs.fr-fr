---
title: Ensemble de lignes DBSCHEMA_CATALOGS | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DBSCHEMA_CATALOGS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DBSCHEMA_CATALOGS rowset
ms.assetid: f02dc75d-5442-4eea-b33a-567dc816be7a
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0632d90765112ee54de8e78a66fdefa1ff27334f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbschemacatalogs-rowset"></a>Ensemble de lignes DBSCHEMA_CATALOGS
  Identifie les attributs physiques associés aux catalogues accessibles à partir du système de gestion de base de données (SGBD).  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DBSCHEMA_CATALOGS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|255|Nom du catalogue. Ne peut pas avoir la valeur null.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description de la table à l'intention des utilisateurs.|  
|**RÔLES**|**DBTYPE_WSTR**||Liste séparée par des virgules des rôles auxquels l'utilisateur actuel appartient.<br /><br /> Un astérisque (\*) est inclus en tant que rôle si l’utilisateur actuel est un serveur ou un administrateur de base de données.<br /><br /> **Username** est ajouté à **ROLES** si l'un des rôles utilise la sécurité dynamique.|  
|**DATE_DE_MODIFICATION**|**DBTYPE_DBTIMESTAMP**||Date de la dernière modification du catalogue.|  
  
 L'ensemble de lignes est trié selon **CATALOG_NAME**.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DBSCHEMA_CATALOGS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB](../../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)  
  
  
