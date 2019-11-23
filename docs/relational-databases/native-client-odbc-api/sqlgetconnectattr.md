---
title: SQLGetConnectAttr | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8e302fe1c5a1f4bcf5f51728a866a72b993076f3
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786726"
---
# <a name="sqlgetconnectattr"></a>SQLGetConnectAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit des attributs de connexion spécifiques au pilote. Certains des attributs sont accessibles à **SQLGetConnectAttr**et la fonction est utilisée pour indiquer leurs paramètres actuels. Les valeurs indiquées pour ces attributs ne sont pas garanties tant qu'une connexion n'a pas été établie ou que l'attribut n'a pas été défini à l'aide de [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Cette rubrique dresse la liste des attributs accessibles en lecture seule. Pour plus d'informations sur les autres attributs de connexion spécifiques au pilote de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC, consultez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="sql_copt_ss_connection_dead"></a>SQL_COPT_SS_CONNECTION_DEAD  
 L'attribut SQL_COPT_SS_CONNECTION_DEAD signale l'état d'une connexion à un serveur. Le pilote interroge le réseau afin de connaître l'état actuel de la connexion.  
  
> [!NOTE]  
>  L'attribut de connexion ODBC standard SQL_ATTR_CONNECTION_DEAD retourne l'état le plus récent de la connexion. Cela peut ne pas être l'état actuel de la connexion.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_CD_TRUE|La connexion au serveur a été perdue.|  
|SQL_CD_FALSE|La connexion est ouverte et disponible pour le traitement d'instruction.|  
  
## <a name="sql_copt_ss_client_connection_id"></a>SQL_COPT_SS_CLIENT_CONNECTION_ID  
 L'attribut SQL_COPT_SS_CLIENT_CONNECTION_ID récupère l'ID de connexion client, qui peut ensuite être utilisé pour localiser :  
  
-   Les informations de diagnostic dans le journal XEvents, si cette option est activée.  
  
-   Les informations d'erreur de connexion dans la mémoire tampon en anneau de connexion.  
  
-   Les informations de diagnostic dans les journaux de suivi d'accès aux données, si cette option est activée.  
  
 Pour plus d’informations, consultez [accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_ERROR|La connexion a échoué.|  
|SQL_SUCCESS|La connexion a abouti. L'ID de connexion client se trouve dans le tampon de sortie.|  
  
## <a name="sql_copt_ss_perf_data"></a>SQL_COPT_SS_PERF_DATA  
 L'attribut SQL_COPT_SS_PERF_DATA retourne un pointeur vers une structure SQLPERF contenant les statistiques actuelles de performances de pilote. **SQLGetConnectAttr** retourne NULL si l'enregistrement de performance n'est pas activé. Les statistiques dans la structure SQLPERF ne sont pas mises à jour de manière dynamique par le pilote. Appelez **SQLGetConnectAttr** chaque fois que les statistiques de performances doivent être actualisées.  
  
|Valeur|Description|  
|-----------|-----------------|  
|NULL|L'enregistrement des performances n'est pas activé.|  
|Toute autre valeur|Pointeur vers une structure SQLPERF.|  
  
## <a name="sql_copt_ss_perf_query"></a>SQL_COPT_SS_PERF_QUERY  
 L'attribut SQL_COPT_SS_PERF_QUERY retourne TRUE si l'enregistrement des longues requêtes est activé. La demande retourne FALSE si l'enregistrement des requêtes n'est pas actif.  
  
## <a name="sql_copt_ss_user_data"></a>SQL_COPT_SS_USER_DATA  
 L'attribut SQL_COPT_SS_USER_DATA extrait le pointeur de données utilisateur. Les données utilisateur sont stockées dans la mémoire détenue par le client et enregistrées par connexion. Si le pointeur de données utilisateur n'a pas été défini, SQL_UD_NOTSET, un pointeur NULL, est retourné.  
  
|Valeur|Description|  
|-----------|-----------------|  
|SQL_UD_NOTSET|Aucun pointeur de données utilisateur n'est défini.|  
|Toute autre valeur|Pointeur vers les données utilisateur.|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a>Prise en charge de SQLGetConnectAttr pour les noms de principaux du service (SPN)  
 SQLGetConnectAttr peut être utilisé pour interroger la valeur des nouveaux attributs de connexion SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD. (Sqlgetconnectoption, peut également être utilisé pour interroger ces valeurs.)  
  
 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD est disponible uniquement pour les connexions ouvertes qui utilisent l'authentification Windows.  
  
 Si SQL_COPT_SS_SERVER_SPN ou SQL_COPT_SS_FAILOVER_PARTNER n'a pas été défini, la valeur par défaut (une chaîne vide) est retournée.  
  
 Pour plus d’informations sur les [noms de principal du &#40;service&#41; , consultez noms &#40;principaux&#41;de service SPN dans connexions client ODBC](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
   de la [fonction SQLGetConnectAttr](https://go.microsoft.com/fwlink/?LinkId=59347)  
 Détails de l’implémentation de l' [API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
