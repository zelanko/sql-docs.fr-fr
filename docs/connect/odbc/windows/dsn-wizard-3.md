---
title: Assistant Source de données, écran 3 (ODBC Driver pour SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63391969f378fdefbfa9547c079dcce4ff259e22
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67936544"
---
# <a name="data-source-wizard-screen-3"></a>Assistant Source de données, écran 3

Spécifiez la base de données par défaut, différentes options ANSI à utiliser par le pilote, et le nom d'un serveur miroir.

## <a name="options"></a>Options

### <a name="change-the-default-database-to"></a>Changer de base de données par défaut

Indique le nom de la base de données par défaut pour toute connexion faite à l'aide de cette source de données. Lorsque cette zone est désactivée, les connexions utilisent la base de données par défaut définie pour l'ID de connexion sur le serveur. Lorsque cette zone est activée, la base de données nommée dans la zone remplace la base de données définie par défaut pour l'ID de connexion. Si la zone **Joindre le nom de fichier de la base de données** contient le nom d’un fichier primaire, la base de données décrite par le fichier primaire est jointe en tant que base de données suivant le nom spécifié dans la zone **Changer de base de données par défaut pour**.

Il est plus efficace d'utiliser la base de données par défaut comme ID de connexion que de spécifier une base de données par défaut dans la source de données ODBC.

### <a name="mirror-server"></a>Serveur miroir

Indique le nom du partenaire de basculement de la base de données à mettre en miroir. Si le nom d’une base de données n’apparaît pas dans la zone **Changer de base de données par défaut pour**, ou si le nom qui apparaît est celui de la base de données par défaut, **Serveur miroir** est grisé.

Facultativement, vous pouvez spécifier un nom de principal du serveur (SPN) pour le serveur miroir. Le SPN du serveur miroir est utilisé pour l'authentification mutuelle entre client et serveur.

### <a name="attach-database-filename"></a>Joindre le nom de fichier de base de données

Indique le nom du fichier primaire d'une base de données joignable. Cette base de données est jointe et utilisée comme base de données par défaut pour la source de données. Spécifiez le chemin d'accès complet du fichier primaire. Le nom de base de données spécifié dans la zone **Changer de base de données par défaut pour** est utilisé comme nom de la base de données jointe.

### <a name="use-ansi-quoted-identifiers"></a>Utiliser des identificateurs entre guillemets ANSI

Spécifie que QUOTED_IDENTIFIERS est activé lors de la connexion d’ODBC Driver for SQL Server. Lorsque cette case est cochée, SQL Server applique les règles ANSI concernant les guillemets. Les guillemets doubles ne doivent être utilisés que pour les identificateurs, tels que les noms de colonne et de table. Les chaînes de caractères doivent apparaître entre guillemets.

```
SELECT "LastName"
FROM "Person.Contact"
WHERE "LastName" = 'O''Brien'
```

Lorsque cette case à cocher est désactivée, les applications qui utilisent des identificateurs entre guillemets, tels que l'utilitaire Microsoft Query qui est fourni avec Microsoft Excel, rencontrent des erreurs lorsqu'ils génèrent des instructions SQL avec des identificateurs entre guillemets.

### <a name="use-ansi-nulls-paddings-and-warnings"></a>Utiliser ANSI_NULLS, ANSI_WARNINGS et ANSI_PADDINGS

Spécifie que les options ANSI_NULLS, ANSI_WARNINGS et ANSI_PADDINGS sont activées lors de la connexion de ODBC Driver for SQL Server.

Avec l'option ANSI_NULLS activée, le serveur met en vigueur les règles ANSI concernant la comparaison des colonnes pour NULL. La syntaxe ANSI "IS NULL" ou "IS NOT NULL" doit être utilisée pour toutes les comparaisons NULL. La syntaxe Transact-SQL "= NULL" n'est pas prise en charge.

Lorsque l’option ANSI_WARNINGS est activée, SQL Server émet des messages d’avertissement en cas de violation des règles ANSI, mais pas des règles Transact-SQL. Les erreurs de ce type peuvent être des données tronquées lors de l'exécution d'une instruction INSERT ou UPDATE, ou la rencontre d'une valeur NULL pendant une fonction d'agrégation. 

Lorsque l’option ANSI_PADDING est activée, les espaces de fin des valeurs **varchar** et les zéros de fin des valeurs **varbinary** ne sont pas éliminés automatiquement.

### <a name="application-intent"></a>Intention de l’application

Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. Les valeurs possibles sont **ReadOnly** et **ReadWrite**.

### <a name="multi-subnet-failover"></a>Basculement de sous-réseaux multiples.

Si votre application se connecte à un groupe de disponibilité (AG) de récupération d’urgence à haute disponibilité (groupes de disponibilité AlwaysOn) sur des sous-réseaux différents, ce qui active le **basculement de sous-réseaux multiples.** Configure ODBC Driver for SQL Server de façon à accélérer la détection du serveur (actuellement) actif et la connexion à ce dernier.

### <a name="transparent-network-ip-resolution"></a>Résolution transparente d’adresses IP réseau.

Modifie le comportement du **basculement de sous-réseaux multiples** pour permettre une reconnexion plus rapide pendant le basculement. Pour plus d’informations, consultez [Utilisation de la résolution d’adresses IP réseau transparente](../../../connect/odbc/using-transparent-network-ip-resolution.md).

### <a name="column-encryption"></a>Chiffrement de colonnes.

Permet le déchiffrement et le chiffrement automatiques des transferts de données vers et depuis des colonnes chiffrées avec la fonctionnalité [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) disponible dans SQL Server 2016 et versions ultérieures.

### <a name="use-fmtonly-metadata-discovery"></a>Utiliser la découverte des métadonnées FMTONLY :

Utilisez la méthode de découverte des métadonnées SET FMTONLY héritée lors de la connexion à SQL Server 2012 ou version ultérieure. Activez cette option uniquement lorsque vous utilisez des requêtes non prises en charge par [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md), notamment celles contenant des tables temporaires. 

### <a name="next"></a>Suivant

Passe à l’écran suivant de l’Assistant.

### <a name="back"></a>Retour

Revient à l’écran précédent de l’Assistant.

## <a name="next-steps"></a>Étapes suivantes

[Assistant Source de données, écran 2](../../../connect/odbc/windows/dsn-wizard-2.md)

[Assistant Source de données, écran 4](../../../connect/odbc/windows/dsn-wizard-4.md)
