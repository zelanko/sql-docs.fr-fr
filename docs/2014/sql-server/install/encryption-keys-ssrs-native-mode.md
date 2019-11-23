---
title: Clés de chiffrement (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.encryptionkeypanel.F1
ms.assetid: cc7e6f84-80e1-4b5e-9409-d0e074edd147
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 540cf25a150349c7b6399975d20d10bc202ed935
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952171"
---
# <a name="encryption-keys-ssrs-native-mode"></a>Clés de chiffrement (SSRS en mode natif)
  Utilisez la page Clés de chiffrement pour gérer la clé symétrique utilisée pour chiffrer et déchiffrer les données dans un serveur de rapports. La gestion des clés de chiffrement représente une partie importante de la configuration du serveur de rapports. La clé symétrique est créée et appliquée automatiquement lorsque vous créez la base de données du serveur de rapports. Créez une copie de sauvegarde de la clé symétrique de façon à pouvoir effectuer les opérations de maintenance de routine. Les tâches de maintenance suivantes nécessitent une copie valide de la clé symétrique :  
  
-   Modification du compte du service Report Server  
  
-   Migration d'une installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vers un autre ordinateur  
  
-   Configuration d'une nouvelle instance de serveur de rapports pour partager ou utiliser une base de données existante du serveur de rapports  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
> [!IMPORTANT]  
>  Par mesure de sécurité, il est recommandé de modifier régulièrement la clé de chiffrement Reporting Services. Il est recommandé de modifier la clé juste après la mise à niveau d'une version principale de Reporting Services. La modification de la clé après une mise à niveau réduit l'interruption de service provoquée par la modification de la clé de chiffrement Reporting Services hors du cycle de mise à niveau.  
  
 La restauration de la clé symétrique est nécessaire si vous avez mis à jour le compte d'utilisateur du service Report Server (et si vous avez utilisé un outil autre que le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour modifier le compte) ou si vous effectuez la migration d'une installation de serveur de rapports vers un nouveau serveur.  
  
 Pour protéger la clé symétrique de tout accès non autorisé, cette clé est chiffrée à l'aide de la clé privée du service Report Server. Seul le service Report Server est capable de déverrouiller et d'utiliser la clé symétrique pour stocker des données sensibles dans la base de données du serveur de rapports. Si vous modifiez l'identité du service Report Server ou si vous effectuez la migration du serveur de rapports vers un nouvel ordinateur, la clé privée du service Report Server ne sera plus capable de déverrouiller la clé symétrique. Pour restaurer l'accès à la clé symétrique, chiffrez-la une nouvelle fois à l'aide de la clé privée de la nouvelle identité du service Report Server. La restauration de la clé symétrique est le processus qui conduit au nouveau chiffrement.  
  
 Vous devez restaurer une clé symétrique seulement s'il s'agit de la même clé actuellement utilisée pour chiffrer et déchiffrer les données dans la base de données du serveur de rapports. Si vous restaurez une clé symétrique non valide, vous ne pourrez plus accéder aux données sensibles. Dans ce cas, vous supprimez et recréez la clé.  
  
> [!IMPORTANT]  
>  La suppression de la clé symétrique ou la création d'une nouvelle clé ne peut pas être inversée ou annulée. La suppression de la clé symétrique ou la création d'une nouvelle clé peut avoir d'importantes conséquences sur votre installation actuelle. Si vous supprimez la clé, toute donnée existante chiffrée par la clé symétrique sera également supprimée. Les données supprimées incluent les chaînes de connexion aux sources de données de rapport externes, les chaînes de connexion stockées et certaines informations d'abonnement.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et sélectionnez le lien dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Backup**  
 Copie la clé symétrique dans un fichier que vous spécifiez. La clé symétrique n'est jamais stockée en texte clair. Vous devez taper un mot de passe pour protéger le fichier.  
  
 **Restaurer**  
 Applique une copie de la clé symétrique enregistrée précédemment à la base de données du serveur de rapports. Vous devez fournir un mot de passe pour déverrouiller le fichier.  
  
 La copie précédente de la clé symétrique de l'instance du serveur de rapports à laquelle vous est actuellement connecté est remplacée par la version restaurée. Après avoir restauré la clé symétrique, vous devez initialiser tous les serveurs de rapports qui utilisent la base de données du serveur de rapports. Pour plus d’informations sur l’initialisation des serveurs de rapports, consultez [initialiser &#40;un Configuration Manager&#41;SSRS de serveur de rapports](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md).  
  
 **Modifiés**  
 Recrée la clé symétrique et rechiffre toutes les valeurs chiffrées de la base de données du serveur de rapports. Veillez à arrêter le service Report Server avant de recréer la clé symétrique.  
  
 Dans un déploiement avec montée en puissance parallèle, toutes les copies de la clé symétrique sont remplacées par les versions plus récentes. Avant de remplacer la clé symétrique, veillez à passer en revue la liste des serveurs joints au déploiement avec montée en puissance parallèle pour vérifier que seules les instances valides du serveur de rapports obtiennent un accès à la nouvelle clé. Les serveurs qui font partie d'un déploiement avec montée en puissance parallèle sont répertoriés dans la page **Déploiement avec montée en puissance parallèle** . Arrêtez le service sur chaque serveur de rapports du déploiement avant de recréer la clé.  
  
 Notez que la régénération de la clé symétrique peut prendre du temps s'il existe un grand nombre de sources de données et d'abonnements.  
  
 **Delete**  
 Supprime la clé symétrique de la totalité du contenu chiffré, notamment les chaînes de connexion et les informations d'identification stockées. Vous devez supprimer uniquement la clé symétrique si vous ne pouvez pas la restaurer.  
  
 Une fois la clé symétrique supprimée, vous devez entrer à nouveau les chaînes de connexion et les informations d'identification stockées manquantes dans les rapports et les sources de données partagées qui ne contiennent plus ces valeurs. Vous devez également mettre à jour tous les abonnements dont les extensions de remise stockent des données chiffrées. Il s'agit notamment de l'extension de remise de partage de fichiers et des éventuelles extensions de remise tierces qui utilisent les valeurs chiffrées.  
  
 Il n'existe pas de méthode automatique de mise à jour de ces informations. Les rapports, les abonnements et les sources de données partagées qui utilisent des informations d'identification stockées et des chaînes de connexion doivent être mis à jour l'un après l'autre.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services les &#40;rubriques d’aide F1 en&#41; mode natif SSRS](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sauvegarder et restaurer les clés de chiffrement Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Supprimer et recréer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)  
  
  
