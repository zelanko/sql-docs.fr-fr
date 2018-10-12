---
title: Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e56d57cb3df19df1cbf09811ebfebca66efe51b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677577"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server sur Windows

Le pilote ODBC 13.1 pour SQL Server contient toutes les fonctionnalités de la version précédente (11) et ajoute la prise en charge pour l’authentification Always Encrypted et Azure Active Directory lorsqu’il est utilisé conjointement avec Microsoft SQL Server 2016.  
  
Le Chiffrement intégral permet aux clients de chiffrer des données sensibles dans des applications clientes et de ne jamais révéler les clés de chiffrement à SQL Server. À cette fin, un pilote de Chiffrement intégral installé sur l’ordinateur client chiffre et déchiffre automatiquement les données sensibles dans l’application cliente SQL Server. Le pilote chiffre les données dans les colonnes sensibles avant de les transmettre à SQL Server et il réécrit automatiquement les requêtes pour que la sémantique de l’application soit conservée. De même, il déchiffre de manière transparente les données stockées dans les colonnes de base de données chiffrées qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory permet aux utilisateurs, DBA et les programmeurs d’applications à utiliser l’authentification Azure Active Directory en tant que mécanisme de connexion à Microsoft Azure SQL Database et Microsoft SQL Server 2016 à l’aide d’identités dans Azure Active Directory (Azure AD ). Pour plus d’informations, consultez [à l’aide de Azure Active Directory avec le pilote ODBC](../../../connect/odbc/using-azure-active-directory.md), et [connexion à la base de données SQL ou SQL Data Warehouse en utilisant Azure Active Directory authentification](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Microsoft® ODBC Driver 11 for SQL Server® dans Windows  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient toutes les fonctionnalités du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fournies avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [Programmation de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est basé sur le pilote ODBC fourni avec le système d’exploitation Windows. Pour plus d’informations, consultez [Windows Data Access Components SDK](http://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Cette version de ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient les nouvelles fonctionnalités suivantes :  
  
### <a name="bcpexe-l-option-for-specifying-a-login-timeout"></a>bcp.exe – l, option permettant de spécifier un délai d’expiration de connexion
 
L’option –l spécifie le nombre de secondes au terme duquel une connexion de `bcp.exe` à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] expire quand vous tentez de vous connecter à un serveur. Le délai d’expiration de la connexion par défaut est de 15 secondes. Le délai de connexion doit être un nombre compris entre 0 et 65534. Si la valeur fournie n'est pas numérique ou n'est pas comprise dans cet intervalle, `bcp.exe` génère un message d'erreur. La valeur 0 spécifie un délai d’attente infini. Un délai d’expiration de la connexion inférieur à (environ) 10 secondes n’est pas fiable.  
  
### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le [regroupement de connexions prenant en charge les pilotes](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). Pour plus d’informations, consultez [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge [l’exécution asynchrone (méthode de notification)](http://msdn.microsoft.com/library/hh405038(VS.85).aspx). Pour obtenir un exemple d’utilisation, consultez [Exemple d’exécution asynchrone &#40;méthode de notification&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Résilience des connexions
Pour vous assurer que les applications restent connectées à Microsoft Azure SQL Database, le pilote ODBC sur Windows peut restaurer les connexions inactives. Pour plus d’informations, consultez [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Modifications de comportement

Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, le `-y0` option pour `sqlcmd.exe` a provoqué la sortie est tronquée à 1 Mo si la largeur d’affichage avait la valeur 0.
  
À compter d’ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il n’existe aucune limite sur la quantité de données pouvant être récupérées dans une même colonne quand vous spécifiez `–y0`. `sqlcmd.exe` diffuse désormais des colonnes allant jusqu’à une taille de 2 Go (valeur maximale du type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
Une autre différence est que le fait de spécifier `-h` et `-y0` génère désormais une erreur signalant que les options sont incompatibles. `-h`, qui spécifie le nombre de lignes à imprimer entre les en-têtes de colonnes et n’a jamais été compatible avec `-y0`, a été ignoré, même si aucun en-tête n’était imprimé.
  
Notez que `-y0` peut provoquer des problèmes de performances sur le serveur et le réseau, en fonction de la taille des données retournées.

## <a name="see-also"></a> Voir aussi  
[Pilote Microsoft ODBC pour SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
