---
title: Pilote Microsoft ODBC pour SQL Server sur Windows | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: be1cdd060537883c0bad107790847003b4749738
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Pilote Microsoft ODBC pour SQL Server sur Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC Driver 13.1, 13 et 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sont des pilotes ODBC autonomes qui fournissent une interface de programmation d’applications (API) implémentant les interfaces ODBC standards dans Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].

Le pilote Microsoft ODBC pour SQL Server peut servir à créer des applications. Vous pouvez également mettre à niveau vos anciennes applications qui utilisent actuellement un pilote ODBC plus ancien. Le pilote ODBC pour SQL Server prend en charge les connexions à la base de données SQL Azure, entrepôt de données SQL Azure, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 et SQL Server 2005.  

## <a name="summary"></a>Résumé

| Version       | Fonctionnalités prises en charge      |
| ------------- |---------------| 
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Authentification Azure AD</li><li>Groupes de disponibilité AlwaysOn (AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Noms de domaine internationaux</li></ul> |
| Microsoft ODBC Driver 11 for SQL Server | <ul><li>Regroupement de connexions prenant en charge les pilotes</li><li>Résilience des connexions</li><li>Exécution asynchrone (méthode d’interrogation)</li></ul> |    

## <a name="documentation"></a>Documentation  
Cette documentation sur Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] inclut ce qui suit :  
  
-   [Notes de publication](../../../connect/odbc/windows/release-notes.md)  
-   [Fonctionnalités de Microsoft ODBC Driver for SQL Server sur Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Configuration système requise, installation et fichiers de pilote](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Regroupement de connexions prenant en charge le pilote dans le pilote ODBC pour SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Exemple d’exécution asynchrone &#40;méthode de notification&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Résilience de connexion du pilote ODBC Windows](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Utilisation du chiffrement intégral avec le pilote ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [À l’aide d’Azure Active Directory avec le pilote ODBC](../../../connect/odbc/using-azure-active-directory.md) 
-   [À l’aide de la résolution IP réseau Transparent](../../../connect/odbc/using-transparent-network-ip-resolution.md)   
  
## <a name="community"></a>Communauté  
- [Blog de l’équipe Microsoft ODBC Driver for SQL Server](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [Forum d'accès aux données SQL Server](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Voir aussi  
- [À propos de SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Génération d'applications avec SQL Server Native Client](https://msdn.microsoft.com/library/ms130904.aspx)   
- [Forum aux questions sur SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [Guide de référence du programmeur ODBC](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](https://msdn.microsoft.com/library/ms131415.aspx)  

