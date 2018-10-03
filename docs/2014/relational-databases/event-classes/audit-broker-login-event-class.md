---
title: Audit Broker Login, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Broker Login event class
ms.assetid: af9b1153-2791-40ef-a95c-50923cd0cc97
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c9ff2e1adad233d7bee51194858d1cca530bdfdd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155279"
---
# <a name="audit-broker-login-event-class"></a>Audit Broker Login, classe d'événements
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée un événement **Audit Broker Login** pour renvoyer des messages d'audit relatifs à la sécurité du transport de Service Broker.  
  
## <a name="audit-broker-login-event-class-data-columns"></a>Colonnes de données de la classe Audit Broker Login  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Inutilisé dans cette classe d'événements.|10|Oui|  
|**ClientProcessID**|**Int**|Inutilisé dans cette classe d'événements.|9|Oui|  
|**DatabaseID**|**Int**|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**Int**|Type de classe d'événements capturée. La valeur est toujours **159** pour **Audit Broker Login**.|27|non|  
|**EventSequence**|**Int**|Numéro de séquence de cet événement.|51|non|  
|**EventSubClass**|**Int**|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Le tableau suivant répertorie les valeurs des sous-classes d'événements pour cet événement.|21|Oui|  
|**FileName**|**nvarchar**|Niveau d'authentification du Broker distant. Méthode d'authentification prise en charge configurée sur le point de terminaison du Broker distant. Lorsque plusieurs méthodes sont disponibles, le point de terminaison cible détermine la première méthode qui sera tentée. Les valeurs possibles sont :<br /><br /> **Aucune**. Aucune méthode d'authentification n'est configurée.<br /><br /> **NTLM**. Requiert l'authentification NTLM.<br /><br /> **KERBEROS**. Requiert l'authentification Kerberos.<br /><br /> **NEGOTIATE**. Windows négocie la méthode d'authentification.<br /><br /> **CERTIFICATE**. Requiert le certificat configuré pour le point de terminaison, qui est stocké dans la base de données **master** .<br /><br /> **NTLM, CERTIFICATE**. Accepte l'authentification par certificat NTLM ou SSL.<br /><br /> **KERBEROS, CERTIFICATE**. Accepte l'authentification Kerberos ou par certificat du point de terminaison.<br /><br /> **NEGOCIATE, CERTIFICAT**. Windows négocie la méthode d'authentification ou un certificat de point de terminaison peut être utilisé pour l'authentification.<br /><br /> **CERTIFICATE, NTLM**. Accepte un certificat de point de terminaison ou NTLM pour l'authentification.<br /><br /> **CERTIFICATE, KERBEROS**. Accepte un certificat de point de terminaison ou Kerberos pour l'authentification.<br /><br /> **CERTIFICAT, NEGOTIATE**. Accepte un certificat de point de terminaison pour l'authentification ou Windows négocie la méthode d'authentification.|36|non|  
|**HostName**|**nvarchar**|Inutilisé dans cette classe d'événements.|8|Oui|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|non|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|**ObjectName**|**nvarchar**|Chaîne de connexion utilisée pour cette connexion.|34|non|  
|**OwnerName**|**nvarchar**|Méthode d'authentification prise en charge configurée sur le point de terminaison du Broker local. Lorsque plusieurs méthodes sont disponibles, le point de terminaison cible détermine la première méthode qui sera tentée. Les valeurs possibles sont :<br /><br /> **Aucune**. Aucune méthode d'authentification n'est configurée.<br /><br /> **NTLM**. Requiert l'authentification NTLM.<br /><br /> **KERBEROS**. Requiert l'authentification Kerberos.<br /><br /> **NEGOTIATE**. Windows négocie la méthode d'authentification.<br /><br /> **CERTIFICATE**. Requiert le certificat configuré pour le point de terminaison, qui est stocké dans la base de données **master** .<br /><br /> **NTLM, CERTIFICATE**. Accepte l'authentification par certificat NTLM ou SSL.<br /><br /> **KERBEROS, CERTIFICATE**. Accepte l'authentification Kerberos ou par certificat du point de terminaison.<br /><br /> **NEGOCIATE, CERTIFICAT**. Windows négocie la méthode d'authentification ou un certificat de point de terminaison peut être utilisé pour l'authentification.<br /><br /> **CERTIFICATE, NTLM**. Accepte un certificat de point de terminaison ou NTLM pour l'authentification.<br /><br /> **CERTIFICATE, KERBEROS**. Accepte un certificat de point de terminaison ou Kerberos pour l'authentification.<br /><br /> **CERTIFICAT, NEGOTIATE**. Accepte un certificat de point de terminaison pour l'authentification ou Windows négocie la méthode d'authentification.|37|non|  
|**ProviderName**|**nvarchar**|Méthode d'authentification utilisée pour cette connexion|46|non|  
|**RoleName**|**nvarchar**|Rôle de la connexion. Il peut prendre la valeur **initiator** ou la valeur **target**.|38|non|  
|**ServerName**|**nvarchar**|Nom de l'instance SQL Server analysée.|26|non|  
|**SPID**|**Int**|ID du processus serveur affecté par SQL Server au processus associé au client.|12|Oui|  
|**StartTime**|**datetime**|Heure de début de l'événement, le cas échéant.|14|Oui|  
|**État**|**Int**|Indique l'emplacement dans le code source SQL Server à l'origine de l'événement. Chaque emplacement susceptible de générer cet événement possède un code d'état spécifique. Un spécialiste de l'assistance technique Microsoft peut se servir de ce code d'état afin de déterminer où l'événement s'est produit.|30|non|  
|**TargetUserName**|**nvarchar**|État de connexion. Une des valeurs suivantes :<br /><br /> INITIAL<br /><br /> WAIT LOGIN NEGOTIATE<br /><br /> ONE ISC<br /><br /> ONE ASC<br /><br /> TWO ISC<br /><br /> TWO ASC<br /><br /> WAIT ISC Confirm<br /><br /> WAIT ASC Confirm<br /><br /> WAIT REJECT<br /><br /> WAIT PRE-MASTER SECRET<br /><br /> WAIT VALIDATION<br /><br /> WAIT ARBITRATION<br /><br /> ONLINE<br /><br /> d’erreur<br /><br /> **Remarque** ISC = Initiate Security Context (initialiser le contexte de sécurité). ASC = Accept Security Context (accepter le contexte de sécurité)|39|non|  
|**TransactionID**|**bigint**|ID affecté à la transaction par le système.|4|non|  
  
 Le tableau suivant répertorie les valeurs des sous-classes pour cette classe d'événements.  
  
