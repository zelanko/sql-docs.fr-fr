---
title: Déterminer si une procédure stockée ou une table doit être déplacée vers l’OLTP en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- Analyze, Migrate, Report
- AMR
ms.assetid: c1ef96f1-290d-4952-8369-2f49f27afee2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de6a778f9cdbfb7ab916f40a5250ca4f9e20c811
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63072370"
---
# <a name="determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp"></a>Déterminer si un tableau ou une procédure stockée doit être déplacée vers l'OLTP en mémoire
  Le collecteur de performances de transaction dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] vous aide à vous évaluez si l’OLTP en mémoire améliore les performances de votre application de base de données. Le rapport d'analyse des performances de transaction indique également le volume de travail nécessaire pour activer l'OLTP en mémoire dans votre application. Après avoir identifié une table sur disque pour la fonctionnalité OLTP en mémoire, utilisez le [Conseiller d’optimisation de la mémoire](memory-optimization-advisor.md)pour migrer la table. De même, le [Conseiller de compilation native](native-compilation-advisor.md) vous aide à déplacer une procédure stockée vers une procédure stockée compilée en mode natif.  
  
 Cette rubrique explique comment :  
  
-   configurer l'entrepôt de données de gestion ;  
  
-   configurer la collecte de données ;  
  
-   générer des rapports d'analyse des performances de transaction pour identifier les tables et les procédures stockées ayant un impact sur les performances.  
  
 Pour plus d’informations sur les méthodologies de migration, consultez [OLTP en mémoire - Modèles de charge de travail courants et considérations relatives à la migration](https://msdn.microsoft.com/library/dn673538.aspx).  
  
 Le collecteur de performances et les rapports d'évaluation des performances de transaction vous aident à effectuer les tâches suivantes :  
  
-   Analyse de votre charge de travail afin de déterminer si l'OLTP en mémoire va améliorer les performances. Le collecteur de performances de transaction collecte et évalue les caractéristiques des performances de votre charge de travail. . Le rapport d'analyse des performances de transaction recommande ensuite les tables et les procédures stockées qui tireront le plus parti de la migration vers l'OLTP en mémoire.  
  
-   Aide pour la planification et l'exécution de votre migration vers l'OLTP en mémoire. Le chemin de migration d'une table sur disque vers une table mémoire optimisée peut prendre beaucoup de temps. Le Conseiller d'optimisation de la mémoire vous aide à identifier les incompatibilités dans votre table que vous devez supprimer avant de déplacer la table vers l'OLTP en mémoire. Le gestionnaire d'optimisation de la mémoire vous aide également à comprendre l'impact que la migration d'une table vers une table mémoire optimisée aura sur votre application.  
  
     Déterminez si votre application va tirer parti de l'OLTP en mémoire, lorsque vous souhaitez planifier votre migration vers l'OLTP en mémoire et lorsque vous travaillez pour migrer certaines de vos tables et procédures stockées vers l'OLTP en mémoire.  
  
    > [!IMPORTANT]  
    >  Les performances d'un système de base de données dépendent de différents facteurs, tous ne pouvant pas être observés et mesurés par le collecteur de performances de transaction. Par conséquent, le rapport d'analyse des performances de transaction ne garantit pas que les gains de performances réels correspondront aux prédictions, si des prédictions sont faites.  
  
 Le collecteur de performances de transaction et la capacité à générer un rapport analyse de performances de transaction sont installés lorsque vous sélectionnez **outils de gestion-Basic** ou **outils de gestion avancés** Lorsque vous installez [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Le flux de travail recommandé est illustré dans l'organigramme suivant. Les nœuds jaunes représentent les procédures facultatives :  
  
 ![Flux de travail AMR](../../database-engine/media/amr-1.gif "flux de travail AMR")  
  
 Vous pouvez utiliser n'importe quelle méthode pour déterminer vos performances de référence, y compris, notamment, les journaux du compteur de performances ou le moniteur d'activité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les informations à utiliser pour déterminer vos performances de base et vos comparaisons sont les suivantes :  
  
-   Consommation de l'UC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Consommation de mémoire de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Activité des E/S de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Débit de l'instance lors du traitement des transactions.  
  
 Le collecteur de performances de transaction capture les données toutes les 15 minutes. Pour obtenir des résultats utilisables, exécutez le collecteur de performances de transaction pendant au moins une heure. Pour obtenir de meilleurs résultats, exécutez le collecteur de performances de transaction aussi longtemps que nécessaire pour capturer des données pour vos principaux scénarios. Générez un rapport d'évaluation des performances de transaction uniquement après avoir terminé de regrouper les données.  
  
 Configurez le collecteur de performances de transaction de façon à ce qu'il s'exécute sur votre instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans l'environnement de production et collecte les données sur une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans votre environnement de développement (test) pour garantir une charge minimale. Pour plus d’informations sur la façon d’enregistrer des données dans une base de données d’entrepôt de données de gestion sur un référentiel distant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] une instance, consultez [configurer la collecte des données sur une Instance distante de SQL Server](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx).  
  
## <a name="performance-impacts"></a>Impacts sur les performances  
 Le collecteur de performances de transaction comprend deux jeux d'éléments de collecte de données :  
  
-   Analyse de l'utilisation des tables  
  
-   Analyse des procédures stockées  
  
 Les jeux d'éléments de collecte collectent des données de trois vues de gestion dynamique toutes les quinze minutes, puis téléchargent les données dans la base de données configurée pour faire office d'entrepôt de données de gestion. Le téléchargement des données collectées a un faible impact sur les performances.  
  
## <a name="use-the-transaction-performance-collector"></a>Utiliser le collecteur de performances de transaction  
 Les étapes suivantes requièrent [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  Ne modifiez pas le schéma (par exemple, en ajoutant ou en supprimant des bases de données ou des tables) lors du profilage. Si vous modifiez le schéma d'une base de données pendant la collecte des données, la base de données peut ne pas être correctement incluse dans le rapport.  
  
### <a name="configure-management-data-warehouse"></a>Configurer l'entrepôt de données de gestion  
 L'entrepôt de données de gestion doit être configuré pour utiliser le collecteur de performances de transaction.  
  
 La version de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur laquelle vous allez collecter les données (profil) doit être identique ou antérieure à celle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] où l'entrepôt de données de gestion est configuré.  
  
1.  Dans l’Explorateur d’objets, développez **Gestion**.  
  
2.  Bouton droit sur **collecte des données** et sélectionnez **tâches** , puis **configurer un entrepôt de données de gestion**. Le **Assistant Configuration de l’entrepôt des données de gestion** commence.  
  
3.  Cliquez sur **suivant** pour sélectionner la base de données qui jouera le rôle de l’entrepôt de données de gestion.  
  
4.  Cliquez sur **New** pour créer une nouvelle base de données pour stocker les données de profil. Après avoir créé la base de données, cliquez sur **suivant** dans l’Assistant.  
  
5.  L'étape suivante de l'Assistant vous permet d'ajouter des utilisateurs et des noms de connexion. Vous pouvez mapper les noms de connexion aux appartenances aux rôles pour l'instance de l'entrepôt de données de gestion (MDW). Cela n'est pas obligatoire pour collecter des données sur l'instance locale. Si vous ne collectez pas de données depuis l'instance locale, vous pouvez accorder l'appartenance au rôle de base de données `mdw_admin` au compte qui exécutera les transactions qui seront profilées. Lorsque vous avez terminé, cliquez sur **suivant**.  
  
6.  Vérifiez que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent s'exécute.  
  
7.  Dans l’écran suivant, cliquez sur **Terminer** pour quitter l’Assistant.  
  
### <a name="configure-data-collection-on-a-local-includessnoversionincludesssnoversion-mdmd-instance"></a>Configurer la collecte de données sur une instance locale de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 La collecte de données requiert le démarrage de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Vous ne devez configurer qu'un collecteur de données sur un serveur.  
  
 Un collecteur de données peut être configuré sur un SQL Server 2012 ou une version ultérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Pour configurer la collecte de données à télécharger vers une base de données de l'entrepôt de données de gestion sur la même instance, procédez comme suit :  
  
1.  Dans **Explorateur d’objets**, développez **gestion**.  
  
2.  Bouton droit sur **collecte des données**, sélectionnez **tâches**, puis **configurer la collecte des données**. Le **configurer un Assistant de collecte de données** commence.  
  
3.  Cliquez sur **suivant** pour sélectionner la base de données qui collectera les données de profil.  
  
4.  Sélectionnez l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] active et une base de données d'entrepôt de données de gestion sur cette instance.  
  
5.  Dans la zone intitulée **sélectionner des ensembles de collecteurs de données vous souhaitez activer**, sélectionnez **collecte de performances de documents informatisés**. Cliquez sur **suivant** lorsque vous avez terminé.  
  
6.  Vérifiez les sélections. Cliquez sur **retour** pour modifier les paramètres. Cliquez sur **Terminer** lorsque vous avez terminé.  
  
###  <a name="xxx"></a> Configurer la collecte de données sur un référentiel distant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Instance  
 La collecte de données nécessite que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] soit démarré sur l'instance qui va collecter les données.  
  
 Un collecteur de données peut être configuré sur un SQL Server 2012 ou une version ultérieure de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Vous avez besoin d'un proxy [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent créé avec des informations d'identification correctes pour qu'un collecteur de données télécharge des données dans une base de données d'entrepôt de données de gestion sur une instance différente de celle où les transactions seront profilées. Pour activer un proxy [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, vous devez d'abord créer des informations d'identification avec un nom de connexion spécifique au domaine. La connexion activée pour le domaine doit être membre du groupe `mdw_admin` pour la base de données de l'entrepôt de données de gestion. Consultez [Procédure : Créer une information d’identification (SQL Server Management Studio)](../security/authentication-access/create-a-credential.md) pour plus d’informations sur la création d’une information d’identification.  
  
 Pour configurer la collecte de données à télécharger vers une base de données de l'entrepôt de données de gestion sur une autre instance, procédez comme suit :  
  
1.  Sur l’instance qui contient les objets sur disque que vous souhaitez migrer vers OLTP en mémoire, développez le **gestion** nœud dans l’Explorateur d’objets.  
  
2.  Bouton droit sur **collecte des données** et sélectionnez **tâches** , puis **configurer la collecte des données**. Le **configurer un Assistant de collecte de données** commence.  
  
3.  Cliquez sur **suivant** pour sélectionner la base de données qui collectera les données de profil.  
  
4.  Assurez-vous qu'il existe un entrepôt de données de gestion sur l'autre instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
5.  Sélectionnez une autre instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et une base de données d'entrepôt de données de gestion sur cette instance.  
  
     La version de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur laquelle vous allez collecter les données (profil) doit être identique ou antérieure à celle de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] où l'entrepôt de données de gestion est configuré.  
  
