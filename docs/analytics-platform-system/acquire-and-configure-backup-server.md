---
title: Obtenir et configurer un serveur de sauvegarde - Parallel Data Warehouse | Microsoft Docs
description: Cet article décrit comment configurer un système de Windows non-appliance comme un serveur de sauvegarde pour une utilisation avec les fonctionnalités de sauvegarde et de restauration dans Analytique Platform System (APS) et Parallel Data Warehouse (PDW).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cba345eb7a5aec9ef857819a1f0499266649f6e4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63040825"
---
# <a name="acquire-and-configure-a-backup-server-for-parallel-data-warehouse"></a>Obtenir et configurer un serveur de sauvegarde pour Parallel Data Warehouse
Cet article décrit comment configurer un système de Windows non-appliance comme un serveur de sauvegarde pour une utilisation avec les fonctionnalités de sauvegarde et de restauration dans Analytique Platform System (APS) et Parallel Data Warehouse (PDW).  
  
  
## <a name="Basics"></a>Principes fondamentaux du serveur de sauvegarde  
Le serveur de sauvegarde :  
  
-   Est fourni et géré par votre propre équipe informatique.  
  
-   Ne nécessite pas de n’importe quel logiciel PDW spécifique ou outils. PDW n’installe pas tous les logiciels sur le serveur de sauvegarde.  
  
-   Se trouve dans votre propre rack non-appliance et ne peut pas être placé dans l’appliance APS.  
  
-   Peut être connecté au réseau InfiniBand appliance. Les sauvegardes peuvent être effectuées sur InfiniBand ou Ethernet ; InfiniBand est recommandée pour des raisons de performances.  
  
-   Se trouve dans votre propre domaine client, pas le domaine de l’appliance. Il n’existe aucune relation d’approbation entre le domaine de votre client et le domaine de l’appliance.  
  
-   Héberge un partage de fichiers de sauvegarde, qui est un partage de fichiers Windows qui utilise le protocole Server Message Block (SMB) au niveau de l’application. Les autorisations de partage de fichier de sauvegarde donner à un utilisateur de domaine Windows (c’est généralement un utilisateur de sauvegarde dédié) la possibilité de sauvegarder et restaurer des opérations sur le partage. Les informations d’identification de nom d’utilisateur et mot de passe de l’utilisateur de domaine Windows sont stockées dans PDW afin que PDW peut sauvegarder et restaurer des opérations sur le partage de fichiers de sauvegarde.  
  
## <a name="Step1"></a>Étape 1 : Déterminer la capacité requise  
La configuration système requise pour le serveur de sauvegarde dépend presque entièrement votre propre charge de travail. Avant d’acheter ou de déploiement d’un serveur de sauvegarde, vous devez déterminer vos besoins en capacité. Le serveur de sauvegarde ne devra pas être dédié uniquement aux sauvegardes, tant qu’il gère les exigences de performances et de stockage de votre charge de travail. Vous pouvez également avoir plusieurs serveurs de sauvegarde pour sauvegarder et restaurer chaque base de données à une de plusieurs serveurs.  
  
Utilisez le [feuille de planification de capacité sauvegarde serveur](backup-capacity-planning-worksheet.md) pour aider à déterminer vos besoins en capacité.  
  
## <a name="Step2"></a>Étape 2 : Acquérir le serveur de sauvegarde  
Maintenant que vous comprenez mieux vos besoins en capacité, vous pouvez planifier les serveurs et les composants réseau dont vous aurez besoin d’acheter ou mettre en service. Incorporer la liste suivante des exigences de votre plan d’achat, puis acheter votre serveur ou configurer un serveur existant.  
  
### <a name="software-requirements"></a>Configuration logicielle requise  
N’importe quel serveur de fichiers qui utilise le protocole de partage de fichiers Windows (SMB).  
  
Nous vous recommandons de Windows Server 2012 ou au-delà de :  
  
