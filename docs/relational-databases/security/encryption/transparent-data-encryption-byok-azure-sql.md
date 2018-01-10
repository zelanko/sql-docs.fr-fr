---
title: TDE - BYOK (Bring Your Own Key) - Azure SQL | Microsoft Docs
description: "Prise en charge du service BYOK (Bring Your Own Key) pour Transparent Data Encryption (TDE) avec Azure Key Vault pour SQL Database et Data Warehouse. Présentation de TDE avec BYOK, avantages, fonctionnement, éléments à prendre en compte et recommandations."
keywords: 
services: sql-database
documentationcenter: 
author: aliceku
manager: craigg
ms.prod: 
ms.reviewer: 
ms.suite: sql
ms.prod_service: sql-database, sql-data-warehouse
ms.service: sql-database
ms.custom: 
ms.component: security
ms.workload: On Demand
ms.tgt_pltfrm: 
ms.devlang: na
ms.topic: article
ms.date: 11/15/2017
ms.author: aliceku
ms.openlocfilehash: 5aaa55cc04e4844889266dc434ac92a0ed22ed00
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="transparent-data-encryption-with-bring-your-own-key-preview-support-for-azure-sql-database-and-data-warehouse"></a>Transparent Data Encryption avec prise en charge de la fonctionnalité BYOK (préversion) pour Azure SQL Database et Data Warehouse
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

Avec la prise en charge de la fonctionnalité BYOK (Bring Your Own Key) pour [Transparent Data Encryption (TDE)](transparent-data-encryption.md), vous pouvez gérer vous-même vos clés de chiffrement TDE et déterminer quels autres utilisateurs sont autorisés à y accéder, et à quel moment. [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault), système de gestion de clés externes cloud Azure, est le premier service de gestion de clés auquel TDE a intégré la prise en charge BYOK. Avec BYOK, la clé de chiffrement de la base de données est protégée par une clé asymétrique stockée dans Key Vault. La clé asymétrique est définie au niveau du serveur et est héritée par toutes les bases de données sur ce serveur. Cette fonctionnalité est actuellement disponible en préversion. Nous vous déconseillons de l’utiliser pour des charges de travail de production avant sa mise à disposition générale.

Avec la prise en charge de BYOK, les utilisateurs peuvent maintenant gérer diverses tâches de gestion des clés, y compris les rotations de clés, les autorisations d’accès à Key Vault, la suppression des clés, ainsi que l’audit et le reporting sur toutes les clés de chiffrement. Key Vault propose une gestion centralisée des clés, tire parti des modules de sécurité matériels (HSM) étroitement surveillés et permet la séparation des responsabilités liées à la gestion des clés et des données pour garantir la conformité réglementaire. 

L’utilisation de TDE avec prise en charge de BYOK présente les avantages suivants :
- Une plus grande transparence et un contrôle plus précis avec la possibilité de gérer soi-même le protecteur TDE   
- Une gestion centralisée des clés de chiffrement TDE (avec d’autres clés et secrets utilisés dans d’autres services Azure) grâce à leur hébergement dans Key Vault
- Séparation des rôles de gestion des clés et des données dans l’organisation, pour permettre la division des responsabilités
- Une sécurité accrue par rapport à vos propres clients, Key Vault étant conçu pour que Microsoft n’ait pas à connaître ou extraire les clés de chiffrement 
- Prise en charge de la rotation des clés

> [!IMPORTANT]
> Si vous utilisez un TDE géré par le service et souhaitez commencer à utiliser une clé Key Vault à la place, sachez que TDE reste activé pendant tout le processus de substitution. Ce processus n’entraîne pas de temps d’arrêt ni de rechiffrement des fichiers de la base de données. La substitution d’une clé gérée par le service par une clé Key Vault nécessite uniquement de rechiffrer la clé de chiffrement de la base de données, qui est une opération rapide s’effectuant en ligne.
>

## <a name="how-does-tde-with-byok-support-work"></a>Comment fonctionne TDE avec prise en charge de BYOK ?
 
![Authentification du serveur auprès de Key Vault](./media/transparent-data-encryption-byok-azure-sql/tde-byok-server-authentication-flow.PNG)

Quand TDE est configuré pour utiliser une clé Key Vault, le serveur envoie la clé de chiffrement de chaque base de données activée avec TDE à Key Vault pour demander d’*inclure la clé*. Key Vault retourne la clé de chiffrement de la base de données chiffrée, qui est stockée dans la base de données utilisateur. 

