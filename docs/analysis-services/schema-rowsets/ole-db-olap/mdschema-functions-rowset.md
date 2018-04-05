---
title: Ensemble de lignes MDSCHEMA_FUNCTIONS | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MDSCHEMA_FUNCTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_FUNCTIONS rowset
ms.assetid: 5253fa8c-b1ce-4504-aff6-a246b5e675c7
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e8a03e34bf6ea617e650132f2a81fb065a014d80
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdschemafunctions-rowset"></a>Ensemble de lignes MDSCHEMA_FUNCTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Décrit les fonctions disponibles pour les applications clientes connectées à la base de données.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **MDSCHEMA_FUNCTIONS** ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Description|  
|-----------------|--------------------|-----------------|  
|**NOM DE LA FONCTION**|**DBTYPE_WSTR**|Nom de la fonction.|  
|**DESCRIPTION**|**DBTYPE_WSTR**|Description de la fonction.|  
|**PARAMETER_LIST**|**DBTYPE_WSTR**|Liste séparée par des virgules de paramètres formatés en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic. Par exemple, un paramètre de nom peut avoir la forme d'une chaîne.|  
|**RETURN_TYPE**|**DBTYPE_I4**|Le **VARTYPE** du type de données de retour de la fonction.|  
|**ORIGINE**|**DBTYPE_I4**|Origine de la fonction :<br /><br /> 1 pour les fonctions MDX.<br /><br /> 2 pour les fonctions définies par l'utilisateur.|  
|**NOM_INTERFACE**|**DBTYPE_WSTR**|Nom de l'interface pour les fonctions définies par l'utilisateur.<br /><br /> Nom de groupe pour les fonctions MDX (Multidimensional Expressions).|  
|**NOM_LIBRAIRIE**|**DBTYPE_WSTR**|Nom de la bibliothèque de types pour les fonctions définies par l'utilisateur. **NULL** pour les fonctions MDX.|  
|**NOM_DLL**|**DBTYPE_WSTR**|(Facultatif) Nom de la classe dans l'assembly qui implémente la fonction définie par l'utilisateur.<br /><br /> Retourne **VT_NULL** pour les fonctions MDX.|  
|**HELP_FILE**|**DBTYPE_WSTR**|(Facultatif) Nom du fichier qui contient la documentation d'aide pour la fonction définie par l'utilisateur.<br /><br /> Retourne **VT_NULL** pour les fonctions MDX.|  
|**HELP_CONTEXT**|**DBTYPE_I4**|(Facultatif) Retourne l'ID du contexte d'aide pour cette fonction.|  
|**OBJET**|**DBTYPE_WSTR**|(Facultatif) Nom générique de la classe de l'objet auquel s'applique une propriété. Par exemple, l’ensemble de lignes correspondant à l’élément < nom_niveau >. Membres de fonction retourne «**niveau**».<br /><br /> Retourne **VT_NULL** pour les fonctions définies par l’utilisateur, ou les fonctions MDX pas une propriété.|  
|**LÉGENDE**|**DBTYPE_WSTR**|Légende d'affichage pour la fonction.|  
  
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
 [Ensembles de lignes de schéma OLE DB pour OLAP](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
