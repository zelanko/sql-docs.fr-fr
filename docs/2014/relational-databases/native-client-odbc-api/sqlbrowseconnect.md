---
title: SQLBrowseConnect | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5300285872c0c03ce25410ba0bfd636c7ccf6bca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208520"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
  **SQLBrowseConnect** utilise des mots clés qui peuvent être classés en trois niveaux d’informations de connexion. Pour chaque mot clé, le tableau suivant indique si une liste de valeurs valides est retournée et si le mot clé est facultatif.  
  
## <a name="level-1"></a>Niveau 1  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DSN|Néant|non|Nom de la source de données retournée par **SQLDataSources**. Le mot clé DSN ne peut pas être utilisé si le mot clé DRIVER est utilisé.|  
|DRIVER|Néant|non|Microsoft® [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom du pilote ODBC Native Client est {[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11}. Le mot clé DRIVER ne peut pas être utilisé si le mot clé DSN est utilisé.|  
  
## <a name="level-2"></a>Niveau 2  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Oui|non|Nom du serveur sur le réseau sur lequel la source de données réside. Le terme « local » peut être entré en tant que serveur, auquel cas une copie locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être utilisée, même lorsqu'il s'agit d'une version hors réseau.|  
|UID|non|Oui|ID de connexion d'utilisateur.|  
|PWD|non|Oui (dépend de l'utilisateur)|Mot de passe spécifié par l'utilisateur.|  
|APP|non|Oui|Nom de l’application qui appelle **SQLBrowseConnect**.|  
|WSID|non|Oui|ID de station de travail. En général, il s'agit du nom réseau de l'ordinateur sur lequel l'application s'exécute.|  
  
## <a name="level-3"></a>Niveau 3  
  
|Mot clé|Liste retournée ?|Facultatif ?|Description|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Oui|Oui|Nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Oui|Oui|Langage national utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** ignore les valeurs des mots clés de langage et de base de données stockées dans les définitions de source de données ODBC. Si la base de données ou la langue spécifiée dans la chaîne de connexion passée à **SQLBrowseConnect** n’est pas valide, **SQLBrowseConnect** retourne SQL_NEED_DATA et les attributs de connexion de niveau 3.  
  
 Les attributs suivants, qui sont définies en appelant [SQLSetConnectAttr](sqlsetconnectattr.md), déterminer le jeu de résultats retourné par **SQLBrowseConnect**.  
  
|Attribute|Description|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Si elle a la valeur SQL_MORE_INFO_YES, **SQLBrowseConnect** retourne une chaîne étendue de propriétés du serveur.<br /><br /> Voici un exemple de chaîne étendue retournée par **SQLBrowseConnect**: Nomserveur\nominstance ; Cluster : No ; Version : 8.00.131<br /><br /> Dans cette chaîne, des points-virgules séparent les différentes parties des informations sur le serveur. Utilisez des virgules pour séparer les différentes instances de serveur.|  
|SQL_COPT_SS_BROWSE_SERVER|Si un nom de serveur est spécifié, **SQLBrowseConnect** retournera les informations pour le serveur spécifié. Si SQL_COPT_SS_BROWSE_SERVER a la valeur NULL, **SQLBrowseConnect** retourne des informations pour tous les serveurs dans le domaine.<br /><br /> En raison de problèmes réseau, **SQLBrowseConnect** ne peut pas recevoir une réponse en temps voulu de tous les serveurs. Par conséquent, la liste des serveurs retournée peut varier pour chaque requête.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Lorsque l'attribut SQL_COPT_SS_BROWSE_CACHE_DATA a la valeur SQL_CACHE_DATA_YES, vous pouvez extraire les données en plusieurs segments lorsque la longueur de la mémoire tampon est insuffisante pour contenir le résultat. Cette longueur est spécifiée dans l’argument BufferLength SQLBrowseConnect.<br /><br /> La valeur SQL_NEED_DATA est retournée lorsque davantage de données sont disponibles. La valeur SQL_SUCCESS est retournée lorsqu'il n'existe plus de données à récupérer.<br /><br /> La valeur par défaut est SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Prise en charge par SQLBrowseConnect des fonctionnalités de récupération d'urgence, haute disponibilité  
 Pour plus d’informations sur l’utilisation de **SQLBrowseConnect** pour se connecter à un [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] un cluster, consultez [SQL Server Native Client prise en charge pour la haute disponibilité, récupération d’urgence](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Prise en charge par SQLBrowseConnect des noms de principaux du service (SPN)  
 Lors de l'ouverture d'une connexion, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit SQL_COPT_SS_MUTUALLY_AUTHENTICATED et SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sur la méthode d'authentification employée pour ouvrir la connexion.  
  
 Pour plus d’informations sur les SPN, consultez [noms principaux de Service &#40;SPN&#41; dans les connexions clientes &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Historique des modifications  
  
|Mise à jour du contenu|  
|---------------------|  
|SQL_COPT_SS_BROWSE_CACHE_DATA documenté.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLBrowseConnect](http://go.microsoft.com/fwlink/?LinkId=59329)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
