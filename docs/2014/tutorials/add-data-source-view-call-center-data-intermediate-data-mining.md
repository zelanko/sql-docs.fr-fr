---
title: Ajout d’une vue de source de données pour les données de centre d’appels (didacticiel sur l’exploration de données intermédiaire) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 04f930c42b0e41a9f10b35d10295a38e8dac7490
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68888687"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données pour les données de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de cette tâche, vous allez ajouter une vue de source de données qui sera utilisée pour accéder aux données d'un centre d'appels. Les mêmes données seront utilisées pour générer aussi bien le modèle de réseau neuronal initial destiné à l'exploration que le modèle de régression logistique que vous utiliserez pour faire des recommandations.  
  
 Vous utiliserez également le concepteur de vue de source de données pour ajouter une colonne pour le jour de la semaine. En effet, bien que les données sources suivent les données de centre d'appels par date, votre expérience indique qu'il existe des modèles récurrents à la fois en termes de volume d'appel et de qualité de service, selon que le jour est un week-end ou un jour de semaine.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **vues de source de données**, puis sélectionnez **nouvelle vue de source de données**.  
  
     L'Assistant Vue de source de données s'ouvre.  
  
2.  Sur la page **Bienvenue dans l'Assistant Sources de données**, cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner une source de données** , sous **sources de données relationnelles**, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] sélectionnez la source de données. Si vous ne disposez pas de cette source de données, consultez le didacticiel sur l' [exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md). Cliquez sur **Suivant**.  
  
4.  Dans la page **Sélectionner des tables et des vues** , sélectionnez le tableau suivant, puis cliquez sur la flèche droite pour l’ajouter à la vue de source de données :  
  
    -   **FactCallCenter (dbo)**  
  
    -   **DimDate**  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **fin de l’Assistant** , la vue de source de données est [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]nommée par défaut. Remplacez le nom par **callcenter**, puis cliquez sur **Terminer**.  
  
     Le concepteur de vue de source de données s’ouvre pour afficher la vue de source de données **callcenter** .  
  
7.  Cliquez avec le bouton droit dans le volet vue de source de données, puis sélectionnez **Ajouter/supprimer des tables**. Sélectionnez la table **DimDate** , puis cliquez sur **OK**.  
  
     Une relation doit être automatiquement ajoutée entre les `DateKey` colonnes de chaque table. Vous allez utiliser cette relation pour récupérer la colonne **EnglishDayNameOfWeek**de la table **DimDate** et l’utiliser dans votre modèle.  
  
8.  Dans le concepteur de vue de source de données, cliquez avec le bouton droit sur la table **FactCallCenter**, puis sélectionnez **nouveau calcul nommé**.  
  
     Dans la boîte de dialogue **créer un calcul nommé** , tapez les valeurs suivantes :  
  
    |||  
    |-|-|  
    |**Nom de la colonne**|DayOfWeek|  
    |**Description**|Obtenir le jour de la semaine depuis la table DimDate|  
    |**Expression**|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     Pour vérifier que l’expression crée les données dont vous avez besoin, cliquez avec le bouton droit sur la table **FactCallCenter**, puis sélectionnez **Explorer les données**.  
  
9. Prenez une minute pour examiner les données disponibles afin de pouvoir comprendre comment elles sont utilisées dans l'exploration de données :  
  
|Nom de la colonne|Contient|  
|-----------------|--------------|  
|FactCallCenterID|Clé arbitraire créée lorsque les données ont été importées vers l'entrepôt de données.<br /><br /> Cette colonne identifie les enregistrements uniques et doit être utilisée comme clé de cas du modèle d'exploration de données.|  
|DateKey|Date de fonctionnement du centre d'appels, sous la forme d'un entier. Les clés de date entières sont souvent utilisées dans les entrepôts de données, mais vous souhaitez peut-être obtenir la date au format date/heure si vous vouliez fonctionner par groupements de valeurs de date.<br /><br /> Notez que les dates ne sont pas uniques car le fournisseur fournit un rapport distinct pour chaque équipe et pour chaque jour de fonctionnement.|  
|WageType|Indique si le jour était un jour de semaine, de week-end ou un jour férié.<br /><br /> Il est possible qu’il existe une différence de qualité du service client sur les week-ends et les jours de la semaine. vous utiliserez donc cette colonne comme entrée.|  
|Shift|Indique l'équipe pour laquelle les appels sont enregistrés. Ce centre d'appels divise la journée de travail en quatre équipes : AM, PM1, PM2 et Midnight.<br /><br /> Il est possible que les horaires des équipes influencent la qualité du service client. Vous utiliserez donc cela comme entrée.|  
|LevelOneOperators|Indique le nombre d’opérateurs de niveau 1 sur le droit.<br /><br /> Les employés de centre d'appels débutent au niveau 1. Ces employés ont donc moins d'expérience.|  
|LevelTwoOperators|Indique le nombre d'opérateurs de niveau 2 qui sont en service.<br /><br /> Un employé doit consigner un certain nombre d’heures de service pour qualifier comme opérateur de niveau 2.|  
|TotalOperators|Nombre total d'opérateurs présents pendant le temps de travail de l'équipe.|  
|Calls|Nombre d'appels reçus pendant la période de travail de l'équipe.|  
|AutomaticResponses|Nombre d'appels qui ont été totalement gérés par traitement automatisé des appels (réponse vocale interactive).|  
|Commandes|Nombre de commandes qui ont fait suite à des appels.|  
|IssuesRaised|Nombre de problèmes, générés par des appels, qui requièrent un suivi.|  
|AverageTimePerIssue|Durée moyenne requise pour répondre à un appel entrant.|  
|ServiceGrade|Métrique qui indique la qualité de service générale, mesurée comme le *taux d’abandon* pour l’ensemble de l’équipe. Plus le taux d'abandon est élevé, plus la probabilité que les clients soient mécontents et que des commandes potentielles soient perdues est forte.|  
  
 Notez que les données incluent quatre colonnes différentes qui sont basées sur une colonne de date unique `WageType`: ****, DayOfWeek `Shift`, et `DateKey`. D'ordinaire, dans l'exploration de données il n'est pas judicieux d'utiliser plusieurs colonnes dérivées des mêmes données, car les valeurs se mettent trop lourdement en corrélation entre elles et peuvent masquer d'autres modèles.  
  
 Toutefois, nous n’utiliserons `DateKey` pas dans le modèle, car il contient trop de valeurs uniques. Il n’existe aucune relation directe `Shift` entre et **DayOfWeek**, `WageType` et la **DayOfWeek** ne sont que partiellement liées. Si vous vous inquiétiez de la collinéarité, vous pouvez créer la structure à l'aide de toutes les colonnes disponibles, puis ignorer d'autres colonnes dans chaque modèle et tester l'effet.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une structure et d’un modèle de réseau neuronal &#40;didacticiel sur l’exploration de données intermédiaire&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
