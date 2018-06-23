---
title: Ensemble de lignes MDSCHEMA_FUNCTIONS | Documents Microsoft
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
- MDSCHEMA_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 8e3086730ad66a0f21d9cc458d34d96a6d0eacc3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140620"
---
# <a name="mdschemafunctions-rowset"></a>Ensemble de lignes MDSCHEMA_FUNCTIONS
  Décrit les fonctions disponibles pour les applications clientes connectées à la base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **MDSCHEMA_FUNCTIONS** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|**NOM DE LA FONCTION**|**DBTYPE_WSTR**||Nom de la fonction.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Description de la fonction.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**||Liste séparée par des virgules de paramètres formatés en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic. Par exemple, un paramètre de nom peut avoir la forme d'une chaîne.|  
|**RETURN_TYPE**|**DBTYPE_I4**||Le **VARTYPE** du type de données de retour de la fonction.|  
|**ORIGINE**|**DBTYPE_I4**||Origine de la fonction :<br /><br /> -1 pour les fonctions MDX.<br />-2 pour les fonctions définies par l’utilisateur.|  
|**NOM_INTERFACE**|**DBTYPE_WSTR**||Nom de l'interface pour les fonctions définies par l'utilisateur.<br /><br /> Nom de groupe pour les fonctions MDX (Multidimensional Expressions).|  
|**NOM_LIBRAIRIE**|**DBTYPE_WSTR**||Nom de la bibliothèque de types pour les fonctions définies par l'utilisateur. **NULL** pour les fonctions MDX.|  
|**NOM_DLL**|**DBTYPE_WSTR**||(Facultatif) Nom de la classe dans l'assembly qui implémente la fonction définie par l'utilisateur.<br /><br /> Retourne **VT_NULL** pour les fonctions MDX.|  
|**HELP_FILE**|**DBTYPE_WSTR**||(Facultatif) Nom du fichier qui contient la documentation d'aide pour la fonction définie par l'utilisateur.<br /><br /> Retourne **VT_NULL** pour les fonctions MDX.|  
|**HELP_CONTEXT**|**DBTYPE_I4**||(Facultatif) Retourne l'ID du contexte d'aide pour cette fonction.|  
|**OBJECT**|**DBTYPE_WSTR**||(Facultatif) Nom générique de la classe de l'objet auquel s'applique une propriété. Par exemple, l’ensemble de lignes correspondant à l’élément < nom_niveau >. Membres de fonction retourne «**niveau**».<br /><br /> Retourne **VT_NULL** pour les fonctions définies par l’utilisateur, ou les fonctions MDX pas une propriété.|  
|**LÉGENDE**|**DBTYPE_WSTR**||Légende d'affichage pour la fonction.|  
  
 L’ensemble de lignes est trié sur **origine**, **nom_interface**, **nom_fonction**.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le **MDSCHEMA_FUNCTIONS** ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**NOM_LIBRAIRIE**|**DBTYPE_WSTR**|Facultatif.|  
|**NOM_INTERFACE**|**DBTYPE_WSTR**|Facultatif.|  
|**NOM DE LA FONCTION**|**DBTYPE_WSTR**|Facultatif.|  
|**ORIGINE**|**DBTYPE_I4**|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma OLE DB pour OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  