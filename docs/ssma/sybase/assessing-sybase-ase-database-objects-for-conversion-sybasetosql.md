---
title: Évaluation des objets de base de données SAP ASE pour la Conversion (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: eb996b7c-1eef-4f73-b5e6-2fa6faf7336c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e7d1b0b68835fe8b909369a87814a3d1c41e07d1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841057"
---
# <a name="assessing-sap-ase-database-objects-for-conversion-sybasetosql"></a>Évaluation des objets de base de données SAP ASE pour la conversion (SybaseToSQL)
Avant de charger des objets et de migrer des données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure, vous devez déterminer comment la complexité de la migration et combien de temps il vous faudra. SSMA peut créer un rapport d’évaluation qui affiche le pourcentage des objets et des procédures qui seront correctement converties en [!INCLUDE[tsql](../../includes/tsql-md.md)]. SSMA vous permet également d’afficher les problèmes spécifiques qui peuvent entraîner des échecs de conversion.  
  
## <a name="create-assessment-reports"></a>Créer des rapports d’évaluation  
Lors de la création de ce rapport d’évaluation, SSMA convertit les objets de base de données SAP Adaptive Server Enterprise (ASE) sélectionnés vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou syntaxe SQL d’Azure, puis affiche les résultats.  
  
**Pour créer un rapport d’évaluation**  
  
1.  Dans l’Explorateur de métadonnées de Sybase, sélectionnez les bases de données que vous souhaitez évaluer.  
  
2.  Pour omettre des objets individuels, désactivez les cases à cocher en regard des objets que vous ne souhaitez pas évaluer.  
  
3.  Avec le bouton droit **bases de données**, puis sélectionnez **créer un rapport**.  
  
    Vous pouvez également analyser les objets individuels en double-cliquant sur un objet, puis en sélectionnant **créer un rapport**.  
  
    SSMA affiche la progression dans la barre d’état en bas de la fenêtre. Si le volet de sortie est visible, vous verrez également les messages connexes.  
  
    Une fois l’évaluation terminée, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant pour Sybase : fenêtre de rapport d’évaluation s’affiche.  
  
## <a name="use-assessment-reports"></a>Utiliser des rapports d’évaluation  
La fenêtre de rapport d’évaluation contient trois volets :  
  
-   Le volet gauche contient la hiérarchie des objets qui sont inclus dans le rapport d’évaluation. Vous pouvez parcourir la hiérarchie et sélectionner des objets et des catégories d’objet pour afficher le code et les statistiques de conversion.  
  
-   Le contenu du volet droit varie en fonction de l’élément est sélectionné dans le volet gauche.  
  
    Si un groupe d’objets (par exemple, un schéma) ou d’une table est sélectionné, le volet droit affiche deux volets. Le **des statistiques de Conversion** volet affiche les statistiques de conversion pour les objets sélectionnés. Le **les objets par catégories** volet affiche les statistiques de conversion pour l’objet ou les catégories d’objets.  
  
    Si une procédure stockée, une vue ou un déclencheur est sélectionnée, le volet de droite contient des statistiques, de code source et de code cible.  
  
    -   La zone supérieure affiche les statistiques globales pour l’objet. Vous devrez peut-être développer **statistiques** pour afficher ces informations. 
    -   La zone Source montre le code source de l’objet qui est sélectionné dans le volet gauche. Les zones en surbrillance affichent le code source problématiques.  
    -   La zone cible montre le code converti. Texte rouge indique les messages d’erreur et de code problématiques.  
  
-   Le volet inférieur affiche les messages de la conversion, regroupés par numéro de message. Sélectionnez **erreurs**, **avertissements**, ou **Info** pour afficher les catégories de messages, puis développez un groupe de messages. Cliquez sur un message individuel pour sélectionner l’objet dans le volet gauche puis affichez les détails dans le volet droit.  
  
## <a name="analyze-conversion-problems-by-using-the-assessment-report"></a>Analyser les problèmes de conversion à l’aide du rapport d’évaluation  
Le **volets de statistiques de Conversion** affichent les statistiques de conversion. Si le pourcentage pour n’importe quelle catégorie est inférieure à 100 %, vous devez déterminer pourquoi la conversion n’a pas réussie.  
  
**Pour afficher les problèmes de conversion**  
  
1.  Créer le rapport d’évaluation en suivant les instructions dans la procédure précédente.  
  
2.  Dans le volet gauche, développez les schémas ou des dossiers qui ont une icône d’erreur rouge. Continuez à développer les éléments jusqu'à ce que vous sélectionnez un élément individuel qui Échec de la conversion.  
  
3.  En haut du volet Source, sélectionnez **problème suivant**.  
    Le code problématique est mis en surbrillance, voici le code connexe dans le **cible Navigation** volet.  
  
4.  Passez en revue les messages d’erreur et déterminer ce que vous voulez faire avec l’objet qui a provoqué le problème de conversion :  
  
    -   Mettre à jour de la syntaxe de l’ASE dans SSMA. Vous pouvez mettre à jour la syntaxe uniquement pour les procédures stockées et déclencheurs. Pour mettre à jour la syntaxe, sélectionnez l’objet dans le volet Explorateur de métadonnées de Sybase, cliquez sur le **SQL** onglet et modifiez le code SQL. Lorsque vous quittez l’élément, vous êtes invité à enregistrer la syntaxe de la mise à jour. Afficher les erreurs signalées pour l’objet sur le **rapport** onglet.  
  
    -   Dans l’environnement ASE, vous pouvez modifier l’objet de l’ASE pour supprimer ou de réviser le code problématique. Pour charger le code mis à jour dans SSMA, vous devrez mettre à jour les métadonnées. Pour plus d’informations, consultez [connexion à Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md).  
  
    -   Vous pouvez exclure l’objet de la migration. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou de l’Explorateur de métadonnées SQL Azure et l’Explorateur de métadonnées de Sybase, désactivez la case à cocher en regard de l’élément avant de charger les objets vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou SQL Azure et migrer des données à partir de l’ASE.
  
## <a name="next-steps"></a>Étapes suivantes  
[Convertir des objets de base de données ASE SAP &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Voir aussi  
[Migration SAP ASE bases de données SQL Server - Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
