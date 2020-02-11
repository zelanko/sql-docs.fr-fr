---
title: Déploiement avec montée en puissance parallèle (serveur de rapports en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.scaleoutdeployment.F1
ms.assetid: 4df38294-6f9d-4b40-9f03-1f01c1f0700c
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: a9fe82102df73ddfa77b4636dd29793ac2694949
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952417"
---
# <a name="scale-out-deployment-native-mode-report-server"></a>Déploiement avec montée en puissance parallèle (serveur de rapports en mode natif)
  Utilisez la page **Déploiement avec montée en puissance parallèle** dans le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour afficher l'état d'initialisation d'un déploiement avec montée en puissance parallèle ou pour joindre un serveur de rapports à un déploiement avec montée en puissance parallèle. Un *déploiement avec montée en puissance* fait référence à deux ou plusieurs instances de serveurs de rapports qui partagent une même base de données de serveur de rapports.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode natif.  
  
 Un *serveur de rapports initialisé* décrit un serveur qui peut chiffrer et déchiffrer les données sensibles stockées dans une base de données de serveur de rapports (par exemple, les informations d'identification et les chaînes de connexion). L'initialisation d'un serveur de rapports est nécessaire à son fonctionnement.  
  
 Un *déploiement avec montée en puissance parallèle* est utilisé dans les scénarios suivants :  
  
-   Comme condition préalable pour l'équilibrage de charge de plusieurs serveurs de rapports dans un cluster de serveurs. Avant de pouvoir soumettre plusieurs serveurs de rapports à l'équilibrage de charge, vous devez les configurer pour qu'ils partagent la même base de données de serveur de rapports.  
  
-   Pour segmenter les applications du serveur de rapports sur différents ordinateurs, en utilisant un serveur pour le traitement interactif des rapports et un autre serveur pour le traitement planifié des rapports. Dans ce scénario, chaque instance de serveur traite les différents types de demandes pour le même contenu de serveur de rapports stocké dans la base de données partagée du serveur de rapports.  
  
 Pour configurer un déploiement avec montée en puissance parallèle, commencez par deux instances de serveurs de rapports ou plus qui sont toutes connectées à la même base de données de serveur de rapports. Après que toutes les instances ont été installées, vous vous connectez au premier serveur de rapports, puis utilisez la page Déploiement avec montée en puissance parallèle pour attacher chaque instance supplémentaire. Seul un serveur de rapports déjà initialisé pour utiliser une base de données peut initialiser des nœuds supplémentaires.  
  
 Pour ouvrir la page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et sélectionnez **Déploiement avec montée en puissance parallèle** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Nom du serveur SQL Server**  
 Spécifiez le nom de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] l’instance qui héberge la base de données du serveur de rapports.  
  
 **Nom de la base de données**  
 Spécifie le nom de la base de données à laquelle l'instance de serveur de rapports est connectée.  
  
 **Mode serveur**  
 Affiche le mode du serveur et de la base de données. Le mode du serveur est le mode natif ou le mode intégré SharePoint. Les déploiements avec montée en puissance parallèle sont pris en charge pour les deux modes.  
  
 **Serveur**  
 Affiche le nom du serveur de rapports. Dans la plupart des cas, il s'agit du nom de l'ordinateur sur lequel le serveur de rapports est installé.  
  
 **Instance**  
 Affiche le nom de l'instance du serveur de rapports. Les instances de serveur de rapports sont basées sur les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **État**  
 Indique si le serveur de rapports est initialisé ou en attente de rejoindre un déploiement avec montée en puissance parallèle :  
  
-   Pour un serveur de rapports qui ne fait pas partie d'un déploiement avec montée en puissance parallèle, cette page montre que l'instance du serveur de rapports est initialisée par rapport à sa base de données de serveur de rapports dédiée. L'état est défini sur **Joint**.  
  
-   Pour un serveur de rapports en attente de joindre un déploiement avec montée en puissance parallèle, cette page contient les valeurs vides de Serveur, Instance et État. Un serveur de rapports attend de joindre un déploiement avec montée en puissance parallèle si vous avez sélectionné une base de données existante du serveur de rapports déjà utilisée par une autre instance de serveur de rapports. Un message de cette page vous demande de vous connecter à un serveur de rapports déjà joint à la batterie de serveurs. Pour compléter cette demande, cliquez sur **Se connecter**, sélectionnez un serveur de rapports déjà initialisé pour utiliser la base de données du serveur de rapports, cliquez sur **Déploiement avec montée en puissance parallèle**, sélectionnez l'instance de serveur de rapports **En attente de joindre**, puis cliquez sur **Initialiser**.  
  
-   Pour un serveur de rapports qui fait actuellement partie d'un déploiement avec montée en puissance parallèle, cette page indique l'état d'initialisation de toutes les instances de serveur de rapports qui partagent la même base de données de serveur de rapports. Lors de l'affichage de l'état d'un déploiement avec montée en puissance parallèle, peu importe le serveur auquel vous êtes connecté. Les informations d'état sont signalées de manière identique pour tous les nœuds du déploiement avec montée en puissance parallèle.  
  
     Pour un serveur de rapports qui fait déjà partie d'un déploiement avec montée en puissance parallèle, vous pouvez utiliser cette page pour ajouter ou supprimer des nœuds.  
  
 **Initialiser**  
 Cliquez sur **Initialiser** pour ajouter un serveur de rapports au déploiement avec montée en puissance parallèle. Cette étape configure un serveur de rapports de telle sorte qu'il utilise une clé symétrique dans une base de données de serveur de rapports partagée. Vous pouvez utiliser **Initialiser** pour ajouter une instance de serveur de rapports à un déploiement avec montée en puissance parallèle ou pour résoudre un problème de migration ou d'installation.  
  
 Une instance de serveur de rapports est disponible uniquement si vous avez précédemment configuré une connexion à une base de données de serveur de rapports partagée. De plus, vous devez effectuer l'initialisation à partir d'un serveur de rapports qui est déjà initialisé pour utiliser la base de données du serveur de rapports.  
  
 **Remove**  
 Cliquez sur **Supprimer** pour supprimer de la base de données du serveur de rapports les clés de chiffrement de l'instance sélectionnée du serveur de rapports. Vous pouvez supprimer des clés pour retirer un serveur de rapports d'un déploiement avec montée en puissance parallèle ou pour résoudre un problème de migration ou d'installation. Avec cette option, seules les clés de chiffrement de l'instance spécifiée du serveur de rapports sont supprimées. Les données chiffrées dans la base de données du serveur de rapports ne sont pas concernées.  
  
 Par précaution, veillez à créer une copie de sauvegarde de la clé symétrique avant de la supprimer. Après avoir supprimé de la liste les clés de chiffrement du dernier serveur de rapports, vous introduisez de nouvelles conditions sur toutes les initialisations ultérieures de serveur de rapports pour cette base de données. En effet, après avoir initialisé un serveur de rapports, vous devez restaurer une copie de sauvegarde de la clé symétrique. La restauration de la clé symétrique est nécessaire pour pouvoir accéder aux données chiffrées actuellement présentes dans la base de données du serveur de rapports.  
  
 Si vous n'avez plus besoin des données chiffrées ou si vous ne possédez pas de copie de sauvegarde de la clé, vous devez supprimer les données chiffrées. Pour plus d’informations, consultez [clés de chiffrement &#40;SSRS en mode natif&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un serveur de rapports &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)   
 [Configurer un déploiement par montée en puissance parallèle de serveurs de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)  
  
  