6.  Dans la zone intitulée **sélectionner des ensembles de collecteurs de données vous souhaitez activer**, sélectionnez **collecte de performances de documents informatisés**.  
  
7.  Sélectionnez **utilisez un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent proxy pour les téléchargements distants**.  
  
8.  Cliquez sur **suivant** lorsque vous avez terminé.  
  
9. Sélectionnez le proxy.  
  
     Si vous souhaitez créer un proxy [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent,  
  
    1.  Cliquez sur **New** pour afficher le **nouveau compte Proxy** boîte de dialogue.  
  
    2.  Dans le **nouveau compte Proxy** boîte de dialogue, entrez le nom du proxy, sélectionnez les informations d’identification et entrez éventuellement une description. Ensuite, cliquez sur **principaux**.  
  
    3.  Cliquez sur **ajouter** et sélectionnez **Msdb** rôle.  
  
    4.  Sélectionnez `dc_proxy` et cliquez sur **OK**. Puis cliquez sur **OK** à nouveau.  
  
     Une fois que le proxy approprié est sélectionné, cliquez sur **suivant**.  
  
10. Pour configurer des jeux d’éléments système, cochez **jeux d’éléments système** et cliquez sur **suivant**.  
  
11. Vérifiez les sélections. Cliquez sur **retour** pour modifier les paramètres. Cliquez sur **Terminer** lorsque vous avez terminé.  
  
 Les jeux d'éléments de collecte de données doivent maintenant être configurés et exécutés sur votre instance.  
  
### <a name="generate-reports"></a>Générer des rapports  
 Vous pouvez générer des rapports d’analyse de performances de transaction en cliquant avec le bouton droit sur la base de données de l’entrepôt de données de gestion et en sélectionnant **rapports**, puis **entrepôt de données de gestion**, puis **Présentation analyse performances des transactions**.  
  
 Le rapport collecte des informations sur toutes les bases de données utilisateur sur le serveur de charge de travail. Si la base de données de l'entrepôt de données de gestion (MDW) se trouve sur l'ordinateur local, la base de données MDW s'affiche dans le rapport.  
  
 Une procédure stockée avec un rapport élevé temps UC/temps écoulé est un candidat pour la migration. Le rapport affiche toutes les références de table, car les procédures stockées compilées en mode natif ne peuvent référencer que les tables mémoire optimisées, ce qui augmente le coût de migration.  
  
 Le rapport détaillé d'une table comprend trois sections :  
  
-   Section des statistiques d'analyse  
  
     Cette section comprend une seule table contenant les statistiques collectées à propos des analyses sur la table de base de données. Les colonnes sont les suivantes :  
  
    -   Pourcentage du total des accès. Pourcentage des analyses et des recherches sur cette table, par rapport à l'activité de la base de données totale. Plus ce pourcentage est élevé, plus la table est sollicitée par rapport aux autres tables de la base de données.  
  
    -   Statistiques de recherche/Statistiques d'analyse de plage. Cette colonne indique le nombre de recherches de point et d'analyses de plage (analyses d'index et de table) effectuées sur la table pendant le profilage. La moyenne par transaction est une estimation.  
  
    -   Gain d'interopérabilité et gain natif. Ces colonnes estiment les avantages au niveau des performances que la recherche de point et l'analyse de plage pourraient offrir si la table était convertie en table mémoire optimisée.  
  
-   Section des statistiques de contention  
  
     Cette section comprend un tableau indiquant la contention sur la table de base de données. Pour plus d’informations sur les verrous de base de données, consultez [Architecture du verrouillage](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx). Les colonnes sont les suivantes :  
  
    -   Pourcentage du total des attentes. Pourcentage des attentes attribuables à un verrou interne et un verrou sur cette table de base de données par rapport à l'activité de la base de données. Plus ce pourcentage est élevé, plus la table est sollicitée par rapport aux autres tables de la base de données.  
  
    -   Statistiques des verrous internes. Ces colonnes indiquent le nombre d'attentes attribuables à un verrou interne pour les requêtes impliquant cette table. Pour plus d’informations sur les verrous internes, consultez [verrouillage interne](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx). Plus ce nombre est élevé, plus il y a de contention de verrous internes sur la table.  
  
    -   Statistiques des verrous. Ce groupe de colonnes indique le nombre d'acquisitions et d'attentes attribuables à des verrous de page pour les requêtes de cette table. Pour plus d’informations sur les verrous, consultez [comprendre le verrouillage dans SQL Server](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx). Plus le nombre d'attentes est élevé, plus il y a de contention de verrous sur la table.  
  
-   Section des difficultés de migration  
  
     Cette section comprend un tableau des difficultés rencontrées pour convertir cette table de base de données en une table mémoire optimisée. Plus le taux de difficultés est élevé, plus il est difficile de convertir la table. Pour afficher les détails de la conversion de cette table de base de données, utilisez le [Memory Optimization Advisor](memory-optimization-advisor.md).  
  
 Statistiques d’analyse et de contention dans le rapport détaillé de table sont collectées et agrégées à partir de [sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).  
  
 Le rapport détaillé d'une procédure stockée comprend deux sections :  
  
-   Section des statistiques d'exécution  
  
     Cette section comprend un tableau contenant les statistiques collectées à propos des exécutions de la procédure stockée. Les colonnes sont les suivantes :  
  
    -   Heure de mise en cache. Heure à laquelle ce plan d'exécution est mis en cache. Si la procédure stockée supprime le cache du plan et recommence, il y aura des heures pour chaque cache.  
  
    -   Temps processeur total. Temps processeur total consommé par la procédure stockée pendant le profilage. Plus ce nombre est élevé, plus la procédure stockée utilise de temps de processeur.  
  
    -   Durée totale d'exécution. Durée d'exécution totale de la procédure stockée pendant le profilage. Plus la différence entre ce chiffre et le temps processeur est élevée, moins le temps processeur est utilisé efficacement par la procédure stockée.  
  
    -   Total des absences dans le cache. Nombre d’absences dans le cache (lectures depuis un stockage physique) causées par les exécutions de la procédure stockée pendant le profilage.  
  
    -   Nombre d'exécutions. Nombre de fois que la procédure stockée est exécutée pendant le profilage.  
  
-   Section des références de table  
  
     Cette section comprend un tableau répertoriant les tables auxquelles cette procédure stockée se réfère. Avant de convertir la procédure stockée en une procédure stockée compilée en mode natif, toutes ces tables doivent être converties en tables mémoire optimisées, et résider sur le même serveur et la même base de données.  
  
 Statistiques d’exécution dans le rapport détaillé de procédure stockée sont collectées et agrégées à partir de [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql). Les références sont obtenues à partir de [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql).  
  
 Pour afficher les détails sur la conversion d’une procédure stockée à une procédure stockée compilée en mode natif, utilisez le [Conseiller de Compilation Native](native-compilation-advisor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
