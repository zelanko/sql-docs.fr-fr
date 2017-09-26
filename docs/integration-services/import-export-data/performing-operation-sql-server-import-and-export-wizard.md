---
title: "Opération (SQL Server Assistant Importation et exportation) | Documents Microsoft"
ms.custom: 
ms.date: 01/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.impexpwizard.performingoperation.f1
ms.assetid: 83259509-71d6-4a64-a7f2-4e9603b30bd4
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 75dc26699071ee88bb0c05368b4bf36ba677c35b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="performing-operation-sql-server-import-and-export-wizard"></a>Exécution de l'opération (Assistant Importation et Exportation SQL Server)
Une fois que vous avez vérifié les choix que vous avez effectués dans l’Assistant et cliqué sur **Terminer** dans la page **Terminer l’Assistant** , l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche **Exécution de l’opération**. Cette page indique la progression et le résultat de l’opération que vous avez configurée dans les pages précédentes. Vous n’avez aucune action à effectuer dans cette page.

## <a name="screen-shot---operation-in-progress"></a>Capture d’écran : opération en cours 
 La capture d’écran suivante montre la page **Exécution de l’opération** de l’Assistant pendant que l’opération est en cours.  
  
 ![Page d’opération d’exécution de l’Assistant Importation et exportation](../../integration-services/import-export-data/media/performing-operation1.png "page opération d’exécution de l’Assistant Importation et exportation")  

## <a name="screen-shot---operation-completed"></a>Capture d’écran : opération terminée 
 La capture d’écran suivante montre la page **Exécution de l’opération** de l’Assistant une fois l’opération terminée. Cliquez sur un élément dans la colonne **Message** pour obtenir plus d’informations sur l’étape correspondante.  
  
 ![Page d’opération d’exécution de l’Assistant Importation et exportation](../../integration-services/import-export-data/media/performing-operation2.png "page opération d’exécution de l’Assistant Importation et exportation")  
  
## <a name="watch-the-progress-of-the-operation"></a>Suivre la progression de l’opération
 **Action**  
 Affiche chaque étape de l’opération.  
  
 **État**  
 Indique l’issue de chaque action (réussite ou échec).  
  
 **Message**  
 Affiche des messages d’information et d’erreur sur l’étape concernée. Cliquez sur un élément dans cette colonne pour obtenir plus d’informations sur l’étape correspondante.

## <a name="interrupt-the-operation-or-save-the-results"></a>Interrompre l’opération ou enregistrer les résultats
 **Arrêter**  
 Interrompez l’opération, si nécessaire, en cliquant sur le bouton **Arrêter** .  
  
 **Rapport**  
 Affichez un rapport de résultats, enregistrez-le dans un fichier, copiez-le vers le Presse-papiers, ou envoyez-le par courrier électronique.  
  
## <a name="whats-next"></a>Étape suivante  
 Une fois que l’opération que vous avez configurée s’est correctement déroulée, l’exécution de l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend fin.  
-   Si vous avez exécuté l’opération sur-le-champ, vous pouvez ouvrir la destination que vous avez sélectionnée pour passer en revue les données copiées par l’Assistant.  
-   Si vous avez enregistré le package SSIS créé par l’Assistant, vous pouvez l’ouvrir dans SQL Server Data Tools pour le personnaliser et le réutiliser. Pour plus d’informations sur la façon de personnaliser le package enregistré et de le réexécuter ultérieurement, consultez [Enregistrer le package SSIS](../../integration-services/import-export-data/save-ssis-package-sql-server-import-and-export-wizard.md).

## <a name="see-also"></a>Voir aussi
[Bien démarrer avec cet exemple simple de l’Assistant Importation et Exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)



