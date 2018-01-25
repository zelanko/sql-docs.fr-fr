---
title: "GROUPE de disponibilité (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_AVAILABILITY_GROUP_TSQL
- DROP AVAILABILITY GROUP
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], Transact-SQL statements
- DROP AVAILABILITY GROUP statement
- Availability Groups [SQL Server], dropping
ms.assetid: c1600289-c990-454a-b279-dba0ebd5d63e
caps.latest.revision: "44"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 82fdb4b104a0be0aa0d6469ccdd23f361f55618b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="drop-availability-group-transact-sql"></a>DROP AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Supprime le groupe de disponibilité spécifié et tous ses réplicas. Si une instance de serveur qui héberge l'un des réplicas de disponibilité est hors connexion lorsque vous supprimez un groupe de disponibilité, une fois de nouveau en ligne, l'instance de serveur supprimera le réplica de disponibilité local. La suppression d'un groupe de disponibilité supprime également l'écouteur du groupe de disponibilité associé, le cas échéant.  
  
> [!IMPORTANT]  
>  si cela est possible, supprimez le groupe de disponibilité uniquement lorsque vous êtes connecté à l'instance de serveur qui héberge le réplica principal. Si le groupe de disponibilité est supprimé du réplica principal, les modifications sont autorisées dans les bases de données primaires précédentes (sans protection haute disponibilité). Suppression d’un groupe de disponibilité à partir d’un réplica secondaire conserve le réplica principal dans le **restauration** état, ainsi que les modifications ne sont pas autorisées sur les bases de données.  
  
 Pour plus d’informations sur les autres méthodes de suppression d’un groupe de disponibilité, consultez [supprimer un groupe de disponibilité &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP AVAILABILITY GROUP group_name   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *group_name*  
 Spécifie le nom du groupe de disponibilité à supprimer.  
  
## <a name="limitations-and-recommendations"></a>Recommandations et limitations  
  
-   L’exécution de **DROP AVAILABILITY GROUP** requiert que la fonctionnalité groupes de disponibilité AlwaysOn est activée sur l’instance de serveur. Pour plus d’informations, consultez [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   **SUPPRIMER un groupe de disponibilité** ne peut pas être exécutée dans le cadre de traitements ou dans des transactions. En outre, les expressions et les variables ne sont pas prises en charge.  
  
-   Vous pouvez supprimer un groupe de disponibilité de tout nœud de clustering de basculement Windows Server (WSFC) qui possède les informations d'identification de sécurité correctes pour le groupe de disponibilité. Cela vous permet de supprimer un groupe de disponibilité lorsqu'il ne reste aucun de ses réplicas de disponibilité.  
  
    > [!IMPORTANT]  
    >  Évitez de supprimer un groupe de disponibilité lorsque le cluster de clustering de basculement Windows Server (WSFC) n'a aucun quorum. Si vous devez supprimer un groupe de disponibilité lorsque le cluster ne dispose pas de quorum, les métadonnées du groupe de disponibilité stockées dans le cluster nesont pas supprimées. Après que le cluster a regagné le quorum, vous devez supprimer à nouveau le groupe de disponibilité pour le supprimer du cluster WSFC.  
  
-   Sur un réplica secondaire, **DROP AVAILABILITY GROUP** doit uniquement être utilisé uniquement en cas d’urgence. Cela est dû au fait que la suppression d'un groupe de disponibilité met le groupe de disponibilité hors connexion. Si vous supprimez le groupe de disponibilité d’un réplica secondaire, le réplica principal ne peut pas déterminer si le **hors connexion** état s’est produite en raison d’une perte de quorum, un basculement forcé, ou un **DROP AVAILABILITY GROUP** commande. Le réplica principal joue le **restauration** état pour éviter un fractionnement possible. Pour plus d’informations, consultez [Fonctionnement : comportements de DROP AVAILABILITY GROUP](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (blog des ingénieurs du Service clientèle et du Support technique de SQL Server).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert **ALTER AVAILABILITY GROUP** l’autorisation sur le groupe de disponibilité, **CONTROL AVAILABILITY GROUP** autorisation, **ALTER ANY AVAILABILITY GROUP** autorisation, ou **CONTROL SERVER** autorisation. Pour supprimer un groupe de disponibilité qui n’est pas hébergé par l’instance de serveur local que vous avez besoin de **CONTROL SERVER** autorisation ou **contrôle** sur ce groupe de disponibilité.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime le `AccountsAG` groupe de disponibilité.  
  
```  
DROP AVAILABILITY GROUP AccountsAG;  
```  
  
##  <a name="RelatedContent"></a> Contenu connexe  
  
-   [Fonctionnement : comportements de DROP AVAILABILITY GROUP](http://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (blog des ingénieurs du Service clientèle et du Support technique de SQL Server)  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Supprimer un groupe de disponibilité &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md)  
  
  