Il est important de noter qu’**une clé ne peut plus quitter Key Vault une fois qu’elle y est stockée**. Une clé sauvegardée dans un module de sécurité matériel (HSM) dans Key Vault ne quitte jamais la limite de sécurité du HSM. Le serveur peut uniquement envoyer des demandes d’opération de clé aux éléments de clé du protecteur TDE contenus dans Key Vault. L’administrateur de Key Vault a le droit de révoquer des autorisations Key Vault pour le serveur à tout moment, auquel cas toutes les connexions au serveur sont interrompues. 

## <a name="considerations"></a>Observations

Quand vous utilisez TDE avec prise en charge de BYOK, vous avez davantage de tâches de gestion des clés à faire et vous avez des coûts supplémentaires liés à l’utilisation de Key Vault. Ces aspects sont abordés dans les deux sections suivantes.

### <a name="key-management-responsibilities"></a>Responsabilités de la gestion des clés

Gérer les clés de chiffrement des ressources d’une application est une responsabilité importante. En utilisant TDE avec l’option BYOK dans Key Vault, vous avez la responsabilité des tâches de gestion des clés ci-dessous :
- **Rotations des clés** : vous devez changer les protecteurs TDE conformément aux stratégies internes ou aux exigences de conformité. Les rotations de clés peuvent être effectuées à partir du coffre de clés associé au protecteur TDE.  
- **Autorisations dans Key Vault** : les autorisations dans Key Vault sont provisionnées au niveau du coffre de clés et du serveur. Vous pouvez révoquer les autorisations d’un serveur sur un coffre de clés à tout moment à l’aide de la stratégie d’accès définie pour le coffre de clés.
- **Redondance dans Key Vault** : étant donné que les éléments de clé ne quittent jamais Azure Key Vault et que le serveur n’a pas accès aux copies mises en cache en dehors du coffre de clés, vous devez configurer la géoréplication Azure Key Vault pour garantir l’accès aux éléments de clé même si une région Azure Key Vault connaît une interruption de service.  Les bases de données géorépliquées qui utilisent un seul coffre de clés Azure Key Vault perdraient l’accès aux éléments de clé associés.
- **Suppression de clés** : vous pouvez supprimer des clés dans Key Vault et sur le serveur SQL Server pour une sécurité supplémentaire ou pour répondre aux exigences de conformité.
- **Audit et reporting sur toutes les clés de chiffrement** : Key Vault fournit des fichiers journaux que vous pouvez facilement injecter dans d’autres outils de gestion des événements et des informations de sécurité (SIEM). Le service [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-azure-key-vault) d’OMS (Operations Management Suite) est un exemple de service déjà intégré.

### <a name="pricing-considerations"></a>Observations tarifaires 

