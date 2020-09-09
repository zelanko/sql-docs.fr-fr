---
description: sp_polybase_join_group (Transact-SQL)
title: sp_polybase_join_group | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 53db2ff3554c095832a6fa21accb061f2575c3d6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548381"
---
# <a name="sp_polybase_join_group-transact-sql"></a>sp_polybase_join_group (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Ajoute une instance de SQL Server en tant que nœud de calcul à un groupe Polybase pour le calcul avec montée en puissance parallèle.  
  
 La fonctionnalité  [Polybase](../../relational-databases/polybase/polybase-guide.md) doit être installée sur l’instance SQL Server.  Polybase permet l’intégration de sources de données non SQL Server, telles que Hadoop et le stockage d’objets BLOB Azure. Voir aussi [sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Arguments  
 * \@ head_node_address* = N «*head_node_address*»  
 Nom de l’ordinateur qui héberge le nœud principal SQL Server du groupe de scale-out Polybase. * \@ head_node_address* est de type nvarchar (255).  
  
 * \@ dms_control_channel_port* = dms_control_channel_port  
 Port sur lequel le canal de contrôle pour le nœud principal Mouvement de données PolyBase service est en cours d’exécution. * \@ dms_control_channel_port* est un __int16 non signé. La valeur par défaut est **16450**.  
  
 * \@ head_node_sql_server_instance_name* = head_node_sql_server_instance_name  
 Nom du nœud principal SQL Server instance dans le groupe de montée en puissance parallèle Polybase. * \@ head_node_sql_server_instance_name* est de type nvarchar (16).  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'autorisation CONTROL SERVER.  
  
## <a name="remarks"></a>Notes  
 Après l’exécution de la procédure stockée, arrêtez le moteur Polybase et redémarrez le service Mouvement de données PolyBase sur l’ordinateur. Pour vérifier l’exécution de la DMV suivante sur le nœud principal : **sys. dm_exec_compute_nodes**.  
  
## <a name="example"></a>Exemple  
 L’exemple joint l’ordinateur actuel en tant que nœud de calcul à un groupe Polybase.  Le nom du nœud principal est **HST01** et le nom de l’instance SQL Server sur le nœud principal est **MSSQLSERVER**.  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
