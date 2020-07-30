---
title: sys. security_predicates (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SYS.SECURITY_PREDICATES
- SECURITY_PREDICATES
- SECURITY_PREDICATES_TSQL
- SYS.SECURITY_PREDICATES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.security_predicates catalog view
- security_predicates catalog view
ms.assetid: c7a2f28c-98da-463d-8b8a-8e5619e2c6a6
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80ca5a060d464562b9b97d2931082af98f3df785
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395230"
---
# <a name="syssecurity_predicates-transact-sql"></a>sys. security_predicates (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Retourne une ligne pour chaque prédicat de sécurité de la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID de la stratégie de sécurité qui contient ce prédicat.|  
|security_predicate_id|**int**|ID de prédicat dans cette stratégie de sécurité.|  
|target_object_id|**int**|ID de l'objet sur lequel le prédicat de la sécurité est lié.|  
|predicate_definition|**nvarchar(max)**|Nom qualifié complet de la fonction qui sera utilisée comme prédicat de sécurité, y compris les arguments. Notez que le nom `schema.function` peut être normalisé (autrement dit, placé dans une séquence d'échappement), ainsi que tout autre élément dans le texte à des fins de cohérence. Par exemple :<br /><br /> `[dbo].[fn_securitypredicate]([wing], [startTime], [endTime])`|  
|predicate_type|**int**|Type de prédicat utilisé par la stratégie de sécurité :<br /><br /> 0 = PRÉDICAT DE FILTRE<br /><br /> 1 = PRÉDICAT DE BLOC|  
|predicate_type_desc|**nvarchar(60)**|Type de prédicat utilisé par la stratégie de sécurité :<br /><br /> FILTER<br /><br /> BLOQUER|  
|opération|**int**|Type d’opération spécifié pour le prédicat :<br /><br /> NULL = toutes les opérations applicables<br /><br /> 1 = APRÈS INSERTION<br /><br /> 2 = APRÈS LA MISE À JOUR<br /><br /> 3 = AVANT MISE À JOUR<br /><br /> 4 = AVANT SUPPRESSION|  
|operation_desc|**nvarchar(60)**|Type d’opération spécifié pour le prédicat :<br /><br /> NULL<br /><br /> APRÈS INSERTION<br /><br /> AFTER UPDATE<br /><br /> AVANT MISE À JOUR<br /><br /> AVANT SUPPRESSION|  
  
## <a name="permissions"></a>Autorisations  
 Les principaux avec l’autorisation **modifier une stratégie de sécurité** ont accès à tous les objets de cet affichage catalogue, ainsi qu’à toute personne avec la **définition de vue** sur l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité au niveau des lignes](../../relational-databases/security/row-level-security.md)   
 [sys.security_policies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [CREATE SECURITY POLICY &#40;Transact-SQL&#41;](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
