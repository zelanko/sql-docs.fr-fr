---
title: GET_TRANSMISSION_STATUS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STATUS_TSQL
- TRANSMISSION
- TRANSMISSION_TSQL
- GET_TRANSMISSION_STATUS
- STATUS
- GET_TRANSMISSION_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], transmission status
- Service Broker errors, transmission status
- transmission status information
- status information [SQL Server], conversations
- GET_TRANSMISSION_STATUS statement
ms.assetid: 621805d5-49ed-4764-b3cb-2ae4a3bf797e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bf05f923a5a7a6333bdca7278efae918aed71f32
ms.sourcegitcommit: 3de1fb410de2515e5a00a5dbf6dd442d888713ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2019
ms.locfileid: "70211419"
---
# <a name="get_transmission_status-transact-sql"></a>GET_TRANSMISSION_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Retourne l'état de la dernière transmission pour un côté d'une conversation.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GET_TRANSMISSION_STATUS ( conversation_handle )  
```  
  
## <a name="arguments"></a>Arguments  
 *conversation_id*  
 Description du descripteur de conversation pour la conversation. Ce paramètre est de type **uniqueidentifier**.  
  
## <a name="return-types"></a>Types de retour  
 **nchar**  
  
## <a name="remarks"></a>Notes   
 Retourne une chaîne décrivant l'état de la dernière tentative de transmission pour la conversation spécifiée. Retourne une chaîne vide en cas de réussite de la dernière tentative de transmission, si aucune tentative de transmission n’a encore été effectuée ou si *conversation_handle* n’existe pas.  
  
 Les informations retournées par cette fonction sont les mêmes que celles affichées dans la colonne last_transmission_error de la vue de gestion sys.transmission_queue. Il est toutefois possible d'utiliser cette fonction pour trouver l'état de transmission des conversations qui n'ont pas de messages dans la file d'attente de transmission.  
  
> [!NOTE]  
>  GET_TRANSMISSION_STATUS ne fournit pas d'informations pour les messages qui n'ont pas de point de terminaison dans l'instance active. C'est-à-dire qu'aucune information n'est disponible pour les messages à transmettre.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique l'état de transmission pour la conversation dotée du descripteur de conversation `58ef1d2d-c405-42eb-a762-23ff320bddf0`.  
  
```  
SELECT Status =  
    GET_TRANSMISSION_STATUS('58ef1d2d-c405-42eb-a762-23ff320bddf0') ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
 ```
 Status  
 ------------------------------- 
 The Service Broker protocol transport is disabled or not configured.
 ```  
  
 Dans ce cas, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas configuré pour permettre à [!INCLUDE[ssSB](../../includes/sssb-md.md)] de communiquer sur le réseau.  
  
## <a name="see-also"></a> Voir aussi  
 [sys.conversation_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)   
 [sys.transmission_queue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  
