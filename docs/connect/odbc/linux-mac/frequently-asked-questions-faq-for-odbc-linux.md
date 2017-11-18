---
title: Forum aux Questions (FAQ) pour ODBC Linux et macOS | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: aa835ce2bb9e35191d9c3056dad2f208445c361a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Forum aux Questions (FAQ) pour ODBC Linux et Mac OS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Voici les réponses aux questions sur le pilote ODBC pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Linux et macOS.
  
## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

**Comment les applications ODBC existantes sur Linux ou macOS ne fonctionnent pas avec le pilote ?**  
Vous devez être en mesure de compiler et exécuter les applications ODBC que vous avez la compilation et en cours d’exécution sur Linux ou macOS à l’aide d’autres pilotes. 
  
**Les fonctionnalités de [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] par cette version de la prise en charge du pilote ?**

Le pilote ODBC sur Linux et macOS prend en charge toutes les fonctionnalités de serveur dans [!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)] à l’exception de la base de données locale. Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] les fonctionnalités prises en charge, consultez [les instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Le pilote prend en charge l’authentification Kerberos ?**  
Oui. Si vous avez une installation existante de l’environnement Kerberos, vous devez être en mesure de se connecter aux serveurs à l’aide de la `Trusted_Connection=Yes` option de chaîne de connexion ou de la source de données. Pour plus d’informations, consultez [à l’aide de l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quel encodage Unicode une application doit-elle utiliser ?**  
UTF-8 pour les données SQL_CHAR et UTF-16 pour les données SQL_WCHAR.  

**Existe-t-il des exemples ODBC que je peux télécharger et exécuter avec le pilote pour tester ou l’évaluer ?**

Pour obtenir un exemple, consultez la page [Use Existing MSDN C++ ODBC Samples for the ODBC Driver on Linux](http://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Cela concerne également le pilote ODBC de macOS. 

**Est le pilote ODBC sur Linux ou macOS en open source ?**

Non, les pilotes ODBC sur Linux et macOS ne sont pas un produit open source.  

## <a name="see-also"></a>Voir aussi
[L’installation de Microsoft ODBC Driver for SQL Server sur Linux et Mac OS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

