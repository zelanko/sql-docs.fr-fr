---
title: Configurer l’initialisation instantanée des fichiers - Analytique Platform System | Microsoft Docs
description: Configurer l’initialisation instantanée des fichiers système de plateforme d’Analytique. Initialisation instantanée des fichiers est une fonctionnalité de SQL Server qui autorise les opérations de fichier de données exécuter plus rapidement.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 959d219565de6577e31d9548f5daea0fe0d2419e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298119"
---
# <a name="instant-file-initialization-configuration"></a>Configuration de l’initialisation instantanée des fichiers
Initialisation instantanée des fichiers est une fonctionnalité de SQL Server qui autorise les opérations de fichier de données exécuter plus rapidement. Cochez la case pour activer l’initialisation instantanée des fichiers améliore les performances de SQL Server PDW. Toutefois, si cela pose un risque de sécurité pour vous business, puis laissez la case désactivée.  
  
> [!IMPORTANT]  
> Lors de l’initialisation instantanée des fichiers est activée, SQL Server ne remplace pas supprimé de bits avec des zéros.  Ce comportement peut créer une faille de sécurité si les utilisateurs non autorisés à accéder aux données supprimées. Toutefois, SQL Server PDW atténue ce risque en veillant à ce que la base de données SQL Server et les fichiers de sauvegarde sont toujours attachés à une instance de SQL Server ; seul le compte de service SQL Server et de l’administrateur local peuvent accéder aux données supprimées sur SQL Server PDW.  
  
L'initialisation instantanée des fichiers n'est pas disponible quand le chiffrement transparent des données est activé.  
  
## <a name="add-permission-for-the-backup-account"></a>Ajoutez l’autorisation pour le compte de sauvegarde  
Le processus de sauvegarde nécessite une information d’identification du réseau (compte d’utilisateur Windows) qui peut accéder à l’emplacement de stockage de sauvegarde. Vous autorisez PDW pour utiliser un compte à l’aide de la [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) procédure. Consultez [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md) pour tout le processus de sauvegarde. Pour utiliser l’initialisation instantanée des fichiers, le compte de sauvegarde doit être accordé le `Perform volume maintenance tasks` autorisation.  
  
1.  Sur le serveur de sauvegarde, ouvrez le **stratégie de sécurité locale** application (`secpol.msc`).  
  
2.  Dans le volet gauche, développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.  
  
3.  Dans le volet droit, double-cliquez sur **Effectuer des tâches de maintenance sur les volumes**.  
  
4.  Cliquez sur **Ajouter un utilisateur ou un groupe** et ajoutez tout compte d’utilisateur utilisé pour les sauvegardes.  
  
5.  Cliquez sur **Appliquer**, puis fermez toutes les boîtes de dialogue **Stratégie de sécurité locale** .  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>Pour activer ou désactiver les initialisation instantanée des fichiers  
  
1.  Lancez le Gestionnaire de Configuration. Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche du Gestionnaire de Configuration, cliquez sur **initialisation instantanée des fichiers**.  
  
3.  Pour activer l’initialisation instantanée des fichiers, activez la case à côté **activer initialisation instantanée des fichiers sur tous les nœuds**. Pour désactiver l’initialisation instantanée des fichiers, désactivez la case à côté **activer initialisation instantanée des fichiers sur tous les nœuds**.  
  
    > [!WARNING]  
    > Lorsque vous désactivez l’initialisation instantanée des fichiers, la considération de sécurité abordée ci-dessus pour la fonctionnalité peut-être toujours appliquer aux fichiers supprimés pendant l’initialisation instantanée des fichiers a été activée.  
  
4.  Cliquez sur **Appliquer**. La modification sera propagée, dans les instances de SQL Server sur SQL Server PDW, lors du prochain que redémarrage des services de l’appliance. Pour redémarrer maintenant les services de l’appliance, consultez [l’état des Services PDW &#40;Analytique Platform System&#41;](pdw-services-status.md).  
  
5.  Vous souhaiterez peut-être répéter les étapes décrites ci-dessus en tant que **ajouter une autorisation pour le compte de sauvegarde** pour supprimer la **effectuer les tâches de maintenance de volume** autorisation.  
  
![DWConfig Appliance PDW initialisation instantanée des fichiers](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
Pour plus d’informations sur l’initialisation instantanée des fichiers, consultez [initialisation instantanée des fichiers](https://technet.microsoft.com/library/ms175935(v=SQL.105).aspx).  
  
