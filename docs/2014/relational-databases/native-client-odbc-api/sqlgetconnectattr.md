---
title: SQLGetConnectAttr | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
caps.latest.revision: 60
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7db4e37d5fa06373bdb60ea9c2288ff7808ec70d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043847"
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit des attributs de connexion spécifiques au pilote. Certains attributs sont disponibles pour `SQLGetConnectAttr`, et la fonction est utilisée pour indiquer leurs paramètres actuels. Les valeurs indiquées pour ces attributs ne sont pas garanties tant après une connexion a été établie ou l’attribut a été défini à l’aide de [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 Cette rubrique dresse la liste des attributs accessibles en lecture seule. Pour plus d’informations sur les autres [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les attributs de connexion spécifiques au pilote ODBC Native Client, consultez [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
## <a name="sqlcoptssconnectiondead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 L'attribut SQL_COPT_SS_CONNECTION_DEAD signale l'état d'une connexion à un serveur. Le pilote interroge le réseau afin de connaître l'état actuel de la connexion.  
  
> [!NOTE]  
>  L'attribut de connexion ODBC standard SQL_ATTR_CONNECTION_DEAD retourne l'état le plus récent de la connexion. Cela peut ne pas être l'état actuel de la connexion.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_CD_TRUE|La connexion au serveur a été perdue.|  
|SQL_CD_FALSE|La connexion est ouverte et disponible pour le traitement d'instruction.|  
  
## <a name="sqlcoptssclientconnectionid"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 L'attribut SQL_COPT_SS_CLIENT_CONNECTION_ID récupère l'ID de connexion client, qui peut ensuite être utilisé pour localiser :  
  
-   Les informations de diagnostic dans le journal XEvents, si cette option est activée.  
  
-   Les informations d'erreur de connexion dans la mémoire tampon en anneau de connexion.  
  
-   Les informations de diagnostic dans les journaux de suivi d'accès aux données, si cette option est activée.  
  
 Pour plus d’informations, consultez [l’accès à des informations de Diagnostic dans le journal des événements étendus](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_ERROR|La connexion a échoué.|  
|SQL_SUCCESS|La connexion a abouti. L'ID de connexion client se trouve dans le tampon de sortie.|  
  
## <a name="sqlcoptssperfdata"></a>SQL_COPT_SS_PERF_DATA  
 L'attribut SQL_COPT_SS_PERF_DATA retourne un pointeur vers une structure SQLPERF contenant les statistiques actuelles de performances de pilote. `SQLGetConnectAttr` retourne NULL si l’enregistrement des performances n’est pas activé. Les statistiques dans la structure SQLPERF ne sont pas mises à jour de manière dynamique par le pilote. Appelez `SQLGetConnectAttr` chaque fois que les statistiques de performances doivent être actualisées.  
  
|Valeur|Description|  
|-----------|-----------------|  
|NULL|L'enregistrement des performances n'est pas activé.|  
|Toute autre valeur|Pointeur vers une structure SQLPERF.|  
  
## <a name="sqlcoptssperfquery"></a>SQL_COPT_SS_PERF_QUERY  
 L'attribut SQL_COPT_SS_PERF_QUERY retourne TRUE si l'enregistrement des longues requêtes est activé. La demande retourne FALSE si l'enregistrement des requêtes n'est pas actif.  
  
## <a name="sqlcoptssuserdata"></a>SQL_COPT_SS_USER_DATA  
 L'attribut SQL_COPT_SS_USER_DATA extrait le pointeur de données utilisateur. Les données utilisateur sont stockées dans la mémoire détenue par le client et enregistrées par connexion. Si le pointeur de données utilisateur n'a pas été défini, SQL_UD_NOTSET, un pointeur NULL, est retourné.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_UD_NOTSET|Aucun pointeur de données utilisateur n'est défini.|  
|Toute autre valeur|Pointeur vers les données utilisateur.|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>Prise en charge de SQLGetConnectAttr pour les noms de principaux du service (SPN)  
 SQLGetConnectAttr peut être utilisé pour interroger la valeur de nouveaux attributs de connexion SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD. (SQLGetConnectOption peut également être utilisée pour interroger ces valeurs.)  
  
 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD est disponible uniquement pour les connexions ouvertes qui utilisent l'authentification Windows.  
  
 Si SQL_COPT_SS_SERVER_SPN ou SQL_COPT_SS_FAILOVER_PARTNER n'a pas été défini, la valeur par défaut (une chaîne vide) est retournée.  
  
 Pour plus d’informations sur les SPN, consultez [noms principaux de Service &#40;SPN&#41; dans les connexions clientes &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLGetConnectAttr](http://go.microsoft.com/fwlink/?LinkId=59347)   
 [Détails d’implémentation API ODBC](odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