TDE avec prise en charge de BYOK est une fonctionnalité de sécurité intégrée à Azure SQL Database et Data Warehouse qui est fournie sans frais supplémentaires. Toutefois, l’utilisation du service Key Vault proprement dit est facturée. Les opérations effectuées par le serveur dans Key Vault sont facturées comme des opérations normales dans votre coffre de clés, selon les [prix](https://azure.microsoft.com/pricing/details/key-vault/) en vigueur pour Key Vault. Le serveur envoie des demandes à Key Vault pour les événements suivants :
- Redémarrages d’instances SQL
- Substitutions de clés
- Recherches des modifications des autorisations du serveur sur Key Vault (toutes les 6 heures)

## <a name="important-warnings"></a>Avertissements importants

### <a name="loss-of-access-to-keys"></a>Perte d’accès aux clés

Quand un serveur n’a plus accès au protecteur TDE (du fait de la suppression d’autorisations Key Vault ou de la suppression d’une clé), **toutes les connexions aux bases de données chiffrées du serveur sont bloquées, et toutes ces bases de données sont mises hors connexion et sont supprimées dans un délai de 24 heures**. De plus, les anciennes sauvegardes chiffrées avec la clé indisponible ne sont plus accessibles. Si vous pensez qu’une clé peut être compromise (par exemple, un service ou un utilisateur y a accédé sans autorisation), supprimez cette clé en suivant les instructions fournies dans [Supprimer une clé potentiellement compromise](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md). Supprimez les bases de données avant de supprimer un protecteur TDE actif pour éviter la perte éventuelle des données des transactions effectuées au cours des 10 dernières minutes.  

### <a name="expired-keys"></a>Clés expirées

Étant donné que la disponibilité du protecteur TDE impacte directement celle de la base de données, vous ne devez pas ajouter une clé avec une date d’expiration à un serveur SQL Server. Si une clé déjà utilisée comme protecteur TDE sur un serveur est ensuite configurée avec une date d’expiration dans Azure Key Vault, **les bases de données chiffrées n’ont plus accès à leur protecteur TDE et seront supprimées dans un délai de 24heures après l’expiration de la clé.**

### <a name="deleted-server-identities"></a>Identités serveur supprimées 

L’accès du serveur à Key Vault est géré par le biais de l’identité AAD (Azure Active Directory) unique du serveur. Si l’identité du serveur est supprimée d’AAD, le serveur perd donc l’accès à ses coffres de clés dans Key Vault. Cela signifie que **toutes les connexions aux bases de données chiffrées du serveur seront bloquées, et toutes ces bases de données seront mises hors connexion et seront supprimées dans un délai de 24 heures**.

## <a name="limitations"></a>Limitations

Les coffres de clés Key Vault utilisés pour TDE doivent se trouver dans le même locataire AAD que le serveur SQL Database ou Data Warehouse. Les interactions entre des coffres de clés et un serveur situés dans des locataires différents ne sont pas prises en charge. Une ressource qui est chiffrée avec une clé Key Vault ne peut pas être déplacée d’un abonnement Azure à un autre. Le déplacement d’une ressource entre abonnements rompt les contrôles d’accès à Key Vault qui sont nécessaires pour utiliser TDE avec prise en charge de BYOK. Si vous devez déplacer une ressource vers un autre abonnement, changez le mode TDE de BYOK à [TDE géré par le service](transparent-data-encryption-azure-sql.md). 

Les protecteurs TDE uniques pour une base de données ou un entrepôt de données ne sont pas pris en charge. Le protecteur TDE est défini au niveau du serveur et est hérité par toutes les ressources du serveur. 

## <a name="guidelines-for-managing-encrypted-databases"></a>Conseils pour la gestion des bases de données chiffrées

### <a name="high-availability-and-disaster-recovery"></a>Haute disponibilité et récupération d’urgence
  
La géoréplication doit être configurée pour le coffre de clés afin de garantir la haute disponibilité des éléments de clé dans Azure Key Vault :

- **Key Vault redondant** : chaque serveur géorépliqué a accès à un coffre de clés distinct, de préférence situé dans la même région Azure. C’est la configuration recommandée, car chaque serveur a ainsi sa propre copie du protecteur TDE pour les bases de données géorépliquées chiffrées. Si une des régions Azure des serveurs n’est plus accessible, les autres serveurs gardent leur accès aux bases de données géorépliquées.  Cela doit être configuré avec soin. En effet, en cas d’indisponibilité d’un coffre de clés, le serveur doit pouvoir accéder à la sauvegarde du protecteur TDE dans l’autre coffre de clés.     


Pour commencer, utilisez l’applet de commande [Add-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey) pour ajouter la clé Key Vault de chaque serveur aux autres serveurs dans le lien de géoréplication.  
(Exemple de valeur KeyId dans Key Vault : *https://contosokeyvault.vault.azure.net/keys/Key1/1a1a2b2b3c3c4d4d5e5e6f6f7g7g8h8h*)

   ```powershell
   <# Include the version guid in the KeyId #>
   Add-AzureRmSqlServerKeyVaultKey `
   -KeyId <KeyVaultKeyId> `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```

>[!NOTE]
>La longueur totale du nom Key Vault et du nom de la clé ne doit pas dépasser 94 caractères.
>

Suivez les étapes décrites dans [Vue d’ensemble de la géoréplication active](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview) pour configurer la géoréplication active avec ces serveurs et déclencher un basculement.  

### <a name="backup-and-restore"></a>Sauvegarde et restauration

Une fois qu’une base de données est chiffrée avec TDE et une clé Key Vault, toutes les sauvegardes effectuées ensuite sont également chiffrées avec le même protecteur TDE.

Pour restaurer une sauvegarde chiffrée avec un protecteur TDE de Key Vault, assurez-vous que les éléments de clé se trouvent toujours dans le coffre Key Vault d’origine sous le nom de clé initial. Quand le protecteur TDE est substitué pour une base de données, les anciennes sauvegardes de la base de données **ne sont pas** mises à jour pour utiliser le nouveau protecteur TDE. C’est pourquoi nous vous recommandons de conserver toutes les anciennes versions du protecteur TDE dans Key Vault pour pouvoir restaurer des sauvegardes de la base de données en cas de besoin. 

Si une clé nécessaire pour restaurer une sauvegarde n’est plus dans le coffre Key Vault d’origine, un message d’erreur similaire à celui-ci est retourné : « Le serveur cible <Servername> n’a pas accès à tous les URI AKV créés entre le <Timestamp #1> et le <Timestamp #2>. Restaurez tous les URI AKV, puis réessayez l’opération. »

Pour corriger cela, utilisez l’applet de commande [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) afin d’obtenir la liste de toutes les clés Key Vault ayant été ajoutées au serveur. Pour vous assurer que toutes les sauvegardes peuvent être restaurées, vérifiez que le serveur cible de sauvegarde a accès à l’ensemble de ces clés.

   ```powershell
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
Pour en savoir plus sur la récupération d’une sauvegarde pour SQL Database, consultez [Récupérer une base de données Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-recovery-using-backups). Pour en savoir plus sur la récupération d’une sauvegarde pour SQL Data Warehouse, consultez [Récupérer un entrepôt de données Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-restore-database-overview).

## <a name="best-practices"></a>Meilleures pratiques

### <a name="key-management"></a>Gestion des clés 

Pour garantir la récupération rapide des clés et avoir accès à vos données en dehors d’Azure, suivez ces conseils :
- Créer votre clé de chiffrement localement sur un appareil HSM local. (Assurez-vous qu’il s’agit d’une clé RSA 2048 bits asymétrique, et donc stockable dans Azure Key Vault.)
- Importez le fichier de clé de chiffrement (.pfx, .byok ou .backup) dans Azure Key Vault. Vous pouvez utiliser un coffre de clés en activant [soft-suppression](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete) pour bénéficier d’une protection de récupération contre une suppression accidentelle de la clé.
- Avant d’utiliser la clé dans le coffre de clés Azure pour la première fois, sauvegardez une clé Azure Key Vault. En savoir plus sur la commande [Backup-AzureKeyVaultKey](https://msdn.microsoft.com/library/mt126292.aspx) .
- Chaque fois que des modifications sont apportées à la clé (par exemple, ajout de listes de contrôle d’accès, ajout de balises, ajout d’attributs clé), veillez à sauvegarder une autre clé Azure Key Vault.
- Si vous effectuez une substitution de clé, n’oubliez pas de **conserver les versions précédentes de la clé** dans le coffre de clés pour pouvoir restaurer d’anciennes sauvegardes de la base de données en cas de besoin. 

Dans les scénarios de production, commencez par créer localement la clé de chiffrement TDE, puis importez la clé asymétrique. Cette méthode est fortement recommandée, car elle permet à l’administrateur de déposer la clé dans un système de dépôt de clé (Key escrow). Si la clé asymétrique est créée dans Azure Key Vault, elle ne peut pas être déposée, car la clé privée ne quitte jamais le coffre. Les clés utilisées pour protéger les données critiques doivent être déposées. Si une clé asymétrique est perdue, les données sont définitivement irrécupérables.

### <a name="pre-configuration-for-replicated-databases"></a>Préconfiguration pour les bases de données répliquées

Si vous devez répliquer une base de données chiffrée sur un autre serveur, assurez-vous que le serveur a accès à une copie des éléments de clé Key Vault utilisés sur l’autre serveur **avant** de déplacer ou répliquer la base de données.  

Nous recommandons de donner à chaque serveur l’accès à une copie des éléments de clé Key Vault qui sont utilisés sur l’autre serveur et stockés dans un coffre de clés séparé (dans l’idéal, les deux doivent être situés dans la même région Azure que le serveur). Avec cette configuration, chaque serveur a sa propre copie du protecteur TDE pour les bases de données répliquées chiffrées. Si une des régions Azure des serveurs n’est plus accessible, les autres serveurs gardent leur accès aux bases de données répliquées.

## <a name="next-steps"></a>Étapes suivantes

- Commencez à utiliser TDE avec prise en charge de Bring Your Own Key : [Activer TDE avec votre propre clé Key Vault à l’aide de PowerShell](transparent-data-encryption-byok-azure-sql-configure.md)
- Découvrez comment effectuer une rotation du protecteur TDE d’un serveur, conformément aux exigences de sécurité : [Effectuer une rotation du protecteur TDE (Transparent Data Encryption) à l’aide de PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md).
- En cas d’incident de sécurité, découvrez comment supprimer un protecteur TDE potentiellement compromis : [Supprimer une clé potentiellement compromise](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md) 
