---
title: Création d’une Structure de modèle d’exploration de données publipostage ciblé (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 112b45f2d5797d6797903661de0376bd4d316c6a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087709"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Création d'une structure de modèle d'exploration de données pour le publipostage ciblé (Didacticiel sur l'exploration de données de base)
  La première étape dans la création d'un scénario de publipostage ciblé consiste à utiliser l'Assistant Exploration de données dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer une structure d'exploration de données et un modèle d'exploration de données du type Arbres de décision.  
  
 Dans cette tâche vous configurez une nouvelle structure d’exploration de données et ajouter un modèle d’exploration de données initial basé sur le [!INCLUDE[msCoName](../includes/msconame-md.md)] algorithme d’arbres de décision. Pour créer la structure, vous allez sélectionner en premier des tables et des vues, puis vous identifierez quelles colonnes seront utilisées pour l'apprentissage et pour le test.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>Pour créer une structure d'exploration de données pour le scénario de publipostage ciblé  
  
1.  Dans l’Explorateur de solutions, cliquez sur **des Structures d’exploration de données** et sélectionnez **nouvelle Structure d’exploration de données** pour démarrer l’Assistant exploration de données.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Sur le **sélectionner la méthode de définition** page, vérifiez que **à partir de l’entrepôt de données ou de la base de données relationnelle existant** est sélectionnée, puis cliquez sur **suivant**.  
  
4.  Sur le **créer la Structure d’exploration de données** page sous **quelle technique d’exploration de données voulez-vous utiliser ?**, sélectionnez **Microsoft Decision Trees**.  
  
    > [!NOTE]  
    >  Si vous obtenez un avertissement indiquant qu'aucun algorithme d'exploration de données n'a été trouvé, les propriétés du projet ne sont peut-être pas configurées correctement. Cet avertissement se produit lorsque le projet tente d'extraire une liste d'algorithmes d'exploration de données du serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et ne trouve pas le serveur. Par défaut, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] utilisera **localhost** que le serveur. Si vous utilisez une instance différente ou une instance nommée, vous devez modifier les propriétés du projet. Pour plus d’informations, consultez [création d’un projet Analysis Services &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Cliquez sur **Suivant**.  
  
6.  Sur le **sélectionner une vue de Source de données** page, dans le **vues de sources de données disponibles** volet, sélectionnez **publipostage ciblé**. Vous pouvez cliquer sur **Parcourir** pour afficher les tables dans la vue de source de données, puis cliquez sur **fermer** pour revenir à l’Assistant.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Sur le **spécifier les Types de Table** , sélectionnez la case à cocher dans la **cas** colonne pour que vTargetMail l’utiliser comme la table de cas, puis cliquez sur **suivant**. Vous utiliserez ultérieurement la table ProspectiveBuyer à des fins de test ; ignorez-la pour le moment.  
  
9. Sur le **spécifier les données d’apprentissage** page, vous allez identifier au moins une colonne prévisible, une colonne clé et une colonne d’entrée pour votre modèle. Sélectionnez la case à cocher dans la **prédictible** colonne dans le **BikeBuyer** ligne.  
  
    > [!NOTE]  
    >  Remarquez l'avertissement en bas de la fenêtre. Vous ne serez pas en mesure d’accéder à la page suivante jusqu'à ce que vous sélectionnez au moins un **entrée** et un **prédictible** colonne.  
  
10. Cliquez sur **suggérer** pour ouvrir le **suggérer des colonnes associées** boîte de dialogue.  
  
     Le **suggérer** bouton est activé chaque fois qu’au moins un attribut prédictible a été sélectionné. Le **suggérer des colonnes associées** boîte de dialogue répertorie les colonnes qui sont plus étroitement liées à la colonne prédictible et classe les attributs en fonction de leur corrélation avec l’attribut prédictible. Les colonnes qui contiennent une corrélation significative (confiance supérieure à 95%) sont automatiquement sélectionnées pour être incluses dans le modèle.  
  
     Examinez les suggestions, puis cliquez sur **Annuler** toignore les suggestions.  
  
    > [!NOTE]  
    >  Si vous cliquez sur **OK**, mentionné toutes les suggestions seront marquées comme colonnes d’entrée dans l’Assistant. Si vous acceptez uniquement certaines des suggestions, vous devez modifier les valeurs manuellement.  
  
11. Vérifiez que la case à cocher dans la **clé** colonne est sélectionnée dans le **CustomerKey** ligne.  
  
    > [!NOTE]  
    >  Si la table source de la vue de source de données indique une clé, l'Assistant Exploration de données choisit automatiquement cette colonne comme clé du modèle.  
  
12. Sélectionnez les cases à cocher dans la **entrée** colonne dans les lignes suivantes. Vous pouvez activer plusieurs colonnes en mettant en surbrillance une plage de cellules et en appuyant sur CTRL tout en activant une case à cocher.  
  
    -   **Âge**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **Gender**  
  
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
  
    -   **firstName**  
  
    -   **lastName**  
  
     Vérifiez que ces lignes n'ont des coches que dans la colonne gauche. Ces colonnes seront ajoutées à votre structure mais ne seront pas incluses dans le modèle. Toutefois, une fois le modèle construit, elles seront disponibles pour l'extraction et le test. Pour plus d’informations sur l’extraction, consultez [requêtes d’extraction &#40;d’exploration de données&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Cliquez sur **Suivant**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Spécification du Type de données et d’un Type de contenu &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les Types de tables &#40;Assistant exploration de données&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Concepteur d’exploration de données](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Algorithme MDT (Microsoft Decision Trees)](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
