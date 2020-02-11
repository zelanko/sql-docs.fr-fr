---
title: sp_get_distributor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
author: stevestein
ms.author: sstein
ms.openlocfilehash: 63916a86757877dc6ae601c798ba7a987256580c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124118"
---
# <a name="sp_get_distributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Détermine si un serveur de distribution est installé sur un serveur. Cette procédure stockée est exécutée sur n'importe quelle base de données de l'ordinateur sur lequel le serveur de distribution est recherché.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**installé**|**int**|**0** = non ; **1** = Oui|  
|**serveur de distribution**|**sysname**|Nom du serveur de distribution|  
|**base de distribution de distribution installée**|**int**|**0** = non ; **1** = Oui|  
|**is distribution publisher**|**int**|**0** = non ; **1** = Oui|  
|**a un serveur de publication de distribution distant**|**int**|**0** = non ; **1** = Oui|  
  
## <a name="remarks"></a>Notes  
 **sp_get_distributor** est principalement utilisé par le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans un instantané, une réplication transactionnelle et une réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 N’importe quel utilisateur peut exécuter **sp_get_distributor**. Un jeu de résultats non NULL est retourné lorsque cette procédure stockée est exécutée par les membres des rôles de base de données fixes **db_owner** ou **replmonitor** sur la base de données de distribution, ou les membres du rôle de base de données fixe **db_owner** sur au moins une base de données publiée. Un jeu de résultats non NULL est également retourné lorsque cette procédure stockée est exécutée par des utilisateurs dans la liste d’accès à la publication (PAL) d’au moins une base de données publiée, ou dans la liste d’accès aux publications de la base de données de distribution pour un serveur de publication non SQL Server, peut également exécuter **sp_get_distributor**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Script d’information du serveur de distribution et du serveur de publication](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
