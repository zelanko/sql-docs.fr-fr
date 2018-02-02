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
ms.openlocfilehash: 5621bbaf20f30371ffabafddc0520dd15b8e4723
ms.sourcegitcommit: e851f3cab09f8f09a9a4cc0673b513a1c4303d2d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="transparent-data-encryption-with-bring-your-own-key-preview-support-for-azure-sql-database-and-data-warehouse"></a>Transparent Data Encryption avec prise en charge de la fonctionnalité BYOK (préversion) pour Azure SQL Database et Data Warehouse
[!INCLUDE[appliesto-xx-asdb-asdw-xxx-md](../../../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

La prise en charge de BYOK (Bring Your Own Key) pour [TDE (Transparent Data Encryption)](transparent-data-encryption.md) vous permet de chiffrer la clé de chiffrement de la base de données (DEK) avec une clé asymétrique appelée protecteur TDE.  Le protecteur TDE est stocké sous votre contrôle dans [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault), système de gestion de clés externes basé sur le cloud Azure. Azure Key Vault est le premier service de gestion de clés auquel TDE a intégré la prise en charge de BYOK. La clé DEK TDE, stockée dans la page de démarrage de la base de données, est chiffrée et déchiffrée par le protecteur TDE. Le protecteur TDE est stocké dans Azure Key Vault et ne quitte jamais le coffre de clés. Si l’accès du serveur au coffre de clés est révoqué, la base de données ne peut pas être déchiffrée et lue en mémoire.  Le protecteur TDE est défini au niveau du serveur logique et est hérité de toutes les bases de données associées à ce serveur. 

Avec la prise en charge de BYOK, les utilisateurs peuvent maintenant gérer diverses tâches de gestion des clés, notamment les rotations de clés, les autorisations de coffre de clés, la suppression de clés, ainsi que l’audit et le reporting sur tous les protecteurs TDE avec la fonctionnalité Azure Key Vault. Key Vault propose une gestion centralisée des clés, tire parti des modules de sécurité matériels (HSM) étroitement surveillés et permet la séparation des responsabilités liées à la gestion des clés et des données pour garantir la conformité réglementaire.  


L’utilisation de TDE avec prise en charge de BYOK présente les avantages suivants :
- Une plus grande transparence et un contrôle plus précis avec la possibilité de gérer soi-même le protecteur TDE   
- Une gestion centralisée des protecteurs TDE (avec d’autres clés et secrets utilisés dans d’autres services Azure) en les hébergeant dans Key Vault
- Séparation des responsabilités de gestion des clés et des données dans l’organisation pour permettre la répartition des tâches
- Une sécurité accrue par rapport à vos propres clients, Key Vault étant conçu pour que Microsoft n’ait pas à connaître ou extraire les clés de chiffrement 
- Prise en charge de la rotation des clés

> [!IMPORTANT]
> Si vous utilisez un chiffrement TDE géré par le service et souhaitez commencer à utiliser Key Vault, sachez que TDE reste activé pendant le processus de remplacement par un protecteur TDE dans Key Vault. Ce processus n’entraîne pas de temps d’arrêt ni de rechiffrement des fichiers de la base de données. Le remplacement d’une clé gérée par le service par une clé Key Vault nécessite uniquement de rechiffrer la clé DEK, qui est une opération en ligne rapide. 
>

## <a name="how-does-tde-with-byok-support-work"></a>Comment fonctionne TDE avec prise en charge de BYOK ?
 
![Authentification du serveur auprès de Key Vault](./media/transparent-data-encryption-byok-azure-sql/tde-byok-server-authentication-flow.PNG)

Quand TDE est d’abord configuré pour utiliser un protecteur TDE dans Key Vault, le serveur envoie la clé DEK de chaque base de données avec TDE activé à Key Vault pour demander d’inclure la clé. Key Vault retourne la clé de chiffrement de la base de données chiffrée, qui est stockée dans la base de données utilisateur.  

>[!IMPORTANT]
>Il est important de noter qu’**une fois qu’un protecteur TDE est stocké dans Azure Key Vault, il ne quitte jamais Azure Key Vault**. Le serveur logique peut uniquement envoyer des demandes d’opération de clé aux éléments de clé du protecteur TDE contenus dans Key Vault et **jamais n’accède ni ne met en cache le protecteur TDE**. L’administrateur de Key Vault a le droit de révoquer les autorisations Key Vault du serveur à tout moment, auquel cas toutes les connexions au serveur sont interrompues. 
>


## <a name="guidelines-for-configuring-tde-with-byok"></a>Instructions de configuration de TDE pour BYOK

### <a name="general-guidelines"></a>Instructions générales
- Vérifiez qu’Azure Key Vault et Azure SQL Database sont dans le même locataire.  Les interactions entre coffre de clés et serveur qui sont dans des locataires différents **ne sont pas prises en charge**.

- Décidez des abonnements qui vont être utilisés pour les ressources requises. Si par la suite vous déplacez le serveur parmi les abonnements, vous devrez réinstaller TDE avec des clés BYOK.
- Configurez Azure Key Vault dans un seul abonnement réservé aux protecteurs TDE SQL Database.  Toutes les bases de données associées à un serveur logique utilisent le même protecteur TDE, donc le regroupement de bases de données dans un serveur logique est à considérer. 
- Recommandé : Conservez une copie du protecteur TDE en local.  Pour ce faire, vous devez avoir un appareil HSM pour créer un protecteur TDE en local et un système de dépôt de clés pour stocker une copie locale du protecteur TDE.


### <a name="guidelines-for-configuring-azure-key-vault"></a>Instructions de configuration d’Azure Key Vault

- Utilisez un coffre de clés avec [soft-delete](https://docs.microsoft.com/azure/key-vault/key-vault-ovw-soft-delete) activé pour éviter de perdre des données en cas de suppression accidentelle d’une clé ou d’un coffre de clés :  
  - Les ressources supprimées de manière réversible sont conservées pendant une durée définie, 90 jours, sauf si elles sont récupérées ou vidées.
  - Les actions de **récupération** et de **vidage** ont leurs propres autorisations associées dans une stratégie d’accès au coffre de clés. 
- Accordez l’accès au serveur logique au coffre de clés avec son identité AAD (Azure Active Directory).  Lorsque vous utilisez l’interface utilisateur du portail, l’identité AAD est automatiquement créée et les autorisations d’accès au coffre de clés sont accordées au serveur.  Si vous utilisez PowerShell pour configurer TDE avec BYOK, l’identité AAD doit être créée et vérifiée. Consultez [Configurer TDE avecBYOK](transparent-data-encryption-byok-azure-sql-configure.md) pour obtenir des instructions détaillées sur l’utilisation de PowerShell.

  >[!NOTE]
  >Si l’identité AAD **est accidentellement supprimée ou si les autorisations du serveur sont révoquées** avec la stratégie d’accès au coffre de clés, le serveur perd l’accès au coffre de clés.
  >
  
- Permettre l’audit et le reporting sur toutes les clés de chiffrement : Key Vault fournit des fichiers journaux que vous pouvez facilement injecter dans d’autres outils de gestion des événements et des informations de sécurité (SIEM). Le service [Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-azure-key-vault) d’OMS (Operations Management Suite) est un exemple de service déjà intégré.
- Pour assurer une haute disponibilité des bases de données chiffrées, configurez chaque serveur logique avec deux coffres de clé Azure de différentes régions.


### <a name="guidelines-for-configuring-the-tde-protector-asymmetric-key-stored-in-azure-key-vault"></a>Instructions de configuration du protecteur TDE (clé asymétrique) stocké dans Azure Key Vault

- Créez votre clé de chiffrement localement sur un appareil HSM local. Vérifiez qu’il s’agit d’une clé RSA 2048 bits asymétrique, et donc stockable dans Azure Key Vault.
- Déposez la clé dans un système de dépôt de clés.  
- Importez le fichier de clé de chiffrement (.pfx, .byok ou .backup) dans Azure Key Vault. 
    
    >[!NOTE] 
    >Pour des tests, il est possible de créer une clé avec Azure Key Vault. Toutefois, cette clé ne peut pas être déposée, car la clé privée ne peut jamais quitter le coffre de clés.  Sauvegardez et déposez toujours les clés utilisées pour chiffrer les données de production, car la perte de la clé (suppression accidentelle dans le coffre de clés, expiration, etc.) entraîne la perte définitive des données.
    >
    
- Utilisez une clé sans date d’expiration et ne définissez jamais une date d’expiration sur une clé déjà en cours d’utilisation : **une fois que la clé expire, les bases de données chiffrées perdent l’accès à leur protecteur TDE et sont supprimées dans les 24 heures**.
- Vérifiez que la clé est activée et qu’elle dispose des autorisations *get*, *wrap key* et *unwrap key*.
- Créez une sauvegarde de la clé Azure Key Vault avant d’utiliser la clé dans Azure Key Vault pour la première fois. En savoir plus sur la commande [Backup-AzureKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey?view=azurermps-5.1.1) .
- Créez une sauvegarde chaque fois que des modifications sont apportées à la clé (par exemple, ajout de listes de contrôle d’accès, de balises ou d’attributs de clé).
- **Conservez les versions précédentes** de la clé dans le coffre de clés lors de la rotation de clés pour pouvoir restaurer d’anciennes sauvegardes. Quand vous changez de protecteur TDE pour une base de données, les anciennes sauvegardes de la base de données **ne sont pas mises à jour** pour utiliser le protecteur TDE le plus récent.  Chaque sauvegarde nécessite le protecteur TDE qu’elle a créé lors de la restauration. Vous pouvez effectuer des rotations de clés en suivant les instructions dans [Effectuer une rotation du protecteur TDE à l’aide de PowerShell](transparent-data-encryption-byok-azure-sql-key-rotation.md).
- Conservez toutes les clés déjà utilisées dans Azure Key Vault après avoir changé les clés gérées par le service.  Vous pourrez ainsi restaurer des sauvegardes de base de données avec les protecteurs TDE stockés dans Azure Key Vault.  Les protecteurs TDE créés avec Azure Key Vault doivent être conservés jusqu'à ce que toutes les sauvegardes stockées soient créées avec les clés gérées par le service.  
- Procédez à des copies de sauvegarde récupérables de ces clés avec [Backup-AzureKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.keyvault/backup-azurekeyvaultkey?view=azurermps-5.1.1).
- Pour supprimer une clé potentiellement compromise pendant un incident de sécurité sans risquer de perdre des données, suivez les étapes dans [Supprimer une clé potentiellement compromise](transparent-data-encryption-byok-azure-sql-remove-tde-protector.md).


## <a name="high-availability-geo-replication-and-backup--restore"></a>Haute disponibilité, géoréplication et sauvegarde/restauration

### <a name="high-availability-and-disaster-recovery"></a>Haute disponibilité et récupération d’urgence

Le mode de configuration de la haute disponibilité avec Azure Key Vault dépend de la configuration de votre base de données et de votre serveur logique. Voici les configurations recommandées pour les deux cas distincts.  Le premier cas est un serveur logique ou une base de données autonome sans géoredondance configurée.  Le deuxième cas est une base de données ou un serveur logique configuré avec des groupes de basculement ou la géoredondance, où vous devez veiller à ce que chaque copie géoredondante ait un coffre de clés Azure local dans le groupe de basculement pour que les géobasculements fonctionnent. Dans le premier cas, si vous avez besoin d’une base de données et d’un serveur logique avec une haute disponibilité sans géoredondance configurée, il est vivement recommandé de configurer le serveur de sorte à utiliser deux coffres de clés distincts dans deux régions distinctes avec les mêmes éléments de clé.  Pour ce faire, vous pouvez créer un protecteur TDE avec le coffre de clés principal situé dans la même région que le serveur logique, puis cloner la clé dans un coffre de clés d’une autre région Azure pour que le serveur ait accès au second coffre de clés si jamais le coffre de clés principal tombe en panne alors que la base de données fonctionne. Utilisez l’applet de commande Backup-AzureKeyVaultKey pour récupérer la clé dans un format chiffré dans le coffre de clé principal, puis utilisez l’applet de commande Restore-AzureKeyVaultKey et spécifiez un coffre de clés dans la seconde région.


![Serveur unique à haute disponibilité et aucune géorécupération d’urgence](./media/transparent-data-encryption-byok-azure-sql/SingleServer_HA_Config.PNG)

Dans le deuxième cas, il est nécessaire de configurer des coffres de clés Azure redondants basés sur les groupes de basculement SQL Database existants ou les copies de géoréplication actives des bases de données pour maintenir une haute disponibilité des protecteurs TDE dans le coffre de clés Azure.  Chaque serveur géorépliqué exige un coffre de clés distinct, de préférence situé dans la même région Azure que son serveur. Si une base de données primaire devient inaccessible en raison d’une panne dans une région et qu’un basculement est déclenché, la base de données secondaire peut prendre le relais avec le coffre de clés secondaire.  

![Groupes de basculement et géorécupération d’urgence](./media/transparent-data-encryption-byok-azure-sql/Geo_DR_Config.PNG)

Pour garantir un accès continu au protecteur TDE dans Azure Key Vault lors d’un basculement, vous devez le configurer avant la réplication ou le basculement d’une base de données sur un serveur secondaire. Les serveurs principal et secondaire doivent stocker les copies des protecteurs TDE dans tous les autres coffres de clés Azure, ce qui signifie que dans cet exemple, les mêmes clés sont stockées dans les deux coffres de clés.

Pour ajouter une clé existante d’un coffre de clés dans un autre coffre de clés, utilisez l’applet de commande [Add-AzureRmSqlServerKeyVaultKey](https://docs.microsoft.com/en-us/powershell/module/azurerm.sql/add-azurermsqlserverkeyvaultkey).

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

Pour corriger cela, exécutez l’applet de commande [Get-AzureRmSqlServerKeyVaultKey](/powershell/module/azurerm.sql/get-azurermsqlserverkeyvaultkey) afin d’obtenir la liste des clés du coffre de clés qui ont été ajoutées au serveur (sauf si elles ont été supprimées par un utilisateur). Pour vous assurer que toutes les sauvegardes peuvent être restaurées, vérifiez que le serveur cible de sauvegarde a accès à l’ensemble de ces clés.

   ```powershell
   Get-AzureRmSqlServerKeyVaultKey `
   -ServerName <LogicalServerName> `
   -ResourceGroup <SQLDatabaseResourceGroupName>
   ```
Pour en savoir plus sur la récupération d’une sauvegarde pour SQL Database, consultez [Récupérer une base de données Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-recovery-using-backups). Pour en savoir plus sur la récupération d’une sauvegarde pour SQL Data Warehouse, consultez [Récupérer un entrepôt de données Azure SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-restore-database-overview).
