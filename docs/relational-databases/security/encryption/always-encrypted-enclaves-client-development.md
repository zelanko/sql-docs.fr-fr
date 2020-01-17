---
title: Développer des applications avec Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9595eb66-284c-4474-828f-8961a05ce989
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7ec032a9a6bd6d02372d77d8844d5e4938fbe945
ms.sourcegitcommit: a26cb217adfbbfb3636dff43fb19a46462e2e994
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74492004"
---
# <a name="develop-applications-using-always-encrypted-with-secure-enclaves"></a>Développer des applications avec Always Encrypted avec enclaves sécurisées
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

[Always Encrypted avec enclaves sécurisées](always-encrypted-enclaves.md) étend [Always Encrypted](always-encrypted-database-engine.md) pour permettre des fonctionnalités plus riches dans les requêtes des applications sur des colonnes de base de données sensibles chiffrées. Elle tire parti des technologies des enclaves sécurisées pour permettre à l’exécuteur d’une requête dans [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)] de déléguer des calculs sur des colonnes chiffrées à une enclave sécurisée à l’intérieur du processus [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)].

## <a name="client-driver-for-always-encrypted-with-secure-enclaves"></a>Pilote client pour Always Encrypted avec enclaves sécurisées

Pour développer des applications en utilisant Always Encrypted avec enclaves sécurisées, vous avez besoin d’une version du pilote client SQL qui prend en charge les enclaves sécurisées. Le pilote client joue le rôle clé suivant :
- Avant de soumettre pour exécution une requête qui utilise une enclave sécurisée à [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)], le pilote lance l’attestation d’enclave, pour vérifier que l’enclave sécurisée est fiable et peut être utilisée de façon sécurisée pour traiter des données sensibles. Pour plus d’informations sur l’attestation, consultez [Attestation des enclaves sécurisées](always-encrypted-enclaves.md#secure-enclave-attestation).
- Une fois l’attestation réussie, le pilote client établit une session sécurisée avec l’enclave en négociant un secret partagé.
- Le pilote utilise le secret partagé pour chiffrer les clés de chiffrement de colonne dont l’enclave aura besoin pour traiter la requête, puis envoie les clés à [!INCLUDE [ssnoversion-md](../../../includes/ssnoversion-md.md)], qui les transfère à l’enclave sécurisée qui déchiffre les clés. 
- Enfin, le pilote envoie la requête pour exécution, ce qui déclenche les calculs à l’intérieur de l’enclave sécurisée.

Pour utiliser les fonctionnalités de l’enclave sécurisée, vous devez configurer votre application et votre pilote client pour activer les calculs d’enclave lors de la connexion à la base de données et spécifier un point de terminaison de service d’attestation (une URL d’attestation de l’enclave) qui pointe vers un service d’attestation pour votre enclave. Les détails dépendent du pilote et du service/protocole d’attestation que vous utilisez.

## <a name="next-steps"></a>Étapes suivantes

Les pilotes clients suivants prennent en charge Always Encrypted avec enclaves sécurisées :
- Fournisseur de données .NET Framework pour SQL Server dans .NET Framework 4.7.2 ou supérieur. 
    - Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec le fournisseur de données .NET Framework pour SQL Server](../../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md).
    - Pour obtenir un tutoriel pas à pas, consultez [Tutoriel : Développer une application .NET Framework avec Always Encrypted avec enclaves sécurisées](../tutorial-always-encrypted-enclaves-develop-net-framework-apps.md)
- Fournisseur de données Microsoft .NET pour SQL Server dans .NET Framework 4.6 ou ultérieur et .NET Core 2.1 ou ultérieur. 
    - Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec le fournisseur de données Microsoft .NET pour SQL Server](../../../connect/ado-net/sql/sqlclient-support-always-encrypted.md).
    - Pour obtenir un tutoriel pas à pas, consultez [Tutoriel : Développer une application .NET en utilisant Always Encrypted avec enclaves sécurisées](../../../connect/ado-net/sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)
- Microsoft ODBC Driver for SQL Server, version 17.4 ou ultérieure. 
    - Pour plus d’informations, consultez [Utilisation d’Always Encrypted avec ODBC Driver](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md). 
    - Pour plus d’informations sur la façon d’activer les calculs d’enclave pour une connexion de base de données en utilisant ODBC, consultez la section [Activation d’Always Encrypted avec enclaves sécurisées](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-with-secure-enclaves).
