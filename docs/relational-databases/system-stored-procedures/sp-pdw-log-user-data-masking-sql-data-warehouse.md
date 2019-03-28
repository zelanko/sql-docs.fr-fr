---
title: sp_pdw_log_user_data_masking (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 43c63b42-03cb-4fb5-8362-ec3b7e22a590
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: a24007abad9148a02da3542587967ae9dcc63f16
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535650"
---
# <a name="sppdwloguserdatamasking-sql-data-warehouse"></a>sp_pdw_log_user_data_masking (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Utilisez **sp_pdw_log_user_data_masking** à des données des utilisateurs de masquage dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité. Le masquage des données utilisateur affecte les instructions sur toutes les bases de données sur l’appliance.  
  
> [!IMPORTANT]  
>  Le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité faisant l’objet **sp_pdw_log_user_data_masking** êtes certain [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité. **sp_pdw_log_user_data_masking** n’affecte pas les journaux de transaction de base de données, ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les journaux d’erreurs.  
  
 **Arrière-plan :** Dans la configuration par défaut [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] contiennent des journaux d’activité complète [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions et peut dans certains cas incluent les données utilisateur contenues dans les opérations telles que **insérer**, **mise à jour**, et **Sélectionnez** instructions. En cas de problème sur l’appliance, cela permet l’analyse des conditions qui a provoqué le problème sans avoir à reproduire le problème. Afin d’éviter les données utilisateur en cours d’écriture [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité, les clients peuvent choisir d’activer sur le masquage des données utilisateur à l’aide de cette procédure stockée. Les instructions sont toujours écrits dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité, mais tous les littéraux dans les instructions qui contiennent des données utilisateur seront masqués ; remplacé avec des valeurs de constante prédéfinies.  
  
 Lorsque le chiffrement transparent des données est activé sur l’appliance, masquage des données utilisateur dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité est automatiquement activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_log_user_data_masking [ [ @masking_mode = ] value ] ;  
```  
  
#### <a name="parameters"></a>Paramètres  
`[ @masking_mode = ] masking_mode` Détermine si les données d’utilisateur du journal de chiffrement transparent des données de masquage sont activées. *masking_mode* est **int**, et peut prendre l’une des valeurs suivantes :  
  
-   0 = désactivé, l’utilisateur les données apparaissent dans le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité.  
  
-   1 = activé, l’utilisateur les instructions données apparaissent dans le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité, mais les données utilisateur est masquée.  
  
-   2 = les instructions contenant des données utilisateur ne sont pas écrites dans le [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité.  
  
 L’exécution de **sp_pdw_ log_user_data_masking** sans paramètres retourne l’état actuel de masquage des données TDE journal utilisateur sur l’appliance comme un jeu de résultats scalaires.  
  
## <a name="remarks"></a>Notes  
 Les données utilisateur de masquage dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] permettre le remplacement de littéraux des journaux d’activité avec des valeurs de constantes prédéfinies dans **sélectionnez** et des instructions DML, car elles peuvent contenir des données utilisateur. Paramètre *masking_mode* à 1 ne masque pas de métadonnées, telles que les noms de colonne ou table. Paramètre *masking_mode* 2 supprime les instructions avec des métadonnées, telles que les noms de colonne ou table.  
  
 Les données utilisateur de masquage dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité est implémenté de la façon suivante :  
  
-   Chiffrement transparent des données et les données utilisateur de masquage dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité sont désactivés par défaut. Les instructions ne seront pas automatiquement masquées si le chiffrement de base de données n’est pas activé sur l’appliance.  
  
-   Activation de TDE sur l’appliance automatiquement active sur le masquage des données utilisateur dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité.  
  
-   La désactivation du chiffrement transparent des données n’affecte pas les données utilisateur de masquage dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité.  
  
-   Vous pouvez activer explicitement dans de masquage des données utilisateur [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] journaux d’activité à l’aide de la **sp_pdw_log_user_data_masking** procédure.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’appartenance dans le **sysadmin** rôle de base de données fixe ou **CONTROL SERVER** autorisation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant active le chiffrement transparent des données journal utilisateur masquage des données sur l’appliance.  
  
```  
EXEC sp_pdw_log_user_data_masking 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_pdw_database_encryption pour &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)   
 [sp_pdw_database_encryption_regenerate_system_keys &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
  
