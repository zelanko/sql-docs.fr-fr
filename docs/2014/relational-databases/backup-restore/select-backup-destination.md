---
title: Sélectionner la destination de la sauvegarde, boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdest.f1
ms.assetid: f79e824b-1525-45de-8ede-513563af41b6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d9b4a0e07f32e074ff7e8875c263615bcebc12d1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874877"
---
# <a name="select-backup-destination"></a>Sélectionner la destination de la sauvegarde
  Utilisez la boîte de dialogue **Sélectionner la destination de la sauvegarde** pour choisir le périphérique de destination de vos sauvegardes. La destination de la sauvegarde peut être un disque ou une unité logique de sauvegarde.  
  
 **Pour utiliser SQL Server Management Studio pour sauvegarder une base de données**  
  
-   [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Créer une sauvegarde différentielle de base de données &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
-   [Sauvegarder des fichiers et des groupes de fichiers &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
## <a name="options"></a>Options  
 Les options de cette boîte de dialogue varient selon que vous sélectionnez un disque ou une bande comme destination de la sauvegarde.  
  
 **Destinations sur disque**  
 Pour spécifier une destination de sauvegarde, sélectionnez l'une des options suivantes.  
  
|||  
|-|-|  
|**Nom de fichier**|Sélectionnez cette option pour entrer le nom d'un fichier local ou distant de destination de la sauvegarde, dans la zone de texte.<br /><br /> Pour spécifier un fichier local, cliquez sur le bouton Parcourir à droite de la zone de texte et accédez à un fichier sur les lecteurs fixes de l’ordinateur qui exécute le serveur, ou entrez directement le chemin d’accès complet et le nom de fichier. par exemple, `C:\Program Files\Microsoft SQL Server\MSSQL\Backup\AdventureWorksBackup.bak`.<br /><br /> Pour spécifier un fichier distant en tant que destination de sauvegarde, tapez son nom complet UNC (Universal Naming Convention). Pour plus d’informations, consultez [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md).<br /><br /> **\*\* Important \*\*** Étant donné que la sauvegarde de données sur un réseau peut faire l’objet d’erreurs réseau, nous vous recommandons de vérifier l’opération de sauvegarde quand elle est terminée. Pour plus d’informations, consultez [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql).|  
|**unité de sauvegarde**|Choisissez cette option pour sélectionner une unité logique de sauvegarde.<br /><br /> Remarque : Pour plus d’informations sur la création d’une unité de sauvegarde sur disque, consultez [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md).|  
  
 **Destinations sur bande**  
 Indiquez comme destination de la sauvegarde un lecteur de bande connecté physiquement à l’ordinateur serveur (celui qui exécute l’instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)]). Choisissez l'une des options suivantes.  
  
|||  
|-|-|  
|**Lecteur de bande**|Choisissez cette option pour sélectionner un lecteur de bande choisi comme destination de la sauvegarde dans la liste des lecteurs de bande physiquement connectés à l'ordinateur qui exécute l'instance de serveur.<br /><br /> Remarque : les unités de sauvegarde sur bande situées sur des ordinateurs distants ne sont pas des destinations de sauvegarde valides.|  
|**unité de sauvegarde**|Choisissez cette option pour sélectionner une unité logique de sauvegarde existante. Ces unités logiques de sauvegarde correspondent aux lecteurs de bande connectés physiquement à l'ordinateur exécutant l'instance de serveur.<br /><br /> Remarque : Pour plus d’informations sur la création d’une unité de sauvegarde sur bande, consultez [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
