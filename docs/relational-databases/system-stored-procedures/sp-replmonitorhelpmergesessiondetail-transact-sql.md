---
title: sp_replmonitorhelpmergesessiondetail (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesessiondetail
- sp_replmonitorhelpmergesessiondetail_TSQL
helpviewer_keywords:
- sp_replmonitorhelpmergesessiondetail
ms.assetid: 805c92fc-3169-410c-984d-f37e063b791d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1cf931f96420dec953011c7c56c8a27285ae8fde
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752157"
---
# <a name="spreplmonitorhelpmergesessiondetail-transact-sql"></a>sp_replmonitorhelpmergesessiondetail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations détaillées de niveau article sur une session spécifique de l'Agent de fusion des réplications, qui permettent de surveiller la réplication des fusions. Le jeu de résultats comprend une ligne de détails pour chaque article synchronisé pendant la session. Il comprend également une ligne qui représente l'initialisation de la session et des lignes qui récapitulent les différentes phases de téléchargement (Upload et Download) de la session. Cette procédure stockée est exécutée sur la base de données de distribution du serveur de distribution ou sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replmonitorhelpmergesessiondetail [ @session_id = ] session_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@session_id** =] *session_id*  
 Spécifie une session d'agent. *session_id* est **int** sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**PhaseID**|**Int**|Phase de la session de synchronisation, qui peut prendre l'une des valeurs suivantes :<br /><br /> **0** = d’initialisation ou de la ligne de synthèse<br /><br /> **1** = téléchargement<br /><br /> **2** = téléchargement|  
|**ArticleName**|**sysname**|Nom de l'article en cours de synchronisation. **ArticleName** contient également des informations de résumé pour les lignes du jeu de résultats qui ne représentent pas les détails de l’article.|  
|**PercentComplete**|**decimal**|Indique le pourcentage de modifications appliqué dans une ligne de détails d'article donnée pour des sessions en cours d'exécution ou ayant échoué.|  
|**RelativeCost**|**decimal**|Indique le temps consacré à la synchronisation de l'article en pourcentage de la durée de synchronisation totale pour la session.|  
|**Duration**|**Int**|Durée de la session de l'Agent.|  
|**Inserts**|**Int**|Nombre d'insertions dans une session.|  
|**Mises à jour**|**Int**|Nombre de mises à jour dans une session.|  
|**Suppressions**|**Int**|Nombre de suppressions dans une session.|  
|**Conflits**|**Int**|Nombre de conflits qui se sont produits dans une session.|  
|**ID d’erreur**|**Int**|ID d'une erreur de session.|  
|**SeqNo**|**Int**|Ordre des sessions dans le jeu de résultats.|  
|**RowType**|**Int**|Indique le type d'informations que représente chaque ligne du jeu de résultats.<br /><br /> **0** = initialisation<br /><br /> **1** = résumé du téléchargement<br /><br /> **2** = détails de chargement de l’article<br /><br /> **3** = résumé du téléchargement<br /><br /> **4** = détails de téléchargement de l’article|  
|**Modifications de schéma**|**Int**|Nombre de modifications de schéma dans une session.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replmonitorhelpmergesessiondetail** est utilisé pour surveiller la réplication de fusion.  
  
 Lors de l’exécution sur l’abonné, **sp_replmonitorhelpmergesessiondetail** retourne uniquement des informations détaillées sur les 5 dernières sessions d’Agent de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **db_owner** ou **replmonitor** rôle de base de données fixe sur la base de données de distribution sur le serveur de distribution ou sur la base de données d’abonnement sur l’abonné peuvent exécuter **sp_ replmonitorhelpmergesessiondetail**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller la réplication par programmation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
