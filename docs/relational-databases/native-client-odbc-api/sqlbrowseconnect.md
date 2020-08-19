---
description: SQLBrowseConnect
title: SQLBrowseConnect | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56b505e4c4dcaf00c77c31e5e0e55617106df0fd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428391"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  **SQLBrowseConnect** utilise des mots clés qui peuvent être classés en trois niveaux d’informations de connexion. Pour chaque mot clé, le tableau suivant indique si une liste de valeurs valides est retournée et si le mot clé est facultatif.  
  
## <a name="level-1"></a>Niveau 1  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|N/A|Non|Nom de la source de données retournée par **SQLDataSources**. Le mot clé DSN ne peut pas être utilisé si le mot clé DRIVER est utilisé.|  
|DRIVER|N/A|Non|Le nom du pilote ODBC de Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est { [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. Le mot clé DRIVER ne peut pas être utilisé si le mot clé DSN est utilisé.|  
  
## <a name="level-2"></a>Niveau 2  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Oui|Non|Nom du serveur sur le réseau sur lequel la source de données réside. Le terme « local » peut être entré en tant que serveur, auquel cas une copie locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisée, même lorsqu'il s'agit d'une version hors réseau.|  
|Identificateur d’utilisateur|Non|Oui|ID de connexion d'utilisateur.|  
|PWD|Non|Oui (dépend de l'utilisateur)|Mot de passe spécifié par l'utilisateur.|  
|APP|Non|Oui|Nom de l’application qui appelle **SQLBrowseConnect**.|  
|WSID|Non|Oui|ID de station de travail. En général, il s'agit du nom réseau de l'ordinateur sur lequel l'application s'exécute.|  
  
## <a name="level-3"></a>Niveau 3  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Oui|Oui|Nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Oui|Oui|Langage national utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** ignore les valeurs de la base de données et les mots clés de langage stockés dans les définitions de source de données ODBC. Si la base de données ou la langue spécifiée dans la chaîne de connexion passée à **SQLBrowseConnect** n’est pas valide, **SQLBrowseConnect** retourne SQL_NEED_DATA et les attributs de connexion de niveau 3.  
  
 Les attributs suivants, qui sont définis en appelant [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), déterminent le jeu de résultats retourné par **SQLBrowseConnect**.  
  
|Attribut|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|S’il est défini sur SQL_MORE_INFO_YES, **SQLBrowseConnect** retourne une chaîne étendue de propriétés du serveur.<br /><br /> Voici un exemple de chaîne étendue retournée par **SQLBrowseConnect**:<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> Dans cette chaîne, des points-virgules séparent les différentes parties des informations sur le serveur. Utilisez des virgules pour séparer les différentes instances de serveur.|  
|SQL_COPT_SS_BROWSE_SERVER|Si un nom de serveur est spécifié, **SQLBrowseConnect** retourne des informations pour le serveur spécifié. Si SQL_COPT_SS_BROWSE_SERVER a la valeur NULL, **SQLBrowseConnect** retourne des informations pour tous les serveurs du domaine.<br /><br /> <br /><br /> Notez qu’en raison de problèmes réseau, **SQLBrowseConnect** peut ne pas recevoir une réponse en temps utile de tous les serveurs. Par conséquent, la liste des serveurs retournée peut varier pour chaque requête.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Lorsque l'attribut SQL_COPT_SS_BROWSE_CACHE_DATA a la valeur SQL_CACHE_DATA_YES, vous pouvez extraire les données en plusieurs segments lorsque la longueur de la mémoire tampon est insuffisante pour contenir le résultat. Cette longueur est spécifiée dans l’argument BufferLength pour SQLBrowseConnect.<br /><br /> La valeur SQL_NEED_DATA est retournée lorsque davantage de données sont disponibles. La valeur SQL_SUCCESS est retournée lorsqu'il n'existe plus de données à récupérer.<br /><br /> La valeur par défaut est SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Prise en charge par SQLBrowseConnect des fonctionnalités de récupération d'urgence, haute disponibilité  
 Pour plus d’informations sur l’utilisation de **SQLBrowseConnect** pour la connexion à un [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, consultez [SQL Server Native Client la prise en charge de la haute disponibilité et de la récupération d’urgence](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Prise en charge par SQLBrowseConnect des noms de principaux du service (SPN)  
 Lors de l'ouverture d'une connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sur la méthode d'authentification employée pour ouvrir la connexion.  
  
 Pour plus d’informations sur les SPN, consultez [noms de principal du Service &#40;spn&#41; dans connexions clientes &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|SQL_COPT_SS_BROWSE_CACHE_DATA documenté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLBrowseConnect](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
