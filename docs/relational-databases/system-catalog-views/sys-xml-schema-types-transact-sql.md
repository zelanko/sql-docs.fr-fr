---
title: Sys.xml_schema_types (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs: TSQL
helpviewer_keywords: sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bc42e2b600a276ad7dd3512b3aa2a20925c84016
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysxmlschematypes-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque composant de schéma XML qui est un Type, **symbol_space** de **T**.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**\<héritée de colonnes >**||Hérite des colonnes de [sys.xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**bit**|1 = Type est un type abstrait. Toutes les instances d’un élément de ce type doivent utiliser **xsi : type** pour indiquer un type dérivé n’est pas abstrait.<br /><br /> 0 = Type n'est pas un type abstrait. (par défaut)|  
|**allows_mixed_content**|**bit**|1 = Les contenus mixtes sont autorisés.<br /><br /> 0 = Les contenus mixtes ne sont pas autorisés. (par défaut)|  
|**is_extension_blocked**|**bit**|1 = remplacement par une extension du type est interdit dans les instances lorsque le bloc d’attributs sur le **complexType** définition ou la **blockDefault** attribut de l’ancêtre \<schéma > élément d’information est définie sur « extension » ou « #all ».<br /><br /> 0 = Le remplacement par l'extension n'est pas interdit.|  
|**is_restriction_blocked**|**bit**|1 = remplacement par une restriction du type est interdit dans les instances lorsque le bloc d’attributs sur le **complexType** définition ou la **blockDefault** attribut de l’ancêtre \<schéma > élément d’information est définie sur « restriction » ou « #all ».<br /><br /> 0 = Le remplacement par la restriction n'est pas interdit. (par défaut)|  
|**is_final_extension**|**bit**|1 = la dérivation par extension du type est interdite lorsque l’attribut final de la **complexType** définition ou la **finalDefault** attribut de l’ancêtre \<schéma > élément d’information est définie sur « extension » ou « #all ».<br /><br /> 0 = Extension autorisée. (par défaut)|  
|**is_final_restriction**|**bit**|1 = la dérivation par restriction du type est interdite lorsque l’attribut final de la simple ou **complexType** définition ou la **finalDefault** attribut de l’ancêtre \<schéma > élément d’information est définie sur « restriction » ou « #all ».<br /><br /> 0 = Restriction autorisée. (par défaut)|  
|**is_final_list_member**|**bit**|1 = Ce type simple ne peut pas être utilisé comme type d'élément dans une liste.<br /><br /> 0 = Ce type est complexe ou peut être utilisé pour les éléments d'une liste. (par défaut)|  
|**is_final_union_member**|**bit**|1 = Ce type simple ne peut pas être utilisé comme type de membre pour un type d'union.<br /><br /> 0 = Ce type est complexe ou peut être utilisé comme type de membre d'union. (par défaut)|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40; Système de Type XML &#41; Affichages catalogue &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
