---
title: Ensemble de lignes DBSCHEMA_CATALOGS | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0180ba3bc28335246cdd5b85cff9b60e5044dd21
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="dbschemacatalogs-rowset"></a>Ensemble de lignes DBSCHEMA_CATALOGS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
  
