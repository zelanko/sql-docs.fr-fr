---
title: "MODIFIER la priorité de service BROKER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_BROKER_TSQL
- ALTER BROKER PRIORITY
- ALTER BROKER
- ALTER_BROKER_PRIORITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER BROKER PRIORITY statement
- ssbdiagnose
ms.assetid: 15fda1b2-e4dd-4f9d-935a-2e38926075b2
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ad652e17039cbb6a6936b074320096fd58a78d3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-broker-priority-transact-sql"></a>ALTER BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'une priorité de conversation [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER BROKER PRIORITY ConversationPriorityName  
FOR CONVERSATION  
{ SET ( [ CONTRACT_NAME = {ContractName | ANY } ]  
        [ [ , ] LOCAL_SERVICE_NAME = {LocalServiceName | ANY } ]  
        [ [ , ] REMOTE_SERVICE_NAME = {'RemoteServiceName' | ANY } ]  
        [ [ , ] PRIORITY_LEVEL = { PriorityValue | DEFAULT } ]  
              )  
}  
[;]  
  
```  
  
## <a name="arguments"></a>Arguments  
 *ConversationPriorityName*  
 Spécifie le nom de la priorité de conversation à modifier. Le nom doit faire référence à une priorité de conversation dans la base de données active.  
  
 SET  
 Spécifie les critères permettant de déterminer si la priorité de conversation s'applique à une conversation. SET est requis et doit contenir au moins un critère : CONTRACT_NAME, LOCAL_SERVICE_NAME, REMOTE_SERVICE_NAME ou PRIORITY_LEVEL.  
  
 CONTRACT_NAME = {*ContractName* | **ANY**}  
 Spécifie le nom d'un contrat à utiliser comme critère pour déterminer si la priorité de conversation s'applique à une conversation. *ContractName* est un [!INCLUDE[ssDE](../../includes/ssde-md.md)] identificateur et vous devez spécifier le nom d’un contrat de base de données active.  
  
 *ContractName*  
 Spécifie que la priorité de conversation peut être appliquée uniquement aux conversations où l’instruction BEGIN DIALOG qui démarre la conversation spécifie ON CONTRACT *ContractName*.  
  
 ANY  
 Indique que la priorité de conversation peut être appliquée à n'importe quelle conversation, quel que soit le contrat qu'elle utilise.  
  
 Si CONTRACT_NAME n'est pas spécifié, la propriété de contrat de la priorité de conversation n'est pas modifiée.  
  
 LOCAL_SERVICE_NAME = {*LocalServiceName* | **ANY**}  
 Spécifie le nom d'un service à utiliser comme critère pour déterminer si la priorité de conversation s'applique à un point de terminaison.  
  
 *LocalServiceName* est un [!INCLUDE[ssDE](../../includes/ssde-md.md)] identificateur et vous devez spécifier le nom d’un service dans la base de données actuelle.  
  
 *LocalServiceName*  
 Spécifie que la priorité de conversation peut être appliquée aux éléments suivants :  
  
-   N’importe quel point de terminaison initiateur dont le nom service initiateur correspond *LocalServiceName*.  
  
-   N’importe quel point de terminaison cible dont nom du service cible correspond à *LocalServiceName*.  
  
 ANY  
 -   Spécifie que la priorité de conversation peut être appliquée à n'importe quel point de terminaison, quel que soit le nom du service local utilisé par le point de terminaison.  
  
 Si LOCAL_SERVICE_NAME n'est pas spécifié, la propriété du service local de la priorité de conversation n'est pas modifiée.  
  
 REMOTE_SERVICE_NAME = {'*RemoteServiceName*' | **ANY**}  
 Spécifie le nom d'un service à utiliser comme critère pour déterminer si la priorité de conversation s'applique à un point de terminaison.  
  
 *RemoteServiceName* est un littéral de type **nvarchar (256)**. [!INCLUDE[ssSB](../../includes/sssb-md.md)]utilise une comparaison octet par octet pour faire correspondre le *RemoteServiceName* chaîne. La comparaison respecte la casse et ne prend pas en compte le classement actuel. Le service cible peut être dans l'instance actuelle du [!INCLUDE[ssDE](../../includes/ssde-md.md)] ou dans une instance distante du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 '*RemoteServiceName*'  
 Spécifie que la priorité de conversation doit être attribuée aux éléments suivants :  
  
-   N’importe quel point de terminaison initiateur dont le nom service cible associé correspond *RemoteServiceName*.  
  
-   N’importe quel point de terminaison cible dont le nom service initiateur associé correspond *RemoteServiceName*.  
  
 ANY  
 Spécifie que la priorité de conversation s'applique à n'importe quel point de terminaison, quel que soit le nom du service distant associé au point de terminaison.  
  
 Si REMOTE_SERVICE_NAME n'est pas spécifié, la propriété du service distant de la priorité de conversation n'est pas modifiée.  
  
 PRIORITY_LEVEL = { *PriorityValue* | **par défaut** }  
 Spécifie le niveau de priorité à attribuer à un point de terminaison qui utilise les contrats et les services spécifiés dans la priorité de conversation. *PriorityValue* doit être un entier littéral à partir de 1 (priorité la plus faible) à 10 (priorité la plus élevée).  
  
 Si PRIORITY_LEVEL n'est pas spécifié, la propriété du niveau de priorité de la conversation n'est pas modifiée.  
  
## <a name="remarks"></a>Notes  
 Aucune propriété modifiée par ALTER BROKER PRIORITY n'est appliquée aux conversations existantes. Les conversations existantes se poursuivent avec la priorité qui leur a été attribuée au démarrage.  
  
 Pour plus d’informations, consultez [CREATE BROKER PRIORITY &#40; Transact-SQL &#41; ](../../t-sql/statements/create-broker-priority-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 L’autorisation de création des valeurs par défaut aux membres d’une priorité de conversation le **db_ddladmin** ou **db_owner** base de données fixe et en le **sysadmin** rôle serveur fixe. Nécessite l'autorisation ALTER sur la base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-only-the-priority-level-of-an-existing-conversation-priority"></a>A. Modification portant uniquement sur le niveau de priorité d'une priorité de conversation existante  
 Modifie le niveau de priorité, mais ne modifie pas le contrat, le service local ni les propriétés du service distant.  
  
```  
ALTER BROKER PRIORITY SimpleContractDefaultPriority  
    FOR CONVERSATION  
    SET (PRIORITY_LEVEL = 3);  
```  
  
### <a name="b-changing-all-of-the-properties-of-an-existing-conversation-priority"></a>B. Modification de toutes les propriétés d'une priorité de conversation existante  
 Modifie les propriétés du niveau de priorité, du contrat, du service local et du service distant.  
  
```  
ALTER BROKER PRIORITY SimpleContractPriority  
    FOR CONVERSATION  
    SET (CONTRACT_NAME = SimpleContractB,  
         LOCAL_SERVICE_NAME = TargetServiceB,  
         REMOTE_SERVICE_NAME = N'InitiatorServiceB',  
         PRIORITY_LEVEL = 8);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une priorité de service BROKER &#40; Transact-SQL &#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP BROKER PRIORITY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [Sys.conversation_priorities &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  

