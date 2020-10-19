---
title: Fonctionnalités de Microsoft ODBC Driver
description: Découvrez les différentes fonctionnalités prises en charge par Microsoft ODBC Driver for SQL Server sur Windows.
ms.custom: ''
ms.date: 05/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: v-makouz
ms.author: v-daenge
ms.openlocfilehash: 5fc07a171e42338ca76d51d66c04af187cb6beda
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92005910"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-174-for-sql-server-on-windows"></a>Microsoft ODBC Driver 17.4 for SQL Server sur Windows

ODBC Driver 17.4 permet d’ajuster les paramètres TCP Keep-Alive. Ces paramètres peuvent être modifiés en ajoutant des valeurs aux clés de Registre du pilote ou du DSN. Les clés se trouvent dans `HKEY_LOCAL_MACHINE\Software\ODBC\` pour les sources de données système, et dans `HKEY_CURRENT_USER\Software\ODBC\` pour les sources de données utilisateur. Pour DSN, les valeurs doivent être ajoutées à `...\Software\ODBC\ODBC.INI\<DSN Name>`, et pour le pilote à `...\Software\ODBC\ODBCINST.INI\ODBC Driver 17 for SQL Server`.

Pour plus d’informations, consultez [Entrées de Registre pour les composants ODBC](../../../odbc/reference/install/registry-entries-for-odbc-components.md).

Les valeurs sont `REG_SZ` et sont les suivantes :

- `KeepAlive` contrôle la fréquence à laquelle TCP tente de vérifier qu’une connexion inactive est toujours intacte en envoyant un paquet keep-alive. La valeur par défaut est 30 secondes.

- `KeepAliveInterval` détermine l’intervalle qui sépare les retransmissions keep-alive jusqu’à ce qu’une réponse soit reçue. La valeur par défaut est 1 seconde.



## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server sur Windows

ODBC Driver 13.1 for SQL Server contient toutes les fonctionnalités de la version précédente (11) et ajoute la prise en charge d’Always Encrypted et de l’authentification Azure Active Directory, lorsqu’il est utilisé conjointement avec Microsoft SQL Server 2016.  
  
Le Chiffrement intégral permet aux clients de chiffrer des données sensibles dans des applications clientes et de ne jamais révéler les clés de chiffrement à SQL Server. À cette fin, un pilote de Chiffrement intégral installé sur l’ordinateur client chiffre et déchiffre automatiquement les données sensibles dans l’application cliente SQL Server. Le pilote chiffre les données dans les colonnes sensibles avant de les transmettre à SQL Server et il réécrit automatiquement les requêtes pour que la sémantique de l’application soit conservée. De même, il déchiffre de manière transparente les données stockées dans les colonnes de base de données chiffrées qui figurent dans les résultats de la requête. Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory permet aux utilisateurs, aux administrateurs de base de données et aux programmeurs d'applications d'utiliser l’authentification Azure Active Directory comme mécanisme de connexion à Microsoft Azure SQL Database et à Microsoft SQL Server 2016 en utilisant des identités d’Azure Active Directory (Azure AD). Pour plus d’informations, consultez [Utilisation d’Azure Active Directory avec ODBC Driver](../using-azure-active-directory.md), et [Connexion à SQL Database ou Azure Synapse Analytics à l’aide de l’authentification Azure Active Directory](/azure/sql-database/sql-database-aad-authentication).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Microsoft® ODBC Driver 11 for SQL Server® dans Windows  

ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient toutes les fonctionnalités du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fournies avec [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Pour plus d’informations, consultez [Programmation de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md). Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est basé sur le pilote ODBC fourni avec le système d’exploitation Windows. Pour plus d’informations, consultez [Windows Data Access Components SDK](/previous-versions/windows/desktop/legacy/aa968814(v=vs.85)).  
  
Cette version de ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contient les nouvelles fonctionnalités suivantes :  
  
### <a name="bcpexe--l-option-for-specifying-a-login-timeout"></a>Option bcp.exe -l pour spécifier un délai d’expiration de la connexion
 
L’option -l spécifie le nombre de secondes au terme duquel une connexion de `bcp.exe` à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] expire quand vous tentez de vous connecter à un serveur. Par défaut, le délai d'expiration de la connexion est de 15 secondes. Le délai de connexion doit être un nombre compris entre 0 et 65534. Si la valeur fournie n'est pas numérique ou n'est pas comprise dans cet intervalle, `bcp.exe` génère un message d'erreur. Une valeur 0 spécifie un délai d’expiration infini. Un délai d’expiration de la connexion inférieur à (environ) 10 secondes n’est pas fiable.  
  
### <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge le [regroupement de connexions prenant en charge les pilotes](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md). Pour plus d’informations, consultez [Regroupement de connexions prenant en charge le pilote dans le pilote ODBC pour SQL Server](driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Exécution asynchrone (méthode de notification)  
ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge [l’exécution asynchrone (méthode de notification)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md). Pour obtenir un exemple d’utilisation, consultez [Exemple d’exécution asynchrone &#40;méthode de notification&#41;](asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Résilience des connexions
Pour vous assurer que les applications restent connectées à Microsoft Azure SQL Database, le pilote ODBC sur Windows peut restaurer les connexions inactives. Pour plus d’informations, consultez [Résilience de connexion du pilote ODBC Windows](connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Modifications de comportement

Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, l’option `-y0` pour `sqlcmd.exe` a entraîné la troncation de la sortie à 1 Mo si la largeur d’affichage était égale à 0.
  
À compter d’ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il n’existe aucune limite sur la quantité de données pouvant être récupérées dans une même colonne quand vous spécifiez `-y0`. `sqlcmd.exe` diffuse désormais des colonnes allant jusqu’à une taille de 2 Go (valeur maximale du type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]).  
  
Autre différence, spécifier à la fois `-h` and `-y0` génère maintenant une erreur indiquant que les options sont incompatibles. `-h`, qui spécifie le nombre de lignes à imprimer entre les en-têtes de colonnes et n’a jamais été compatible avec `-y0`, a été ignoré, même si aucun en-tête n’était imprimé.
  
Notez que `-y0` peut provoquer des problèmes de performances sur le serveur et le réseau, en fonction de la taille des données retournées.

## <a name="see-also"></a>Voir aussi  
[Microsoft ODBC Driver for SQL Server sur Windows](microsoft-odbc-driver-for-sql-server-on-windows.md)  
