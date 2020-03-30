---
title: Questions fréquentes (FAQ) pour ODBC Linux et macOS | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65bfd6d2-c83d-4528-a5e1-a85b125a4f4a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cab35e67c7c93ce0634a2bf1cd5a8c3c5677179d
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "79058786"
---
# <a name="frequently-asked-questions-faq-for-odbc-linux-and-macos"></a>Questions fréquentes (FAQ) pour ODBC Linux et macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Voici les réponses aux questions sur ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.
  
## <a name="frequently-asked-questions"></a>Forum Aux Questions (FAQ)

**Comment les applications ODBC existantes sur Linux ou macOS fonctionnent-elles avec le pilote ?**  
Vous devriez pouvoir compiler et exécuter les applications ODBC que vous avez compilées et exécutées sur Linux ou macOS à l’aide d’autres pilotes. 
  
**Quelles sont les fonctionnalités de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] prises en charge par cette version du pilote ?**

Le pilote ODBC sur Linux et macOS prend en charge toutes les fonctionnalités de serveur dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] à l’exception de la base de données locale. Pour plus d’informations sur les fonctionnalités de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prises en charge, consultez [Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
**Le pilote prend-il en charge l’authentification Kerberos ?**  
Oui. Si vous disposez déjà d'un environnement Kerberos configuré, vous devriez pouvoir vous connecter à des serveurs en utilisant l'option DSN ou chaîne de connexion `Trusted_Connection=Yes`. Pour plus d’informations, consultez [Utilisation de l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).  
  
**Quel encodage Unicode une application doit-elle utiliser ?**  
UTF-8 pour les données SQL_CHAR et UTF-16 pour les données SQL_WCHAR. En fonction des paramètres régionaux système et de la version du pilote, les données non-UTF-8 dans l'un des différents encodages peuvent également être prises en charge. Pour plus d’informations, consultez [Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md).

**Existe-t-il des exemples ODBC que je peux télécharger et exécuter avec le pilote pour le tester ou l’évaluer ?**

Pour obtenir un exemple, consultez la page [Utiliser des exemples ODBC MSDN C ++ existants pour le pilote ODBC sous Linux](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) . Ceci s’applique également au pilote ODBC macOS. 

**Le pilote ODBC sur Linux ou macOS est-il open source ?**

Non, les pilotes ODBC sur Linux et macOS ne sont pas des produits open source.  

## <a name="see-also"></a>Voir aussi

- [Installation de Microsoft ODBC Driver for SQL Server sur Linux](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installation de Microsoft ODBC Driver for SQL Server sur macOS](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
