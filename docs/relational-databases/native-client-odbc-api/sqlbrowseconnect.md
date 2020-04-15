---
title: SQLBrowseConnect - France Microsoft Docs
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
ms.openlocfilehash: 3a2b6d1b5bdc722a362c5ed67bff611602a860e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302650"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLBrowseConnect** utilise des mots clés qui peuvent être classés en trois niveaux d’informations de connexion. Pour chaque mot clé, le tableau suivant indique si une liste de valeurs valides est retournée et si le mot clé est facultatif.  
  
## <a name="level-1"></a>Niveau 1  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|N/A|Non|Nom de la source de données retourné par **SQLDataSources**. Le mot clé DSN ne peut pas être utilisé si le mot clé DRIVER est utilisé.|  
|DRIVER|N/A|Non|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC nom pilote[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est «Native Client 11». Le mot clé DRIVER ne peut pas être utilisé si le mot clé DSN est utilisé.|  
  
## <a name="level-2"></a>Niveau 2  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Oui|Non|Nom du serveur sur le réseau sur lequel la source de données réside. Le terme « local » peut être entré en tant que serveur, auquel cas une copie locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisée, même lorsqu'il s'agit d'une version hors réseau.|  
|Identificateur d’utilisateur|Non|Oui|ID de connexion d'utilisateur.|  
|PWD|Non|Oui (dépend de l'utilisateur)|Mot de passe spécifié par l'utilisateur.|  
|APP|Non|Oui|Nom de l’application appelant **SQLBrowseConnect**.|  
|WSID|Non|Oui|ID de poste de travail. En général, il s'agit du nom réseau de l'ordinateur sur lequel l'application s'exécute.|  
  
## <a name="level-3"></a>Niveau 3  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Oui|Oui|Nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Oui|Oui|Langage national utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** ignore les valeurs des mots clés DATABASE et LANGUAGE stockés dans les définitions de source de données ODBC. Si la base de données ou la langue spécifiée dans la chaîne de connexion passée à **SQLBrowseConnect est invalide,** **SQLBrowseConnect renvoie** SQL_NEED_DATA et les attributs de connexion de niveau 3.  
  
 Les attributs suivants, qui sont définis en appelant [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), déterminer le résultat établi par **SQLBrowseConnect**.  
  
|Attribut|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|S’il est réglé pour SQL_MORE_INFO_YES, **SQLBrowseConnect** retourne une série étendue de propriétés serveur.<br /><br /> Ce qui suit est un exemple d’une chaîne prolongée retournée par **SQLBrowseConnect**:<br /><br /> <br /><br /> `ServerName\InstanceName;Clustered:No;Version:8.00.131`<br /><br /> <br /><br /> Dans cette chaîne, des points-virgules séparent les différentes parties des informations sur le serveur. Utilisez des virgules pour séparer les différentes instances de serveur.|  
|SQL_COPT_SS_BROWSE_SERVER|Si un nom de serveur est spécifié, **SQLBrowseConnect** retournera les informations pour le serveur spécifié. Si SQL_COPT_SS_BROWSE_SERVER est configuré à NULL, **SQLBrowseConnect renvoie** des informations pour tous les serveurs du domaine.<br /><br /> <br /><br /> Notez qu’en raison de problèmes de réseau, **SQLBrowseConnect** pourrait ne pas recevoir une réponse en temps opportun de tous les serveurs. Par conséquent, la liste des serveurs retournée peut varier pour chaque requête.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Lorsque l'attribut SQL_COPT_SS_BROWSE_CACHE_DATA a la valeur SQL_CACHE_DATA_YES, vous pouvez extraire les données en plusieurs segments lorsque la longueur de la mémoire tampon est insuffisante pour contenir le résultat. Cette longueur est spécifiée dans l’argument De BufferLength à SQLBrowseConnect.<br /><br /> La valeur SQL_NEED_DATA est retournée lorsque davantage de données sont disponibles. La valeur SQL_SUCCESS est retournée lorsqu'il n'existe plus de données à récupérer.<br /><br /> La valeur par défaut est SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Prise en charge par SQLBrowseConnect des fonctionnalités de récupération d'urgence, haute disponibilité  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] **SQLBrowseConnect** pour vous connecter à un cluster, consultez [SQL Server Native Client Support for High Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Prise en charge par SQLBrowseConnect des noms de principaux du service (SPN)  
 Lors de l'ouverture d'une connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sur la méthode d'authentification employée pour ouvrir la connexion.  
  
 Pour plus d’informations sur les SPN, voir [Noms principaux de service &#40;les SPN&#41; dans les connexions aux clients &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|SQL_COPT_SS_BROWSE_CACHE_DATA documenté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLBrowseConnect](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [Détails de l’implémentation d’API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
