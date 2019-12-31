---
title: Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fc99b725f4c5895306d544df14bf2a9390189066
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244532"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database
  Cette page fournit des liens qui vous aideront à trouver les informations dont vous avez besoin sur la sécurité et la protection dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Les fonctionnalités d’ [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] ne cessent d’être améliorées. Consultez la version la plus récente de cette rubrique pour obtenir les dernières informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Authentification : qui êtes-vous ?|Autorisation : que pouvez-vous faire ?|Chiffrement : stockage de données secrètes|Sécurité de connexion : restriction et sécurisation|Audit : enregistrement de l’accès|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Qui s’authentifie ?**<br /><br /> [![Plan du Centre de sécurité - Authentification Windows](../../database-engine/media/security-center-map-windows-authenticaion.png "Plan du Centre de sécurité - Authentification Windows")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Plan du Centre de sécurité - Authentification SQL Server](../../database-engine/media/security-center-map-sql-authenticaion.png "Plan du Centre de sécurité - Authentification SQL Server")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Où est-il authentifié ?**<br /><br /> [![Plan du Centre de sécurité - Connexions et utilisateurs](../../database-engine/media/security-center-map-logins-users.png "Plan du Centre de sécurité - Connexions et utilisateurs")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Plan du Centre de sécurité - Utilisateurs de base de données autonome](../../database-engine/media/security-center-map-contained-users.png "Plan du Centre de sécurité - Utilisateurs de base de données autonome")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Utilisation d’autres identités**<br /><br /> [![Plan du Centre de sécurité - Informations d’identification](../../database-engine/media/security-center-map-credentials.png "Plan du Centre de sécurité - Informations d’identification")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Plan du Centre de sécurité - Exécuter en tant que connexion](../../database-engine/media/security-center-map-exec-as-login.png "Plan du Centre de sécurité - Exécuter en tant que connexion")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Plan du Centre de sécurité - Exécuter en tant qu’utilisateur](../../database-engine/media/security-center-map-exec-as-user.png "Plan du Centre de sécurité - Exécuter en tant qu’utilisateur")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Octroi, révocation et refus d’autorisations**<br /><br /> [![Plan du Centre de sécurité - Classes sécurisables](../../database-engine/media/security-center-map-securable-classes.png "Plan du Centre de sécurité - Classes sécurisables")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Plan du Centre de sécurité - Autorisations de serveur](../../database-engine/media/security-center-map-srv-perms.png "Plan du Centre de sécurité - Autorisations de serveur")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Plan du Centre de sécurité - Autorisations de base de données](../../database-engine/media/security-center-map-db-perms.png "Plan du Centre de sécurité - Autorisations de base de données")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sécurité par rôle**<br /><br /> [![Plan du Centre de sécurité - Rôles serveur](../../database-engine/media/security-center-map-srv-roles.png "Plan du Centre de sécurité - Rôles serveur")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Plan du Centre de sécurité - Rôles de base de données](../../database-engine/media/security-center-map-db-roles.png "Plan du Centre de sécurité - Rôles de base de données")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Plan du Centre de sécurité - Vues et procédures](../../database-engine/media/security-center-map-view-procs.png "Plan du Centre de sécurité - Vues et procédures")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Plan du Centre de sécurité - Sécurité au niveau des lignes](../../database-engine/media/security-center-map-row-level-sec.png "Plan du Centre de sécurité - Sécurité au niveau des lignes")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Plan du Centre de sécurité - Masquage des données dynamiques](../../database-engine/media/security-center-map-data-masking.png "Plan du Centre de sécurité - Masquage des données dynamiques")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Plan du Centre de sécurité - Objets signés](../../database-engine/media/security-center-map-signed-objects.png "Plan du Centre de sécurité - Objets signés")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Chiffrement des fichiers**<br /><br /> [![Plan du Centre de sécurité - BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Plan du Centre de sécurité - BitLocker")](https://support.microsoft.com/kb/2855131)<br /><br /> [![Plan du Centre de sécurité - Chiffrement NTFS](../../database-engine/media/security-center-map-ntfs-encryp.png "Plan du Centre de sécurité - Chiffrement NTFS")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Plan du Centre de sécurité - TDE](../../database-engine/media/security-center-map-tde.png "Plan du Centre de sécurité - TDE")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Plan du Centre de sécurité - Chiffrement de sauvegarde](../../database-engine/media/security-center-map-backup-encryp.png "Plan du Centre de sécurité - Chiffrement de sauvegarde")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Chiffrement des sources**<br /><br /> [![Plan du Centre de sécurité - EKM](../../database-engine/media/security-center-map-ekm.png "Plan du Centre de sécurité - EKM")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Plan du Centre de sécurité - Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Plan du Centre de sécurité - Azure Key Vault")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Colonne, données & le chiffrement de clé**<br /><br /> [![Security Center mapper le chiffrement par certificat](../../database-engine/media/security-center-map-cert.png "Security Center mapper le chiffrement par certificat")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Plan du Centre de sécurité - Chiffrement par clé symétrique](../../database-engine/media/security-center-map-sym-key.png "Plan du Centre de sécurité - Chiffrement par clé symétrique")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Plan du Centre de sécurité - Chiffrer par clé asymétrique](../../database-engine/media/security-center-map-asym-key.png "Plan du Centre de sécurité - Chiffrer par clé asymétrique")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Plan du Centre de sécurité - Chiffrement par mot de passe](../../database-engine/media/security-center-map-passphrase.png "Plan du Centre de sécurité - Chiffrement par mot de passe")](https://msdn.microsoft.com/library/ms190357.aspx)|**Protection par pare-feu**<br /><br /> [![Plan du Centre de sécurité - Pare-feu Windows](../../database-engine/media/security-center-map-windows-firewall.png "Plan du Centre de sécurité - Pare-feu Windows")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Plan du Centre de sécurité - Pare-feu du service](../../database-engine/media/security-center-map-service-firewall.png "Plan du Centre de sécurité - Pare-feu du service")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Plan du Centre de sécurité - Pare-feu de base de données](../../database-engine/media/security-center-map-db-firewall.png "Plan du Centre de sécurité - Pare-feu de base de données")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Chiffrement des données en transit**<br /><br /> [![Plan du Centre de sécurité - SSL forcé](../../database-engine/media/security-center-map-forced-ssl.png "Plan du Centre de sécurité - SSL forcé")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Plan du Centre de sécurité - SSL facultatif](../../database-engine/media/security-center-map-opt-ssl.png "Plan du Centre de sécurité - SSL facultatif")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")|**Audit automatisé**<br /><br /> [![Plan du Centre de sécurité - SQL Server Audit](../../database-engine/media/security-center-map-sql-audit.png "Plan du Centre de sécurité - SQL Server Audit")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Plan du Centre de sécurité - Audit SQL Database](../../database-engine/media/security-center-map-sqldb-audit.png "Plan du Centre de sécurité - Audit SQL Database")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Audit personnalisé**<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> [![Plan du Centre de sécurité - Déclencheurs](../../database-engine/media/security-center-map-triggers.png "Plan du Centre de sécurité - Déclencheurs")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Satisfaire**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Placeholder](../../database-engine/media/security-center-map-blankplaceholder.png "Placeholder")<br /><br /> ![Légende du Centre de sécurité](../../database-engine/media/security-center-map-legend.png "Légende du Centre de sécurité")|  
  
## <a name="links-to-specific-related-topics"></a>Liens vers des rubriques connexes  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **authentification : qui êtes-vous ?**  
 **Qui s’authentifie ? (Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Choisir un mode d’authentification](choose-an-authentication-mode.md)  
  
 **S’authentifier au niveau de la base de données Master** (connexions et utilisateurs de base de données)  
  
-   [Créer une connexion SQL Server](authentication-access/create-a-login.md)  
  
-   [Gestion des bases de données et des connexions dans Azure SQL Database](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Créer un utilisateur de base de données](authentication-access/create-a-database-user.md)  
  
 **S'authentifier auprès d'une base de données utilisateur**  
  
-   [Utilisateurs de base de données à relation contenant-contenu-rendre votre base de données portable](contained-database-users-making-your-database-portable.md)  
  
 **Utilisation d’autres identités**  
  
-   [Informations d’identification &#40;Moteur de base de données&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Exécuter en tant qu’autre connexion](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Exécuter en tant qu’autre utilisateur de base de données](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **chiffrement : stockage des données secrètes**  
 **Chiffrement des fichiers**  
  
-   [BitLocker (au niveau du lecteur)](https://support.microsoft.com/kb/2855131)  
  
-   [Chiffrement NTFS (au niveau du dossier)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Transparent Data Encryption (au niveau du fichier)](encryption/transparent-data-encryption.md)  
  
-   [Chiffrement de la sauvegarde (au niveau du fichier)](../backup-restore/backup-encryption.md)  
  
 **Chiffrement des sources**  
  
-   [Module de gestion de clés extensible](encryption/extensible-key-management-ekm.md)  
  
-   [Clés stockées dans le Azure Key Vault](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Chiffrement des colonnes, des données et des clés**  
  
-   [Chiffrer par certificat](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Chiffrer par clé asymétrique](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Chiffrer par clé symétrique](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Chiffrer par phrase secrète](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **autorisation : que pouvez-vous faire ?**  
 **Octroi, révocation et refus d’autorisations**  
  
-   [Hiérarchie des autorisations &#40;Moteur de base de données&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Autorisations](permissions-database-engine.md)  
  
-   [Éléments sécurisables](securables.md)  
  
 **Sécurité par rôle**  
  
-   [Rôles au niveau du serveur](authentication-access/server-level-roles.md)  
  
-   [Rôles au niveau de la base de données](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Limiter l'accès aux données à l'aide de [Vues](../views/views.md) et de [Procédures](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Sécurité au niveau des lignes](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Masquage de données dynamiques](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Objets signés](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **sécurité de connexion : restriction et sécurisation**  
 **Protection par pare-feu**  
  
-   [Configurer un pare-feu Windows pour l’accès Moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Paramètres du pare-feu Azure SQL Database](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Paramètres du pare-feu du service Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Chiffrement des données en transit**  
  
-   [protocole SSL pour le Moteur de base de données](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [protocole SSL pour SQL Database](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **audit : enregistrement** de l’accès  
 **Audit automatisé**  
  
-   [Audit SQL Server &#40;Moteur de base de données&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Audit des SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Implémentation de l’audit personnalisé**  
  
-   Création de [DDL Triggers](../triggers/ddl-triggers.md) et de [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **compatibilité**  
 **SQL Server**  
  
-   [Critères communs](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL Database**  
  
-   [Centre de gestion de la confidentialité Microsoft Azure : conformité par fonctionnalité](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de SQL Server](securing-sql-server.md)   
 [Principaux &#40;Moteur de base de données&#41;](authentication-access/principals-database-engine.md)   
 [Certificats SQL Server et clés asymétriques](sql-server-certificates-and-asymmetric-keys.md)   
 [Chiffrement SQL Server](encryption/sql-server-encryption.md)   
 [Configuration de la surface d’exposition](surface-area-configuration.md)   
 [Mots de passe forts](strong-passwords.md)   
 [Propriété de base de données TRUSTWORTHY](trustworthy-database-property.md)   
 [Fonctionnalités et tâches de Moteur de base de données](../../database-engine/database-engine-features-and-tasks.md)  
  
  
