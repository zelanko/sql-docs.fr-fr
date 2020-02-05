---
title: Propriétés du serveur (page Paramètres de base de données) | Microsoft Docs
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
ms.custom: ''
ms.date: 05/23/2019
ms.openlocfilehash: bdefcbbfe6d5987de4ac69ab60d1e80b004a5db6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68025449"
---
# <a name="server-properties---database-settings-page"></a>Propriétés du serveur - page Paramètres de base de données

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Utilisez cette page pour consulter ou modifier vos paramètres de base de données.  
  
## <a name="options"></a>Options

### <a name="default-index-fill-factor"></a>Facteur de remplissage par défaut de l'index

Spécifie le taux de remplissage que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit appliquer à chaque page lorsqu'il crée un nouvel index à partir de données existantes. Le facteur de remplissage affecte les performances étant donné que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit prendre le temps de fractionner les pages lors de leur remplissage.
  
La valeur par défaut est 0 ; la plage des valeurs valides s'étend de 0 à 100. Un facteur de remplissage égal à 0 ou à 100 permet de créer des index cluster contenant des pages de données pleines et des index non cluster contenant des pages de feuilles pleines, mais laisse de l'espace dans le niveau supérieur de l'arborescence de l'index. Les facteurs de remplissage de valeur 0 et 100 sont en tout point identiques.
  
Avec des petits facteurs de remplissage, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée des index contenant des pages qui ne sont pas remplies. Chaque index prend une plus grande quantité d'espace de stockage, mais il y a aussi plus de place pour effectuer ultérieurement des insertions sans avoir à fractionner les pages.
  
### <a name="wait-indefinitely"></a>Attendre indéfiniment

Indique que l'opération de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas expirer tant que l'insertion d'une nouvelle bande de sauvegarde est en attente.  

### <a name="try-once"></a>Essayer une fois

Indique que l'opération de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] va expirer si une bande de sauvegarde n'est pas disponible au moment voulu.

### <a name="try-for-minutes"></a>Essayer pendant

Indique que l'opération de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] va expirer si une bande de sauvegarde n'est pas disponible dans le délai spécifié.  

### <a name="default-backup-media-retention-in-days"></a>Délai de rétention par défaut du support de sauvegarde (jours)

Définit pour l'ensemble du système un délai de rétention par défaut de chaque support utilisé pour la sauvegarde d'une base de données ou d'un journal des transactions. Cette option permet d'éviter l'écrasement des sauvegardes pendant le nombre de jours spécifié.  

#### <a name="compress-backup"></a>Compresser la sauvegarde

Dans [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (ou versions ultérieures), indique la configuration actuelle de l’option **compression par défaut des sauvegardes** . Cette option détermine la valeur par défaut au niveau du serveur pour la compression des sauvegardes, comme suit :

- Si la case à cocher **Compresser la sauvegarde** est désactivée, les nouvelles sauvegardes ne sont pas compressées par défaut.

- Si la case à cocher **Compresser la sauvegarde** est activée, les nouvelles sauvegardes sont compressées par défaut.
  
    > [!IMPORTANT]
    >  Par défaut, la compression augmente considérablement l'utilisation de l'UC et l'UC supplémentaire consommée par le processus de compression peut nuire aux opérations simultanées. Par conséquent, il peut être préférable de créer une sauvegarde compressée de priorité basse dans une session où l’utilisation de l’UC est limitée par [Resource Governor](../../relational-databases/resource-governor/resource-governor.md). Pour plus d'informations, consultez [Utiliser Resource Governor pour limiter l’utilisation de l’UC par compression de la sauvegarde &#40;Transact-SQL&#41;](../.. relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).
  
Si vous êtes membre du rôle serveur fixe **sysadmin** ou **serveradmin** , vous pouvez modifier le paramètre en activant la case à cocher **Compresser la sauvegarde** .  
  
Pour plus d’informations, consultez [Afficher ou configurer l’option de configuration du serveur valeur par défaut de compression de la sauvegarde](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md) et [Compression de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).  

#### <a name="backup-checksum"></a>Somme de contrôle de sauvegarde

Cette option vous permet d’activer le paramètre sp_configure pour le *paramètre par défaut de la somme de contrôle de sauvegarde*. Cette fonctionnalité facilite l’activation du paramètre par défaut de la somme de contrôle de sauvegarde.

### <a name="recovery-interval-minutes"></a>Intervalle de récupération (minutes)

Définit le nombre maximal de minutes par base de données pour la récupération des bases de données. La valeur par défaut est égale à 0, ce qui correspond à une configuration automatique par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les bases de données actives, cette option représente concrètement une durée de récupération inférieure à une minute et un point de contrôle chaque minute environ. Pour plus d'informations, consultez [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md).  
  
### <a name="data"></a>Données

Spécifie l'emplacement par défaut des fichiers de données. Cliquez sur le bouton Parcourir pour accéder à un nouvel emplacement par défaut. N’entre pas en vigueur tant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas redémarré.  
  
### <a name="log"></a>Journal
  
Spécifie l'emplacement par défaut des fichiers journaux. Cliquez sur le bouton Parcourir pour accéder à un nouvel emplacement par défaut. N’entre pas en vigueur tant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas redémarré.  
  
### <a name="configured-values"></a>Valeurs configurées

Affiche les valeurs configurées pour les options de ce volet. Si vous modifiez ces valeurs, cliquez sur **Valeurs en cours d’exécution** pour vérifier si les modifications ont été prises en compte. Si elles n’ont pas été appliquées, vous devez d’abord redémarrer l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="running-values"></a>Valeurs en cours d’exécution

Affiche les valeurs en cours d'exécution pour les options de ce volet. Ces valeurs sont en lecture seule.  
  
## <a name="see-also"></a>Voir aussi

- [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)

- [Spécifier un facteur de remplissage pour un index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)