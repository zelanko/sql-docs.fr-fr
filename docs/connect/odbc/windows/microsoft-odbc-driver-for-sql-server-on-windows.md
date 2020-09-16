---
description: Pilote Microsoft ODBC pour SQL Server sur Windows
title: Microsoft ODBC Driver for SQL Server sur Windows | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64a2c7ff06534865c4105ab28c2f3bc42b783de3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462235"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Pilote Microsoft ODBC pour SQL Server sur Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Les pilotes Microsoft ODBC pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont des pilotes ODBC autonomes qui fournissent une interface de programmation d’applications (API) implémentant les interfaces ODBC standard dans Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Microsoft ODBC Driver for SQL Server peut servir à créer des applications. Vous pouvez également mettre à niveau vos anciennes applications qui utilisent actuellement un pilote ODBC plus ancien. ODBC Driver for SQL Server prend en charge les connexions à Azure SQL Database, Azure SQL Data Warehouse et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

## <a name="summary"></a>Résumé

| Version       | Fonctionnalités prises en charge      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 for SQL Server | <ul><li>Prise en charge d’Always Encrypted pour l’API BCP</li><li>Le nouvel attribut de chaîne de connexion UseFMTONLY conduit le pilote à utiliser les métadonnées héritées dans les cas spéciaux nécessitant des tables temporaires</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Azure AD Authentication</li><li>Groupes de disponibilité AlwaysOn</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Noms de domaine internationaux</li></ul> |
| Pilote Microsoft ODBC 11 pour SQL Server | <ul><li>Regroupement de connexions prenant en charge les pilotes</li><li>Résilience des connexions</li><li>Exécution asynchrone (méthode d’interrogation)</li></ul> |    

## <a name="documentation"></a>Documentation  
Cette documentation sur Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comporte :  
  
-   [Notes de publication relatives à ODBC pour SQL Server sur Windows](../../../connect/odbc/windows/release-notes-odbc-sql-server-windows.md)  
-   [Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Configuration système requise, installation et fichiers de pilote](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Regroupement de connexions prenant en charge le pilote dans ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Exemple d’exécution asynchrone &#40;méthode de notification&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Résilience de connexion du pilote ODBC Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Utilisation d’Azure Active Directory avec ODBC Driver](../../../connect/odbc/using-azure-active-directory.md) 
-   [Utilisation de la résolution d’adresses IP réseau transparente](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Communauté  
- [Blog sur les pilotes SQL Server](https://techcommunity.microsoft.com/t5/sql-server/bg-p/SQLServer/label-name/SQLServerDrivers)  
- [Forum sur l’accès aux données SQL Server](https://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Voir aussi  
- [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [Forum aux questions sur SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [Guide de référence du programmeur ODBC](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