-   Obtenir l’amélioration des performances de préallocation de fichiers sur SMB.  
  
-   Utilisez l’initialisation instantanée de fichiers (IFI) pour les opérations de sauvegarde. Votre équipe informatique gère ce paramètre sur le serveur de sauvegarde. Le Gestionnaire de Configuration PDW (dwconfig.exe) ne pas définir ou contrôler l’initialisation instantanée de fichiers sur votre serveur de sauvegarde. Les versions précédentes de Windows n’ont pas IFI, mais il peuvent toujours être utilisées comme serveurs de sauvegarde.  
  
### <a name="networking-requirements"></a>Configuration réseau requise  
Bien que non obligatoire, InfiniBand est le type de connexion recommandée pour les serveurs de sauvegarde. Pour préparer connectant le chargement du serveur au réseau InfiniBand appliance :  
  
1.  Envisagez de monter en rack de serveur suffisamment proches pour l’appliance afin que vous pouvez vous connecter à l’appliance InfiniBand bascule. Pour plus d’informations à partir de Technologies Mellanox InfiniBand, consultez le livre blanc, [présentation InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Acheter une carte Mellanox ConnectX-3 FDR InfiniBand port simple ou double. Nous vous recommandons d’acheter la carte réseau avec deux ports pour une tolérance de panne pendant la transmission de données. Une carte réseau de deux port est requise pour la haute disponibilité.  
  
3.  Acheter 2 câbles FDR InfiniBand pour une carte de port double ou 1 câble FDR InfiniBand pour une carte de port unique. Les câbles FDR InfiniBand se connectera le chargement du serveur au réseau InfiniBand appliance. La longueur du câble dépend de la distance entre le serveur de chargement et les commutateurs InfiniBand du matériel, en fonction de votre environnement.  
  
## <a name="Step3"></a>Étape 3 : Connectez le serveur aux réseaux InfiniBand  
Suivez ces étapes pour connecter le serveur de chargement pour le réseau InfiniBand. Si le serveur n’utilise pas le réseau InfiniBand, ignorez cette étape.  
  
1.  Le serveur de rack suffisamment à l’appliance afin que vous pouvez vous connecter au réseau InfiniBand appliance.  
  
2.  Installez l’adaptateur de réseau InfiniBand Mellanox ConnectX-3 FDR InfiniBand sur le serveur de chargement.  
  
3.  Utilisez les câbles FDR pour connecter la carte réseau InfiniBand à un des deux commutateurs InfiniBand dans le rack appliance premier.  
  
4.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    -   Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium d’entreprises de fournisseurs de InfiniBand.  Le pilote correct peut ont été distribué avec votre carte de réseau InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
5.  Configurez les paramètres DNS et InfiniBand pour les cartes réseau. Pour obtenir des instructions de configuration, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
## <a name="Step4"></a>Étape 4 : Configurer le partage de fichiers de sauvegarde  
PDW accéderont au serveur de sauvegarde via un partage de fichiers UNC. Pour configurer le partage de fichiers :  
  
1.  Créez un dossier sur le serveur de sauvegarde pour stocker vos sauvegardes.  
  
2.  Créer un partage de fichiers, appelé un partage de sauvegarde pour le dossier de sauvegarde.  
  
3.  Désigner ou créer un compte de domaine Windows dans votre domaine de client que vous souhaitez utiliser dans le cadre de l’exécution de sauvegardes et restaurations. Pour des raisons de sécurité, il est préférable d’utiliser un compte dédié en tant que l’utilisateur de sauvegarde.  
  
4.  Ajouter des autorisations pour la sauvegarde partagent afin que seuls les comptes approuvés et un compte de sauvegarde du domaine puissent accéder, lire et écrire dans l’emplacement du partage.  
  
5.  Ajoutez les informations d’identification du compte de domaine de sauvegarde à PDW.  
  
    Exemple :  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    Pour plus d’informations, consultez ces procédures stockées :  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="Step5"></a>Étape 5 : Démarrer la sauvegarde de vos données  
Vous êtes maintenant prêt à démarrer la sauvegarde des données sur le serveur de sauvegarde.  
  
Pour sauvegarder des données, utilisez un client de requête pour se connecter à SQL Server PDW, puis envoyez sauvegarde de base de données ou de restauration de base de données des commandes. Utiliser le disque = clause pour spécifier l’emplacement de sauvegarde et de serveur de sauvegarde.  
  
> [!IMPORTANT]  
> Pensez à utiliser l’adresse InfiniBand IP du serveur de sauvegarde. Sinon, les données seront copiées sur Ethernet au lieu de InfiniBand.  
  
Exemple :  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
Pour plus d'informations, consultez : 
  
-   [BASE DE DONNÉES DE SAUVEGARDE](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="Security"></a>Avis de sécurité  
Le serveur de sauvegarde n’est pas joint au domaine privé pour l’appliance. Il se trouve dans votre propre réseau, et il n’existe aucune relation d’approbation entre votre propre domaine et privé appliance.  
  
Dans la mesure où les sauvegardes PDW ne sont pas stockées sur l’appliance, votre équipe informatique est chargé de gérer tous les aspects de la sécurité de la sauvegarde. Par exemple, cela inclut la gestion de la sécurité de la sécurité de l’infrastructure de mise en réseau qui connecte le serveur de sauvegarde vers l’appliance APS, les données de sauvegarde et la sécurité du serveur utilisé pour stocker les sauvegardes.  
  
### <a name="manage-network-credentials"></a>Gérer les informations d’identification réseau  
  
L’accès réseau au répertoire de sauvegarde est basé sur la sécurité standard des partages de fichiers Windows. Avant d’effectuer une sauvegarde, vous devez créer ou désigner un compte Windows qui sera utilisé pour l’authentification PDW au répertoire de sauvegarde. Ce compte Windows doit être doté d’un droit d’accès, de création et d’écriture sur le répertoire de sauvegarde.  
  
> [!IMPORTANT]  
> Pour réduire les risques de sécurité liés à vos données, il vous est conseillé de désigner un compte Windows qui servira uniquement aux opérations de sauvegarde et de restauration. Autorisez ce compte à accéder à l’emplacement de sauvegarde et à aucun autre emplacement.  
  
Pour stocker le nom d’utilisateur et le mot de passe dans PDW, utilisez le [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) procédure stockée. PDW utilise le Gestionnaire d’informations d’identification Windows pour stocker et de chiffrer les noms d’utilisateur et mots de passe sur le nœud de contrôle et de nœuds de calcul. Les informations d’identification ne sont pas sauvegardées avec la commande BACKUP DATABASE.  
  
Pour supprimer les informations d’identification réseau de PDW, utilisez le [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) procédure stockée.  
  
Pour répertorier toutes les informations d’identification réseau stockées dans SQL Server PDW, utilisez le [sys.dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) vue de gestion dynamique.  
  
### <a name="secure-communications"></a>Communications sécurisées  
  
Opérations sur le serveur de chargement peuvent utiliser un chemin d’accès UNC pour extraire les données à partir de l’extérieur du réseau interne approuvé. Une personne malveillante sur le réseau ou avec la possibilité pour influencer la résolution de noms peut intercepter ou modifier des données envoyées à l’empaquetage. Cela pose un risque de divulgation d’informations et de falsification. Pour aider à atténuer le risque de falsification :

- Demander la signature sur la connexion. 
- Sur le serveur de chargement, définissez l’option de stratégie de groupe suivante dans Security Settings\Local Policies\Security Options :  Client réseau Microsoft : Communications signées numériquement (toujours) : activé.  
  
## <a name="see-also"></a>Voir aussi  
[Sauvegarde et restauration](backup-and-restore-overview.md)  
  
