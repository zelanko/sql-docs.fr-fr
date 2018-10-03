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
ms.openlocfilehash: e3084e9d878085c20ab8af27cffb04758efceaab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200839"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database
  Cette page fournit des liens qui vous aideront à trouver les informations dont vous avez besoin sur la sécurité et la protection dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Les fonctionnalités d’ [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] ne cessent d’être améliorées. Consultez la version la plus récente de cette rubrique pour obtenir les dernières informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Authentification : qui êtes-vous ?|Autorisation : que pouvez-vous faire ?|Chiffrement : stockage de données secrètes|Sécurité de connexion : restriction et sécurisation|Audit : enregistrement de l’accès|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Qui effectue l'authentification ?**<br /><br /> [![Plan du centre de sécurité-authentification Windows](../../database-engine/media/security-center-map-windows-authenticaion.png "plan du centre de sécurité, authentification de Windows")](http://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Authentification SQL Server de Security Center carte](../../database-engine/media/security-center-map-sql-authenticaion.png "Security Center carte authentification SQL Server")](http://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Où est effectuée l’authentification ?**<br /><br /> [![Centre de sécurité mapper les connexions et utilisateurs](../../database-engine/media/security-center-map-logins-users.png "Security Center mapper les connexions et utilisateurs")](http://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Plan du centre de sécurité contenus aux utilisateurs de base de données](../../database-engine/media/security-center-map-contained-users.png "sécurité centrer la carte contenait des utilisateurs de base de données")](http://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Utilisation d'autres identités**<br /><br /> [![Informations d’identification de carte de Security Center](../../database-engine/media/security-center-map-credentials.png "informations d’identification de carte de Security Center")](http://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Plan du centre de sécurité-exécuter en tant que connexion](../../database-engine/media/security-center-map-exec-as-login.png "plan du centre de sécurité-exécuter en tant que connexion")](http://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Plan du centre de sécurité-exécuter en tant qu’utilisateur](../../database-engine/media/security-center-map-exec-as-user.png "plan du centre de sécurité-exécuter en tant qu’utilisateur")](http://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")|**Octroi, révocation et refus d'autorisations**<br /><br /> [![Centre de sécurité mapper des Classes sécurisables](../../database-engine/media/security-center-map-securable-classes.png "Security Center mapper des Classes sécurisables")](http://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Plan du centre de sécurité, autorisations de serveur](../../database-engine/media/security-center-map-srv-perms.png "plan du centre de sécurité, autorisations de serveur")](http://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Plan du centre de sécurité, autorisations de base de données](../../database-engine/media/security-center-map-db-perms.png "plan du centre de sécurité, autorisations de base de données")](http://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sécurité par rôles**<br /><br /> [![Plan du centre de sécurité, rôles de serveur](../../database-engine/media/security-center-map-srv-roles.png "plan du centre de sécurité, rôles de serveur")](http://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Plan du centre de sécurité, rôles de base de données](../../database-engine/media/security-center-map-db-roles.png "plan du centre de sécurité, rôles de base de données")](http://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Procédures et vues de carte de Security Center](../../database-engine/media/security-center-map-view-procs.png "procédures et vues de carte de Security Center")](http://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Sécurité au niveau des lignes de carte de Security Center](../../database-engine/media/security-center-map-row-level-sec.png "sécurité au niveau des lignes de carte de Security Center")](http://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Centre de sécurité carte masquage dynamique des données](../../database-engine/media/security-center-map-data-masking.png "Security Center carte masquage dynamique des données")](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Plan du centre de sécurité des objets signés](../../database-engine/media/security-center-map-signed-objects.png "sécurité centrer la carte les objets signés")](http://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")|**Chiffrement de fichiers**<br /><br /> [![Centre de sécurité carte BitLocker](../../database-engine/media/security-center-map-bitlocker.png "BitLocker de carte de Security Center")](http://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Plan du centre de sécurité-chiffrement NTFS](../../database-engine/media/security-center-map-ntfs-encryp.png "plan du centre de sécurité-chiffrement NTFS")](http://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Mappage de Security Center TDE](../../database-engine/media/security-center-map-tde.png "Security Center carte TDE")](http://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Plan du centre de sécurité-chiffrement sauvegarde](../../database-engine/media/security-center-map-backup-encryp.png "plan du centre de sécurité-chiffrement sauvegarde")](http://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Chiffrement des sources**<br /><br /> [![Mappage de Security Center EKM](../../database-engine/media/security-center-map-ekm.png "Security Center carte EKM")](http://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Centre de sécurité mapper Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Security Center mapper Azure Key Vault")](http://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Colonne, données et chiffrement à clé**<br /><br /> [![Plan du centre de sécurité-chiffrement par certificat](../../database-engine/media/security-center-map-cert.png "plan du centre de sécurité-chiffrement par certificat")](http://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Plan du centre de sécurité-chiffrement par clé symétrique](../../database-engine/media/security-center-map-sym-key.png "plan du centre de sécurité-chiffrement par clé symétrique")](http://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Plan du centre de sécurité-chiffrement par clé asymétrique](../../database-engine/media/security-center-map-asym-key.png "plan du centre de sécurité-chiffrement par clé asymétrique")](http://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Plan du centre de sécurité-chiffrement par mot de passe](../../database-engine/media/security-center-map-passphrase.png "plan du centre de sécurité-chiffrement par mot de passe")](http://msdn.microsoft.com/library/ms190357.aspx)|**Protection par pare-feu**<br /><br /> [![Plan du centre de sécurité-pare-feu Windows](../../database-engine/media/security-center-map-windows-firewall.png "plan du centre de sécurité-pare-feu Windows")](http://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Plan du centre de sécurité-pare-feu Service](../../database-engine/media/security-center-map-service-firewall.png "plan du centre de sécurité, pare-feu de Service")](http://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Plan du centre de sécurité, pare-feu de base de données](../../database-engine/media/security-center-map-db-firewall.png "plan du centre de sécurité, pare-feu de base de données")](http://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Chiffrement des données en transit**<br /><br /> [![Mappage de centre de sécurité SSL forcé](../../database-engine/media/security-center-map-forced-ssl.png "sécurité centrer la carte SSL forcé")](http://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Centre de sécurité mapper SSL facultatif](../../database-engine/media/security-center-map-opt-ssl.png "Security Center mapper SSL facultatives")](http://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")|**Audit automatisé**<br /><br /> [![Mappage de centre de sécurité SQL Server Audit](../../database-engine/media/security-center-map-sql-audit.png "Security Center mappage SQL Server Audit")](http://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Plan du centre de sécurité SQL Audit de base de données](../../database-engine/media/security-center-map-sqldb-audit.png "plan du centre de sécurité SQL Audit de base de données")](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Audit personnalisé**<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> [![Déclencheurs de carte de Security Center](../../database-engine/media/security-center-map-triggers.png "déclencheurs de carte de Security Center")](http://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Conformité**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](http://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "espace réservé")<br /><br /> ![Légende du centre de sécurité](../../database-engine/media/security-center-map-legend.png "légende du centre de sécurité")|  
  
## <a name="links-to-specific-related-topics"></a>Liens vers des rubriques connexes  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "petite icône de dossier de fichiers") **authentification : qui êtes-vous ?**  
 **Qui effectue l’authentification ? (Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Choisir un mode d’authentification](choose-an-authentication-mode.md)  
  
 **S'authentifier auprès de la base de données MASTER** (connexions et utilisateurs de base de données)  
  
-   [Créer une connexion SQL Server](authentication-access/create-a-login.md)  
  
-   [Gestion des bases de données et des connexions dans Azure SQL Database](http://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Créer un utilisateur de base de données](authentication-access/create-a-database-user.md)  
  
 **S’authentifier auprès d’une base de données utilisateur**  
  
-   [Utilisateurs de base de données autonome - Rendre votre base de données portable](contained-database-users-making-your-database-portable.md)  
  
 **Utilisation d'autres identités**  
  
-   [Informations d’identification &#40;moteur de base de données&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Exécuter en tant qu'autre connexion](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Exécuter en tant qu'autre utilisateur de base de données](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Icône de dossier petit fichier](../../integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") **chiffrement : stockage de données secrètes**  
 **Chiffrement de fichiers**  
  
-   [BitLocker (au niveau du lecteur)](http://support.microsoft.com/kb/2855131)  
  
-   [Chiffrement NTFS (au niveau du dossier)](http://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Chiffrement transparent des données (au niveau du fichier)](encryption/transparent-data-encryption.md)  
  
-   [Chiffrement de la sauvegarde (au niveau du fichier)](../backup-restore/backup-encryption.md)  
  
 **Chiffrement des sources**  
  
-   [Module Gestion de clés extensible](encryption/extensible-key-management-ekm.md)  
  
-   [Clés stockées dans le coffre de clés Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Colonne, données et chiffrement à clé**  
  
-   [Chiffrer par certificat](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Chiffrer par clé asymétrique](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Chiffrer par clé symétrique](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Chiffrer par mot de passe](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "petite icône de dossier de fichiers") **autorisation : que pouvez-vous faire ?**  
 **Octroi, révocation et refus d'autorisations**  
  
-   [Hiérarchie des autorisations &#40;moteur de base de données&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Autorisations](permissions-database-engine.md)  
  
-   [Éléments sécurisables](securables.md)  
  
 **Sécurité par rôles**  
  
-   [Rôles de niveau serveur](authentication-access/server-level-roles.md)  
  
-   [Rôles au niveau de la base de données](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Limiter l'accès aux données à l'aide de [Vues](../views/views.md) et de [Procédures](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Sécurité au niveau des lignes](http://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Masquage dynamique des données](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Objets signés](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Icône de dossier petit fichier](../../integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") **sécurité de la connexion : restriction et sécurisation**  
 **Protection par pare-feu**  
  
-   [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Paramètres de pare-feu Azure SQL Database](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Paramètres de pare-feu du service Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Chiffrement des données en transit**  
  
-   [SSL (Secure Sockets Layer) pour le moteur de base de données](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [SSL (Secure Sockets Layer) pour SQL Database](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Icône de dossier petit fichier](../../integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") **l’audit : enregistrement de l’accès**  
 **Audit automatisé**  
  
-   [SQL Server Audit &#40moteur de base de données&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Audit SQL Database](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Implémentation d’un Audit personnalisé**  
  
-   Création de [DDL Triggers](../triggers/ddl-triggers.md) et de [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Icône de dossier petit fichier](../../integration-services/media/filefolder-small.gif "icône dossier de petits fichiers") **conformité**  
 **SQL Server**  
  
-   [Critères courants](http://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL Database**  
  
-   [Microsoft Azure Trust Center : Conformité par fonctionnalité](http://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de SQL Server](securing-sql-server.md)   
 [Principaux &#40;moteur de base de données&#41;](authentication-access/principals-database-engine.md)   
 [Certificats et clés asymétriques SQL Server](sql-server-certificates-and-asymmetric-keys.md)   
 [Chiffrement SQL Server](encryption/sql-server-encryption.md)   
 [Configuration de la surface d'exposition](surface-area-configuration.md)   
 [Mots de passe forts](strong-passwords.md)   
 [Propriété de base de données TRUSTWORTHY](trustworthy-database-property.md)   
 [Fonctionnalités et tâches du moteur de base de données](../../database-engine/database-engine-features-and-tasks.md)  
  
  
