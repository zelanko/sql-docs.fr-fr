---
title: sp_pdw_remove_network_credentials (SQL Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: system-objects
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: c12696a2-5939-402b-9866-8a837ca4c0a3
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c44633ebcfb79b433a7420055343faf36774da39
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989281"
---
# <a name="sppdwremovenetworkcredentials-sql-data-warehouse"></a>sp_pdw_remove_network_credentials (SQL Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Cela supprime les informations d’identification réseau stockées dans [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] pour accéder à un partage de fichiers réseau. Par exemple, utiliser cette procédure stockée pour supprimer l’autorisation de [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] de sauvegarde et restauration sur un serveur qui se trouve dans votre propre réseau.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_pdw_remove_network_credentials 'target_server_name'  
```  
  
## <a name="arguments"></a>Arguments  
 '*target_server_name*'  
 Spécifie le nom d’hôte serveur cible ou l’adresse IP. Informations d’identification pour accéder à ce serveur seront retirées [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Cela ne pas modifier ou supprimer toutes les autorisations sur le serveur cible réelle qui est géré par votre propre équipe.  
  
 *nom_du_serveur_cible* est défini comme nvarchar(337).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Requiert **ALTER SERVER STATE** autorisation.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 Une erreur se produit si la suppression des informations d’identification ne réussit pas sur le nœud de contrôle et tous les nœuds de calcul.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Cette procédure stockée supprime les informations d’identification réseau à partir du compte NetworkService pour [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Le compte NetworkService s’exécute chaque instance de SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur le nœud de contrôle et les nœuds de calcul. Par exemple, quand une opération de sauvegarde s’exécute, le nœud de contrôle et de chaque nœud de calcul utilisera les informations d’identification du compte NetworkService pour accéder au serveur cible.  
  
## <a name="metadata"></a>Métadonnées  
 Pour répertorier toutes les informations d’identification et pour vérifier les informations d’identification ont été supprimées, utilisez [sys.dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
 Pour ajouter des informations d’identification, utilisez [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="a-remove-credentials-for-performing-a-database-backup"></a>A. Supprimer les informations d’identification pour effectuer une sauvegarde de base de données  
 L’exemple suivant supprime les références de nom et mot de passe utilisateur pour accéder au serveur cible qui a une adresse IP de 10.192.147.63.  
  
```  
EXEC sp_pdw_remove_network_credentials '10.192.147.63';  
```  
  
  

