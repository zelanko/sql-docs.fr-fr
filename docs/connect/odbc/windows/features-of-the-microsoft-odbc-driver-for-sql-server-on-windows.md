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
author: v-makouz
ms.author: genemi
ms.openlocfilehash: 6e3f7929c17b161d3534474d3d9ad99e559714d2
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653805"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-174-for-sql-server-on-windows"></a>Microsoft ODBC Driver 17.4 for SQL Server sur Windows

Le pilote ODBC 17,4 comprend la possibilité d’ajuster les paramètres TCP Keep-Alive. Ils peuvent être modifiés en ajoutant des valeurs aux clés de Registre du pilote ou du DSN. Les clés se trouvent dans `HKEY_LOCAL_MACHINE\Software\ODBC\` pour les sources de données système et `HKEY_CURRENT_USER\Software\ODBC\` dans pour les sources de données utilisateur. Pour DSN, les valeurs doivent être ajoutées à `...\Software\ODBC\ODBC.INI\<DSN Name>` et au `...\Software\ODBC\ODBCINST.INI\ODBC Driver 17 for SQL Server`pilote.

Pour plus d’informations, consultez [entrées de Registre pour les composants ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md) .

Les valeurs sont `REG_SZ` et sont les suivantes :

- `KeepAlive`contrôle la fréquence à laquelle TCP tente de vérifier qu’une connexion inactive est toujours intacte en envoyant un paquet KeepAlive. La valeur par défaut est 30 secondes.

- `KeepAliveInterval`détermine l’intervalle séparant les retransmissions KeepAlive jusqu’à la réception d’une réponse. La valeur par défaut est 1 seconde.



## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server sur Windows

Le pilote ODBC 13,1 pour SQL Server contient toutes les fonctionnalités de la version précédente (11) et ajoute la prise en charge de l’authentification Always Encrypted et Azure Active Directory lorsqu’elle est utilisée conjointement avec Microsoft SQL Server 2016.  
  
Le Chiffrement intégral permet aux clients de chiffrer des données sensibles dans des applications clientes et de ne jamais révéler les clés de chiffrement à SQL Server. À cette fin, un pilote de Chiffrement intégral installé sur l’ordinateur client chiffre et déchiffre automatiquement les données sensibles dans l’application cliente SQL Server. Le pilote chiffre les données dans les colonnes sensibles avant de les transmettre à SQL Server et il réécrit automatiquement les requêtes pour que la sémantique de l’application soit conservée. De même, il déchiffre de manière transparente les données stockées dans les colonnes de base de données chiffrées qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory permet aux utilisateurs, aux administrateurs DBA et aux programmeurs d’applications d’utiliser l’authentification Azure Active Directory comme mécanisme de connexion à Microsoft Azure SQL Database et Microsoft SQL Server 2016 à l’aide d’identités dans Azure Active Directory (Azure AD ). Pour plus d’informations, consultez [utilisation de Azure Active Directory avec le pilote ODBC](../../../connect/odbc/using-azure-active-directory.md)et [connexion à SQL Database ou SQL Data Warehouse à l’aide de l’authentification Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Microsoft® ODBC Driver 11 for SQL Server® dans Windows  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient toutes les fonctionnalités du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fournies avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [Programmation de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est basé sur le pilote ODBC fourni avec le système d’exploitation Windows. Pour plus d’informations, consultez [Windows Data Access Components SDK](https://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Cette version de ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient les nouvelles fonctionnalités suivantes :  
  
### <a name="bcpexe--l-option-for-specifying-a-login-timeout"></a>BCP. exe-l (option) pour spécifier un délai de connexion
 
L’option -l spécifie le nombre de secondes au terme duquel une connexion de `bcp.exe` à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] expire quand vous tentez de vous connecter à un serveur. Le délai d’expiration de connexion par défaut est de 15 secondes. Le délai de connexion doit être un nombre compris entre 0 et 65534. Si la valeur fournie n'est pas numérique ou n'est pas comprise dans cet intervalle, `bcp.exe` génère un message d'erreur. La valeur 0 spécifie un délai d’expiration infini. Un délai d’expiration de la connexion inférieur à (environ) 10 secondes n’est pas fiable.  
  
### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le [regroupement de connexions prenant en charge les pilotes](https://msdn.microsoft.com/library/hh405031(VS.85).aspx). Pour plus d’informations, consultez [Regroupement de connexions prenant en charge le pilote dans le pilote ODBC pour SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge [l’exécution asynchrone (méthode de notification)](https://msdn.microsoft.com/library/hh405038(VS.85).aspx). Pour obtenir un exemple d’utilisation, consultez [Exemple d’exécution asynchrone &#40;méthode de notification&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Résilience des connexions
Pour vous assurer que les applications restent connectées à Microsoft Azure SQL Database, le pilote ODBC sur Windows peut restaurer les connexions inactives. Pour plus d’informations, consultez [Résilience de connexion du pilote ODBC Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Modifications de comportement

Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, l' `-y0` option pour `sqlcmd.exe` a entraîné la troncation de la sortie à 1 Mo si la largeur d’affichage était égale à 0.
  
À compter d’ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il n’existe aucune limite sur la quantité de données pouvant être récupérées dans une même colonne quand vous spécifiez `-y0`. `sqlcmd.exe` diffuse désormais des colonnes allant jusqu’à une taille de 2 Go (valeur maximale du type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
Une autre différence est que le `-h` fait `-y0` de spécifier à la fois et génère maintenant une erreur signalant que les options sont incompatibles. `-h`, qui spécifie le nombre de lignes à imprimer entre les en-têtes de colonnes et n’a jamais été compatible avec `-y0`, a été ignoré, même si aucun en-tête n’était imprimé.
  
Notez que `-y0` peut provoquer des problèmes de performances sur le serveur et le réseau, en fonction de la taille des données retournées.

## <a name="see-also"></a>Voir aussi  
[Pilote Microsoft ODBC pour SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
