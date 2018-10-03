---
title: Sys.dm_db_mirroring_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_mirroring_connections
- dm_db_mirroring_connections
- sys.dm_db_mirroring_connections_TSQL
- dm_db_mirroring_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_mirroring_connections dynamic management view
ms.assetid: e4df91b6-0240-45d0-ae22-cb2c0d52e0b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 624e3d8cd6bd92d07bf655e29060ed8809922cc2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815357"
---
# <a name="database-mirroring---sysdmdbmirroringconnections"></a>Base de données mise en miroir - sys.dm_db_mirroring_connections
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne pour chaque connexion établie pour une mise en miroir de base de données.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|Identificateur de la connexion.|  
|**transport_stream_id**|**uniqueidentifier**|Identificateur de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion d’Interface réseau (SNI) utilisée par cette connexion pour les communications TCP/IP.|  
|**state**|**smallint**|État actuel de la connexion. Valeurs possibles :<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = FERMÉ|  
|**state_desc**|**nvarchar(60)**|État actuel de la connexion. Valeurs possibles :<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|Date et heure d'ouverture de la connexion.|  
|**login_time**|**datetime**|Date et heure à laquelle l'ouverture de session a réussi pour la connexion.|  
|**authentication_method**|**nvarchar(128)**|Nom de la méthode d'Authentification Windows (par exemple NTLM ou KERBEROS). La valeur est fournie par Windows.|  
|**principal_name**|**nvarchar(128)**|Nom de l'ouverture de session validée pour les autorisations de connexion. Pour l'authentification Windows, cette valeur est le nom de l'utilisateur distant. Pour l'authentification par certificat, cette valeur est le propriétaire du certificat.|  
|**remote_user_name**|**nvarchar(128)**|Nom de l'utilisateur homologue provenant de l'autre base de données utilisée par l'authentification Windows.|  
|**last_activity_time**|**datetime**|Date et heure de dernière utilisation de la connexion pour envoyer ou recevoir des informations.|  
|**is_accept**|**bit**|Indique si l'origine de la connexion se trouve du côté distant.<br /><br /> 1 = la connexion est une demande acceptée provenant de l'instance distante.<br /><br /> 0 = la connexion a été démarrée par l'instance locale.|  
|**login_state**|**smallint**|État du processus de cette connexion. Valeurs possibles :<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = EN LIGNE<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|État actuel de la connexion en provenance de l'ordinateur distant. Valeurs possibles :<br /><br /> La négociation de connexion est initialisée.<br /><br /> La négociation de connexion attend le message de négociation de la connexion.<br /><br /> La négociation de connexion a initialisé et envoyé le contexte de sécurité pour l'authentification.<br /><br /> La négociation de connexion a reçu et accepté le contexte de sécurité pour l'authentification.<br /><br /> La négociation de connexion a initialisé et envoyé le contexte de sécurité pour l'authentification. Il existe un mécanisme facultatif disponible pour l'authentification des homologues.<br /><br /> La négociation de connexion a reçu et envoyé le contexte de sécurité accepté pour l'authentification. Il existe un mécanisme facultatif disponible pour l'authentification des homologues.<br /><br /> La négociation de connexion attend le message de confirmation d'initialisation du contexte de sécurité.<br /><br /> La négociation de connexion attend le message de confirmation d'acceptation du contexte de sécurité.<br /><br /> La négociation de connexion attend le message de rejet SSPI pour l'authentification qui a échoué.<br /><br /> La négociation de connexion attend le message secret pré-master.<br /><br /> La négociation de connexion attend le message de validation.<br /><br /> La négociation de connexion attend le message d'arbitrage.<br /><br /> La négociation de connexion est terminée et en ligne (prêt) pour l'échange de messages.<br /><br /> La connexion présente une erreur.|  
|**peer_certificate_id**|**Int**|L’ID d’objet local du certificat utilisé par l’instance distante pour l’authentification. Le propriétaire de ce certificat doit avoir les autorisations de connexion CONNECT au point de terminaison de mise en miroir de la base de données.|  
|**encryption_algorithm**|**smallint**|Algorithme de chiffrement utilisé pour cette connexion. Accepte la valeur NULL. Valeurs possibles :<br /><br /> **Valeur :** 0<br /><br /> **Description :** None<br /><br /> **Option DDL :** désactivé<br /><br /> **Valeur :** 1<br /><br /> **Description :** RC4<br /><br /> **Option DDL :** {requis &#124; Required algorithm RC4}<br /><br /> **Valeur :** 2<br /><br /> **Description :** AES<br /><br /> **Option DDL :** algorithme AES obligatoire<br /><br /> **Valeur :** 3<br /><br /> **Description :** None, RC4<br /><br /> **Option DDL :** {pris en charge &#124; algorithme pris en charge RC4}<br /><br /> **Valeur :** 4<br /><br /> **Description :** none, AES<br /><br /> **Option DDL :** algorithme pris en charge RC4<br /><br /> **Valeur :** 5<br /><br /> **Description :** RC4, AES<br /><br /> **Option DDL :** algorithme RC4 AES obligatoire<br /><br /> **Valeur :** 6<br /><br /> **Description :** AES, RC4<br /><br /> **Option DDL :** requis algorithme AES RC4<br /><br /> **Valeur :** 7<br /><br /> **Description :** NONE, RC4, AES<br /><br /> **Option DDL :** pris en charge d’algorithme RC4 AES<br /><br /> **Valeur :** 8<br /><br /> **Description :** aucun, AES, RC4<br /><br /> **Option DDL :** algorithme pris en charge AES RC4<br /><br /> **Remarque :** l’algorithme RC4 est uniquement pris en charge pour la compatibilité descendante. Le nouveau matériel ne peut être chiffré à l'aide de RC4 ou de RC4_128 que lorsque la base de données se trouve dans le niveau de compatibilité 90 ou 100. (Non recommandé.) Utilisez à la place un algorithme plus récent, tel qu'un des algorithmes AES. Dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et versions ultérieures, le matériel chiffré à l’aide de RC4 ou RC4_128 peut être déchiffré dans n’importe quel niveau de compatibilité.|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Représentation textuelle de l'algorithme de chiffrement. Accepte la valeur NULL. Valeurs possibles :<br /><br /> **Description :** None<br /><br /> **Option DDL :** désactivé<br /><br /> **Description :** RC4<br /><br /> **Option DDL :** {requis &#124; requis algorithme RC4}<br /><br /> **Description :** AES<br /><br /> **Option DDL :** requis de l’algorithme AES<br /><br /> **Description :** NONE, RC4<br /><br /> **Option DDL :** {pris en charge &#124; pris en charge d’algorithme RC4}<br /><br /> **Description :** NONE, AES<br /><br /> **Option DDL :** pris en charge d’algorithme RC4<br /><br /> **Description :** RC4, AES<br /><br /> **Option DDL :** requis algorithme RC4 AES<br /><br /> **Description :** AES, RC4<br /><br /> **Option DDL :** requis algorithme AES RC4<br /><br /> **Description :** NONE, RC4, AES<br /><br /> **Option DDL :** pris en charge d’algorithme RC4 AES<br /><br /> **Description :** aucun, AES, RC4<br /><br /> **Option DDL :** pris en charge d’algorithme AES RC4|  
|**receives_posted**|**smallint**|Nombre de réceptions asynchrones sur le réseau qui ne sont pas encore terminées pour cette connexion.|  
|**is_receive_flow_controlled**|**bit**|Indique si les réceptions sur le réseau ont été retardées en raison du contrôle de flux car le réseau est occupé.<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|Nombre d'envois asynchrones sur le réseau qui ne sont pas encore terminés pour cette connexion.|  
|**is_send_flow_controlled**|**bit**|Indique si les envois sur le réseau ont été retardés en raison du contrôle de flux sur le réseau et parce que ce dernier est occupé.<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|Nombre total d'octets envoyés par cette connexion.|  
|**total_bytes_received**|**bigint**|Nombre total d’octets reçus par cette connexion.|  
|**total_fragments_sent**|**bigint**|Nombre total de fragments de messages de mise en miroir de la base de données envoyés par cette connexion.|  
|**total_fragments_received**|**bigint**|Nombre total de fragments de messages de mise en miroir de la base de données reçus par cette connexion.|  
|**total_sends**|**bigint**|Nombre total de réseau envoyer les demandes émises par cette connexion.|  
|**total_receives**|**bigint**|Nombre total de demandes de réception sur le réseau émises par cette connexion.|  
|**peer_arbitration_id**|**uniqueidentifier**|Identificateur interne du point de terminaison. Accepte la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="physical-joins"></a>Jointures physiques  
 ![jointure pour sys.join_dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/media/join-dm-db-mirroring-connections.gif "jointure pour sys.join_dm_db_mirroring_connections")  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|From|Pour|Relation|  
|----------|--------|------------------|  
|**dm_db_mirroring_connections.connection_id**|**dm_exec_connections.connection_id**|Un à un|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Surveillance de la mise en miroir de bases de données &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  
