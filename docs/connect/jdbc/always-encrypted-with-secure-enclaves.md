---
title: Utilisation d’Always Encrypted avec enclaves sécurisées | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
author: reneye
ms.author: v-reye
ms.openlocfilehash: 441adf8e3623f06bfa98718ebc6c01c314c94828
ms.sourcegitcommit: 4b2c9d648b7a7bdf9c3052ebfeef182e2f9d66af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "77004708"
---
# <a name="using-always-encrypted-with-the-secure-enclaves"></a>Utilisation d’Always Encrypted avec enclaves sécurisées
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Cette page fournit des informations sur la façon de développer des applications Java à l’aide d’[Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md) et de Microsoft JDBC Driver 8.2 (ou version ultérieure) pour SQL Server.

Les enclaves sécurisées sont un ajout à la fonctionnalité [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) existante. Les enclaves sécurisées visent à résoudre les problèmes de limitations rencontrées lors de l’utilisation de données Always Encrypted. Avant, les utilisateurs pouvaient uniquement effectuer des comparaisons d’égalité sur des données Always Encrypted ; ils devaient récupérer et déchiffrer les données pour faire d’autres opérations. Les enclaves sécurisées suppriment ces limitations en autorisant les calculs sur les données de texte en clair à l’intérieur d’une enclave sécurisée côté serveur. Une enclave sécurisée est une région de mémoire protégée dans le processus SQL Server qui agit comme un environnement d’exécution approuvé pour le traitement des données sensibles dans le moteur SQL Server. Une enclave sécurisée apparaît sous la forme d’une boîte noire pour le reste de SQL Server et des autres processus sur l’ordinateur d’hébergement. Il n’existe aucun moyen d’afficher les données ou le code à l’intérieur de l’enclave depuis l’extérieur, même avec un débogueur.

## <a name="prerequisites"></a>Prérequis
- Assurez-vous que Microsoft JDBC Driver 8.2 (ou version ultérieure) pour SQL Server est installé sur votre machine de développement. 

> [!Note]
> Si vous utilisez une version antérieure de JDK 8, vous devrez peut-être télécharger et installer les fichiers de stratégie Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction. Veillez à lire le fichier Lisez-moi inclus dans le fichier zip pour obtenir les instructions d’installation et des informations pertinentes sur les éventuels problèmes d’importation/exportation.  
>
> Vous pouvez télécharger les fichiers de stratégie à partir de la page web [Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 8 Download](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).

## <a name="setting-up-secure-enclaves"></a>Configuration des enclaves sécurisées
Suivez ce [tutoriel](../../relational-databases/security/tutorial-getting-started-with-always-encrypted-enclaves.md) pour commencer à utiliser les enclaves sécurisées. Pour avoir des informations plus complètes, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="connection-string-properties"></a>Propriétés de chaîne de connexion
**enclaveAttestationUrl** : URL du point de terminaison du service d’attestation.

**enclaveAttestationProtocol** : protocole du service d’attestation. Actuellement, la seule valeur possible est **HGS** (Host Guardian Service).

Les utilisateurs doivent activer **columnEncryptionSetting** et configurer correctement les **deux** propriétés de chaîne de connexion ci-dessus pour activer Always Encrypted avec enclaves sécurisées à partir de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

## <a name="working-with-secure-enclaves"></a>Utilisation d’enclaves sécurisées
Une fois que les propriétés de connexion aux enclaves ont été correctement définies, la fonctionnalité est transparente pour l’utilisateur. Le pilote détermine automatiquement si la requête nécessite l’utilisation d’une enclave sécurisée. Les exemples ci-dessous montrent des requêtes qui déclenchent des calculs d’enclave. La configuration d’une base de données et d’une table est expliquée dans [Bien démarrer avec Always Encrypted avec enclaves sécurisées](../../relational-databases/security/tutorial-getting-started-with-always-encrypted-enclaves.md).

Les requêtes enrichies déclenchent des calculs d’enclave :
```java
private static final String URL = "jdbc:sqlserver://<server>:<port>;user=<username>;password=<password>;databaseName=ContosoHR;columnEncryptionSetting=enabled;enclaveAttestationUrl=<attestation-url>;enclaveAttestationProtocol=<attestation-protocol>;";
try (Connection c = DriverManager.getConnection(URL)) {
    try (PreparedStatement p = c.prepareStatement("SELECT * FROM Employees WHERE SSN LIKE ?")) {
        p.setString(1, "%6818");
        try (ResultSet rs = p.executeQuery()) {
            while (rs.next()) {
                // Do work with data
            }
        }
    }
    
    try (PreparedStatement p = c.prepareStatement("SELECT * FROM Employees WHERE SALARY > ?")) {
        ((SQLServerPreparedStatement) p).setMoney(1, new BigDecimal(0));
        try (ResultSet rs = p.executeQuery()) {
            while (rs.next()) {
                // Do work with data
            }
        }
    }
}
```

L’activation du chiffrement sur une colonne déclenche également des calculs d’enclave :
```java
private static final String URL = "jdbc:sqlserver://<server>:<port>;user=<username>;password=<password>;databaseName=ContosoHR;columnEncryptionSetting=enabled;enclaveAttestationUrl=<attestation-url>;enclaveAttestationProtocol=<attestation-protocol>;";
try (Connection c = DriverManager.getConnection(URL);Statement s = c.createStatement()) {
    s.executeUpdate("ALTER TABLE Employees ALTER COLUMN SSN CHAR(11) NULL WITH (ONLINE = ON)");
}
```

## <a name="java-8-users"></a>Utilisateurs de Java 8
Cette fonctionnalité requiert l’algorithme de signature RSASSA-PSA. Cet algorithme a été ajouté dans JDK 11, mais il n’a pas été rétroporté dans JDK 8. Les utilisateurs qui souhaitent utiliser cette fonctionnalité avec la version JDK 8 de [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ont deux solutions : charger leur propre fournisseur qui prend en charge l’algorithme de signature RSASSA-PSA ou inclure la dépendance facultative BouncyCastleProvider. La dépendance sera supprimée à une date ultérieure si l’algorithme de signature est rétroporté dans JDK 8 ou si le cycle de vie de la prise en charge de JDK 8 se termine.

## <a name="see-also"></a>Voir aussi
[Utilisation d'Always Encrypted avec le pilote JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)  