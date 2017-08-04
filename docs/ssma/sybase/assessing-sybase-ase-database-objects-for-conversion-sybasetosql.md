---
title: "Évaluation des objets de base de données Sybase ASE pour la Conversion (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9683542427256511b961ad8f6ffd74af43eb23d5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="assessing-sybase-ase-database-objects-for-conversion-sybasetosql"></a>Évaluation des objets de Sybase ASE de base de données pour la Conversion (SybaseToSQL)
Avant de charger des objets et de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure, vous devez déterminer combien de temps et de complexité la migration sera prend la migration. SSMA peut créer un rapport d’évaluation qui affiche le pourcentage des objets et des procédures qui seront converties correctement en [!INCLUDE[tsql](../../includes/tsql_md.md)]. SSMA permet également d’afficher les problèmes spécifiques qui entraînent des échecs de conversion.  
  
## <a name="creating-assessment-reports"></a>Création de rapports d’évaluation  
Lorsqu’il crée ce rapport d’évaluation, SSMA convertit les objets de base de données Sybase Adaptive Server Enterprise (ASE) sélectionnés vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou syntaxe de SQL Azure, puis affiche les résultats.  
  
**Pour créer un rapport d’évaluation**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez les bases de données que vous souhaitez évaluer.  
  
2.  Pour omettre des objets individuels, désactivez les cases à cocher en regard des objets que vous ne souhaitez pas évaluer.  
  
3.  Avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**.  
  
    Vous pouvez également analyser les objets individuels en cliquant sur un objet, puis en sélectionnant **créer un rapport**.  
  
    SSMA affiche la progression dans la barre d’état en bas de la fenêtre. Si le volet de résultats est visible, vous verrez également les messages dans le volet de sortie.  
  
    Une fois l’évaluation terminée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant pour Sybase : état de l’évaluation de la fenêtre s’affiche.  
  
## <a name="using-assessment-reports"></a>À l’aide de rapports d’évaluation  
La fenêtre de rapport d’évaluation contient trois volets :  
  
-   Le volet gauche contient la hiérarchie des objets qui sont inclus dans le rapport d’évaluation. Vous pouvez parcourir la hiérarchie et sélectionner des objets et des catégories d’objets à afficher les statistiques de conversion et le code.  
  
-   Le contenu du volet droit dépend de l’élément sélectionné dans le volet gauche.  
  
    Si un groupe d’objets est activée, un tel schéma ou une table est sélectionnée du volet droit contient un volet Statistiques de Conversion et d’un objet par le volet des catégories. Le volet des statistiques de Conversion affiche les statistiques de conversion pour les objets sélectionnés. Les objets par le volet des catégories affiche les statistiques de conversion pour l’objet ou les catégories d’objets.  
  
    Si une procédure stockée, une vue ou un déclencheur est sélectionnée, le volet de droite contient des statistiques, de code source et de code cible.  
  
    -   La zone supérieure affiche les statistiques globales pour l’objet. Vous devrez peut-être développer **statistiques** pour afficher ces informations.  
  
    -   La zone Source montre le code source de l’objet sélectionné dans le volet gauche. Les zones en surbrillance affichent le code source problématique.  
  
    -   La zone cible affiche le code converti. Texte rouge affiche des messages d’erreur et le code problématiques.  
  
-   Le volet inférieur affiche les messages de la conversion, regroupés par numéro de message. Vous pouvez cliquer sur **erreurs**, **avertissements**, ou **Info** à afficher les catégories de messages, puis développez un groupe de messages. Cliquez sur un message individuel, sélectionnez l’objet dans le volet gauche et afficher les détails dans le volet droit.  
  
## <a name="analyzing-conversion-problems-using-the-assessment-report"></a>Analyse des problèmes de Conversion à l’aide de l’état d’évaluation  
Les volets des statistiques de Conversion affichent les statistiques de conversion. Si le pourcentage pour n’importe quelle catégorie est inférieure à 100 %, vous devez déterminer la raison pour laquelle la conversion n’a pas réussi.  
  
**Pour afficher les problèmes de conversion**  
  
1.  Créer le rapport d’évaluation en utilisant les instructions dans la procédure précédente.  
  
2.  Dans le volet gauche, développez les schémas ou des dossiers qui ont une icône d’erreur rouge. Continuez à développer les éléments jusqu'à ce que vous sélectionnez un élément individuel qui Échec de la conversion.  
  
3.  En haut du volet Source, cliquez sur **problème suivant**.  
  
    Le code problématique est mis en surbrillance, comme le code connexe dans le volet de Navigation de la cible.  
  
4.  Passez en revue les messages d’erreur, puis déterminez ce que vous voulez faire avec l’objet qui a provoqué le problème de conversion :  
  
    -   Mettre à jour la syntaxe ASE dans SSMA. Vous pouvez mettre à jour la syntaxe uniquement pour les procédures stockées et les déclencheurs. Pour mettre à jour la syntaxe, sélectionnez l’objet dans le volet Explorateur de métadonnées Sybase, cliquez sur le **SQL** onglet, puis modifier le code SQL. Lorsque vous quittez l’élément, vous devrez enregistrer la syntaxe de la mise à jour. Vous pouvez afficher les erreurs signalées pour l’objet sur le **rapport** onglet.  
  
    -   Dans ASE, vous pouvez modifier l’objet ASE pour supprimer ou modifier tout code problématique. Pour charger le code mis à jour dans SSMA, vous devez mettre à jour les métadonnées. Pour plus d’informations, consultez [la connexion à Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou l’Explorateur de métadonnées SQL Azure et l’Explorateur de métadonnées Sybase, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ou SQL Azure et migrer les données à partir de ASE.  
  
## <a name="next-step"></a>Étape suivante  
[Conversion des objets de Sybase ASE de base de données &#40; SybaseToSQL &#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration Sybase ASE bases de données SQL Server : base de données SQL Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

