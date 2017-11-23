---
title: CONNECTIONPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs: TSQL
helpviewer_keywords: CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ab513c11d86ca5d7496ad1fca2ff7527d69bba6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne des informations sur les propriétés de la connexion unique par le biais de laquelle une demande a été transférée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>Arguments  
*propriété*  
Propriété de la connexion. *propriété* peut prendre l’une des valeurs suivantes.
  
|Valeur|Type de données| Description|  
|---|---|---|
|net_transport|**nvarchar (40)**|Retourne le protocole de transport physique utilisé par cette connexion. N'accepte pas la valeur NULL.<br /><br /> Valeurs de retour sont : **HTTP**, **d’un canal nommé**, **Session**, **mémoire partagée**, **SSL**, **TCP**, et **VIA**.<br /><br /> Remarque : Retourne toujours **Session** quand une connexion a plusieurs jeux de résultats actifs (MARS) activés, et le regroupement de connexions est activé.|  
|protocol_type|**nvarchar (40)**|Retourne le type de protocole de la charge utile. Il effectue la distinction entre TDS (TSQL) et SOAP. Autorise la valeur NULL.|  
|auth_scheme|**nvarchar (40)**|Retourne le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schéma d’authentification pour une connexion. Le schéma d'authentification est soit l'authentification Windows (NTLM, KERBEROS, DIGEST, BASIC, NEGOTIATE), soit l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. N'accepte pas la valeur NULL.|  
|local_net_address|**varchar(48)**|Retourne l'adresse IP sur le serveur ciblé par cette connexion. Disponible uniquement pour les connexions utilisant le fournisseur de transport TCP. Autorise la valeur NULL.|  
|local_tcp_port|**int**|Retourne le port TCP du serveur ciblé par cette connexion s'il s'agissait d'une connexion utilisant le transport TCP. Autorise la valeur NULL.|  
|client_net_address|**varchar(48)**|Demande l'adresse du client se connectant à ce serveur. Autorise la valeur NULL.|  
|physical_net_transport|**nvarchar (40)**|Retourne le protocole de transport physique utilisé par cette connexion. Précis lorsque plusieurs jeux MARS (Multiple Active Result Set) sont activés pour une connexion.|  
|\<Toute autre chaîne >||Retourne la valeur NULL si l'entrée n'est pas valide.|  
  
## <a name="remarks"></a>Notes  
**local_net_address** et **local_tcp_port** retourner la valeur NULL dans [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
Les valeurs qui sont retournées sont les mêmes que les options affichées pour les colonnes correspondantes dans le [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) vue de gestion dynamique. Exemple :
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>Voir aussi
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[Sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
