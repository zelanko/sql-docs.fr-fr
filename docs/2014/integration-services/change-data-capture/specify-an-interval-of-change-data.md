---
title: Spécifier un intervalle de données modifiées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 80126a2f1955356ae451e2f1092869e962674689
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84922470"
---
# <a name="specify-an-interval-of-change-data"></a>Spécifier un intervalle de données modifiées
  Dans le flux de contrôle d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui effectue un charge incrémentielle de données modifiées, la première tâche consiste à calculer les points de terminaison de l’intervalle de modification. Ces points de terminaison sont des valeurs `datetime` qui seront stockées dans des variables de package pour une utilisation ultérieure dans le package.  
  
> [!NOTE]  
>  Pour obtenir une description du processus d’ensemble de la conception du flux de contrôle, consultez [Capture de données modifiées &#40;SSIS&#41;](change-data-capture-ssis.md).  
  
## <a name="set-up-package-variables-for-the-endpoints"></a>Configurer des variables de package pour les points de terminaison  
 Avant de configurer la tâche d'exécution SQL pour calculer les points de terminaison, vous devez définir les variables de package qui stockeront les points de terminaison.  
  
#### <a name="to-set-up-package-variables"></a>Pour configurer des variables de package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez un nouveau projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Dans la fenêtre **Variables** , créez les variables suivantes :  
  
    1.  Créez une variable du type de données `datetime` pour contenir le point de départ de l'intervalle.  
  
         Cet exemple utilise le nom de variable ExtractStartTime.  
  
    2.  Créez une autre variable du type de données `datetime` pour contenir le point de fin pour l'intervalle.  
  
         Cet exemple utilise le nom de variable ExtractEndTime.  
  
 Si vous calculez les points de terminaison dans un package principal qui exécute plusieurs packages enfants, vous pouvez utiliser des configurations Variable de package parent pour passer les valeurs de ces variables à chaque package enfant. Pour plus d’informations, consultez [Tâche d’exécution de package](../control-flow/execute-package-task.md) et [Utiliser les valeurs des variables et des paramètres dans un package enfant](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a>Calculer un point de départ et un point de fin pour les données modifiées  
 Après avoir configuré les variables de package pour les points de terminaison d'intervalle, vous pouvez calculer les valeurs réelles pour ces points de terminaison et mapper ces valeurs aux variables de package correspondantes. Ces points de terminaison étant des valeurs `datetime`, vous devez utiliser des fonctions capables de calculer ou d'exploiter des valeurs `datetime`. Le langage d'expression [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et Transact-SQL possèdent des fonctions qui prennent en charge les valeurs `datetime` :  
  
 Fonctions en langage d'expression [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui prennent en charge les valeurs `datetime`  
 -   [DATEADD &#40;expression SSIS&#41;](../expressions/dateadd-ssis-expression.md)  
  
-   [DATEDIFF &#40;expression SSIS&#41;](../expressions/datediff-ssis-expression.md)  
  
-   [DATEPART &#40;expression SSIS&#41;](../expressions/datepart-ssis-expression.md)  
  
-   [DAY &#40;expression SSIS&#41;](../expressions/day-ssis-expression.md)  
  
-   [GETDATE &#40;expression SSIS&#41;](../expressions/getdate-ssis-expression.md)  
  
-   [GETUTCDATE &#40;expression SSIS&#41;](../expressions/getutcdate-ssis-expression.md)  
  
-   [MONTH &#40;expression SSIS&#41;](../expressions/month-ssis-expression.md)  
  
-   [YEAR &#40;expression SSIS&#41;](../expressions/year-ssis-expression.md)  
  
 Fonctions en Transact-SQL qui prennent en charge les valeurs `datetime`  
 [Types de données et fonctions de date et d’heure &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).  
  
 Avant d'utiliser l'une de ces fonctions `datetime` pour calculer les points de terminaison, vous devez déterminer si l'intervalle est fixe et s'il a lieu selon une planification régulière. En général, vous appliquez les modifications qui se sont produites dans les tables sources aux tables de destination selon une planification régulière. Par exemple, vous pouvez appliquer ces modifications toutes les heures, tous les jours ou toutes les semaines.  
  
 Après avoir déterminé si votre intervalle de modification est fixe ou plus aléatoire, vous pouvez calculer les points de terminaison :  
  
-   **Calcul de la date et de l’heure de début**. Vous utilisez la date et l'heure de fin du chargement précédent comme date et heure de début actuelles. Si vous utilisez un intervalle fixe pour les chargements incrémentiels, vous pouvez calculer cette valeur en utilisant les fonctions `datetime` de Transact-SQL ou du langage d'expression [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Autrement, vous devrez peut-être rendre les points de terminaison persistants entre les exécutions et utilisez une tâche d'exécution SQL ou une tâche de script pour charger le point de terminaison précédent.  
  
-   **Calcul de la date et de l’heure de fin**. Si vous utilisez un intervalle fixe pour les chargements incrémentiels, calculez la date et l'heure de fin actuelles sur la base d'un décalage par rapport à la date et à l'heure de début. Là encore, vous pouvez calculer cette valeur à l’aide `datetime` des fonctions de Transact-SQL ou du [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] langage d’expression.  
  
 Dans la procédure suivante, l'intervalle de modification utilise un intervalle fixe et suppose que le package de chargement incrémentiel est exécuté tous les jours sans exception. Sinon, les données modifiées pour les intervalles ratés seraient perdues. Le point de départ pour l'intervalle est avant-hier à minuit, soit une période écoulée comprise entre 24 à 48 heures. Le point de fin pour l'intervalle est hier à minuit (la nuit précédente), soit une période écoulée comprise entre 0 et 24 heures.  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a>Pour calculer le point de départ et le point de fin pour l'intervalle de capture  
  
1.  Sous l’onglet **Flux de contrôle** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , ajoutez une tâche d’exécution SQL au package.  
  
2.  Ouvrez **l’Éditeur de tâche d’exécution de requêtes SQL**, puis dans la page **Général** de l’éditeur, sélectionnez les options suivantes :  
  
    1.  Pour **ResultSet**, sélectionnez **Ligne unique**.  
  
    2.  Configurez une connexion valide à la base de données source.  
  
    3.  Pour **SQLSourceType**, sélectionnez **Entrée directe**.  
  
    4.  Pour **SQLStatement**, entrez l’instruction SQL suivante :  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  Dans la page **Ensemble de résultats** de **Éditeur de tâche d’exécution de requêtes SQL**, mappez le résultat d’ExtractStartTime à la variable de package ExtractStartTime, et le résultat d’ExtractEndTime à la variable de package ExtractEndTime.  
  
    > [!NOTE]  
    >  Quand vous utilisez une expression pour définir la valeur d’une variable [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , l’expression est évaluée chaque fois que la valeur de la variable fait l’objet d’un accès.  
  
## <a name="next-step"></a>étape suivante  
 Une fois que vous avez calculé le point de départ et le point de fin pour une plage de modifications, l'étape suivante consiste à déterminer si les données modifiées sont prêtes.  
  
 **Rubrique suivante :** [Déterminer si les données modifiées sont prêtes](determine-whether-the-change-data-is-ready.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des variables dans des packages](../use-variables-in-packages.md)   
 [Expressions Integration Services &#40;SSIS&#41;](../expressions/integration-services-ssis-expressions.md)   
 [Exécution de requêtes SQL, tâche](../control-flow/execute-sql-task.md)   
 [Tâche de script](../control-flow/script-task.md)  
  
  
