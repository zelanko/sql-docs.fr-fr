---
title: SQLDriverConnect | Microsoft Docs
description: En savoir plus sur les attributs de connexion SQLDriverConnect et la prise en charge de la haute disponibilité, de la récupération d’urgence et des SPN dans le pilote ODBC SQL Server Native Client.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 53804692b3bb27fa4be5c3ca46e516e178288846
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465270"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit des attributs de connexion qui remplacent ou améliorent les mots clés de chaînes de connexion. Plusieurs mots clés de chaînes de connexion ont des valeurs par défaut définies par le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Pour obtenir la liste des mots clés disponibles dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client, consultez [utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Pour plus d’informations sur les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attributs de connexion et les comportements par défaut du pilote, consultez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Pour plus d’informations sur les mots clés de chaîne de connexion valides pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, consultez [utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Quand la valeur du paramètre **SQLDriverConnect**_DriverCompletion_ est SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE ou SQL_DRIVER_COMPLETE_REQUIRED, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client récupère les valeurs des mots clés dans la boîte de dialogue affichée. Si la valeur de mot clé est transmise à la chaîne de connexion et si l'utilisateur ne modifie pas la valeur pour le mot clé dans la boîte de dialogue, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilise la valeur issue de la chaîne de connexion. Si la valeur n'est pas définie dans la chaîne de connexion et si l'utilisateur ne procède à aucune affectation dans la boîte de dialogue, le pilote utilise la valeur par défaut.  
  
 L’affichage de la boîte de dialogue de connexion du pilote doit être donné à **SQLDriverConnect** avec *une valeur* *WindowHandle* valide. Un handle non valide retourne SQL_ERROR.  
  
 Spécifiez le mot clé DRIVER ou DSN. ODBC indique que, de ces deux mots clés, un pilote utilise celui qui est situé le plus à gauche et ignore l'autre si les deux sont spécifiés. Si DRIVER est spécifié ou est le plus à gauche des deux, et que la valeur du paramètre **SQLDriverConnect**_DriverCompletion_ est SQL_DRIVER_NOPROMPT, le mot clé Server et une valeur appropriée sont requis.  
  
 Lorsque SQL_DRIVER_NOPROMPT est spécifié, les mots clés d'authentification utilisateur doivent être fournis avec des valeurs. Le pilote garantit que la chaîne « Trusted_Connection=yes » ou les mots clés UID et PWD à la fois sont disponibles.  
  
 Si la valeur du paramètre *DriverCompletion* est SQL_DRIVER_NOPROMPT ou SQL_DRIVER_COMPLETE_REQUIRED et que la langue ou la base de données provient de la chaîne de connexion et que l’une ou l’autre n’est pas valide, **SQLDriverConnect** retourne SQL_ERROR.  
  
 Si la valeur du paramètre *DriverCompletion* est SQL_DRIVER_NOPROMPT ou SQL_DRIVER_COMPLETE_REQUIRED et que la langue ou la base de données provient des définitions de source de données ODBC et que l’une ou l’autre n’est pas valide, **SQLDriverConnect** utilise la langue ou la base de données par défaut pour l’ID utilisateur spécifié et retourne SQL_SUCCESS_WITH_INFO.  
  
 Si la valeur du paramètre *DriverCompletion* est SQL_DRIVER_COMPLETE ou SQL_DRIVER_PROMPT et si la langue ou la base de données n’est pas valide, **SQLDriverConnect** réaffiche la boîte de dialogue.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect prend en charge les fonctionnalités de récupération d'urgence, haute disponibilité  
 Pour plus d’informations sur l’utilisation de **SQLDriverConnect** pour se connecter à un [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>Prise en charge de SQLDriverConnect pour les noms de principaux du service (SPN)  
 SQLDDriverConnect utilise la boîte de dialogue de connexion ODBC boîte invite est activée. Celle-ci vous permet d'entrer des SPN à la fois pour le serveur principal et pour le partenaire de basculement.  
  
 SQLDriverConnect acceptera les nouveaux mots clés de chaîne de connexion **ServerSPN** et **FailoverPartnerSPN ne**, et reconnaîtra les nouveaux attributs de connexion SQL_COPT_SS_SERVER_SPN et SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Lorsqu'une valeur d'attribut de connexion est définie plus d'une fois, toute valeur définie par programme à priorité sur la valeur d'un DSN et sur toute valeur dans une chaîne de connexion. Une valeur dans un DSN est prioritaire par rapport à une valeur dans une chaîne de connexion.  
  
 Lors de l'ouverture d'une connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sur la méthode d'authentification employée pour ouvrir la connexion.  
  
 Pour plus d’informations sur les SPN, consultez [noms de principal du Service &#40;spn&#41; dans connexions clientes &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Exemples  
 L’appel suivant illustre la quantité de données minimale requise pour **SQLDriverConnect**:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Les chaînes de connexion suivantes illustrent les données minimales requises lorsque la valeur du paramètre *DriverCompletion* est SQL_DRIVER_NOPROMPT :  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)   
 [Détails de l’implémentation de l’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
