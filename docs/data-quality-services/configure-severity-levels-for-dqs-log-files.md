---
description: Configurer les niveaux de gravité pour les fichiers journaux DQS
title: Configurer les niveaux de gravité pour les fichiers journaux DQS
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: swinarko
ms.author: sawinark
ms.openlocfilehash: 6a23806f7b7def561d7cecc8e1592772c5675f58
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449911"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a>Configurer les niveaux de gravité pour les fichiers journaux DQS

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sqlserver.md)]

  Cette rubrique décrit comment configurer des niveaux de gravité pour différents modules et activités dans [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Les niveaux de gravité définissent l'intensité des événements qui se produisent dans DQS. Les événements DQS ont les niveaux de gravité suivants, dans l'ordre décroissant de gravité :  
  
-   **Irrécupérable**: erreurs d'exécution critiques qui peuvent avoir des conséquences lourdes/inattendues.  
  
-   **Erreur**: autres erreurs d'exécution.  
  
-   **Avertir**: avertissement concernant des événements qui peuvent entraîner une erreur.  
  
-   **Informations**: information sur des événements généraux qui n'est pas une erreur ni un avertissement. Par exemple, un processus DQS a démarré.  
  
-   **Déboguer**: information détaillée (commentée) sur l'événement.  
  
 En configurant des niveaux de gravité pour différents modules et activités DQS, vous filtrez les informations qui doivent être enregistrées et écrites dans le fichier journal DQS pour l'activité ou le module DQS respectif. Par exemple, si vous affectez à une activité DQS le niveau de gravité **Avertir**, seuls les messages d'avertissement et de gravité supérieure (Erreur et Irrécupérable) associés à l'activité DQS sont enregistrés.  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez disposer du rôle dqs_administrator sur la base de données DQS_MAIN pour configurer les paramètres de gravité du journal.  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a> Configurer les niveaux de gravité au niveau de l’activité  
 Vous pouvez configurer des paramètres de gravité du journal pour les activités suivantes dans DQS : gestion de l'arborescence du domaine, découverte des connaissances, stratégie de correspondance, nettoyage des données, correspondance de données et services de données de référence. Pour cela :  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)][Exécutez l’Application Data Quality client](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Dans l'écran d'accueil de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] , cliquez sur **Configuration**.  
  
3.  Ensuite, cliquez sur l’onglet **paramètres du journal** . Les activités DQS suivantes sont répertoriées pour lesquelles vous pouvez sélectionner un niveau de gravité : gestion de l’ensemble du **domaine**, **découverte des connaissances**, projet de **nettoyage (par exemple, RDS)**, **stratégie de correspondance et projet de correspondance**, et **RDS**.  
  
4.  Pour une activité DQS, sélectionnez le niveau de gravité qui doit être enregistré. Vous pouvez sélectionner une valeur parmi les suivantes : **Irrécupérable**, **Erreur**, **Avertir**, **Informations**et **Déboguer**. Par exemple, si vous voulez que seuls les messages d'erreur irrécupérable soient écrits dans les fichiers journaux DQS pour l'activité de découverte des connaissances, sélectionnez **Irrécupérable** dans la liste déroulante pour l'activité **Découverte des connaissances** .  
  
    > [!NOTE]  
    >  Par défaut, le niveau **Erreur** est sélectionné pour chacune des activités. Cela implique que les messages d'erreur et les messages d'erreur irrécupérable seront écrits dans les fichiers journaux DQS pour chaque activité, par défaut.  
  
5.  Cliquez sur **Fermer**.  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a> Configurer les niveaux de gravité au niveau du module (avancé)  
 La section **Avancé** sous l'onglet **Paramètres de journal** vous permet de configurer des paramètres de gravité du journal au niveau d'un module. Les modules sont des assemblys système DQS qui implémentent différentes fonctions au sein d'une fonctionnalité dans DQS. Par exemple, l'activité de gestion de l'arborescence du domaine contient diverses fonctions telles que la définition des règles de domaine, la définition des conditions de règle, la définition des règles entre domaines pour les domaines composites, et ainsi de suite.  
  
 Dans certains cas, le niveau de granularité au niveau de l'activité n'est pas suffisant. Vous pouvez analyser un problème qui se produit dans un module particulier au sein d'une activité. Il est utile de disposer d'une option pour configurer les niveaux de gravité de journal au niveau du module pour isoler et suivre le problème plus précisément.  
  
 Le paramètre de gravité du journal spécifié au niveau de l'activité détermine le paramètre de gravité du journal de tous les modules qui constituent l'activité. Toutefois, en cas de conflit entre les paramètres de gravité du journal aux niveaux de l'activité et du module, les paramètres de gravité au niveau du module sont pris en compte.  
  
> [!NOTE]
>  -   Par défaut, le module **Microsoft.Ssdqs.Core.Startup** est préconfiguré dans la section **Avancé** avec le niveau de gravité **Informations**. Cela permet d'activer l'enregistrement des événements de gravités Informations et supérieures (Avertir, Erreur et Irrécupérable) relatifs au démarrage et à l'arrêt des services DQS.  
> -   Vous devez configurer des niveaux de gravité de journal au niveau du module uniquement si vous êtes un utilisateur expérimenté de DQS et familiarisé avec des assemblys système DQS.  
  
 Pour configurer les niveaux de gravité de journal au niveau du module :  
  
1.  Sous l'onglet **Paramètres de journal** , cliquez sur la flèche bas dans **Avancé** pour afficher la zone.  
  
2.  Dans la grille qui s'affiche, sélectionnez un nom de module dans la liste déroulante de la colonne **Module** .  
  
3.  Sélectionnez ensuite un niveau de gravité pour le module dans la liste déroulante de la colonne **Gravité** . Vous pouvez sélectionner une valeur parmi les suivantes : **Irrécupérable**, **Erreur**, **Avertir**, **Informations**et **Déboguer**.  
  
     Par exemple, dans l'activité de gestion de l'arborescence du domaine, vous pouvez définir un niveau de granularité différent pour la fonction de définition de règle de domaine de l'activité de gestion de l'arborescence du domaine en sélectionnant le module **Microsoft.Ssdqs.DomainRules.Define** , puis en sélectionnant un niveau de gravité de journal différent. De même, vous pouvez définir un niveau de granularité différent pour la fonction de règle entre domaines en sélectionnant le module **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** , puis en sélectionnant un niveau de gravité de journal différent.  
  
4.  Répétez les étapes 2 et 3 pour d'autres modules, si nécessaire. Vous pouvez également ajouter ou supprimer des lignes dans la grille en cliquant sur les icônes **Ajouter un module** et **Supprimer le module** .  
  
5.  Cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les paramètres avancés pour les fichiers journaux DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