|ID|Sous-classe|Description|  
|--------|--------------|-----------------|  
|1|Login Success|Un événement Login Success indique que le processus de connexion du Broker adjacent s'est correctement terminé.|  
|2|Login Protocol Error|Un événement Login Protocol Error indique que le Broker reçoit un message correct mais non valide pour l'état actuel du processus de connexion. Le message a peut-être été perdu ou envoyé hors séquence.|  
|3|Message Format Error|Un événement Message Format Error indique que le Broker a reçu un message qui ne correspond pas au format attendu. Il est possible que le message ait été endommagé ou qu'un programme autre que SQL Server envoie les messages au port utilisé par Service Broker.|  
|4|Negotiate Failure|Un événement Negotiate Failure indique que le Broker local et le Broker distant prennent en charge des niveaux d'authentification qui s'excluent mutuellement.|  
|5|Authentication Failure|Un événement Authentication Failure indique que Service Broker ne peut pas authentifier la connexion en raison d'une erreur. Dans le cas d'une authentification Windows, cet événement indique que Service Broker n'est pas en mesure d'utiliser cette authentification. Dans le cas d'une authentification à base de certificat, cet événement indique que Service Broker n'est pas en mesure d'accéder au certificat.|  
|6|Authorization Failure|Un événement Authorization Failure indique que Service Broker a refusé l'autorisation de la connexion. En ce qui concerne l'authentification Windows, cet événement indique que l'identificateur de sécurité pour la connexion ne correspond pas à un utilisateur de base de données. Dans le cas d'une authentification à base de certificat, cet événement indique que la clé publique fournie dans le message ne correspond pas à un certificat dans la base de données.|  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)   
 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
