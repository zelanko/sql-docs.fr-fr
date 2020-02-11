---
title: Création d’une structure de modèle d’exploration de données de publipostage ciblé (didacticiel sur l’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2bd2e9d0decc730a59b63ee600bec2d080cc85fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62856164"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Création d'une structure de modèle d'exploration de données pour le publipostage ciblé (Didacticiel sur l'exploration de données de base)
  La première étape dans la création d'un scénario de publipostage ciblé consiste à utiliser l'Assistant Exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer une structure d'exploration de données et un modèle d'exploration de données du type Arbres de décision.  
  
 Dans cette tâche, vous allez configurer une nouvelle structure d’exploration de données et ajouter un modèle d’exploration de [!INCLUDE[msCoName](../includes/msconame-md.md)] données initial basé sur l’algorithme MDT (Decision Trees). Pour créer la structure, vous allez sélectionner en premier des tables et des vues, puis vous identifierez quelles colonnes seront utilisées pour l'apprentissage et pour le test.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>Pour créer une structure d'exploration de données pour le scénario de publipostage ciblé  
  
1.  Dans Explorateur de solutions, cliquez avec le bouton droit sur **structures d’exploration** de données et sélectionnez **nouvelle structure d’exploration** de données pour démarrer l’Assistant Exploration de données.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur la page **Sélectionner la méthode de définition** , vérifiez que **à partir de la base de données relationnelle ou de l’entrepôt de données existant** est sélectionné, puis cliquez sur **suivant**.  
  
4.  Dans la page **créer la structure d’exploration de données** , sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **Microsoft Decision Trees**.  
  
    > [!NOTE]  
    >  Si vous obtenez un avertissement indiquant qu'aucun algorithme d'exploration de données n'a été trouvé, les propriétés du projet ne sont peut-être pas configurées correctement. Cet avertissement se produit lorsque le projet tente d'extraire une liste d'algorithmes d'exploration de données du serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et ne trouve pas le serveur. Par défaut, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] utilise **localhost** comme serveur. Si vous utilisez une instance différente ou une instance nommée, vous devez modifier les propriétés du projet. Pour plus d’informations, consultez [création d’un projet de Analysis Services &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Cliquez sur **Suivant**.  
  
6.  Dans la page **Sélectionner une vue de source de données** , dans le volet vues de sources de **données disponibles** , sélectionnez **Publipostage ciblé**. Vous pouvez cliquer sur **Parcourir** pour afficher les tables dans la vue de source de données, puis cliquer sur **Fermer** pour revenir à l’Assistant.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Dans la page **spécifier les types des tables** , activez la case à cocher dans la colonne **cas** pour que vTargetMail l’utilise comme table de cas, puis cliquez sur **suivant**. Vous utiliserez ultérieurement la table ProspectiveBuyer à des fins de test ; ignorez-la pour le moment.  
  
9. Dans la page **spécifier les données d’apprentissage** , vous allez identifier au moins une colonne prévisible, une colonne clé et une colonne d’entrée pour votre modèle. Activez la case à cocher dans la colonne **prévisible** de la ligne **BikeBuyer** .  
  
    > [!NOTE]  
    >  Remarquez l'avertissement en bas de la fenêtre. Vous ne pouvez pas accéder à la page suivante tant que vous n’avez pas sélectionné au moins une colonne **d’entrée** et une colonne **prévisible** .  
  
10. Cliquez sur **suggérer** pour ouvrir la boîte de dialogue **suggérer les colonnes associées** .  
  
     Le bouton **suggérer** est activé chaque fois qu’au moins un attribut prévisible a été sélectionné. La boîte de dialogue **suggérer les colonnes associées** répertorie les colonnes qui sont le plus étroitement liées à la colonne prévisible et classe les attributs en fonction de leur corrélation avec l’attribut prévisible. Les colonnes qui contiennent une corrélation significative (confiance supérieure à 95%) sont automatiquement sélectionnées pour être incluses dans le modèle.  
  
     Passez en revue les suggestions, puis cliquez sur **Annuler** toignore les suggestions.  
  
    > [!NOTE]  
    >  Si vous cliquez sur **OK**, toutes les suggestions répertoriées sont marquées comme colonnes d’entrée dans l’Assistant. Si vous acceptez uniquement certaines des suggestions, vous devez modifier les valeurs manuellement.  
  
11. Vérifiez que la case à cocher dans la colonne **clé** est sélectionnée dans la ligne **CustomerKey** .  
  
    > [!NOTE]  
    >  Si la table source de la vue de source de données indique une clé, l'Assistant Exploration de données choisit automatiquement cette colonne comme clé du modèle.  
  
12. Activez les cases à cocher dans la colonne **d’entrée** dans les lignes suivantes. Vous pouvez activer plusieurs colonnes en mettant en surbrillance une plage de cellules et en appuyant sur CTRL tout en activant une case à cocher.  
  
    -   **Vieillissement**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **Sexe**  
  
    -   **GeographyKey**  
  
    -   **HouseOwnerFlag**  
  
    -   **MaritalStatus**  
  
    -   **NumberCarsOwned**  
  
    -   **NumberChildrenAtHome**  
  
    -   **Région**  
  
    -   **TotalChildren**  
  
    -   **YearlyIncome**  
  
13. Sur la colonne d'extrême gauche de la page, activez les cases à cocher dans les lignes suivantes.  
  
    -   **AddressLine1**  
  
    -   **AddressLine2**  
  
    -   **DateFirstPurchase**  
  
    -   **EmailAddress**  
  
    -   **FirstName**  
  
    -   **LastName**  
  
     Vérifiez que ces lignes n'ont des coches que dans la colonne gauche. Ces colonnes seront ajoutées à votre structure mais ne seront pas incluses dans le modèle. Toutefois, une fois le modèle construit, elles seront disponibles pour l'extraction et le test. Pour plus d’informations sur l’extraction, consultez [requêtes d’extraction &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Cliquez sur **Suivant**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Spécification du type de données et du type de contenu &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les types de tables &#40;l’Assistant Exploration de données&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme MDT (Microsoft Decision Trees)](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
