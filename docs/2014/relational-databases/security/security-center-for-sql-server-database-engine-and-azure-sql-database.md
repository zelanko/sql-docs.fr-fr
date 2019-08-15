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
ms.openlocfilehash: 131fb3639f84c1b59796d59bcfff17159da8f063
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028657"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database
  Cette page fournit des liens qui vous aideront à trouver les informations dont vous avez besoin sur la sécurité et la protection dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)].  
  
> [!NOTE]  
>  Les fonctionnalités d’ [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] ne cessent d’être améliorées. Consultez la version la plus récente de cette rubrique pour obtenir les dernières informations sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Authentification : qui êtes-vous ?|L' que pouvez-vous faire ?|Chiffre stockage de données secrètes|Sécurité de la connexion: restriction et sécurisation|Audit : enregistrement de l’accès|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Qui effectue l'authentification ?**<br /><br /> [![Security Center mapper l’authentification Windows](../../database-engine/media/security-center-map-windows-authenticaion.png "Security Center mapper l’authentification Windows")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![SQL Server l’authentification par mappage de Security Center](../../database-engine/media/security-center-map-sql-authenticaion.png "SQL Server l’authentification par mappage de Security Center")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Où est effectuée l’authentification ?**<br /><br /> [![Security Center mapper des connexions et des utilisateurs](../../database-engine/media/security-center-map-logins-users.png "Security Center mapper des connexions et des utilisateurs")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Carte de Security Center contenu utilisateurs de la base de données](../../database-engine/media/security-center-map-contained-users.png "Carte de Security Center contenu utilisateurs de la base de données")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Utilisation d'autres identités**<br /><br /> [![Informations d’identification] de la carte de Security Center (../../database-engine/media/security-center-map-credentials.png "Informations d’identification") de la carte de Security Center](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Security Center mapper exécuter en tant que connexion](../../database-engine/media/security-center-map-exec-as-login.png "Security Center mapper exécuter en tant que connexion")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Security Center mapper exécuter en tant qu’utilisateur](../../database-engine/media/security-center-map-exec-as-user.png "Security Center mapper exécuter en tant qu’utilisateur")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")|**Octroi, révocation et refus d'autorisations**<br /><br /> [![Classes sécurisables de mappage de Security Center](../../database-engine/media/security-center-map-securable-classes.png "Classes sécurisables de mappage de Security Center")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Security Center mapper des autorisations de serveur](../../database-engine/media/security-center-map-srv-perms.png "Security Center mapper des autorisations de serveur")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Security Center mapper des autorisations de base de données](../../database-engine/media/security-center-map-db-perms.png "Security Center mapper des autorisations de base de données")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sécurité par rôles**<br /><br /> [![Rôles de serveur de carte de Security Center](../../database-engine/media/security-center-map-srv-roles.png "Rôles de serveur de carte de Security Center")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Rôles de base de données Security Center Map](../../database-engine/media/security-center-map-db-roles.png "Rôles de base de données Security Center Map")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Vues et procédures de la carte de Security Center](../../database-engine/media/security-center-map-view-procs.png "Vues et procédures de la carte de Security Center")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Carte de Security Center sécurité au niveau des lignes](../../database-engine/media/security-center-map-row-level-sec.png "Carte de Security Center sécurité au niveau des lignes")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Carte de Security Center Dynamic Data Masking](../../database-engine/media/security-center-map-data-masking.png "Carte de Security Center Dynamic Data Masking")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Security Center mapper des objets signés](../../database-engine/media/security-center-map-signed-objects.png "Security Center mapper des objets signés")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")|**Chiffrement de fichiers**<br /><br /> [![Carte de Security Center BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Carte de Security Center BitLocker")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Security Center mapper le chiffrement NTFS](../../database-engine/media/security-center-map-ntfs-encryp.png "Security Center mapper le chiffrement NTFS")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![TDE carte de Security Center](../../database-engine/media/security-center-map-tde.png "TDE carte de Security Center")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [Chiffrement de la ![sauvegarde de Security Center mappage] Chiffrement de la (../../database-engine/media/security-center-map-backup-encryp.png "sauvegarde de Security Center mappage")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Chiffrement des sources**<br /><br /> [![EKM carte de Security Center](../../database-engine/media/security-center-map-ekm.png "EKM carte de Security Center")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Carte de Security Center Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Carte de Security Center Azure Key Vault")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Colonne, données & le chiffrement de clé**<br /><br /> [![Security Center mapper le chiffrement par certificat](../../database-engine/media/security-center-map-cert.png "Security Center mapper le chiffrement par certificat")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Security Center carte chiffrer par clé symétrique](../../database-engine/media/security-center-map-sym-key.png "Security Center carte chiffrer par clé symétrique")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Security Center mapper le chiffrement par clé asymétrique](../../database-engine/media/security-center-map-asym-key.png "Security Center mapper le chiffrement par clé asymétrique")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Security Center le chiffrement de la carte par phrase secrète](../../database-engine/media/security-center-map-passphrase.png "Security Center le chiffrement de la carte par phrase secrète")](https://msdn.microsoft.com/library/ms190357.aspx)|**Protection par pare-feu**<br /><br /> [![Security Center le pare-feu Windows](../../database-engine/media/security-center-map-windows-firewall.png "Security Center le pare-feu Windows")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Pare-feu de service de carte Security Center](../../database-engine/media/security-center-map-service-firewall.png "Pare-feu de service de carte Security Center")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Pare-feu de base de données Security Center](../../database-engine/media/security-center-map-db-firewall.png "Pare-feu de base de données Security Center")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Chiffrement des données en transit**<br /><br /> [![Mappage de Security Center SSL forcé](../../database-engine/media/security-center-map-forced-ssl.png "Mappage de Security Center SSL forcé")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Carte de Security Center SSL facultatif](../../database-engine/media/security-center-map-opt-ssl.png "Carte de Security Center SSL facultatif")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")|**Audit automatisé**<br /><br /> [![Audit de la carte de Security Center SQL Server](../../database-engine/media/security-center-map-sql-audit.png "Audit de la carte de Security Center SQL Server")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Audit de la carte de Security Center SQL Database](../../database-engine/media/security-center-map-sqldb-audit.png "Audit de la carte de Security Center SQL Database")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Audit personnalisé**<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> [![Security Center] les déclencheurs de mappage (../../database-engine/media/security-center-map-triggers.png "Security Center") les déclencheurs de mappage](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Conformité**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Espace réservé](../../database-engine/media/security-center-map-blankplaceholder.png "Espace réservé")<br /><br /> ![Légende Security Center](../../database-engine/media/security-center-map-legend.png "Légende Security Center")|  
  
## <a name="links-to-specific-related-topics"></a>Liens vers des rubriques connexes  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Authentification: Qui es-tu?**  
 **Qui s’authentifie? (Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Choisir un mode d’authentification](choose-an-authentication-mode.md)  
  
 **S'authentifier auprès de la base de données MASTER** (connexions et utilisateurs de base de données)  
  
-   [Créer une connexion SQL Server](authentication-access/create-a-login.md)  
  
-   [Gestion des bases de données et des connexions dans Azure SQL Database](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Créer un utilisateur de base de données](authentication-access/create-a-database-user.md)  
  
 **S’authentifier sur une base de données utilisateur**  
  
-   [Utilisateurs de base de données autonome - Rendre votre base de données portable](contained-database-users-making-your-database-portable.md)  
  
 **Utilisation d'autres identités**  
  
-   [Informations d’identification &#40;moteur de base de données&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Exécuter en tant qu'autre connexion](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Exécuter en tant qu'autre utilisateur de base de données](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Chiffrement: Stockage des données secrètes**  
 **Chiffrement de fichiers**  
  
-   [BitLocker (au niveau du lecteur)](https://support.microsoft.com/kb/2855131)  
  
-   [Chiffrement NTFS (au niveau du dossier)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Chiffrement transparent des données (au niveau du fichier)](encryption/transparent-data-encryption.md)  
  
-   [Chiffrement de la sauvegarde (au niveau du fichier)](../backup-restore/backup-encryption.md)  
  
 **Chiffrement des sources**  
  
-   [Module Gestion de clés extensible](encryption/extensible-key-management-ekm.md)  
  
-   [Clés stockées dans le coffre de clés Azure](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Chiffrement de colonne, de données et de clé**  
  
-   [Chiffrer par certificat](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Chiffrer par clé asymétrique](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Chiffrer par clé symétrique](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Chiffrer par mot de passe](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Autorisation: Que pouvez-vous faire?**  
 **Octroi, révocation et refus d'autorisations**  
  
-   [Hiérarchie des autorisations &#40;moteur de base de données&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Autorisations](permissions-database-engine.md)  
  
-   [Éléments sécurisables](securables.md)  
  
 **Sécurité par rôles**  
  
-   [Rôles de niveau serveur](authentication-access/server-level-roles.md)  
  
-   [Rôles au niveau de la base de données](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Limiter l'accès aux données à l'aide de [Vues](../views/views.md) et de [Procédures](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Sécurité au niveau des lignes](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Masquage dynamique des données](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Objets signés](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Sécurité de la connexion: Restriction et sécurisation**  
 **Protection par pare-feu**  
  
-   [Configurer un pare-feu Windows pour accéder au moteur de base de données](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Paramètres de pare-feu Azure SQL Database](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Paramètres de pare-feu du service Azure](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Chiffrement des données en transit**  
  
-   [SSL (Secure Sockets Layer) pour le moteur de base de données](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [SSL (Secure Sockets Layer) pour SQL Database](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Audit: Enregistrement de l’accès**  
 **Audit automatisé**  
  
-   [SQL Server Audit &#40moteur de base de données&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [Audit SQL Database](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Implémentation de l’audit personnalisé**  
  
-   Création de [DDL Triggers](../triggers/ddl-triggers.md) et de [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Petite icône de dossier de fichiers](../../integration-services/media/filefolder-small.gif "Petite icône de dossier de fichiers") **Conformité**  
 **SQL Server**  
  
-   [Critères courants](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL Database**  
  
-   [Centre de confidentialité Microsoft Azure : conformité par fonctionnalité](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation de SQL Server](securing-sql-server.md)   
 [Principaux &#40;moteur de base de données&#41;](authentication-access/principals-database-engine.md)   
 [Certificats et clés asymétriques SQL Server](sql-server-certificates-and-asymmetric-keys.md)   
 [Chiffrement SQL Server](encryption/sql-server-encryption.md)   
 [Configuration de la surface d'exposition](surface-area-configuration.md)   
 [Mots de passe forts](strong-passwords.md)   
 [Propriété de base de données TRUSTWORTHY](trustworthy-database-property.md)   
 [Fonctionnalités et tâches du moteur de base de données](../../database-engine/database-engine-features-and-tasks.md)  
  
  
