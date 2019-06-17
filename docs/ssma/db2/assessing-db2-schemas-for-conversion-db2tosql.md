---
title: Évaluation des schémas DB2 pour la Conversion (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8892f5a4-72ba-4406-8649-7a9d67f4c1d9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fe66ff5b8902a737ff9a2ac0815069a4f01ea129
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63453424"
---
# <a name="assessing-db2-schemas-for-conversion-db2tosql"></a>Évaluation des schémas DB2 pour la Conversion (DB2ToSQL)
Avant de charger des objets et de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez déterminer comment complexe sera la migration et combien de temps l’opération prendra. SSMA peut créer un rapport d’évaluation qui affiche le pourcentage d’objets qui seront converties correctement. SSMA vous permet également d’afficher les problèmes spécifiques qui provoquent des échecs de conversion.  
  
## <a name="creating-assessment-reports"></a>Création de rapports d’évaluation  
Lorsqu’il crée ce rapport d’évaluation, SSMA convertit les objets de base de données DB2 sélectionnés vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] syntaxe, puis affiche les résultats.  
  
**Pour créer un rapport d’évaluation**  
  
1.  Dans l’Explorateur de métadonnées de DB2, sélectionnez les schémas à évaluer.  
  
2.  Pour omettre des objets individuels, désactivez les cases à cocher en regard de ceux.  
  
3.  Avec le bouton droit **schémas**, puis sélectionnez **créer un rapport**.  
  
    Vous pouvez également analyser les objets individuels en double-cliquant sur un objet, puis en sélectionnant **créer un rapport**.  
  
    SSMA affiche la progression dans la barre d’état en bas de la fenêtre. Si le volet de sortie est visible, vous verrez également des messages dans le volet de sortie.  
  
    Une fois l’évaluation terminée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Assistant de Migration pour DB2 : Fenêtre de rapport d’évaluation s’affiche.  
  
## <a name="using-assessment-reports"></a>À l’aide de rapports d’évaluation  
La fenêtre de rapport d’évaluation contient trois volets :  
  
-   Le volet gauche contient la hiérarchie des objets qui sont inclus dans le rapport d’évaluation. Vous pouvez parcourir la hiérarchie et sélectionner les objets et les catégories d’objets à afficher le code et les statistiques de conversion.  
  
-   Le contenu du volet droit dépend de l’élément est sélectionné dans le volet gauche.  
  
    Si un groupe d’objets est sélectionné, un tel schéma, ou si une table est sélectionnée, le volet droit contient un volet de statistiques de Conversion et les objets un par volet des catégories. Le volet de statistiques de Conversion affiche les statistiques de conversion pour les objets sélectionnés. Les objets par le volet des catégories affiche les statistiques de conversion pour l’objet ou les catégories d’objets.  
  
    Si une fonction, package, procédure, séquence ou une vue est sélectionnée, le volet de droite contient des statistiques, de code source et de code cible.  
  
    -   La zone supérieure affiche les statistiques globales pour l’objet. Vous devrez peut-être développer **statistiques** pour afficher ces informations.  
  
    -   La zone Source montre le code source de l’objet qui est sélectionné dans le volet gauche. Les zones en surbrillance affichent le code source problématiques.  
  
    -   La zone cible montre le code converti. Texte rouge indique les messages d’erreur et de code problématiques.  
  
-   Le volet inférieur affiche les messages de la conversion, regroupés par numéro de message. Vous pouvez cliquer sur **erreurs**, **avertissements**, ou **Info** pour afficher les catégories de messages, puis développez un groupe de messages. Cliquez sur un message individuel pour sélectionner l’objet dans le volet gauche et afficher les détails dans le volet droit.  
  
## <a name="analyzing-conversion-problems-by-using-the-assessment-report"></a>Analyse des problèmes de Conversion à l’aide du rapport d’évaluation  
Le volet de statistiques de Conversion affiche les statistiques de conversion. Si le pourcentage pour n’importe quelle catégorie est inférieure à 100 %, vous devez déterminer pourquoi la conversion n’a pas réussie.  
  
**Pour afficher les problèmes de conversion**  
  
1.  Créer le rapport d’évaluation en suivant les instructions dans la procédure précédente.  
  
2.  Dans le volet gauche, développez les schémas ou des dossiers qui ont une icône d’erreur rouge. Continuez à développer les éléments jusqu'à ce que vous sélectionnez un élément individuel qui Échec de la conversion.  
  
3.  En haut du volet Source, cliquez sur **problème suivant**.  
  
    Le code problématique est mis en surbrillance, voici le code connexe dans le volet de Navigation de la cible.  
  
4.  Passez en revue les messages d’erreur et déterminer ce que vous voulez faire avec l’objet qui a provoqué le problème de conversion :  
  
    -   Mettre à jour de la syntaxe de DB2 dans SSMA. Vous pouvez mettre à jour la syntaxe pour les procédures, fonctions, déclencheurs, fonctions empaquetées et empaquetée. Pour mettre à jour la syntaxe, sélectionnez l’objet dans le volet Explorateur de métadonnées de DB2, cliquez sur le **SQL** onglet et modifiez le code SQL. Lorsque vous quittez l’élément, vous devrez enregistrer la syntaxe de la mise à jour. Vous pouvez afficher les erreurs signalées pour l’objet sur le **rapport** onglet.  
  
    -   Dans DB2, vous pouvez modifier l’objet de DB2 pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devrez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à la base de données DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md).  
  
    -   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Explorateur de métadonnées et l’Explorateur de métadonnées de DB2, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et migrer des données à partir de DB2.  
  
## <a name="next-step"></a>Étape suivante  
[Conversion de schémas DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration de DB2 vers SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
