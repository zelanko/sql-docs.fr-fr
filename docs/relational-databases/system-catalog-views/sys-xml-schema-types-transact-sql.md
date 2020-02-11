---
title: sys. xml_schema_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a78730509cc1f9eeec83b8d9ff9cb0917e0ed99
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060430"
---
# <a name="sysxml_schema_types-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par composant de schéma XML qui est un type, **symbol_space** de **T**.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**\<colonnes héritées>**||Hérite des colonnes de [sys. xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**bit**|1 = Type est un type abstrait. Toutes les instances d’un élément de ce type doivent utiliser **xsi : type** pour indiquer un type dérivé qui n’est pas abstrait.<br /><br /> 0 = Type n'est pas un type abstrait. (par défaut)|  
|**allows_mixed_content**|**bit**|1 = Les contenus mixtes sont autorisés.<br /><br /> 0 = Les contenus mixtes ne sont pas autorisés. (par défaut)|  
|**is_extension_blocked**|**bit**|1 = le remplacement par une extension du type est bloqué dans les instances lorsque l’attribut de bloc sur la définition de **complexType** ou l’attribut **BlockDefault** du schéma ancêtre \<> élément d’informations d’élément a la valeur « extension » ou « #all ».<br /><br /> 0 = Le remplacement par l'extension n'est pas interdit.|  
|**is_restriction_blocked**|**bit**|1 = le remplacement par une restriction du type est bloqué dans les instances lorsque l’attribut de bloc sur la définition de **complexType** ou l’attribut **BlockDefault** du schéma ancêtre \<> élément d’informations d’élément a la valeur « restriction » ou « #all ».<br /><br /> 0 = Le remplacement par la restriction n'est pas interdit. (par défaut)|  
|**is_final_extension**|**bit**|1 = la dérivation par extension du type est bloquée lorsque l’attribut final sur la définition de **complexType** ou l’attribut **finalDefault** du \<schéma ancêtre> élément d’informations d’élément a la valeur « extension » ou « #all ».<br /><br /> 0 = Extension autorisée. (par défaut)|  
|**is_final_restriction**|**bit**|1 = la dérivation par restriction du type est bloquée lorsque l’attribut final sur la définition simple ou **complexType** ou l’attribut **finalDefault** du schéma \<ancêtre> élément d’informations de l’élément a la valeur « restriction » ou « #all ».<br /><br /> 0 = Restriction autorisée. (par défaut)|  
|**is_final_list_member**|**bit**|1 = Ce type simple ne peut pas être utilisé comme type d'élément dans une liste.<br /><br /> 0 = Ce type est complexe ou peut être utilisé pour les éléments d'une liste. (par défaut)|  
|**is_final_union_member**|**bit**|1 = Ce type simple ne peut pas être utilisé comme type de membre pour un type d'union.<br /><br /> 0 = Ce type est complexe ou peut être utilisé comme type de membre d'union. (par défaut)|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Schémas XML &#40;les affichages catalogue du système de type XML&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
