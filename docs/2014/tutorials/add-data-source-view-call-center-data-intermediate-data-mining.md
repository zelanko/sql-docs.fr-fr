---
title: Ajout de données vue de Source pour les données de centre d’appels (didacticiel sur l’exploration des données intermédiaires) | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 128ff8a4cbd1bafcf9c15c32f5cd7c5e127710d9
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312327"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a>Ajout d'une vue de source de données pour les données de centre d'appels (Didacticiel sur l'exploration de données intermédiaire)
  Au cours de cette tâche, vous allez ajouter une vue de source de données qui sera utilisée pour accéder aux données d'un centre d'appels. Les mêmes données seront utilisées pour générer aussi bien le modèle de réseau neuronal initial destiné à l'exploration que le modèle de régression logistique que vous utiliserez pour faire des recommandations.  
  
 Vous utiliserez également le concepteur de vue de source de données pour ajouter une colonne pour le jour de la semaine. En effet, bien que les données sources suivent les données de centre d'appels par date, votre expérience indique qu'il existe des modèles récurrents à la fois en termes de volume d'appel et de qualité de service, selon que le jour est un week-end ou un jour de semaine.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-add-a-data-source-view"></a>Pour ajouter une vue de source de données  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit **vues de sources de données**, puis sélectionnez **nouvelle vue de Source de données**.  
  
     L'Assistant Vue de source de données s'ouvre.  
  
2.  Dans la page **Assistant Vue de source de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner une Source de données** sous **sources de données relationnelles**, sélectionnez le [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] source de données. Si vous n’avez pas de cette source de données, consultez [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md). Cliquez sur **Suivant**.  
  
4.  Sur le **sélectionner des Tables et vues** page et sélectionnez la table suivante, puis cliquez sur la flèche droite pour l’ajouter à la vue de source de données :  
  
    -   **FactCallCenter (dbo)**  
  
    -   **DimDate**  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **fin de l’Assistant** page, la vue de source de données est nommée par défaut [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Remplacez le nom par **CallCenter**, puis cliquez sur **Terminer**.  
  
     Concepteur de vue de Source de données s’ouvre et affiche le **CallCenter** vue de source de données.  
  
7.  Avec le bouton droit dans le volet de la vue de Source de données, puis sélectionnez **ajouter/supprimer des Tables**. Sélectionnez la table, **DimDate** et cliquez sur **OK**.  
  
     Une relation doit être ajoutée automatiquement entre le `DateKey` colonnes dans chaque table. Vous utiliserez cette relation pour obtenir la colonne, **EnglishDayNameOfWeek**, à partir de la **DimDate** de table et l’utiliser dans votre modèle.  
  
8.  Dans le Concepteur de vue de Source de données, cliquez sur la table, **FactCallCenter**, puis sélectionnez **nouveau calcul nommé**.  
  
     Dans le **créer un calcul nommé** boîte de dialogue, tapez les valeurs suivantes :  
  
    |||  
    |-|-|  
    |**Nom de colonne**|DayOfWeek|  
    |**Description**|Obtenir le jour de la semaine depuis la table DimDate|  
    |**Expression**|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     Pour vérifier que l’expression crée les données vous devez, cliquez sur la table **FactCallCenter**, puis sélectionnez **Explorer les données**.  
  
9. Prenez une minute pour examiner les données disponibles afin de pouvoir comprendre comment elles sont utilisées dans l'exploration de données :  
  
|Nom de colonne|Contient|  
|-----------------|--------------|  
|FactCallCenterID|Clé arbitraire créée lorsque les données ont été importées vers l'entrepôt de données.<br /><br /> Cette colonne identifie les enregistrements uniques et doit être utilisée comme clé de cas du modèle d'exploration de données.|  
|DateKey|Date de fonctionnement du centre d'appels, sous la forme d'un entier. Les clés de date entières sont souvent utilisées dans les entrepôts de données, mais vous souhaitez peut-être obtenir la date au format date/heure si vous vouliez fonctionner par groupements de valeurs de date.<br /><br /> Notez que les dates ne sont pas uniques car le fournisseur fournit un rapport distinct pour chaque équipe et pour chaque jour de fonctionnement.|  
|WageType|Indique si le jour était un jour de semaine, de week-end ou un jour férié.<br /><br /> Il est possible que les week-ends et jours de la semaine ne soit une différence de qualité de service du client afin de vous utiliserez cette colonne en tant qu’entrée.|  
|Shift|Indique l'équipe pour laquelle les appels sont enregistrés. Ce centre d'appels divise la journée de travail en quatre équipes : AM, PM1, PM2 et Midnight.<br /><br /> Il est possible que les horaires des équipes influencent la qualité du service client. Vous utiliserez donc cela comme entrée.|  
|LevelOneOperators|Indique le nombre d’opérateurs de niveau 1 sur droit.<br /><br /> Les employés de centre d'appels débutent au niveau 1. Ces employés ont donc moins d'expérience.|  
|LevelTwoOperators|Indique le nombre d'opérateurs de niveau 2 qui sont en service.<br /><br /> Un employé doit enregistrer un certain nombre d’heures de service pour être considérée comme un opérateur de niveau 2.|  
|TotalOperators|Nombre total d'opérateurs présents pendant le temps de travail de l'équipe.|  
|Calls|Nombre d'appels reçus pendant la période de travail de l'équipe.|  
|AutomaticResponses|Nombre d'appels qui ont été totalement gérés par traitement automatisé des appels (réponse vocale interactive).|  
|Orders|Nombre de commandes qui ont fait suite à des appels.|  
|IssuesRaised|Nombre de problèmes, générés par des appels, qui requièrent un suivi.|  
|AverageTimePerIssue|Durée moyenne requise pour répondre à un appel entrant.|  
|ServiceGrade|Une mesure qui indique la qualité générale du service, mesurée sous la forme la *taux d’abandon* de l’équipe entière. Plus le taux d'abandon est élevé, plus la probabilité que les clients soient mécontents et que des commandes potentielles soient perdues est forte.|  
  
 Notez que les données contient quatre colonnes différentes qui sont basées sur une colonne de date : `WageType`, **DayOfWeek**, `Shift`, et `DateKey`. D'ordinaire, dans l'exploration de données il n'est pas judicieux d'utiliser plusieurs colonnes dérivées des mêmes données, car les valeurs se mettent trop lourdement en corrélation entre elles et peuvent masquer d'autres modèles.  
  
 Toutefois, nous utiliserons pas `DateKey` dans le modèle, car elle contient trop de valeurs uniques. Il n’existe aucune relation directe entre `Shift` et **DayOfWeek**, et `WageType` et **DayOfWeek** sont uniquement liées en partie. Si vous vous inquiétiez de la collinéarité, vous pouvez créer la structure à l'aide de toutes les colonnes disponibles, puis ignorer d'autres colonnes dans chaque modèle et tester l'effet.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Création d’une Structure de réseau neuronal et le modèle &#40;intermédiaire Didacticiel d’exploration de données&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  