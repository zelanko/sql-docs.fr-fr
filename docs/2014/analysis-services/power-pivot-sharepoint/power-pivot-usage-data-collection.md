---
title: Collecte des données d’utilisation de PowerPivot | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 9057cb89-fb17-466e-a1ce-192c8ca20692
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e8993c4033112dd81be611bc3e2d36bfb1f30243
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304689"
---
# <a name="powerpivot-usage-data-collection"></a>Collecte des données d'utilisation PowerPivot
  La collecte des données d'utilisation est une fonctionnalité SharePoint au niveau de la batterie de serveurs. Le service PowerPivot pour SharePoint utilise et étend ce système pour fournir des rapports intégrés dans le tableau de bord de gestion PowerPivot qui indiquent la manière dont les données et services PowerPivot sont utilisés. Selon la façon dont vous avez installé votre serveur SharePoint, la collecte des données d'utilisation peut être désactivée pour la batterie de serveurs. Un administrateur de batterie doit activer la journalisation de l'utilisation pour créer les données d'utilisation qui s'affichent dans le tableau de bord de gestion PowerPivot. Pour plus d’informations sur comment activer et configurer la collecte de données d’utilisation pour PowerPivot consultez événements [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 Pour plus d’informations sur les données d’utilisation dans le tableau de bord de gestion PowerPivot, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **Dans cette rubrique :**  
  
 [Collecte des données d’utilisation et Architecture de création de rapports](#usagearch)  
  
 [Sources de données d’utilisation](#sources)  
  
 [Services et travaux du minuteur](#servicesjobs)  
  
 [Création de rapports sur les données d’utilisation](#reporting)  
  
##  <a name="usagearch"></a> Collecte de données d'utilisation et architecture de la création de rapports  
 Les données d'utilisation PowerPivot sont collectées, stockées et gérées à l'aide d'une combinaison de fonctionnalités de l'infrastructure SharePoint et des composants serveur PowerPivot. L'infrastructure SharePoint fournit un service d'utilisation centralisé et des travaux de minuteur intégrés. PowerPivot pour SharePoint ajoute un stockage à plus long terme des données d'utilisation PowerPivot et des rapports que vous affichez dans l'Administration centrale SharePoint.  
  
 Dans le système de collecte des données d'utilisation, les informations d'événement sont intégrées au système de collecte des données d'utilisation sur le serveur d'applications ou le serveur Web frontal. Les données d'utilisation se déplacent dans le système en réponse aux travaux du minuteur : les données des fichiers de données temporaires sur le serveur physique sont déplacées vers un emplacement de stockage permanent sur un serveur de base de données. Le tableau suivant présente les composants et les traitements qui déplacent les données d'utilisation au sein du système de collecte des données et de création de rapports.  
  
 **Remarque :** vérifiez que la collecte des données d'utilisation est activée. Pour le vérifier, accédez à **Analyse** dans l'Administration centrale SharePoint. Pour plus d’informations, consultez [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
 ![Composants et les processus de collecte des données d’utilisation. ] (../media/gmni-usagedata.gif "Composants et les processus de collecte des données d’utilisation.")  
  
|Phase|Description|  
|-----------|-----------------|  
| 1|La collecte des données d'utilisation est déclenchée par des événements générés par les composants PowerPivot et les fournisseurs de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans les déploiements SharePoint. Les événements configurables susceptibles d'être activés ou désactivés sont les suivants : demandes de connexion, demandes de chargement et de déchargement, et événements de temps de réponse aux requêtes qui sont supervisés par le service PowerPivot sur le serveur d'applications. Vous ne pouvez pas désactiver les autres événements qui sont gérés exclusivement par le serveur, tels que les événements d'actualisation des données et d'intégrité des serveurs.<br /><br /> Les données d'utilisation sont tout d'abord collectées et stockées dans les fichiers journaux locaux à l'aide des fonctionnalités de collecte des données du système SharePoint. Les fichiers et leur emplacement font partie du système standard de collecte des données d'utilisation de SharePoint. L'emplacement des fichiers est le même sur chaque serveur de la batterie. Pour afficher ou modifier l'emplacement du répertoire de journalisation, accédez à **Analyse** dans l'Administration centrale de SharePoint, puis cliquez sur **Configurer la collection des données d'utilisation et d'intégrité**.|  
|2|À intervalles planifiés (par défaut, toutes les heures), le travail du minuteur Importation des données d'utilisation de Microsoft SharePoint Foundation déplace les données d'utilisation des fichiers locaux vers la base de données d'application de service PowerPivot. Si vous disposez de plusieurs applications de service PowerPivot dans une batterie de serveurs, chacune d'elle est dotée de sa propre base de données. Les événements incluent des informations internes qui identifient l'application de service PowerPivot qui a produit l'événement. Les identificateurs d'application vérifient que les données d'utilisation sont liées à l'application qui les a créées.|  
|3|Les données sont copiées dans une base de données de création de rapports interne, disponible dans le Tableau de bord de gestion PowerPivot dans l'Administration centrale.|  
|4|La source de données est un classeur PowerPivot auquel vous pouvez accéder pour créer des rapports personnalisés dans Excel. Il existe une seule instance du classeur source. Les rapports localisés sont tous basés sur le même classeur source.|  
|5|Les données d'utilisation sont présentées dans des rapports pour les administrateurs d'applications de service PowerPivot qui gèrent les performances et la disponibilité des serveurs. Les instances localisées des classeurs sont créées pour les langues prises en charge par SharePoint.<br /><br /> Pour plus d'informations, consultez [Création de rapports sur les données d'utilisation](#reporting) dans cette rubrique.|  
  
##  <a name="sources"></a> Sources des données d'utilisation  
 Lorsque la collecte des données d'utilisation est activée, des données sont générées pour les événements serveur suivants.  
  
|Événement|Description|Configurable|  
|-----------|-----------------|------------------|  
|Connexions|Il s'agit des connexions au serveur établies pour le compte d'un utilisateur qui interroge des données PowerPivot dans un classeur Excel. Les événements de connexion identifient la personne ayant établi une connexion à un classeur PowerPivot. Dans les rapports, ces informations permettent d'identifier les utilisateurs les plus fréquents, les sources de données PowerPivot qui sont utilisées par les mêmes utilisateurs, ainsi que les tendances des connexions dans le temps.|Vous pouvez activer et désactiver [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Temps de réponse aux requêtes|Il s'agit des statistiques de réponse aux requêtes qui classent les requêtes en fonction de leur durée d'exécution. Ces statistiques révèlent des modèles en termes de temps de réponse aux requêtes par le serveur.|Vous pouvez activer et désactiver [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Chargement des données|Il s'agit des opérations de chargement des données effectuées par le [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]. Les événements de chargement des données identifient les sources de données qui sont le plus fréquemment utilisées.|Vous pouvez activer et désactiver [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Déchargement des données|Il s'agit des opérations de déchargement des données effectuées par les applications de service PowerPivot. Un [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] décharge les sources de données PowerPivot inactives si elles ne sont pas utilisées, ou lorsque le serveur est soumis à une sollicitation de la mémoire ou a besoin d'une plus grande quantité de mémoire pour exécuter des travaux d'actualisation des données.|Vous pouvez activer et désactiver [Configure Usage Data Collection pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).|  
|Intégrité du serveur|Il s'agit des opérations serveur indiquant l'intégrité du serveur, qui est mesurée d'après l'utilisation du processeur et de la mémoire. Il s'agit de données d'historique ; elles ne fournissent pas d'informations en temps réel sur la charge de traitement actuelle du serveur.|Non. Les données d'utilisation sont systématiquement collectées pour cet événement.|  
|Actualisation des données|Il s'agit des opérations d'actualisation des données lancées par le service PowerPivot pour les mises à jour de données planifiées. L'historique d'utilisation pour l'actualisation des données est collecté au niveau application pour les rapports opérationnels, et il est répercuté dans les pages Gérer l'actualisation des données des classeurs.<br /><br /> **Remarque :** pour les déploiements de [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] et SharePoint 2013, l'actualisation des données est gérée par Excel Services et non par le serveur Analysis Services.|Non. Les données d'utilisation de l'actualisation des données sont systématiquement collectées si vous activez l'actualisation des données pour l'application de service PowerPivot.|  
  
##  <a name="servicesjobs"></a> Services et travaux du minuteur  
 Le tableau suivant décrit les services et les emplacements de stockage de la collecte des données dans le système de collecte des données d'utilisation. Pour obtenir des instructions sur la façon de remplacer les planifications du travail du minuteur forcer une actualisation des données des données d’intégrité et de l’utilisation du serveur dans les rapports de tableau de bord de gestion PowerPivot, consultez [d’actualisation des données PowerPivot avec SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md). Vous pouvez afficher les travaux du minuteur dans l'Administration centrale de SharePoint. Accédez à **Analyse**, puis cliquez sur **Vérifier l’état du travail**. Cliquez sur **Examiner les définitions de travail**.  
  
|Composant|Planification par défaut|Description|  
|---------------|----------------------|-----------------|  
|Service du minuteur SharePoint (SPTimerV4)||Ce service Windows s'exécute localement sur chaque ordinateur membre de la batterie de serveurs et traite tous les travaux du minuteur définis au niveau de la batterie.|  
|Importation des données d'utilisation de Microsoft SharePoint Foundation|Toutes les 30 minutes dans SharePoint 2010. Toutes les 5 minutes dans SharePoint 2013.|Ce travail du minuteur est configuré globalement au niveau de la batterie de serveurs. Il déplace les données d'utilisation des fichiers journaux d'utilisation locaux vers la base de données centrale de collecte des données d'utilisation. Vous pouvez exécuter ce travail du minuteur manuellement pour forcer une opération d'importation des données.|  
|Travail du minuteur pour le traitement des données d'utilisation de Microsoft SharePoint Foundation|Tous les jours à 3h00|**(\*)** Compter de SQL Server 2012 PowerPivot pour SharePoint, ce travail du minuteur est pris en charge les scénarios de mise à niveau ou migration comportant des données d’utilisation plus anciennes bases de données d’utilisation SharePoint. À compter de SQL Server 2012 PowerPivot pour SharePoint, la base de données d'utilisation de SharePoint n'est pas utilisée pour le flux de travail de collecte des données d'utilisation PowerPivot et du tableau de bord de gestion. Le travail du minuteur peut être exécuté manuellement pour déplacer toutes les données PowerPivot figurant encore dans la base de données d'utilisation de SharePoint vers les bases de données d'application de service PowerPivot.<br /><br /> Ce travail du minuteur est configuré globalement au niveau de la batterie de serveurs. Il vérifie si des données d'utilisation expirées (c'est-à-dire, des données datant de plus de 30 jours) sont présentes dans la base de données centrale de collecte des données d'utilisation. Pour les serveurs PowerPivot de la batterie, ce travail du minuteur effectue une vérification supplémentaire pour les données d'utilisation PowerPivot. Lorsque des données d'utilisation PowerPivot sont détectées, le travail du minuteur les déplace vers une base de données d'application de service à l'aide d'un identificateur d'application pour rechercher la base de données correcte.<br /><br /> Vous pouvez exécuter ce travail du minuteur manuellement pour forcer une vérification de la présence de données expirées, ou pour forcer l'importation des données d'utilisation PowerPivot vers une base de données d'application de service PowerPivot.|  
|Travail du minuteur pour le traitement du tableau de bord de gestion PowerPivot|Tous les jours à 3h00|Ce travail du minuteur met à jour le classeur PowerPivot interne qui fournit des données d'administration au tableau de bord de gestion PowerPivot. Il obtient des informations actualisées gérées par SharePoint, notamment les noms de serveur, d'utilisateur, d'application et de fichier qui s'affichent dans les rapports du tableau de bord ou les composants WebPart.|  
  
##  <a name="reporting"></a> Création de rapports sur les données d'utilisation  
 Pour afficher les données d'utilisation des données PowerPivot, vous pouvez accéder à des rapports intégrés dans le tableau de bord de gestion PowerPivot. Les rapports intégrés regroupent les données d'utilisation récupérées à partir des structures de données de création de rapports dans la base de données d'application de service. Les données de rapport sous-jacentes sont mises à jour quotidiennement. Par conséquent, les rapports d'utilisation intégrés affichent les informations mises à jour uniquement après que le travail du minuteur pour le traitement des données d'utilisation de Microsoft SharePoint Foundation a copié les données dans une base de données d'application de service PowerPivot. Par défaut, cela se produit une fois par jour.  
  
 Pour plus d’informations sur l’affichage des rapports, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de bord de gestion PowerPivot et les données d’utilisation](power-pivot-management-dashboard-and-usage-data.md)   
 [Référence de paramètre de configuration &#40;PowerPivot pour SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Configurer la collecte de données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)  
  
  
