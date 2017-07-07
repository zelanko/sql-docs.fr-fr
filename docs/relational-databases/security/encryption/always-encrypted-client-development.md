---
title: "Always Encrypted (développement client) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
caps.latest.revision: 33
author: stevestein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 8cb39d4ae3ff02fffe83e7f0e4646ade1545ce72
ms.openlocfilehash: f1ad5de594493c65688d5c1ca2d69ac421661770
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="always-encrypted-client-development"></a>Always Encrypted (développement client)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

[Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) est une technologie de chiffrement côté client qui garantit que les données sensibles (et les clés de chiffrement liées) ne soient jamais révélées à SQL Server et à Azure SQL Database. Grâce à Always Encrypted, un pilote client peut chiffrer des données sensibles de manière transparente avant de les transmettre au moteur de base de données, et peut déchiffrer de manière transparente des données récupérées à partir de colonnes de base de données chiffrées.

Pour plus d’informations sur le développement d’applications qui utilisent des bases de données protégées par Always Encrypted, et sur les pilotes clients et les versions de pilotes prises en charge par Always Encrypted, consultez :

- [Utilisation d’Always Encrypted avec le fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)
- [Utilisation du chiffrement intégral avec le pilote JDBC](../../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)
- [Utilisation du chiffrement intégral avec le pilote ODBC de Windows](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)



## <a name="see-also"></a>Voir aussi

[Always Encrypted (moteur de base de données)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)


