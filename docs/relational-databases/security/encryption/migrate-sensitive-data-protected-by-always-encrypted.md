---
title: Charger en masse des données chiffrées dans des colonnes à l’aide d’Always Encrypted
description: Découvrez comment charger en masse des données dans des colonnes en utilisant Always Encrypted avec SQL Server.
ms.custom: seo-lt-2019
ms.date: 11/04/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, bulk import
ms.assetid: b2ca08ed-a927-40fb-9059-09496752595e
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 22ad17c49a2f084453c87f26b9c782404f93483d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784030"
---
# <a name="bulk-load-encrypted-data-to-columns-using-always-encrypted"></a>Charger en masse des données chiffrées dans des colonnes à l’aide d’Always Encrypted
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

Pour charger des données chiffrées sans effectuer de contrôle des métadonnées sur le serveur pendant les opérations de copie en bloc, créez l’utilisateur avec l’option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** . Cette option doit être utilisée par les outils hérités ou les flux de travail ETL (Extract-Transform-Load) tiers qui ne peuvent pas utiliser Always Encrypted. Cela permet à un utilisateur de déplacer des données en toute sécurité d’un ensemble de tables contenant des colonnes chiffrées vers un autre ensemble de tables avec des colonnes chiffrées (dans la même base de données ou dans une autre).  

 ## <a name="the-allow_encrypted_value_modifications-option"></a>L’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS  
 [CREATE USER](../../../t-sql/statements/create-user-transact-sql.md) et [ALTER USER](../../../t-sql/statements/alter-user-transact-sql.md) comprennent l’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS. Si cette option est définie sur ON (la valeur par défaut est OFF), elle supprime les contrôles des métadonnées de chiffrement sur le serveur dans les opérations de copie en bloc, ce qui permet à l’utilisateur de copier en bloc des données chiffrées entre des tables ou des bases de données, sans déchiffrage des données.  
  
## <a name="data-migration-scenarios"></a>Scénarios de migration de données  
Le tableau suivant présente les paramètres appropriés recommandés pour plusieurs scénarios de migration.  
 
![always-encrypted-migration](../../../relational-databases/security/encryption/media/always-encrypted-migration.PNG "always-encrypted-migration")  

## <a name="bulk-loading-of-encrypted-data"></a>Chargement en masse de données chiffrées  
Procédez comme suit pour charger des données chiffrées.  

1.  Définissez l’option sur ON pour l’utilisateur dans la base de données qui est la cible de l’opération de copie en bloc. Par exemple :  
 
   ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON;  
   ```  

2.  Exécutez votre application de copie en bloc ou l’outil de connexion avec l’identité de cet utilisateur. (Si votre application utilise un pilote client compatible avec Always Encrypted, assurez-vous que la chaîne de connexion pour la source de données ne contient pas **column encryption setting=enabled** (paramètre de chiffrement de colonne = activé) de sorte que les données récupérées à partir des colonnes chiffrées restent chiffrées. Pour plus d’informations, consultez [Développer des applications à l’aide d’Always Encrypted](always-encrypted-client-development.md).  
  
3.  Redéfinissez l’option ALLOW_ENCRYPTED_VALUE_MODIFICATIONS sur OFF. Par exemple :  

    ```  
    ALTER USER Bob WITH ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = OFF;  
    ```  

## <a name="potential-for-data-corruption"></a>Risque d’altération des données  
Une utilisation incorrecte de cette option peut entraîner une altération des données. L’option **ALLOW_ENCRYPTED_VALUE_MODIFICATIONS** permet à l’utilisateur d’insérer des données quelconques dans des colonnes chiffrées de la base de données, notamment des données chiffrées avec des clés différentes, chiffrées de manière erronée ou non chiffrées. Si l’utilisateur copie accidentellement des données qui ne sont pas correctement chiffrées à l’aide du schéma de chiffrement (clé de chiffrement de colonne, algorithme, type de chiffrement) défini pour la colonne cible, vous ne serez pas en mesure de déchiffrer les données (les données seront endommagées). Cette option doit être utilisée avec précaution, car il risque d’endommager les données dans la base de données.  

Le scénario suivant indique comment une importation de données incorrecte peut entraîner un endommagement des données :  

1.  L’option est définie sur ON pour un utilisateur.  
 
2.  L’utilisateur exécute l’application qui se connecte à la base de données. L’application utilise des API en bloc pour insérer des valeurs en texte brut dans des colonnes chiffrées. L’application attend un pilote client compatible avec Always Encrypted pour chiffrer les données lors de l’insertion. Cependant, l’application est mal configurée. Et elle utilise finalement un pilote qui ne prend pas en charge Always Encrypted, ou la chaîne de connexion ne contient pas **column encryption setting=enabled**.  

3.  L’application envoie des valeurs en texte en clair au serveur. Les contrôles des métadonnées de chiffrement étant désactivés dans le serveur pour l’utilisateur, le serveur permet l’insertion de données incorrectes (texte brut au lieu de texte correctement chiffré) dans une colonne chiffrée.  
 
4.  La même application (ou une autre) se connecte à la base de données à l’aide d’un pilote compatible Always Encrypted et avec la présence de **column encryption setting=enabled** dans la chaîne de connexion, puis récupère les données. L’application s’attend à ce que les données soient déchiffrées en toute transparence. Toutefois, le pilote n’est pas en mesure de déchiffrer les données, car il s’agit de textes chiffrés incorrects.  

## <a name="best-practice"></a>Bonne pratique  
 
Utilisez les comptes d’utilisateur désignés pour les charges de travail de longue durée utilisant cette option.  
 
Pour des applications ou des outils de copie en bloc à exécution courte qui doivent déplacer des données chiffrées sans déchiffrage, définissez l’option ON immédiatement avant d’exécuter l’application, et redésactivez-la (OFF) immédiatement après l’exécution de l’opération.  
 
N’utilisez pas cette option pour développer de nouvelles applications. Utilisez plutôt un pilote client qui fournit une API afin de supprimer les vérifications des métadonnées de chiffrement pour une seule session, par exemple, l’option AllowEncryptedValueModifications dans le fournisseur de données .NET Framework pour SQL Server. Consultez [Copie de données chiffrées à l’aide de SqlBulkCopy](develop-using-always-encrypted-with-net-framework-data-provider.md#copying-encrypted-data-using-sqlbulkcopy). 

## <a name="next-steps"></a>Étapes suivantes
- [Interroger des colonnes en utilisant Always Encrypted avec SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Développer des applications avec Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>Voir aussi  
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Migrer des données à partir ou à destination de colonnes à l’aide d’Always Encrypted avec l’Assistant Importation et exportation SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [CREATE USER &#40;Transact-SQL&#41;](../../../t-sql/statements/create-user-transact-sql.md)   
- [ALTER USER &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-user-transact-sql.md)   

