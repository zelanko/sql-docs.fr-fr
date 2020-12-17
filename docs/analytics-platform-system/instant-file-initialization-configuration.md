---
title: Configurer l’initialisation instantanée des fichiers
description: Configurez l’initialisation instantanée des fichiers sur Analytics Platform System. L’initialisation instantanée de fichiers est une fonctionnalité SQL Server qui permet aux opérations de fichiers de données de s’exécuter plus rapidement.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6843efa430fcd43149d048c9d21c5120954ab896
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97637815"
---
# <a name="instant-file-initialization-configuration"></a>Configuration de l’initialisation instantanée des fichiers
L’initialisation instantanée de fichiers est une fonctionnalité SQL Server qui permet aux opérations de fichiers de données de s’exécuter plus rapidement. Si vous activez la case à cocher pour activer l’initialisation instantanée des fichiers, vous améliorerez les performances de SQL Server PDW. Toutefois, si cela pose un risque de sécurité pour votre entreprise, laissez la case désactivée.  
  
> [!IMPORTANT]  
> Lorsque l’initialisation instantanée de fichiers est activée, SQL Server ne remplace pas les bits supprimés par des zéros.  Ce comportement peut créer une faille de sécurité si des utilisateurs non autorisés accèdent aux données supprimées. Toutefois, SQL Server PDW atténue ce risque en garantissant que la base de données SQL Server et les fichiers de sauvegarde sont toujours attachés à une instance de SQL Server ; seul le compte de service SQL Server et l’administrateur local peuvent accéder aux données supprimées sur SQL Server PDW.  
  
L'initialisation instantanée des fichiers n'est pas disponible quand le chiffrement transparent des données est activé.  
  
## <a name="add-permission-for-the-backup-account"></a>Ajouter une autorisation pour le compte de sauvegarde  
Le processus de sauvegarde nécessite des informations d’identification réseau (compte d’utilisateur Windows) qui peuvent accéder à l’emplacement de stockage de la sauvegarde. Vous autorisez PDW à utiliser le compte à l’aide de la procédure [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) . Consultez [Backup database](../t-sql/statements/backup-transact-sql.md) pour l’ensemble du processus de sauvegarde. Pour utiliser l’initialisation instantanée des fichiers, l’autorisation doit être accordée au compte de sauvegarde `Perform volume maintenance tasks` .  
  
1.  Sur le serveur de sauvegarde, ouvrez l’application **stratégie de sécurité locale** ( `secpol.msc` ).  
  
2.  Dans le volet gauche, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
3.  Dans le volet droit, double-cliquez sur **Effectuer des tâches de maintenance sur les volumes**.  
  
4.  Cliquez sur **Ajouter un utilisateur ou un groupe** et ajoutez tout compte d’utilisateur utilisé pour les sauvegardes.  
  
5.  Cliquez sur **Appliquer**, puis fermez toutes les boîtes de dialogue **Stratégie de sécurité locale** .  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>Pour activer ou désactiver l’initialisation instantanée de fichiers  
  
1.  Lancez le Configuration Manager. Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la Configuration Manager, cliquez sur **initialisation instantanée des fichiers**.  
  
3.  Pour activer l’initialisation instantanée des fichiers, activez la case à cocher en regard de **activer l’initialisation instantanée des fichiers sur tous les nœuds**. Pour désactiver l’initialisation instantanée des fichiers, décochez la case en regard de **activer l’initialisation instantanée des fichiers sur tous les nœuds**.  
  
    > [!WARNING]  
    > Lorsque vous désactivez l’initialisation instantanée des fichiers, la considération de sécurité décrite ci-dessus pour cette fonctionnalité peut toujours s’appliquer aux fichiers supprimés pendant l’activation de l’initialisation instantanée des fichiers.  
  
4.  Cliquez sur **Appliquer**. La modification se propage à travers les instances de SQL Server sur SQL Server PDW lors du redémarrage suivant des services de l’appliance. Pour redémarrer les services de l’appliance maintenant, consultez l' [État des services PDW &#40;Analytics Platform System&#41;](pdw-services-status.md).  
  
5.  Vous pouvez répéter les étapes décrites ci-dessus en tant qu' **autorisation Ajouter pour le compte de sauvegarde** pour supprimer l’autorisation **effectuer des tâches de maintenance de volume** .  
  
![Initialisation d'instantanés de fichier PDW des appliances DWConfig](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
Pour plus d’informations sur l’initialisation instantanée des fichiers, consultez [initialisation instantanée des fichiers](/previous-versions/sql/sql-server-2008-r2/ms175935(v=sql.105)).  
