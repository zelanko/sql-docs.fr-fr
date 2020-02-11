---
title: MSreplmonthresholdmetrics (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3e8b9c2443a6fa74e113dc1a3f25880ac753dc0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079943"
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La table **MSreplmonthresholdmetrics** définit les métriques fournies pour la surveillance de la réplication. Cette table est stockée dans la base de données **msdb** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Identifie une mesure de performance de réplication, et peut avoir l'une des valeurs ci-dessous.<br /><br /> **1** = expiration<br /><br /> **2** = latence<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergeslowrunspeed|  
|**bonhomme**|**sysname**|Nom de la mesure de performance de réplication|  
|**warningbitstatus**|**int**|Identificateur au niveau du bit utilisé pour générer un avertissement de violation de seuil pour l'une des mesures suivantes :<br /><br /> **1** = expiration : un abonnement à une publication transactionnelle a dépassé la période de rétention au-delà du seuil autorisé, en pourcentage de la période de rétention.<br /><br /> **2** = latence : le temps nécessaire à la réplication des données d’un serveur de publication transactionnel vers l’abonné dépasse le seuil, en secondes.<br /><br /> **4** = mergeexpiration : un abonnement à une publication de fusion a dépassé la période de rétention au-delà du seuil autorisé, en pourcentage de la période de rétention.<br /><br /> **8** = mergefastrunduration-le temps nécessaire pour effectuer la synchronisation d’un abonnement de fusion dépasse le seuil, en secondes, sur une connexion réseau rapide.<br /><br /> **16** = mergeslowrunduration-le temps nécessaire pour effectuer la synchronisation d’un abonnement de fusion dépasse le seuil, en secondes, sur une connexion réseau lente ou d’accès à distance.<br /><br /> **32** = mergefastrunspeed-la vitesse de transmission des lignes pendant la synchronisation d’un abonnement de fusion n’a pas réussi à maintenir le taux de seuil, en lignes par seconde, sur une connexion réseau rapide.<br /><br /> **64** = mergeslowrunspeed-la vitesse de transmission des lignes pendant la synchronisation d’un abonnement de fusion n’a pas réussi à maintenir le taux de seuil, en lignes par seconde, sur une connexion réseau lente ou d’accès à distance.|  
|**alertmessageid**|**int**|ID du message d'erreur qui s'affiche lorsque la condition générant un avertissement de seuil se produit.|  
|**description**|**nvarchar (3000)**|Description de la mesure de performance de réplication|  
|**default_value**|**sql_variant**|Valeur par défaut pour la mesure de performance de réplication|  
|**min_value**|**sql_variant**|Valeur minimale pour une mesure de performance de réplication limitée|  
|**max_value**|**sql_variant**|Valeur maximale pour une mesure de performance de la réplication limitée|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
