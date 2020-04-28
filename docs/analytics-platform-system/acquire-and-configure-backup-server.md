---
title: Acquérir & configurer le serveur de sauvegarde
description: Cet article explique comment configurer un système non-appareil Windows comme serveur de sauvegarde à utiliser avec les fonctionnalités de sauvegarde et de restauration dans Analytics Platform System (APS) et Parallel Data Warehouse (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: e160c606b19933934ec844b477ffec08475307d8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401495"
---
# <a name="acquire-and-configure-a-backup-server-for-parallel-data-warehouse"></a>Acquérir et configurer un serveur de sauvegarde pour les Data Warehouse parallèles
Cet article explique comment configurer un système non-appareil Windows comme serveur de sauvegarde à utiliser avec les fonctionnalités de sauvegarde et de restauration dans Analytics Platform System (APS) et Parallel Data Warehouse (PDW).  
  
  
## <a name="backup-server-basics"></a><a name="Basics"></a>Notions de base sur le serveur de sauvegarde  
Le serveur de sauvegarde :  
  
-   Est fourni et géré par votre propre équipe informatique.  
  
-   Ne nécessite aucun logiciel ou outil spécifique au PDW. PDW n’installe pas de logiciel sur le serveur de sauvegarde.  
  
-   Se trouve dans votre propre rack non-appliance et ne peut pas être placé dans l’appliance APS.  
  
-   Peut être connecté au réseau de l’appliance InfiniBand. Les sauvegardes peuvent être effectuées sur InfiniBand ou Ethernet ; InfiniBand est recommandé pour des raisons de performances.  
  
-   Se trouve dans votre propre domaine de client, et non dans le domaine de l’appliance. Il n’existe aucune relation d’approbation entre votre domaine client et le domaine de l’appliance.  
  
-   Héberge un partage de fichiers de sauvegarde, qui est un partage de fichiers Windows qui utilise le protocole réseau au niveau de l’application SMB (Server Message Block). Les autorisations de partage de fichiers de sauvegarde donnent à un utilisateur de domaine Windows (généralement, il s’agit d’un utilisateur de sauvegarde dédié) la possibilité d’effectuer des opérations de sauvegarde et de restauration sur le partage. Les informations d’identification de nom d’utilisateur et de mot de passe de l’utilisateur de domaine Windows sont stockées dans PDW afin que PDW puisse effectuer des opérations de sauvegarde et de restauration sur le partage de fichiers de sauvegarde.  
  
## <a name="step-1-determine-capacity-requirements"></a><a name="Step1"></a>Étape 1 : déterminer les besoins en capacité  
La configuration système requise pour le serveur de sauvegarde dépend presque entièrement de votre propre charge de travail. Avant d’acheter ou de configurer un serveur de sauvegarde, vous devez déterminer vos besoins en capacité. Le serveur de sauvegarde n’a pas besoin d’être dédié uniquement aux sauvegardes, à condition qu’il gère les exigences de performances et de stockage de votre charge de travail. Vous pouvez également disposer de plusieurs serveurs de sauvegarde afin de sauvegarder et de restaurer chaque base de données sur un ou plusieurs serveurs.  
  
Utilisez la [feuille de planification](backup-capacity-planning-worksheet.md) de la capacité du serveur de sauvegarde pour vous aider à déterminer vos besoins en capacité.  
  
## <a name="step-2-acquire-the-backup-server"></a><a name="Step2"></a>Étape 2 : acquérir le serveur de sauvegarde  
Maintenant que vous comprenez mieux vos besoins en matière de capacité, vous pouvez planifier les serveurs et les composants de mise en réseau que vous devrez acheter ou approvisionner. Incorporez la liste suivante d’exigences dans votre plan d’achat, puis achetez votre serveur ou approvisionnez un serveur existant.  
  
### <a name="software-requirements"></a>Configuration logicielle requise  
Tout serveur de fichiers qui utilise le protocole de partage de fichiers Windows (SMB).  
  
Nous vous recommandons Windows Server 2012 ou ultérieur pour effectuer les opérations suivantes :  
  
-   Tirez parti des avantages en matière de performances de préallocation de fichiers sur SMB.  
  
-   Utilisez l’initialisation instantanée des fichiers (IFI) pour les opérations de sauvegarde. Votre équipe informatique gère ce paramètre sur le serveur de sauvegarde. Le Configuration Manager PDW (dwconfig. exe) ne définit pas ou ne contrôle pas IFI sur votre serveur de sauvegarde. Les versions précédentes de Windows n’ont pas IFI, mais peuvent toujours être utilisées comme serveurs de sauvegarde.  
  
### <a name="networking-requirements"></a>Configuration requise du réseau  
Bien que cela ne soit pas obligatoire, InfiniBand est le type de connexion recommandé pour les serveurs de sauvegarde. Pour préparer la connexion du serveur de chargement au réseau de l’appliance InfiniBand :  
  
1.  Envisagez de monter en rack le serveur suffisamment près de l’appareil afin de pouvoir le connecter aux commutateurs InfiniBand de l’appliance. Pour plus d’informations sur les technologies Mellanox sur InfiniBand, consultez le livre blanc [Introduction à InfiniBand](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf).  
  
2.  Achetez une carte réseau Mellanox ConnectX-3 FDR InfiniBand ou double port. Nous vous recommandons d’acheter la carte réseau avec deux ports pour la tolérance de panne pendant la transmission des données. Une carte réseau à deux ports est requise pour la haute disponibilité.  
  
3.  Acheter 2 câbles FDR InfiniBand pour une carte à double port, ou un câble de 1 FDR InfiniBand pour une seule carte de port. Les câbles FDR InfiniBand connectent le serveur de chargement au réseau de l’appliance InfiniBand. La longueur du câble dépend de la distance entre le serveur de chargement et les commutateurs InfiniBand de l’appliance, en fonction de votre environnement.  
  
## <a name="step-3-connect-the-server-to-the-infiniband-networks"></a><a name="Step3"></a>Étape 3 : connecter le serveur aux réseaux InfiniBand  
Procédez comme suit pour connecter le serveur de chargement au réseau InfiniBand. Si le serveur n’utilise pas le réseau InfiniBand, ignorez cette étape.  
  
1.  Rackez le serveur suffisamment près de l’appareil pour pouvoir le connecter au réseau de l’appliance InfiniBand.  
  
2.  Installez la carte réseau InfiniBand Mellanox ConnectX-3 FDR InfiniBand dans le serveur de chargement.  
  
3.  Utilisez les câbles FDR pour connecter la carte réseau InfiniBand à l’un des deux commutateurs InfiniBand dans le premier rack d’appliances.  
  
4.  Installez et configurez le pilote Windows approprié pour la carte réseau InfiniBand.  
  
    -   Les pilotes InfiniBand pour Windows sont développés par OpenFabrics Alliance, un consortium de l’industrie des fournisseurs InfiniBand.  Le pilote approprié a peut-être été distribué avec votre carte réseau InfiniBand. Si ce n’est pas le cas, le pilote peut être téléchargé à partir de www.openfabrics.org.  
  
5.  Configurez les paramètres InfiniBand et DNS pour les cartes réseau. Pour obtenir des instructions de configuration, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
## <a name="step-4-configure-the-backup-file-share"></a><a name="Step4"></a>Étape 4 : configurer le partage de fichiers de sauvegarde  
PDW accède au serveur de sauvegarde via un partage de fichiers UNC. Pour configurer le partage de fichiers :  
  
1.  Créez un dossier sur le serveur de sauvegarde pour stocker vos sauvegardes.  
  
2.  Créez un partage de fichiers, appelé partage de sauvegarde, pour le dossier de sauvegarde.  
  
3.  Désignez ou créez un compte de domaine Windows dans le domaine de votre client que vous souhaitez utiliser pour effectuer des sauvegardes et des restaurations. Pour des raisons de sécurité, il est préférable d’utiliser un compte dédié en tant qu’utilisateur de sauvegarde.  
  
4.  Ajoutez des autorisations au partage de sauvegarde afin que seuls les comptes approuvés et un compte de sauvegarde de domaine puissent accéder, lire et écrire dans l’emplacement du partage.  
  
5.  Ajoutez les informations d’identification du compte de domaine de sauvegarde à PDW.  
  
    Par exemple :  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    Pour plus d’informations, consultez les procédures stockées suivantes :  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="step-5-start-backing-up-your-data"></a><a name="Step5"></a>Étape 5 : démarrer la sauvegarde de vos données  
Vous êtes maintenant prêt à démarrer la sauvegarde des données sur votre serveur de sauvegarde.  
  
Pour sauvegarder des données, utilisez une requête client pour vous connecter à SQL Server PDW puis envoyer des commandes BACKUP DATABASE ou RESTORE DATABASE. Utilisez la clause DISK = pour spécifier le serveur de sauvegarde et l’emplacement de sauvegarde.  
  
> [!IMPORTANT]  
> N’oubliez pas d’utiliser l’adresse IP InfiniBand du serveur de sauvegarde. Dans le cas contraire, les données seront copiées sur Ethernet au lieu de InfiniBand.  
  
Par exemple :  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
Pour plus d’informations, voir : 
  
-   [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="security-notices"></a><a name="Security"></a>Notifications de sécurité  
Le serveur de sauvegarde n’est pas joint au domaine privé de l’appliance. Il se trouve dans votre propre réseau, et il n’existe aucune relation d’approbation entre votre propre domaine et votre propre domaine d’appliance privé.  
  
Étant donné que les sauvegardes PDW ne sont pas stockées sur l’appliance, votre équipe informatique est responsable de la gestion de tous les aspects de la sécurité de la sauvegarde. Par exemple, il s’agit de la gestion de la sécurité des données de sauvegarde, de la sécurité du serveur utilisé pour stocker les sauvegardes et de la sécurité de l’infrastructure réseau qui connecte le serveur de sauvegarde à l’appliance APS.  
  
### <a name="manage-network-credentials"></a>Gérer les informations d’identification réseau  
  
L’accès réseau au répertoire de sauvegarde est basé sur la sécurité standard des partages de fichiers Windows. Avant d’effectuer une sauvegarde, vous devez créer ou désigner un compte Windows qui sera utilisé pour l’authentification PDW dans le répertoire de sauvegarde. Ce compte Windows doit être doté d’un droit d’accès, de création et d’écriture sur le répertoire de sauvegarde.  
  
> [!IMPORTANT]  
> Pour réduire les risques de sécurité liés à vos données, il vous est conseillé de désigner un compte Windows qui servira uniquement aux opérations de sauvegarde et de restauration. Autorisez ce compte à accéder à l’emplacement de sauvegarde et à aucun autre emplacement.  
  
Pour stocker le nom d’utilisateur et le mot de passe dans PDW, utilisez la procédure stockée [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) . PDW utilise le gestionnaire d’informations d’identification Windows pour stocker et chiffrer les noms d’utilisateur et les mots de passe sur le nœud de contrôle et les nœuds de calcul. Les informations d’identification ne sont pas sauvegardées avec la commande BACKUP DATABASE.  
  
Pour supprimer les informations d’identification réseau de PDW, utilisez la procédure stockée [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) .  
  
Pour répertorier toutes les informations d’identification réseau stockées dans SQL Server PDW, utilisez la vue de gestion dynamique [sys. dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) .  
  
### <a name="secure-communications"></a>Communications sécurisées  
  
Les opérations sur le serveur de chargement peuvent utiliser un chemin UNC pour extraire des données de l’extérieur du réseau interne approuvé. Une personne malveillante sur le réseau ou avec la possibilité d’influencer la résolution de noms peut intercepter ou modifier les données envoyées au PDW. Cela présente un risque de falsification et de divulgation d’informations. Pour limiter le risque de falsification :

- Exiger la signature sur la connexion. 
- Sur le serveur de chargement, définissez l’option de stratégie de groupe suivante dans paramètres de sécurité \ stratégies de sécurité réseau : client réseau Microsoft : communications signées numériquement (toujours) : activé.  
  
## <a name="see-also"></a>Voir aussi  
[Sauvegarde et restauration](backup-and-restore-overview.md)  
  
